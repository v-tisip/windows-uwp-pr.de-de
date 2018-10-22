---
author: TylerMSFT
title: Erstellen einer universellen Windows-App mit mehreren Instanzen
description: In diesem Thema wird beschrieben, wie UWP-Apps erstellt werden, die die Multiinstanzerstellung unterstützen.
keywords: UWP mit mehreren Instanzen
ms.author: twhitney
ms.date: 09/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: dd4e0ced4de2419858424a88f5fa5ce66f5b4286
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5400687"
---
# <a name="create-a-multi-instance-universal-windows-app"></a><span data-ttu-id="23f37-104">Erstellen einer universellen Windows-App mit mehreren Instanzen</span><span class="sxs-lookup"><span data-stu-id="23f37-104">Create a multi-instance Universal Windows App</span></span>

<span data-ttu-id="23f37-105">In diesem Thema wird beschrieben, wie Universelle Windows-Plattform (UWP)-Apps mit mehreren Instanzen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="23f37-105">This topic describes how to create multi-instance Universal Windows Platform (UWP) apps.</span></span>

<span data-ttu-id="23f37-106">Von Windows 10, Version 1803 (10.0; Build 17134) ideenreicher, Ihre UWP-app kann entscheiden Sie sich für mehrere Instanzen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="23f37-106">From Windows 10, version 1803 (10.0; Build 17134) onward, your UWP app can opt in to support multiple instances.</span></span> <span data-ttu-id="23f37-107">Wenn eine Instanz einer UWP-App mit mehreren Instanzen ausgeführt wird und eine nachfolgende Aktivierungsanforderung eingeht, wird die vorhandene Instanz von der Plattform nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="23f37-107">If an instance of an multi-instance UWP app is running, and a subsequent activation request comes through, the platform will not activate the existing instance.</span></span> <span data-ttu-id="23f37-108">Stattdessen wird eine neue Instanz erstellt, die in einem separaten Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="23f37-108">Instead, it will create a new instance, running in a separate process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23f37-109">Für die multiinstanzerstellung wird für JavaScript-Anwendungen unterstützt, für die multiinstanzerstellung Umleitung ist jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="23f37-109">Multi-instancing is supported for JavaScript applications, but multi-instancing redirection is not.</span></span> <span data-ttu-id="23f37-110">Da für die multiinstanzerstellung Umleitung für JavaScript-Anwendungen nicht unterstützt wird, ist die [**AppInstance**](/uwp/api/windows.applicationmodel.appinstance) -Klasse nicht nützlich für solche Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="23f37-110">Since multi-instancing redirection is not supported for JavaScript applications, the [**AppInstance**](/uwp/api/windows.applicationmodel.appinstance) class is not useful for such applications.</span></span>

## <a name="opt-in-to-multi-instance-behavior"></a><span data-ttu-id="23f37-111">Melden Sie sich für Mehrfachinstanz-Verhalten</span><span class="sxs-lookup"><span data-stu-id="23f37-111">Opt in to multi-instance behavior</span></span>

<span data-ttu-id="23f37-112">Wenn Sie eine neue Multiinstanz-Anwendung erstellen, können Sie die **Mehrfachinstanz-App-Projekt Templates.VSIX** installieren, die im [Visual Studio Marketplace ](https://aka.ms/E2nzbv) erhältlich sind.</span><span class="sxs-lookup"><span data-stu-id="23f37-112">If you are creating a new multi-instance application, you can install the **Multi-Instance App Project Templates.VSIX**, available from the [Visual Studio Marketplace](https://aka.ms/E2nzbv).</span></span> <span data-ttu-id="23f37-113">Nachdem Sie die Vorlagen installieren, sind sie im Dialogfeld **Neues Projekt** Dialogfeld unter **Visual C#-> Windows Universal** (oder **Andere Sprachen > Visual C++ > Windows Universal**) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="23f37-113">Once you install the templates, they will be available in the **New Project** dialog under **Visual C# > Windows Universal** (or **Other Languages > Visual C++ > Windows Universal**).</span></span>

<span data-ttu-id="23f37-114">Es werden zwei Vorlagen installiert: **UWP-Apps mit mehreren Instanzen**, die die Vorlage für die Erstellung einer Mulitiinstanz-App bereitstellt sowie **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen), die zusätzlich die Möglichkeit bietet, eine neue Instanz zu starten oder selektiv eine Instanz zu aktivieren, die bereits gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="23f37-114">Two templates are installed: **Multi-Instance UWP app**, which provides the template for creating a multi-instance app, and **Multi-Instance Redirection UWP app**, which provides additional logic that you can build on to either launch a new instance or selectively activate an instance that has already been launched.</span></span> <span data-ttu-id="23f37-115">Wenn beispielsweise ein Dokument in nur einer einzelnen Instanz bearbeitet werden soll, verschieben Sie die Instanz, in der die Datei geöffnet ist, in den Vordergrund, statt eine neue Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="23f37-115">For example, perhaps you only want once instance at a time editing the same document, so you bring the instance that has that file open to the foreground rather than launching a new instance.</span></span>

<span data-ttu-id="23f37-116">Beide Vorlagen fügen `SupportsMultipleInstances` auf die `package.appxmanifest` Datei.</span><span class="sxs-lookup"><span data-stu-id="23f37-116">Both templates add `SupportsMultipleInstances` to the `package.appxmanifest` file.</span></span> <span data-ttu-id="23f37-117">Beachten Sie das Namespacepräfix `desktop4` und `iot2`: nur Projekte, die auf den Desktop abzielen oder Internet der Dinge (IoT)-Projekte, bieten Unterstützung für die multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="23f37-117">Note the namespace prefix `desktop4` and `iot2`: only projects that target the desktop, or Internet of Things (IoT) projects, support multi-instancing.</span></span>

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

## <a name="multi-instance-activation-redirection"></a><span data-ttu-id="23f37-118">Umleitung der Multiinstanz-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="23f37-118">Multi-instance activation redirection</span></span>

 <span data-ttu-id="23f37-119">Bei der Unterstützung für die Multiinstanzerstellung geht es nicht nur darum, den Start mehrerer Instanzen der App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="23f37-119">Multi-instancing support for UWP apps goes beyond simply making it possible to launch multiple instances of the app.</span></span> <span data-ttu-id="23f37-120">Vielmehr bietet sie Ihnen die Möglichkeit auszuwählen, ob eine neue Instanz Ihrer App gestartet oder eine Instanz, die bereits ausgeführt wird, aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="23f37-120">It allows for customization in cases where you want to select whether a new instance of your app is launched or an instance that is already running is activated.</span></span> <span data-ttu-id="23f37-121">Wenn die App beispielsweise gestartet wird, um eine Datei zu bearbeiten, die bereits in einer anderen Instanz bearbeitet wird, können Sie die Aktivierung an die Instanz umleiten, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23f37-121">For example, if the app is launched to edit a file that is already being edited in another instance, you may want to redirect the activation to that instance instead of opening up another instance that  that is already editing the file.</span></span>

<span data-ttu-id="23f37-122">Um es in Aktion zu sehen, sehen Sie sich ein Video zum Erstellen von UWP-apps mit mehreren Instanzen an.</span><span class="sxs-lookup"><span data-stu-id="23f37-122">To see it in action, watch this video about Creating multi-instance UWP apps.</span></span>

> [!VIDEO https://www.youtube.com/embed/clnnf4cigd0]

<span data-ttu-id="23f37-123">Die Vorlage **Multi-Instance Redirection UWP app** (UWP-App mit Umleitung für mehrere Instanzen) fügt der Datei „Package.appxmanifest” nicht nur wie oben beschrieben `SupportsMultipleInstances` hinzu, sondern fügt Ihrem Projekt auch die Funktion **Program.cs** (oder **Program.cpp**, wenn Sie die C++-Version der Vorlage verwenden), die eine `Main()`-Funktion enthält.</span><span class="sxs-lookup"><span data-stu-id="23f37-123">The **Multi-Instance Redirection UWP app** template adds `SupportsMultipleInstances` to the package.appxmanifest file as shown above, and also adds a **Program.cs** (or **Program.cpp**, if you are using the C++ version of the template) to your project that contains a `Main()` function.</span></span> <span data-ttu-id="23f37-124">Die Logik für die Umleitung der Aktivierung wird in die `Main`-Funktion eingefügt.</span><span class="sxs-lookup"><span data-stu-id="23f37-124">The logic for redirecting activation goes in the `Main` function.</span></span> <span data-ttu-id="23f37-125">Nachfolgend finden Sie die Vorlage für **Program.cs** .</span><span class="sxs-lookup"><span data-stu-id="23f37-125">The template for **Program.cs** is shown below.</span></span>

<span data-ttu-id="23f37-126">Die Eigenschaft [**AppInstance.RecommendedInstance**](/uwp/api/windows.applicationmodel.appinstance.recommendedinstance) stellt die Shell bereitgestellten bevorzugte Instanz für diese aktivierungsanforderung dar, sofern vorhanden (oder `null` kein Computerkonto vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="23f37-126">The [**AppInstance.RecommendedInstance**](/uwp/api/windows.applicationmodel.appinstance.recommendedinstance) property represents the shell-provided preferred instance for this activation request, if there is one (or `null` if there isn't one).</span></span> <span data-ttu-id="23f37-127">Wenn die Shell eine Einstellung enthält, dann Sie können können Aktivierung an die Instanz umleiten oder kann ignoriert werden, wenn Sie auswählen.</span><span class="sxs-lookup"><span data-stu-id="23f37-127">If the shell provides a preference, then you can can redirect activation to that instance, or you can ignore it if you choose.</span></span>

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

`Main()` <span data-ttu-id="23f37-128">ist der erste Schritt, der ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="23f37-128">is the first thing that runs.</span></span> <span data-ttu-id="23f37-129">Er wird vor dem [**OnLaunched**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) und [**OnActivated**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_)ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="23f37-129">It runs before [**OnLaunched**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnLaunched_Windows_ApplicationModel_Activation_LaunchActivatedEventArgs_) and [**OnActivated**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application#Windows_UI_Xaml_Application_OnActivated_Windows_ApplicationModel_Activation_IActivatedEventArgs_).</span></span> <span data-ttu-id="23f37-130">Dadurch können Sie bestimmen, ob Sie diese oder eine andere Instanz aktivieren möchten, bevor irgend ein anderer Initialisierungscode in Ihrer App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="23f37-130">This allows you to determine whether to activate this, or another instance, before any other initialization code in your app runs.</span></span>

<span data-ttu-id="23f37-131">Der obige Code bestimmt, ob eine vorhandene oder neue Instanz der App aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="23f37-131">The code above determines whether an existing, or new, instance of your application is activated.</span></span> <span data-ttu-id="23f37-132">Um festzustellen, ob eine vorhandene Instanz aktiviert werden kann, wird ein Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="23f37-132">A key is used to determine whether there is an existing instance that you want to activate.</span></span> <span data-ttu-id="23f37-133">Wenn Ihre App beispielsweise nach [Behandeln der Dateiaktivierung](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation) gestartet wird, können Sie den Namen der Datei als Schlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="23f37-133">For example, if your app can be launched to [Handle file activation](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/handle-file-activation), you might use the file name as a key.</span></span> <span data-ttu-id="23f37-134">Anschließend können Sie überprüfen, ob bereits eine Instanz Ihrer App mit diesem Schlüssel registriert ist, und sie aktivieren, statt eine neue Instanz zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23f37-134">Then you can check whether an instance of your app is already registered with that key and activate it instead of opening a new instance.</span></span> <span data-ttu-id="23f37-135">Der Code erfüllt den folgenden Sinn:</span><span class="sxs-lookup"><span data-stu-id="23f37-135">This is the idea behind the code:</span></span> `var instance = AppInstance.FindOrRegisterInstanceForKey(key);`

<span data-ttu-id="23f37-136">Wenn eine Instanz gefunden wird, die bereits mit dem Schlüssel registriert ist, wird diese Instanz aktiviert.</span><span class="sxs-lookup"><span data-stu-id="23f37-136">If an instance registered with the key is found, then that instance is activated.</span></span> <span data-ttu-id="23f37-137">Wenn der Schlüssel nicht gefunden wird, erstellt die aktuelle Instanz (die Instanz, die zurzeit `Main` ausführt) ihr Anwendungsobjekt und wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="23f37-137">If the key is not found, then the current instance (the instance that is currently running `Main`) creates its application object  and starts running.</span></span>

## <a name="background-tasks-and-multi-instancing"></a><span data-ttu-id="23f37-138">Hintergrundaufgaben und die Multiinstanzerstellung</span><span class="sxs-lookup"><span data-stu-id="23f37-138">Background tasks and multi-instancing</span></span>

- <span data-ttu-id="23f37-139">Hintergrundaufgaben außerhalb von Prozessen bieten Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="23f37-139">Out-of-proc background tasks support multi-instancing.</span></span> <span data-ttu-id="23f37-140">Jeder neuer Trigger führt in der Regel zu einer neue Instanz der Hintergrundaufgabe (obwohl technisch gesehen mehrere Hintergrundaufgaben in demselben Hostprozess ausgeführt werden können).</span><span class="sxs-lookup"><span data-stu-id="23f37-140">Typically, each new trigger results in a new instance of the background task (although technically speaking multiple background tasks may run in same host process).</span></span> <span data-ttu-id="23f37-141">Dennoch wird eine neue Instanz der Hintergrundaufgabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="23f37-141">Nevertheless, a different instance of the background task is created.</span></span>
- <span data-ttu-id="23f37-142">Hintergrundaufgaben innerhalb von Prozessen bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="23f37-142">In-proc background tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="23f37-143">Audiohintergrundaufgaben bieten keine Unterstützung für die Multiinstanzerstellung.</span><span class="sxs-lookup"><span data-stu-id="23f37-143">Background audio tasks do not support multi-instancing.</span></span>
- <span data-ttu-id="23f37-144">Wenn eine App eine Hintergrundaufgabe registriert , wird in der Regel zuerst überprüft, ob die Aufgabe bereits registriert ist. Gegebenenfalls wird die Aufgabe dann gelöscht, erneut registriert oder es wird keine Aktion ausgeführt, um die vorhandenen Registrierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="23f37-144">When an app registers a background task, it usually first checks to see if the task is already registered and then either deletes and re-registers it, or does nothing in order to keep the existing registration.</span></span> <span data-ttu-id="23f37-145">Mit Mehrfachinstanz-Apps verhält es sich normalerweise genauso.</span><span class="sxs-lookup"><span data-stu-id="23f37-145">This is still the typical behavior with multi-instance apps.</span></span> <span data-ttu-id="23f37-146">Jedoch kann eine App mit Multiinstanzerstellung den Namen einer anderen Hintergrundaufgabe pro Instanz registrieren.</span><span class="sxs-lookup"><span data-stu-id="23f37-146">However, a multi-instancing app may choose to register a different background task name on a per-instance basis.</span></span> <span data-ttu-id="23f37-147">Dies führt zu mehrfachen Registrierungen für einen Trigger, sodass mehrere Instanzen von Hintergrundaufgaben aktiviert werden, wenn der Trigger ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="23f37-147">This will result in multiple registrations for the same trigger, and multiple background task instances will be activated when the trigger fires.</span></span>
- <span data-ttu-id="23f37-148">App-Dienste starten für jede Verbindung eine separate Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="23f37-148">App-services launch a separate instance of the app-service background task for every connection.</span></span> <span data-ttu-id="23f37-149">Dies bleibt im Falle von Apps mit mehreren Instanzen unverändert, d.h. jede Instanz einer Mehrfachinstanz-App erhält eine eigene Instanz der Hintergrundaufgabe des App-Dienstes.</span><span class="sxs-lookup"><span data-stu-id="23f37-149">This remains unchanged for multi-instance apps, that is each instance of a multi-instance app will get its own instance of the  app-service background task.</span></span> 

## <a name="additional-considerations"></a><span data-ttu-id="23f37-150">Weitere Überlegungen</span><span class="sxs-lookup"><span data-stu-id="23f37-150">Additional considerations</span></span>

- <span data-ttu-id="23f37-151">Die Multiinstanzerstellung wird von UWP-Apps unterstützt, die auf Desktop- und Internet der Dinge (IoT)-Projekte ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="23f37-151">Multi-instancing is supported by UWP apps that target desktop and Internet of Things (IoT) projects.</span></span>
- <span data-ttu-id="23f37-152">Um Racebedingungen und Dateizugriffskonflike zu vermeiden, müssen Apps mit mehreren Instanzen Maßnahmen für die Partition/Synchronisierung des Zugriffs auf Einstellungen, lokalen App-Speicher und andere Ressourcen (z.B. Benutzerdateien, Datenspeicher usw.) sorgen, die von mehreren Instanzen gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="23f37-152">To avoid race-conditions and contention issues, multi-instance apps need to take steps to partition/synchronize access to settings, app-local storage, and any other resource (such as user files, a data store, and so on) that can be shared among multiple instances.</span></span> <span data-ttu-id="23f37-153">Standard-Synchronisierungsmechanismen wie Mutexe, Semaphoren, Ereignisse usw., sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="23f37-153">Standard synchronization mechanisms such as mutexes, semaphores, events, and and so on, are available.</span></span>
- <span data-ttu-id="23f37-154">Wenn in der Datei „Package.appxmanifest” der App `SupportsMultipleInstances` enthalten ist, müssen ihre Erweiterungen nicht `SupportsMultipleInstances` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="23f37-154">If the app has `SupportsMultipleInstances` in its Package.appxmanifest file, then its extensions do not need to declare `SupportsMultipleInstances`.</span></span> 
- <span data-ttu-id="23f37-155">Wenn Sie einer anderen Erweiterung außer Hintergrundaufgaben oder App-Diensten `SupportsMultipleInstances` hinzufügen und die App, die die Erweiterung hostet, in ihrer Datei „Package.appxmanifest” nicht auch `SupportsMultipleInstances` deklariert, wird ein Schemafehler generiert.</span><span class="sxs-lookup"><span data-stu-id="23f37-155">If you add `SupportsMultipleInstances` to any other extension, apart from background tasks or app-services, and the app that hosts the extension doesn't also declare `SupportsMultipleInstances` in its Package.appxmanifest file, then a schema error is generated.</span></span>
- <span data-ttu-id="23f37-156">Apps können die [**ResourceGroup**](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) -Deklaration im Manifest verwenden, um mehrere Hintergrundaufgaben im gleichen Host zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="23f37-156">Apps can use the [**ResourceGroup**](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) declaration in their manifest to group multiple background tasks into the same host.</span></span> <span data-ttu-id="23f37-157">Dies steht im Konflikt mit der Multiinstanzerstellung, da dort jede Aktivierung in einen separaten Host wechselt.</span><span class="sxs-lookup"><span data-stu-id="23f37-157">This conflicts with multi-instancing, where each activation goes into a separate host.</span></span> <span data-ttu-id="23f37-158">Eine App kann deshalb in der Manifestdatei nicht sowohl `SupportsMultipleInstances`, als auch `ResourceGroup` deklarieren.</span><span class="sxs-lookup"><span data-stu-id="23f37-158">Therefore an app cannot declare both `SupportsMultipleInstances` and `ResourceGroup` in their manifest.</span></span>

## <a name="sample"></a><span data-ttu-id="23f37-159">Beispiel</span><span class="sxs-lookup"><span data-stu-id="23f37-159">Sample</span></span>

<span data-ttu-id="23f37-160">Finden Sie ein Beispiel für die Umleitung der multiinstanz-Aktivierung [mit mehreren Instanzen Beispiel](https://aka.ms/Kcrqst) .</span><span class="sxs-lookup"><span data-stu-id="23f37-160">See [Multi-Instance sample](https://aka.ms/Kcrqst) for an example of multi-instance activation redirection.</span></span>

## <a name="see-also"></a><span data-ttu-id="23f37-161">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="23f37-161">See also</span></span>

<span data-ttu-id="23f37-162">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span><span class="sxs-lookup"><span data-stu-id="23f37-162">[AppInstance.FindOrRegisterInstanceForKey](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_FindOrRegisterInstanceForKey_System_String_)
[AppInstance.GetActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_GetActivatedEventArgs)
[AppInstance.RedirectActivationTo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinstance#Windows_ApplicationModel_AppInstance_RedirectActivationTo)
[Handle app activation](https://docs.microsoft.com/windows/uwp/launch-resume/activate-an-app)</span></span>