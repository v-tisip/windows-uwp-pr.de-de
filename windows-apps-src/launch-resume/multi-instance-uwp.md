---
author: TylerMSFT
title: Erstellen einer universellen Windows-App mit mehreren Instanzen
description: In diesem Thema wird beschrieben, wie UWP-Apps erstellt werden, die die Multiinstanzerstellung unterstützen.
keywords: UWP mit mehreren Instanzen
ms.author: twhitney
ms.date: 09/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 9302ed0375739153eb95ac2b54c1ed396b14daee
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4126995"
---
# <a name="create-a-multi-instance-universal-windows-app"></a><span data-ttu-id="5db57-104">Erstellen einer universellen Windows-App mit mehreren Instanzen</span><span class="sxs-lookup"><span data-stu-id="5db57-104">Create a multi-instance Universal Windows App</span></span>

<span data-ttu-id="5db57-105">In diesem Thema wird beschrieben, wie Universelle Windows-Plattform (UWP)-Apps mit mehreren Instanzen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="5db57-105">This topic describes how to create multi-instance Universal Windows Platform (UWP) apps.</span></span>

<span data-ttu-id="5db57-106">Von Windows 10, Version 1803 (10.0; Build 17134) ideenreicher, Ihre UWP-app kann entscheiden Sie sich für mehrere Instanzen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5db57-106">From Windows 10, version 1803 (10.0; Build 17134) onward, your UWP app can opt in to support multiple instances.</span></span> <span data-ttu-id="5db57-107">Wenn eine Instanz einer UWP-App mit mehreren Instanzen ausgeführt wird und eine nachfolgende Aktivierungsanforderung eingeht, wird die vorhandene Instanz von der Plattform nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5db57-107">If an instance of an multi-instance UWP app is running, and a subsequent activation request comes through, the platform will not activate the existing instance.</span></span> <span data-ttu-id="5db57-108">Stattdessen wird eine neue Instanz erstellt, die in einem separaten Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5db57-108">Instead, it will create a new instance, running in a separate process.</span></span>

## <a name="opt-in-to-multi-instance-behavior"></a><span data-ttu-id="5db57-109">Melden Sie sich für Mehrfachinstanz-Verhalten</span><span class="sxs-lookup"><span data-stu-id="5db57-109">Opt in to multi-instance behavior</span></span>

<span data-ttu-id="5db57-110">Wenn Sie eine neue Multiinstanz-Anwendung erstellen, können Sie die **Mehrfachinstanz-App-Projekt Templates.VSIX** installieren, die im [Visual Studio Marketplace ](https://aka.ms/E2nzbv) erhältlich sind.</span><span class="sxs-lookup"><span data-stu-id="5db57-110">If you are creating a new multi-instance application, you can install the **Multi-Instance App Project Templates.VSIX**, available from the [Visual Studio Marketplace](https://aka.ms/E2nzbv).</span></span> <span data-ttu-id="5db57-111">Nachdem Sie die Vorlagen installieren, sind sie im Dialogfeld **Neues Projekt** Dialogfeld unter **Visual C#-> Windows Universal** (oder **Andere Sprachen > Visual C++ > Windows Universal**) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5db57-111">Once you install the templates, they will be available in the **New Project** dialog under **Visual C# > Windows Universal** (or **Other Languages > Visual C++ > Windows Universal**).</span></span>

<span data-ttu-id="5db57-112">Es werden zwei Vorlagen installiert: **UWP-Apps mit mehreren Instanzen**, die die Vorlage für die Erstellung einer Mulitiinstanz-App bereitstellt sowie **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen), die zusätzlich die Möglichkeit bietet, eine neue Instanz zu starten oder selektiv eine Instanz zu aktivieren, die bereits gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="5db57-112">Two templates are installed: **Multi-Instance UWP app**, which provides the template for creating a multi-instance app, and **Multi-Instance Redirection UWP app**, which provides additional logic that you can build on to either launch a new instance or selectively activate an instance that has already been launched.</span></span> <span data-ttu-id="5db57-113">Wenn beispielsweise ein Dokument in nur einer einzelnen Instanz bearbeitet werden soll, verschieben Sie die Instanz, in der die Datei geöffnet ist, in den Vordergrund, statt eine neue Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5db57-113">For example, perhaps you only want once instance at a time editing the same document, so you bring the instance that has that file open to the foreground rather than launching a new instance.</span></span>

<span data-ttu-id="5db57-114">Beide Vorlagen fügen `SupportsMultipleInstances` auf die `package.appxmanifest` Datei.</span><span class="sxs-lookup"><span data-stu-id="5db57-114">Both templates add `SupportsMultipleInstances` to the `package.appxmanifest` file.</span></span> <span data-ttu-id="5db57-115">Beachten Sie das Namespacepräfix `desktop4` und `iot2`: nur Projekte, die auf den Desktop abzielen oder Internet der Dinge (IoT)-Projekte, bieten Unterstützung für die multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5db57-115">Note the namespace prefix `desktop4` and `iot2`: only projects that target the desktop, or Internet of Things (IoT) projects, support multi-instancing.</span></span>

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

## <a name="multi-instance-activation-redirection"></a><span data-ttu-id="5db57-116">Umleitung der Multiinstanz-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="5db57-116">Multi-instance activation redirection</span></span>

 <span data-ttu-id="5db57-117">Bei der Unterstützung für die Multiinstanzerstellung geht es nicht nur darum, den Start mehrerer Instanzen der App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5db57-117">Multi-instancing support for UWP apps goes beyond simply making it possible to launch multiple instances of the app.</span></span> <span data-ttu-id="5db57-118">Vielmehr bietet sie Ihnen die Möglichkeit auszuwählen, ob eine neue Instanz Ihrer App gestartet oder eine Instanz, die bereits ausgeführt wird, aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="5db57-118">It allows for customization in cases where you want to select whether a new instance of your app is launched or an instance that is already running is activated.</span></span> <span data-ttu-id="5db57-119">Wenn die App beispielsweise gestartet wird, um eine Datei zu bearbeiten, die bereits in einer anderen Instanz bearbeitet wird, können Sie die Aktivierung an die Instanz umleiten, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5db57-119">For example, if the app is launched to edit a file that is already being edited in another instance, you may want to redirect the activation to that instance instead of opening up another instance that  that is already editing the file.</span></span>

<span data-ttu-id="5db57-120">Um es in Aktion zu sehen, sehen Sie sich ein Video zum Erstellen von UWP-apps mit mehreren Instanzen an.</span><span class="sxs-lookup"><span data-stu-id="5db57-120">To see it in action, watch this video about Creating multi-instance UWP apps.</span></span>

> [!VIDEO https://www.youtube.com/embed/clnnf4cigd0]

<span data-ttu-id="5db57-121">Die Vorlage **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen) fügt der Datei „Package.appxmanifest” nicht nur wie oben beschrieben `SupportsMultipleInstances` hinzu, sondern fügt Ihrem Projekt auch die Funktion **Program.cs** (oder **Program.cpp**, wenn Sie die C++-Version der Vorlage verwenden), die eine `Main()`-Funktion enthält.</span><span class="sxs-lookup"><span data-stu-id="5db57-121">The **Multi-Instance Redirection UWP app** template adds `SupportsMultipleInstances` to the package.appxmanifest file as shown above, and also adds a **Program.cs** (or **Program.cpp**, if you are using the C++ version of the template) to your project that contains a `Main()` function.</span></span> <span data-ttu-id="5db57-122">Die Logik für die Umleitung der Aktivierung wird in die `Main`-Funktion eingefügt.</span><span class="sxs-lookup"><span data-stu-id="5db57-122">The logic for redirecting activation goes in the `Main` function.</span></span> <span data-ttu-id="5db57-123">Die Vorlage für **Program.cs** sieht folgendermaßen aus.</span><span class="sxs-lookup"><span data-stu-id="5db57-123">The template for **Program.cs** is shown below.</span></span>

<span data-ttu-id="5db57-124">Die Eigenschaft [AppInstance.RecommendedInstance](/uwp/api/windows.applicationmodel.appinstance.recommendedinstance) stellt die Shell bereitgestellten bevorzugte Instanz für diese aktivierungsanforderung dar, sofern vorhanden (oder `null` Wenn nicht vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="5db57-124">The [AppInstance.RecommendedInstance](/uwp/api/windows.applicationmodel.appinstance.recommendedinstance) property represents the shell-provided preferred instance for this activation request, if there is one (or `null` if there isn't one).</span></span> <span data-ttu-id="5db57-125">Wenn die Shell eine Einstellung enthält, dann Sie können können Aktivierung an die Instanz umleiten oder kann ignoriert werden, wenn Sie auswählen.</span><span class="sxs-lookup"><span data-stu-id="5db57-125">If the shell provides a preference, then you can can redirect activation to that instance, or you can ignore it if you choose.</span></span>

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

`Main()` <span data-ttu-id="5db57-126">ist der erste Schritt, der ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5db57-126">is the first thing that runs.</span></span> <span data-ttu-id="5db57-127">Er wird vor [OnLaunched()](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) und [OnActivated ](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_) ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5db57-127">It runs before [OnLaunched()](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) and [OnActivated](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_).</span></span> <span data-ttu-id="5db57-128">Dadurch können Sie bestimmen, ob Sie diese oder eine andere Instanz aktivieren möchten, bevor irgend ein anderer Initialisierungscode in Ihrer App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5db57-128">This allows you to determine whether to activate this, or another instance, before any other initialization code in your app runs.</span></span>

<span data-ttu-id="5db57-129">Der obige Code bestimmt, ob eine vorhandene oder neue Instanz der App aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="5db57-129">The code above determines whether an existing, or new, instance of your application is activated.</span></span> <span data-ttu-id="5db57-130">Um festzustellen, ob eine vorhandene Instanz aktiviert werden kann, wird ein Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="5db57-130">A key is used to determine whether there is an existing instance that you want to activate.</span></span> <span data-ttu-id="5db57-131">Wenn Ihre App beispielsweise nach [Behandeln der Dateiaktivierung](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation) gestartet wird, können Sie den Namen der Datei als Schlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="5db57-131">For example, if your app can be launched to [Handle file activation](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation), you might use the file name as a key.</span></span> <span data-ttu-id="5db57-132">Anschließend können Sie überprüfen, ob bereits eine Instanz Ihrer App mit diesem Schlüssel registriert ist, und sie aktivieren, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5db57-132">Then you can check whether an instance of your app is already registered with that key and activate it instead of opening a new instance.</span></span> <span data-ttu-id="5db57-133">Der Code erfüllt den folgenden Sinn:</span><span class="sxs-lookup"><span data-stu-id="5db57-133">This is the idea behind the code:</span></span> `var instance = AppInstance.FindOrRegisterInstanceForKey(key);`

<span data-ttu-id="5db57-134">Wenn eine Instanz gefunden wird, die bereits mit dem Schlüssel registriert ist, wird diese Instanz aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5db57-134">If an instance registered with the key is found, then that instance is activated.</span></span> <span data-ttu-id="5db57-135">Wenn der Schlüssel nicht gefunden wird, erstellt die aktuelle Instanz (die Instanz, die zurzeit `Main` ausführt) ihr Anwendungsobjekt und wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="5db57-135">If the key is not found, then the current instance (the instance that is currently running `Main`) creates its application object  and starts running.</span></span>

## <a name="background-tasks-and-multi-instancing"></a><span data-ttu-id="5db57-136">Hintergrundaufgaben und die Multiinstanzerstellung</span><span class="sxs-lookup"><span data-stu-id="5db57-136">Background tasks and multi-instancing</span></span>

- <span data-ttu-id="5db57-137">Hintergrundaufgaben außerhalb von Prozessen bieten Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5db57-137">Out-of-proc background tasks support multi-instancing.</span></span> <span data-ttu-id="5db57-138">Jeder neuer Trigger führt in der Regel zu einer neue Instanz der Hintergrundaufgabe (obwohl technisch gesehen mehrere Hintergrundaufgaben in demselben Hostprozess ausgeführt werden können).</span><span class="sxs-lookup"><span data-stu-id="5db57-138">Typically, each new trigger results in a new instance of the background task (although technically speaking multiple background tasks may run in same host process).</span></span> <span data-ttu-id="5db57-139">Dennoch wird eine neue Instanz der Hintergrundaufgabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="5db57-139">Nevertheless, a different instance of the background task is created.</span></span>
- <span data-ttu-id="5db57-140">Hintergrundaufgaben innerhalb von Prozessen bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5db57-140">In-proc background tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="5db57-141">Audiohintergrundaufgaben bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="5db57-141">Background audio tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="5db57-142">Wenn eine App eine Hintergrundaufgabe registriert , wird in der Regel zuerst überprüft, ob die Aufgabe bereits registriert ist. Gegebenenfalls wird die Aufgabe dann gelöscht, erneut registriert oder es wird keine Aktion ausgeführt, um die vorhandenen Registrierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5db57-142">When an app registers a background task, it usually first checks to see if the task is already registered and then either deletes and re-registers it, or does nothing in order to keep the existing registration.</span></span> <span data-ttu-id="5db57-143">Mit Mehrfachinstanz-Apps verhält es sich normalerweise genauso.</span><span class="sxs-lookup"><span data-stu-id="5db57-143">This is still the typical behavior with multi-instance apps.</span></span> <span data-ttu-id="5db57-144">Jedoch kann eine App mit Multiinstanzerstellung den Namen einer anderen Hintergrundaufgabe pro Instanz registrieren.</span><span class="sxs-lookup"><span data-stu-id="5db57-144">However, a multi-instancing app may choose to register a different background task name on a per-instance basis.</span></span> <span data-ttu-id="5db57-145">Dies führt zu mehrfachen Registrierungen für einen Trigger, sodass mehrere Instanzen von Hintergrundaufgaben aktiviert werden, wenn der Trigger ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5db57-145">This will result in multiple registrations for the same trigger, and multiple background task instances will be activated when the trigger fires.</span></span>
- <span data-ttu-id="5db57-146">App-Dienste starten für jede Verbindung eine separate Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="5db57-146">App-services launch a separate instance of the app-service background task for every connection.</span></span> <span data-ttu-id="5db57-147">Dies bleibt im Falle von Apps mit mehreren Instanzen unverändert, d.h. jede Instanz einer Mehrfachinstanz-App erhält eine eigene Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="5db57-147">This remains unchanged for multi-instance apps, that is each instance of a multi-instance app will get its own instance of the  app-service background task.</span></span> 

## <a name="additional-considerations"></a><span data-ttu-id="5db57-148">Weitere Überlegungen</span><span class="sxs-lookup"><span data-stu-id="5db57-148">Additional considerations</span></span>

- <span data-ttu-id="5db57-149">Die Multiinstanzerstellung wird von UWP-Apps unterstützt, die auf Desktop- und Internet der Dinge (IoT)-Projekte ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="5db57-149">Multi-instancing is supported by UWP apps that target desktop and Internet of Things (IoT) projects.</span></span>
- <span data-ttu-id="5db57-150">Um Racebedingungen und Dateizugriffskonflike zu vermeiden, müssen Apps mit mehreren Instanzen Maßnahmen für die Partition/Synchronisierung des Zugriffs auf Einstellungen, lokalen App-Speicher und andere Ressourcen (z.B. Benutzerdateien, Datenspeicher usw.) sorgen, die von mehreren Instanzen gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="5db57-150">To avoid race-conditions and contention issues, multi-instance apps need to take steps to partition/synchronize access to settings, app-local storage, and any other resource (such as user files, a data store, and so on) that can be shared among multiple instances.</span></span> <span data-ttu-id="5db57-151">Standard-Synchronisierungsmechanismen wie Mutexe, Semaphoren, Ereignisse usw., sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5db57-151">Standard synchronization mechanisms such as mutexes, semaphores, events, and and so on, are available.</span></span>
- <span data-ttu-id="5db57-152">Wenn in der Datei „Package.appxmanifest” der App `SupportsMultipleInstances` enthalten ist, müssen ihre Erweiterungen nicht `SupportsMultipleInstances` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="5db57-152">If the app has `SupportsMultipleInstances` in its Package.appxmanifest file, then its extensions do not need to declare `SupportsMultipleInstances`.</span></span> 
- <span data-ttu-id="5db57-153">Wenn Sie einer anderen Erweiterung außer Hintergrundaufgaben oder App-Diensten `SupportsMultipleInstances` hinzufügen und die App, die die Erweiterung hostet, in ihrer Datei „Package.appxmanifest” nicht auch `SupportsMultipleInstances` deklariert, wird ein Schemafehler generiert.</span><span class="sxs-lookup"><span data-stu-id="5db57-153">If you add `SupportsMultipleInstances` to any other extension, apart from background tasks or app-services, and the app that hosts the extension doesn't also declare `SupportsMultipleInstances` in its Package.appxmanifest file, then a schema error is generated.</span></span>
- <span data-ttu-id="5db57-154">Apps können die [ResourceGroup](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)-Deklaration in ihrer Manifestdatei dazu verwenden, mehrere Hintergrundaufgaben im gleichen Host zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="5db57-154">Apps can use the [ResourceGroup](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) declaration in their manifest to group multiple background tasks into the same host.</span></span> <span data-ttu-id="5db57-155">Dies steht im Konflikt mit der Multiinstanzerstellung, da dort jede Aktivierung in einen separaten Host wechselt.</span><span class="sxs-lookup"><span data-stu-id="5db57-155">This conflicts with multi-instancing, where each activation goes into a separate host.</span></span> <span data-ttu-id="5db57-156">Eine App kann deshalb in der Manifestdatei nicht sowohl `SupportsMultipleInstances`, als auch `ResourceGroup` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="5db57-156">Therefore an app cannot declare both `SupportsMultipleInstances` and `ResourceGroup` in their manifest.</span></span>

## <a name="sample"></a><span data-ttu-id="5db57-157">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5db57-157">Sample</span></span>

<span data-ttu-id="5db57-158">Finden Sie ein Beispiel für die Umleitung der multiinstanz-Aktivierung [mit mehreren Instanzen Beispiel](https://aka.ms/Kcrqst) .</span><span class="sxs-lookup"><span data-stu-id="5db57-158">See [Multi-Instance sample](https://aka.ms/Kcrqst) for an example of multi-instance activation redirection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5db57-159">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5db57-159">See also</span></span>

<span data-ttu-id="5db57-160">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span><span class="sxs-lookup"><span data-stu-id="5db57-160">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span></span>