---
author: TylerMSFT
title: Behandeln des Anhaltens von Apps
description: Hier erfahren Sie, wie Sie wichtige Anwendungsdaten speichern, wenn das System die App anhält.
ms.assetid: F84F1512-24B9-45EC-BF23-A09E0AC985B0
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- vb
- cppwinrt
- cpp
ms.openlocfilehash: 7cb93c410f583884f75f21d9beda03db87c024f9
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6191268"
---
# <a name="handle-app-suspend"></a>Behandeln des Anhaltens von Apps

**Wichtige APIs**

- [**Anhalten**](https://msdn.microsoft.com/library/windows/apps/br242341)

Hier erfahren Sie, wie Sie wichtige Anwendungsdaten speichern, wenn das System die App anhält. Im Beispiel wird ein Ereignishandler für das [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignis registriert und eine Zeichenfolge in einer Datei gespeichert.

## <a name="register-the-suspending-event-handler"></a>Registrieren des Suspending-Ereignishandlers

Registrieren Sie die Behandlung des [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignisses, das angibt, dass die App ihre Anwendungsdaten speichern sollte, bevor sie vom System angehalten wird.

```csharp
using System;
using Windows.ApplicationModel;
using Windows.ApplicationModel.Activation;
using Windows.UI.Xaml;

partial class MainPage
{
   public MainPage()
   {
      InitializeComponent();
      Application.Current.Suspending += new SuspendingEventHandler(App_Suspending);
   }
}
```

```vb
Public NotInheritable Class MainPage

   Public Sub New()
      InitializeComponent()
      AddHandler Application.Current.Suspending, AddressOf App_Suspending
   End Sub
   
End Class
```

```cppwinrt
MainPage::MainPage()
{
    InitializeComponent();
    Windows::UI::Xaml::Application::Current().Suspending({ this, &MainPage::App_Suspending });
}
```

```cpp
using namespace Windows::ApplicationModel;
using namespace Windows::ApplicationModel::Activation;
using namespace Windows::Foundation;
using namespace Windows::UI::Xaml;
using namespace AppName;

MainPage::MainPage()
{
   InitializeComponent();
   Application::Current->Suspending +=
       ref new SuspendingEventHandler(this, &MainPage::App_Suspending);
}
```

## <a name="save-application-data-before-suspension"></a>Speichern von App-Daten vor dem Anhalten

Wenn die App das [**Suspending**](https://msdn.microsoft.com/library/windows/apps/br242341)-Ereignis behandelt, kann sie die wichtigen App-Daten in der Handlerfunktion speichern. Die App sollte die [**LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622)-Speicher-API verwenden, um einfache Anwendungsdaten synchron zu speichern.

```csharp
partial class MainPage
{
    async void App_Suspending(
        Object sender,
        Windows.ApplicationModel.SuspendingEventArgs e)
    {
        // TODO: This is the time to save app data in case the process is terminated.
    }
}
```

```vb
Public NonInheritable Class MainPage

    Private Sub App_Suspending(
        sender As Object,
        e As Windows.ApplicationModel.SuspendingEventArgs) Handles OnSuspendEvent.Suspending

        ' TODO: This is the time to save app data in case the process is terminated.
    End Sub

End Class
```

```cppwinrt
void MainPage::App_Suspending(
    Windows::Foundation::IInspectable const& /* sender */,
    Windows::ApplicationModel::SuspendingEventArgs const& /* e */)
{
    // TODO: This is the time to save app data in case the process is terminated.
}
```

```cpp
void MainPage::App_Suspending(Object^ sender, SuspendingEventArgs^ e)
{
    // TODO: This is the time to save app data in case the process is terminated.
}
```

## <a name="release-resources"></a>Freigeben von Ressourcen

Sie sollten exklusive Ressourcen und Dateihandles freigeben, damit andere Apps darauf zugreifen können, während Ihre App angehalten wird. Beispiele für exklusive Ressourcen sind Kameras, E/A-Geräte, externe Geräte und Netzwerkressourcen. Durch die explizite Freigabe exklusiver Ressourcen und Dateihandles kann sichergestellt werden, dass andere Apps darauf zugreifen können, während Ihre App angehalten ist. Wenn die App fortgesetzt wird, sollte sie ihre exklusiven Ressourcen und Dateihandles erneut abrufen.

## <a name="remarks"></a>Anmerkungen

Das System hält Ihre App an, wenn der Benutzer zu einer anderen App oder zum Desktop bzw. Startbildschirm wechselt. Wenn der Benutzer wieder zu Ihrer App wechselt, wird diese vom System fortgesetzt. Beim Fortsetzen der App haben die Variablen und Datenstrukturen den gleichen Inhalt wie vor der Unterbrechung. Das System stellt die App exakt so wieder her, wie sie unterbrochen wurde. Dadurch entsteht für den Benutzer der Eindruck, die App wäre im Hintergrund weiter ausgeführt worden.

Das System versucht, die App und die dazugehörigen Daten zu speichern, während sie angehalten ist. Wenn das System aber nicht über die notwendigen Ressourcen verfügt, um die App im Arbeitsspeicher zu behalten, beendet es die App. Wenn der Benutzer wieder zu einer angehaltenen App wechselt, die beendet wurde, sendet das System ein [**Activated**](https://msdn.microsoft.com/library/windows/apps/br225018)-Ereignis, und es sollte die App-Daten in der [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335)-Methode wiederherstellen.

Das System benachrichtigt eine App nicht, wenn sie beendet wird. Wenn Ihre App angehalten wird, muss sie daher die App-Daten speichern und die exklusiven Ressourcen und Dateihandles freigeben, damit diese beim erneuten Aktivieren der App nach der Beendigung wiederhergestellt werden können.

Wenn Sie innerhalb Ihres Handlers einen asynchronen Aufruf ausführen, wird die Steuerung sofort von diesem asynchronen Aufruf zurückgegeben. Das bedeutet, dass die Ausführung dann vom Ereignishandler zurückgegeben werden kann und die App in den nächsten Zustand übergeht, obwohl der asynchrone Aufruf noch nicht abgeschlossen wurde. Verwenden Sie die [**GetDeferral**](http://aka.ms/Kt66iv)-Methode für das an den Ereignishandler übergebene [**EnteredBackgroundEventArgs**](http://aka.ms/Ag2yh4)-Objekt, um das Anhalten zu verzögern, bis Sie für das zurückgegebene [**Windows.Foundation.Deferral**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.aspx)-Objekt die [**Complete**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.complete.aspx)-Methode aufgerufen haben.

Durch eine Verzögerung verlängert sich nicht die Zeit, die Ihr Code ausgeführt werden muss, bevor die App beendet wird. Dabei wird nur die Beendigung verzögert, bis die *Complete*-Methode der Verzögerung aufgerufen wird oder die Frist abläuft, *je nachdem, was zuerst eintritt*. Zeit verwendeter Zustand angehalten [ **ExtendedExecutionSession** erweitern](run-minimized-with-extended-execution.md)

> [!NOTE]
> Zum Verbessern der Reaktionsfähigkeit des Systems in Windows8.1 sind apps mit niedriger Prioritätszugriff auf Ressourcen gewährt, nachdem sie angehalten wurden. Zur Unterstützung dieser neuen Priorität wird das Timeout für den Anhaltevorgang ausgedehnt, sodass die App für normale Priorität unter Windows über einen 5-Sekunden-Timeout und unter WindowsPhone über einen Timeout von 1 bis 10Sekunden verfügt. Dieses Timeout-Fenster kann weder verlängert noch geändert werden.

**Hinweis zum Debuggen mit Visual Studio:** Visual Studio verhindert, dass in Windows eine an den Debugger angefügte App angehalten wird. Dies hat den Zweck, dem Benutzer das Anzeigen der Debugging-Benutzeroberfläche von Visual Studio zu ermöglichen, während die App ausgeführt wird. Beim Debuggen einer App können Sie mit VisualStudio ein Anhalteereignis an die App senden. Stellen Sie sicher, dass die Symbolleiste **Debugspeicherort** angezeigt wird, und klicken Sie dann auf das Symbol **Anhalten**.

## <a name="related-topics"></a>Verwandte Themen

* [App-Lebenszyklus](app-lifecycle.md)
* [Behandeln der App-Aktivierung](activate-an-app.md)
* [Behandeln der App-Fortsetzung](resume-an-app.md)
* [UX-Richtlinien für das Starten, Anhalten und Fortsetzen von Apps](https://msdn.microsoft.com/library/windows/apps/dn611862)
* [Erweiterte Ausführung](run-minimized-with-extended-execution.md)

 

 
