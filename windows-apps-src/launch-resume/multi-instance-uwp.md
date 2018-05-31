---
author: TylerMSFT
title: Erstellen einer universellen Windows-App mit mehreren Instanzen
description: In diesem Thema wird beschrieben, wie UWP-Apps erstellt werden, die die Multiinstanzerstellung unterstützen.
keywords: UWP mit mehreren Instanzen
ms.author: twhitney
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 5e0717ac9a2af0a0e1078e39af8f7300ac506823
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816545"
---
# <a name="create-a-multi-instance-universal-windows-app"></a><span data-ttu-id="5e537-104">Erstellen einer universellen Windows-App mit mehreren Instanzen</span><span class="sxs-lookup"><span data-stu-id="5e537-104">Create a multi-instance Universal Windows App</span></span>

<span data-ttu-id="5e537-105">In diesem Thema wird beschrieben, wie Universelle Windows-Plattform (UWP)-Apps mit mehreren Instanzen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="5e537-105">This topic describes how to create multi-instance Universal Windows Platform (UWP) apps.</span></span>

<span data-ttu-id="5e537-106">Vor Windows10, Version 1803, konnten nicht mehrere Instanzen einer UWP-App gleichzeitig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5e537-106">Prior to Windows 10, version 1803, only one instance of a UWP app could be running at a time.</span></span> <span data-ttu-id="5e537-107">Jetzt kann die Unterstützung der UWP-App für mehrere Instanzen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="5e537-107">Now, a UWP app can opt-in to support multiple instances.</span></span> <span data-ttu-id="5e537-108">Wenn eine Instanz einer UWP-App mit mehreren Instanzen ausgeführt wird und eine nachfolgende Aktivierungsanforderung eingeht, wird die vorhandene Instanz von der Plattform nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5e537-108">If an instance of an multi-instance UWP app is running, and a subsequent activation request comes through, the platform will not activate the existing instance.</span></span> <span data-ttu-id="5e537-109">Stattdessen wird eine neue Instanz erstellt, die in einem separaten Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e537-109">Instead, it will create a new instance, running in a separate process.</span></span>

## <a name="opt-in-to-multi-instance-behavior"></a><span data-ttu-id="5e537-110">Teilnahme an Mehrfachinstanz-Verhalten</span><span class="sxs-lookup"><span data-stu-id="5e537-110">Opt-in to multi-instance behavior</span></span>

<span data-ttu-id="5e537-111">Wenn Sie eine neue Multiinstanz-Anwendung erstellen, können Sie die **Mehrfachinstanz-App-Projekt Templates.VSIX** installieren, die im [Visual Studio Marketplace ](https://aka.ms/E2nzbv) erhältlich sind.</span><span class="sxs-lookup"><span data-stu-id="5e537-111">If you are creating a new multi-instance application, you can install the **Multi-Instance App Project Templates.VSIX**, available from the [Visual Studio Marketplace](https://aka.ms/E2nzbv).</span></span> <span data-ttu-id="5e537-112">Nachdem Sie die Vorlagen installieren, sind sie im Dialogfeld **Neues Projekt** Dialogfeld unter **Visual C#-> Windows Universal** (oder **Andere Sprachen > Visual C++ > Windows Universal**) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5e537-112">Once you install the templates, they will be available in the **New Project** dialog under **Visual C# > Windows Universal** (or **Other Languages > Visual C++ > Windows Universal**).</span></span>

<span data-ttu-id="5e537-113">Es werden zwei Vorlagen installiert: **UWP-Apps mit mehreren Instanzen**, die die Vorlage für die Erstellung einer Mulitiinstanz-App bereitstellt sowie **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen), die zusätzlich die Möglichkeit bietet, eine neue Instanz zu starten oder selektiv eine Instanz zu aktivieren, die bereits gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="5e537-113">Two templates are installed: **Multi-Instance UWP app**, which provides the template for creating a multi-instance app, and **Multi-Instance Redirection UWP app**, which provides additional logic that you can build on to either launch a new instance or selectively activate an instance that has already been launched.</span></span> <span data-ttu-id="5e537-114">Wenn beispielsweise ein Dokument in nur einer einzelnen Instanz bearbeitet werden soll, verschieben Sie die Instanz, in der die Datei geöffnet ist, in den Vordergrund, statt eine neue Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5e537-114">For example, perhaps you only want once instance at a time editing the same document, so you bring the instance that has that file open to the foreground rather than launching a new instance.</span></span>

<span data-ttu-id="5e537-115">Beide Vorlagen fügen der Datei „package.appxmanifest” `SupportsMultipleInstances` hinzu.</span><span class="sxs-lookup"><span data-stu-id="5e537-115">Both templates add `SupportsMultipleInstances` to the package.appxmanifest file.</span></span> <span data-ttu-id="5e537-116">Beachten Sie das Namespacepräfix `desktop4`und `iot2`: Nur Projekte, die auf Desktop- oder Internet der Dinge (IoT)-Projekte ausgerichtet sind, bieten Unterstützung für die Multiinstanzerstellung:</span><span class="sxs-lookup"><span data-stu-id="5e537-116">Note the namespace prefix `desktop4` and `iot2`: Only projects that target the desktop, or Internet of Things (IoT) projects support multi-instancing:</span></span>

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

## <a name="multi-instance-activation-redirection"></a><span data-ttu-id="5e537-117">Umleitung der Multiinstanz-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="5e537-117">Multi-instance activation redirection</span></span>

 <span data-ttu-id="5e537-118">Bei der Unterstützung für die Multiinstanzerstellung geht es nicht nur darum, den Start mehrerer Instanzen der App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5e537-118">Multi-instancing support for UWP apps goes beyond simply making it possible to launch multiple instances of the app.</span></span> <span data-ttu-id="5e537-119">Vielmehr bietet sie Ihnen die Möglichkeit auszuwählen, ob eine neue Instanz Ihrer App gestartet oder eine Instanz, die bereits ausgeführt wird, aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="5e537-119">It allows for customization in cases where you want to select whether a new instance of your app is launched or an instance that is already running is activated.</span></span> <span data-ttu-id="5e537-120">Wenn die App beispielsweise gestartet wird, um eine Datei zu bearbeiten, die bereits in einer anderen Instanz bearbeitet wird, können Sie die Aktivierung an die Instanz umleiten, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5e537-120">For example, if the app is launched to edit a file that is already being edited in another instance, you may want to redirect the activation to that instance instead of opening up another instance that  that is already editing the file.</span></span>

<span data-ttu-id="5e537-121">Hier können Sie sich ein Video über das Erstellen von UWP-Konsolen-Apps mit mehreren Instanzen ansehen:</span><span class="sxs-lookup"><span data-stu-id="5e537-121">To see it in action, watch this video about Creating multi-instance UWP apps:</span></span>
> [!VIDEO https://www.youtube.com/embed/clnnf4cigd0]

<span data-ttu-id="5e537-122">Die Vorlage **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen) fügt der Datei „Package.appxmanifest” nicht nur wie oben beschrieben `SupportsMultipleInstances` hinzu, sondern fügt Ihrem Projekt auch die Funktion **Program.cs** (oder **Program.cpp**, wenn Sie die C++-Version der Vorlage verwenden), die eine `Main()`-Funktion enthält.</span><span class="sxs-lookup"><span data-stu-id="5e537-122">The **Multi-Instance Redirection UWP app** template adds `SupportsMultipleInstances` to the package.appxmanifest file as shown above, and also adds a **Program.cs** (or **Program.cpp**, if you are using the C++ version of the template) to your project that contains a `Main()` function.</span></span> <span data-ttu-id="5e537-123">Die Logik für die Umleitung der Aktivierung wird in die `Main`-Funktion eingefügt.</span><span class="sxs-lookup"><span data-stu-id="5e537-123">The logic for redirecting activation goes in the `Main` function.</span></span> <span data-ttu-id="5e537-124">Die Vorlage für **Program.cs** sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5e537-124">The template for **Program.cs** looks like this:</span></span>

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

        // In some scenarios, the platform might indicate a recommended instance.
        // If so, we can redirect this activation to that instance instead, if we wish.
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

`Main()` <span data-ttu-id="5e537-125">ist der erste Schritt, der ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e537-125">is the first thing that runs.</span></span> <span data-ttu-id="5e537-126">Er wird vor [OnLaunched()](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) und [OnActivated ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5e537-126">It runs before [OnLaunched()](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) and [OnActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_).</span></span> <span data-ttu-id="5e537-127">Dadurch können Sie bestimmen, ob Sie diese oder eine andere Instanz aktivieren möchten, bevor irgend ein anderer Initialisierungscode in Ihrer App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e537-127">This allows you to determine whether to activate this, or another instance, before any other initialization code in your app runs.</span></span>

<span data-ttu-id="5e537-128">Der obige Code bestimmt, ob eine vorhandene oder neue Instanz der App aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="5e537-128">The code above determines whether an existing, or new, instance of your application is activated.</span></span> <span data-ttu-id="5e537-129">Um festzustellen, ob eine vorhandene Instanz aktiviert werden kann, wird ein Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="5e537-129">A key is used to determine whether there is an existing instance that you want to activate.</span></span> <span data-ttu-id="5e537-130">Wenn Ihre App beispielsweise nach [Behandeln der Dateiaktivierung](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation) gestartet wird, können Sie den Namen der Datei als Schlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="5e537-130">For example, if your app can be launched to [Handle file activation](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation), you might use the file name as a key.</span></span> <span data-ttu-id="5e537-131">Anschließend können Sie überprüfen, ob bereits eine Instanz Ihrer App mit diesem Schlüssel registriert ist, und sie aktivieren, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5e537-131">Then you can check whether an instance of your app is already registered with that key and activate it instead of opening a new instance.</span></span> <span data-ttu-id="5e537-132">Der Code erfüllt den folgenden Sinn:</span><span class="sxs-lookup"><span data-stu-id="5e537-132">This is the idea behind the code:</span></span> `var instance = AppInstance.FindOrRegisterInstanceForKey(key);`

<span data-ttu-id="5e537-133">Wenn eine Instanz gefunden wird, die bereits mit dem Schlüssel registriert ist, wird diese Instanz aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5e537-133">If an instance registered with the key is found, then that instance is activated.</span></span> <span data-ttu-id="5e537-134">Wenn der Schlüssel nicht gefunden wird, erstellt die aktuelle Instanz (die Instanz, die zurzeit `Main` ausführt) ihr Anwendungsobjekt und wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="5e537-134">If the key is not found, then the current instance (the instance that is currently running `Main`) creates its application object  and starts running.</span></span>


## <a name="background-tasks-and-multi-instancing"></a><span data-ttu-id="5e537-135">Hintergrundaufgaben und die Multiinstanzerstellung</span><span class="sxs-lookup"><span data-stu-id="5e537-135">Background tasks and multi-instancing</span></span>

- <span data-ttu-id="5e537-136">Hintergrundaufgaben außerhalb von Prozessen bieten Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5e537-136">Out-of-proc background tasks support multi-instancing.</span></span> <span data-ttu-id="5e537-137">Jeder neuer Trigger führt in der Regel zu einer neue Instanz der Hintergrundaufgabe (obwohl technisch gesehen mehrere Hintergrundaufgaben in demselben Hostprozess ausgeführt werden können).</span><span class="sxs-lookup"><span data-stu-id="5e537-137">Typically, each new trigger results in a new instance of the background task (although technically speaking multiple background tasks may run in same host process).</span></span> <span data-ttu-id="5e537-138">Dennoch wird eine neue Instanz der Hintergrundaufgabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="5e537-138">Nevertheless, a different instance of the background task is created.</span></span>
- <span data-ttu-id="5e537-139">Hintergrundaufgaben innerhalb von Prozessen bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5e537-139">In-proc background tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="5e537-140">Audiohintergrundaufgaben bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5e537-140">Background audio tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="5e537-141">Wenn eine App eine Hintergrundaufgabe registriert , wird in der Regel zuerst überprüft, ob die Aufgabe bereits registriert ist. Gegebenenfalls wird die Aufgabe dann gelöscht, erneut registriert oder es wird keine Aktion ausgeführt, um die vorhandenen Registrierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5e537-141">When an app registers a background task, it usually first checks to see if the task is already registered and then either deletes and re-registers it, or does nothing in order to keep the existing registration.</span></span> <span data-ttu-id="5e537-142">Mit Mehrfachinstanz-Apps verhält es sich normalerweise genauso.</span><span class="sxs-lookup"><span data-stu-id="5e537-142">This is still the typical behavior with multi-instance apps.</span></span> <span data-ttu-id="5e537-143">Jedoch kann eine App mit Multiinstanzerstellung den Namen einer anderen Hintergrundaufgabe pro Instanz registrieren.</span><span class="sxs-lookup"><span data-stu-id="5e537-143">However, a multi-instancing app may choose to register a different background task name on a per-instance basis.</span></span> <span data-ttu-id="5e537-144">Dies führt zu mehrfachen Registrierungen für einen Trigger, sodass mehrere Instanzen von Hintergrundaufgaben aktiviert werden, wenn der Trigger ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5e537-144">This will result in multiple registrations for the same trigger, and multiple background task instances will be activated when the trigger fires.</span></span>
- <span data-ttu-id="5e537-145">App-Dienste starten für jede Verbindung eine separate Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="5e537-145">App-services launch a separate instance of the app-service background task for every connection.</span></span> <span data-ttu-id="5e537-146">Dies bleibt im Falle von Apps mit mehreren Instanzen unverändert, d.h. jede Instanz einer Mehrfachinstanz-App erhält eine eigene Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="5e537-146">This remains unchanged for multi-instance apps, that is each instance of a multi-instance app will get its own instance of the  app-service background task.</span></span> 

## <a name="additional-considerations"></a><span data-ttu-id="5e537-147">Weitere Überlegungen</span><span class="sxs-lookup"><span data-stu-id="5e537-147">Additional considerations</span></span>

- <span data-ttu-id="5e537-148">Die Multiinstanzerstellung wird von UWP-Apps unterstützt, die auf Desktop- und Internet der Dinge (IoT)-Projekte ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="5e537-148">Multi-instancing is supported by UWP apps that target desktop and Internet of Things (IoT) projects.</span></span>
- <span data-ttu-id="5e537-149">Um Racebedingungen und Dateizugriffskonflike zu vermeiden, müssen Apps mit mehreren Instanzen Maßnahmen für die Partition/Synchronisierung des Zugriffs auf Einstellungen, lokalen App-Speicher und andere Ressourcen (z.B. Benutzerdateien, Datenspeicher usw.) sorgen, die von mehreren Instanzen gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="5e537-149">To avoid race-conditions and contention issues, multi-instance apps need to take steps to partition/synchronize access to settings, app-local storage, and any other resource (such as user files, a data store, and so on) that can be shared among multiple instances.</span></span> <span data-ttu-id="5e537-150">Standard-Synchronisierungsmechanismen wie Mutexe, Semaphoren, Ereignisse usw., sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5e537-150">Standard synchronization mechanisms such as mutexes, semaphores, events, and and so on, are available.</span></span>
- <span data-ttu-id="5e537-151">Wenn in der Datei „Package.appxmanifest” der App `SupportsMultipleInstances` enthalten ist, müssen ihre Erweiterungen nicht `SupportsMultipleInstances` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="5e537-151">If the app has `SupportsMultipleInstances` in its Package.appxmanifest file, then its extensions do not need to declare `SupportsMultipleInstances`.</span></span> 
- <span data-ttu-id="5e537-152">Wenn Sie einer anderen Erweiterung außer Hintergrundaufgaben oder App-Diensten `SupportsMultipleInstances` hinzufügen und die App, die die Erweiterung hostet, in ihrer Datei „Package.appxmanifest” nicht auch `SupportsMultipleInstances` deklariert, wird ein Schemafehler generiert.</span><span class="sxs-lookup"><span data-stu-id="5e537-152">If you add `SupportsMultipleInstances` to any other extension, apart from background tasks or app-services, and the app that hosts the extension doesn't also declare `SupportsMultipleInstances` in its Package.appxmanifest file, then a schema error is generated.</span></span>
- <span data-ttu-id="5e537-153">Apps können die [ResourceGroup](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)-Deklaration in ihrer Manifestdatei dazu verwenden, mehrere Hintergrundaufgaben im gleichen Host zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="5e537-153">Apps can use the [ResourceGroup](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) declaration in their manifest to group multiple background tasks into the same host.</span></span> <span data-ttu-id="5e537-154">Dies steht im Konflikt mit der Multiinstanzerstellung, da dort jede Aktivierung in einen separaten Host wechselt.</span><span class="sxs-lookup"><span data-stu-id="5e537-154">This conflicts with multi-instancing, where each activation goes into a separate host.</span></span> <span data-ttu-id="5e537-155">Eine App kann deshalb in der Manifestdatei nicht sowohl `SupportsMultipleInstances`, als auch `ResourceGroup` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="5e537-155">Therefore an app cannot declare both `SupportsMultipleInstances` and `ResourceGroup` in their manifest.</span></span>

## <a name="sample"></a><span data-ttu-id="5e537-156">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5e537-156">Sample</span></span>

<span data-ttu-id="5e537-157">Unter [Beispiel für Multiinstanz](https://aka.ms/Kcrqst) finden Sie ein Beispiel für die Umleitung einer Multiinstanz-Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="5e537-157">See [Multi-Instance sample](https://aka.ms/Kcrqst) for an example of Multi-instance activation redirection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e537-158">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5e537-158">See also</span></span>

<span data-ttu-id="5e537-159">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span><span class="sxs-lookup"><span data-stu-id="5e537-159">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span></span>