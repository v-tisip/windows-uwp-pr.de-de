---
author: TylerMSFT
title: Erstellen einer universellen Windows-App mit mehreren Instanzen
description: In diesem Thema wird beschrieben, wie UWP-Apps erstellt werden, die die Multiinstanzerstellung unterstützen.
keywords: UWP mit mehreren Instanzen
ms.author: twhitney
ms.date: 09/21/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 8729ec5219159884ae0e99d8cc6eaa8dbe900d90
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5563539"
---
# <a name="create-a-multi-instance-universal-windows-app"></a>Erstellen einer universellen Windows-App mit mehreren Instanzen

In diesem Thema wird beschrieben, wie Universelle Windows-Plattform (UWP)-Apps mit mehreren Instanzen erstellt werden.

Von Windows 10, Version 1803 (10.0; Build 17134) ideenreicher, Ihre UWP-app kann entscheiden Sie sich für mehrere Instanzen zu unterstützen. Wenn eine Instanz einer UWP-App mit mehreren Instanzen ausgeführt wird und eine nachfolgende Aktivierungsanforderung eingeht, wird die vorhandene Instanz von der Plattform nicht aktiviert. Stattdessen wird eine neue Instanz erstellt, die in einem separaten Prozess ausgeführt wird.

> [!IMPORTANT]
> Für die multiinstanzerstellung wird für JavaScript-Anwendungen unterstützt, für die multiinstanzerstellung Umleitung ist jedoch nicht. Da für die multiinstanzerstellung Umleitung für JavaScript-Anwendungen nicht unterstützt wird, ist die [**AppInstance**](/uwp/api/windows.applicationmodel.appinstance) -Klasse nicht nützlich für solche Anwendungen.

## <a name="opt-in-to-multi-instance-behavior"></a>Melden Sie sich für Mehrfachinstanz-Verhalten

Wenn Sie eine neue Multiinstanz-Anwendung erstellen, können Sie die **Mehrfachinstanz-App-Projekt Templates.VSIX** installieren, die im [Visual Studio Marketplace ](https://aka.ms/E2nzbv) erhältlich sind. Nachdem Sie die Vorlagen installieren, sind sie im Dialogfeld **Neues Projekt** Dialogfeld unter **Visual C#-> Windows Universal** (oder **Andere Sprachen > Visual C++ > Windows Universal**) verfügbar.

Es werden zwei Vorlagen installiert: **UWP-Apps mit mehreren Instanzen**, die die Vorlage für die Erstellung einer Mulitiinstanz-App bereitstellt sowie **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen), die zusätzlich die Möglichkeit bietet, eine neue Instanz zu starten oder selektiv eine Instanz zu aktivieren, die bereits gestartet wurde. Wenn beispielsweise ein Dokument in nur einer einzelnen Instanz bearbeitet werden soll, verschieben Sie die Instanz, in der die Datei geöffnet ist, in den Vordergrund, statt eine neue Instanz zu erstellen.

Beide Vorlagen fügen `SupportsMultipleInstances` für die `package.appxmanifest` Datei. Beachten Sie das Namespacepräfix `desktop4` und `iot2`: nur Projekte, die auf den Desktop abzielen oder Internet der Dinge (IoT)-Projekte, bieten Unterstützung für die multiinstanzerstellung.

```xml
<Package
  ...
  xmlns:desktop4="http://schemas.microsoft.com/appx/manifest/desktop/windows10/4"
  xmlns:iot2="http://schemas.microsoft.com/appx/manifest/iot/windows10/2"  
  IgnorableNamespaces="uap mp desktop4 iot2">
  ...
  <Applications>
    <Application Id="App"
      ...
      desktop4:SupportsMultipleInstances="true"
      iot2:SupportsMultipleInstances="true">
      ...
    </Application>
  </Applications>
   ...
</Package>
```

## <a name="multi-instance-activation-redirection"></a>Umleitung der Multiinstanz-Aktivierung

 Bei der Unterstützung für die Multiinstanzerstellung geht es nicht nur darum, den Start mehrerer Instanzen der App zu ermöglichen. Vielmehr bietet sie Ihnen die Möglichkeit auszuwählen, ob eine neue Instanz Ihrer App gestartet oder eine Instanz, die bereits ausgeführt wird, aktiviert werden soll. Wenn die App beispielsweise gestartet wird, um eine Datei zu bearbeiten, die bereits in einer anderen Instanz bearbeitet wird, können Sie die Aktivierung an die Instanz umleiten, statt eine neue Instanz zu öffnen.

Um dies in Aktion zu sehen, sehen Sie sich ein Video zum Erstellen von UWP-apps mit mehreren Instanzen an.

> [!VIDEO https://www.youtube.com/embed/clnnf4cigd0]

Die Vorlage **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen) fügt der Datei „Package.appxmanifest” nicht nur wie oben beschrieben `SupportsMultipleInstances` hinzu, sondern fügt Ihrem Projekt auch die Funktion **Program.cs** (oder **Program.cpp**, wenn Sie die C++-Version der Vorlage verwenden), die eine `Main()`-Funktion enthält. Die Logik für die Umleitung der Aktivierung wird in die `Main`-Funktion eingefügt. Die Vorlage für **Program.cs** ist unten dargestellt.

Die Eigenschaft [**AppInstance.RecommendedInstance**](/uwp/api/windows.applicationmodel.appinstance.recommendedinstance) stellt die Shell bereitgestellten bevorzugte Instanz für diese aktivierungsanforderung dar, sofern vorhanden (oder `null` kein Computerkonto vorhanden ist). Wenn die Shell eine Einstellung enthält, klicken Sie können können Aktivierung an die Instanz umleiten oder kann ignoriert werden, wenn Sie sich entscheiden.

``` csharp
public static class Program
{
    // This example code shows how you could implement the required Main method to
    // support multi-instance redirection. The minimum requirement is to call
    // Application.Start with a new App object. Beyond that, you may delete the
    // rest of the example code and replace it with your custom code if you wish.

    static void Main(string[] args)
    {
        // First, we'll get our activation event args, which are typically richer
        // than the incoming command-line args. We can use these in our app-defined
        // logic for generating the key for this instance.
        IActivatedEventArgs activatedArgs = AppInstance.GetActivatedEventArgs();

        // If the Windows shell indicates a recommended instance, then
        // the app can choose to redirect this activation to that instance instead.
        if (AppInstance.RecommendedInstance != null)
        {
            AppInstance.RecommendedInstance.RedirectActivationTo();
        }
        else
        {
            // Define a key for this instance, based on some app-specific logic.
            // If the key is always unique, then the app will never redirect.
            // If the key is always non-unique, then the app will always redirect
            // to the first instance. In practice, the app should produce a key
            // that is sometimes unique and sometimes not, depending on its own needs.
            string key = Guid.NewGuid().ToString(); // always unique.
                                                    //string key = "Some-App-Defined-Key"; // never unique.
            var instance = AppInstance.FindOrRegisterInstanceForKey(key);
            if (instance.IsCurrentInstance)
            {
                // If we successfully registered this instance, we can now just
                // go ahead and do normal XAML initialization.
                global::Windows.UI.Xaml.Application.Start((p) => new App());
            }
            else
            {
                // Some other instance has registered for this key, so we'll 
                // redirect this activation to that instance instead.
                instance.RedirectActivationTo();
            }
        }
    }
}
```

`Main()` ist der erste Schritt, der ausgeführt wird. Es wird vor [**OnLaunched**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) und [**OnActivated**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_)ausgeführt. Dadurch können Sie bestimmen, ob Sie diese oder eine andere Instanz aktivieren möchten, bevor irgend ein anderer Initialisierungscode in Ihrer App ausgeführt wird.

Der obige Code bestimmt, ob eine vorhandene oder neue Instanz der App aktiviert wird. Um festzustellen, ob eine vorhandene Instanz aktiviert werden kann, wird ein Schlüssel verwendet. Wenn Ihre App beispielsweise nach [Behandeln der Dateiaktivierung](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation) gestartet wird, können Sie den Namen der Datei als Schlüssel verwenden. Anschließend können Sie überprüfen, ob bereits eine Instanz Ihrer App mit diesem Schlüssel registriert ist, und sie aktivieren, statt eine neue Instanz zu öffnen. Der Code erfüllt den folgenden Sinn: `var instance = AppInstance.FindOrRegisterInstanceForKey(key);`

Wenn eine Instanz gefunden wird, die bereits mit dem Schlüssel registriert ist, wird diese Instanz aktiviert. Wenn der Schlüssel nicht gefunden wird, erstellt die aktuelle Instanz (die Instanz, die zurzeit `Main` ausführt) ihr Anwendungsobjekt und wird gestartet.

## <a name="background-tasks-and-multi-instancing"></a>Hintergrundaufgaben und die Multiinstanzerstellung

- Hintergrundaufgaben außerhalb von Prozessen bieten Unterstützung für die Multiinstanzerstellung. Jeder neuer Trigger führt in der Regel zu einer neue Instanz der Hintergrundaufgabe (obwohl technisch gesehen mehrere Hintergrundaufgaben in demselben Hostprozess ausgeführt werden können). Dennoch wird eine neue Instanz der Hintergrundaufgabe erstellt.
- Hintergrundaufgaben innerhalb von Prozessen bieten keine Unterstützung für die Multiinstanzerstellung.
- Audiohintergrundaufgaben bieten keine Unterstützung für die Multiinstanzerstellung.
- Wenn eine App eine Hintergrundaufgabe registriert , wird in der Regel zuerst überprüft, ob die Aufgabe bereits registriert ist. Gegebenenfalls wird die Aufgabe dann gelöscht, erneut registriert oder es wird keine Aktion ausgeführt, um die vorhandenen Registrierung zu erhalten. Mit Mehrfachinstanz-Apps verhält es sich normalerweise genauso. Jedoch kann eine App mit Multiinstanzerstellung den Namen einer anderen Hintergrundaufgabe pro Instanz registrieren. Dies führt zu mehrfachen Registrierungen für einen Trigger, sodass mehrere Instanzen von Hintergrundaufgaben aktiviert werden, wenn der Trigger ausgelöst wird.
- App-Dienste starten für jede Verbindung eine separate Instanz der Hintergrundaufgabe des App-Dienstes. Dies bleibt im Falle von Apps mit mehreren Instanzen unverändert, d.h. jede Instanz einer Mehrfachinstanz-App erhält eine eigene Instanz der Hintergrundaufgabe des App-Dienstes. 

## <a name="additional-considerations"></a>Weitere Überlegungen

- Die Multiinstanzerstellung wird von UWP-Apps unterstützt, die auf Desktop- und Internet der Dinge (IoT)-Projekte ausgerichtet sind.
- Um Racebedingungen und Dateizugriffskonflike zu vermeiden, müssen Apps mit mehreren Instanzen Maßnahmen für die Partition/Synchronisierung des Zugriffs auf Einstellungen, lokalen App-Speicher und andere Ressourcen (z.B. Benutzerdateien, Datenspeicher usw.) sorgen, die von mehreren Instanzen gemeinsam genutzt werden können. Standard-Synchronisierungsmechanismen wie Mutexe, Semaphoren, Ereignisse usw., sind verfügbar.
- Wenn in der Datei „Package.appxmanifest” der App `SupportsMultipleInstances` enthalten ist, müssen ihre Erweiterungen nicht `SupportsMultipleInstances` deklarieren. 
- Wenn Sie einer anderen Erweiterung außer Hintergrundaufgaben oder App-Diensten `SupportsMultipleInstances` hinzufügen und die App, die die Erweiterung hostet, in ihrer Datei „Package.appxmanifest” nicht auch `SupportsMultipleInstances` deklariert, wird ein Schemafehler generiert.
- Apps können die [**ResourceGroup**](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) -Deklaration im Manifest verwenden, um mehrere Hintergrundaufgaben im gleichen Host zu gruppieren. Dies steht im Konflikt mit der Multiinstanzerstellung, da dort jede Aktivierung in einen separaten Host wechselt. Eine App kann deshalb in der Manifestdatei nicht sowohl `SupportsMultipleInstances`, als auch `ResourceGroup` deklarieren.

## <a name="sample"></a>Beispiel

Finden Sie ein Beispiel für die Umleitung der multiinstanz-Aktivierung- [Beispiel mit mehreren Instanzen](https://aka.ms/Kcrqst) .

## <a name="see-also"></a>Weitere Informationen:

[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)