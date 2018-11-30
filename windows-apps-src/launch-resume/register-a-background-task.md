---
title: Registrieren einer Hintergrundaufgabe
description: Hier erfahren Sie, wie eine Funktion erstellt wird, die zum sicheren Registrieren der meisten Hintergrundaufgaben wiederverwendet werden kann.
ms.assetid: 8B1CADC5-F630-48B8-B3CE-5AB62E3DFB0D
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
ms.openlocfilehash: f940b0433c5cf7818102f92c9e61a6fe012bf4b9
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8212775"
---
# <a name="register-a-background-task"></a><span data-ttu-id="f600d-104">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-104">Register a background task</span></span>


**<span data-ttu-id="f600d-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="f600d-105">Important APIs</span></span>**

-   [**<span data-ttu-id="f600d-106">BackgroundTaskRegistration-Klasse</span><span class="sxs-lookup"><span data-stu-id="f600d-106">BackgroundTaskRegistration class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224786)
-   [**<span data-ttu-id="f600d-107">BackgroundTaskBuilder-Klasse</span><span class="sxs-lookup"><span data-stu-id="f600d-107">BackgroundTaskBuilder class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
-   [**<span data-ttu-id="f600d-108">SystemCondition-Klasse</span><span class="sxs-lookup"><span data-stu-id="f600d-108">SystemCondition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224834)

<span data-ttu-id="f600d-109">Hier erfahren Sie, wie eine Funktion erstellt wird, die zum sicheren Registrieren der meisten Hintergrundaufgaben wiederverwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f600d-109">Learn how to create a function that can be re-used to safely register most background tasks.</span></span>

<span data-ttu-id="f600d-110">Dieses Thema gilt für In-Process-Hintergrundaufgaben sowie für Out-of-Process-Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="f600d-110">This topic is applicable to both in-process background tasks and out-of-process background tasks.</span></span> <span data-ttu-id="f600d-111">In diesem Thema wird davon ausgegangen, dass Sie bereits über eine Hintergrundaufgabe verfügen, die registriert werden muss.</span><span class="sxs-lookup"><span data-stu-id="f600d-111">This topic assumes that you already have a background task that needs to be registered.</span></span> <span data-ttu-id="f600d-112">(Informationen zum Erstellen einer Hintergrundaufgabe finden Sie unter [Erstellen und Registrieren einer außerhalb des Prozesses ausgeführten Hintergrundaufgabe](create-and-register-a-background-task.md) oder [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md)).</span><span class="sxs-lookup"><span data-stu-id="f600d-112">(See [Create and register a background task that runs out-of-process](create-and-register-a-background-task.md) or [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) for information about how to write a background task).</span></span>

<span data-ttu-id="f600d-113">Dieses Thema behandelt schrittweise eine Hilfsfunktion, die Hintergrundaufgaben registriert.</span><span class="sxs-lookup"><span data-stu-id="f600d-113">This topic walks through a utility function that registers background tasks.</span></span> <span data-ttu-id="f600d-114">Diese Hilfsfunktion sucht zuerst nach vorhandenen Registrierungen, um Probleme mit mehrfachen Registrierungen zu vermeiden. Sie kann außerdem eine Systembedingung auf die Hintergrundaufgabe anwenden.</span><span class="sxs-lookup"><span data-stu-id="f600d-114">This utility function checks for existing registrations first before registering the task multiple times to avoid problems with multiple registrations, and it can apply a system condition to the background task.</span></span> <span data-ttu-id="f600d-115">Die exemplarische Vorgehensweise enthält ein vollständiges lauffähiges Beispiel für diese Hilfsfunktion.</span><span class="sxs-lookup"><span data-stu-id="f600d-115">The walkthrough includes a complete, working example of this utility function.</span></span>

**<span data-ttu-id="f600d-116">Hinweis</span><span class="sxs-lookup"><span data-stu-id="f600d-116">Note</span></span>**  

<span data-ttu-id="f600d-117">Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrund-Triggertypen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="f600d-117">Universal Windows apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="f600d-118">Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f600d-118">To ensure that your Universal Windows app continues to run properly after you release an update, you must call [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) and then call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) when your app launches after being updated.</span></span> <span data-ttu-id="f600d-119">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f600d-119">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

## <a name="define-the-method-signature-and-return-type"></a><span data-ttu-id="f600d-120">Definieren von Methodensignatur und Rückgabetyp</span><span class="sxs-lookup"><span data-stu-id="f600d-120">Define the method signature and return type</span></span>

<span data-ttu-id="f600d-121">Diese Methode übernimmt den Einstiegspunkt der Aufgabe, den Namen der Aufgabe, einen vorgefertigten Trigger für die Hintergrundaufgabe und (optional) eine [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) für die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="f600d-121">This method takes in the task entry point, task name, a pre-constructed background task trigger, and (optionally) a [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) for the background task.</span></span> <span data-ttu-id="f600d-122">Diese Methode gibt ein [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="f600d-122">This method returns a [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786) object.</span></span>

> [!Important]
> `taskEntryPoint` <span data-ttu-id="f600d-123">– für Hintergrundaufgaben, die außerhalb eines Prozesses ausgeführt werden, muss dies als der Namespace-Name, '.', und der Name der Klasse, die Ihre Hintergrund-Klasse enthält, konstruiert werden.</span><span class="sxs-lookup"><span data-stu-id="f600d-123">- for background tasks that run in out of process, this must be constructed as the namespace name, '.', and the name of the class containing your background class.</span></span> <span data-ttu-id="f600d-124">Die Zeichenfolge beachtet die Groß-/Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="f600d-124">The string is case-sensitive.</span></span>  <span data-ttu-id="f600d-125">Wenn Sie beispielsweise den Namespace „MyBackgroundTasks“ und eine Klasse „BackgroundTask1“ haben, die Ihren Hintergrund-Klassen-Code enthält, ist die Zeichenfolge für `taskEntryPoint` „MyBackgroundTasks.BackgroundTask1“.</span><span class="sxs-lookup"><span data-stu-id="f600d-125">For example, if you had a namespace "MyBackgroundTasks" and a class "BackgroundTask1" that contained your background class code, the string for `taskEntryPoint` would be "MyBackgroundTasks.BackgroundTask1".</span></span>
> <span data-ttu-id="f600d-126">Wenn Ihre Hintergrundaufgabe im gleichen Prozess wie Ihre App (d. h. als In-Prozess-Hintergrundaufgabe) ausgeführt wird, sollte `taskEntryPoint` nicht festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f600d-126">If your background task runs in the same process as your app (i.e. a in-process background task) `taskEntryPoint` should not be set.</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> public static BackgroundTaskRegistration RegisterBackgroundTask(
>                                                 string taskEntryPoint,
>                                                 string name,
>                                                 IBackgroundTrigger trigger,
>                                                 IBackgroundCondition condition)
> {
>     
>     // We'll add code to this function in subsequent steps.
>
> }
> ```
> ``` cpp
> BackgroundTaskRegistration^ MainPage::RegisterBackgroundTask(
>                                              Platform::String ^ taskEntryPoint,
>                                              Platform::String ^ taskName,
>                                              IBackgroundTrigger ^ trigger,
>                                              IBackgroundCondition ^ condition)
> {
>     
>     // We'll add code to this function in subsequent steps.
>
> }
> ```

## <a name="check-for-existing-registrations"></a><span data-ttu-id="f600d-127">Überprüfung von vorhandenen Registrierungen</span><span class="sxs-lookup"><span data-stu-id="f600d-127">Check for existing registrations</span></span>

<span data-ttu-id="f600d-128">Überprüfen Sie, ob die Aufgabe bereits registriert ist.</span><span class="sxs-lookup"><span data-stu-id="f600d-128">Check whether the task is already registered.</span></span> <span data-ttu-id="f600d-129">Diese Überprüfung ist wichtig, denn eine mehrfach registrierte Hintergrundaufgabe wird mehrfach aufgerufen, wenn sie ausgelöst wird. Dies kann die CPU überlasten und zu unerwartetem Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="f600d-129">It's important to check this because if a task is registered multiple times, it will run more than once whenever it’s triggered; this can use excess CPU and may cause unexpected behavior.</span></span>

<span data-ttu-id="f600d-130">Sie können die vorhandenen Registrierungen durch Abfrage der [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787)-Eigenschaft und Iteration über das Ergebnis überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f600d-130">You can check for existing registrations by querying the [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) property and iterating on the result.</span></span> <span data-ttu-id="f600d-131">Überprüfen Sie die Namen aller Instanzen: wenn ein Name mit dem Namen der Aufgabe übereinstimmt, die registriert werden soll, verlassen Sie die Schleife, und legen Sie eine Flag-Variable fest, damit Ihr Code im nächsten Schritt einen anderen Pfad wählen kann.</span><span class="sxs-lookup"><span data-stu-id="f600d-131">Check the name of each instance – if it matches the name of the task you’re registering, then break out of the loop and set a flag variable so that your code can choose a different path in the next step.</span></span>

> <span data-ttu-id="f600d-132">**Hinweis:** verwenden Namen für Hintergrundaufgaben, die für Ihre app eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="f600d-132">**Note**Use background task names that are unique to your app.</span></span> <span data-ttu-id="f600d-133">Stellen Sie sicher, dass jede Hintergrundaufgabe einen eindeutigen Namen hat.</span><span class="sxs-lookup"><span data-stu-id="f600d-133">Ensure each background task has a unique name.</span></span>

<span data-ttu-id="f600d-134">Der folgende Code registriert eine Hintergrundaufgabe mit dem im vorigen Schritt erstellten [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838):</span><span class="sxs-lookup"><span data-stu-id="f600d-134">The following code registers a background task using the [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838) we created in the last step:</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> public static BackgroundTaskRegistration RegisterBackgroundTask(
>                                                 string taskEntryPoint,
>                                                 string name,
>                                                 IBackgroundTrigger trigger,
>                                                 IBackgroundCondition condition)
> {
>     //
>     // Check for existing registrations of this background task.
>     //
>
>     foreach (var cur in BackgroundTaskRegistration.AllTasks)
>     {
>
>         if (cur.Value.Name == name)
>         {
>             //
>             // The task is already registered.
>             //
>
>             return (BackgroundTaskRegistration)(cur.Value);
>         }
>     }
>     
>     // We'll register the task in the next step.
> }
> ```
> ``` cpp
> BackgroundTaskRegistration^ MainPage::RegisterBackgroundTask(
>                                              Platform::String ^ taskEntryPoint,
>                                              Platform::String ^ taskName,
>                                              IBackgroundTrigger ^ trigger,
>                                              IBackgroundCondition ^ condition)
> {
>     //
>     // Check for existing registrations of this background task.
>     //
>     
>     auto iter   = BackgroundTaskRegistration::AllTasks->First();
>     auto hascur = iter->HasCurrent;
>     
>     while (hascur)
>     {
>         auto cur = iter->Current->Value;
>         
>         if(cur->Name == name)
>         {
>             //
>             // The task is registered.
>             //
>             
>             return (BackgroundTaskRegistration ^)(cur);
>         }
>         
>         hascur = iter->MoveNext();
>     }
>     
>     // We'll register the task in the next step.
> }
> ```

## <a name="register-the-background-task-or-return-the-existing-registration"></a><span data-ttu-id="f600d-135">Registrieren der Hintergrundaufgabe (oder Rückgabe der bereits vorhandenen Registrierung)</span><span class="sxs-lookup"><span data-stu-id="f600d-135">Register the background task (or return the existing registration)</span></span>


<span data-ttu-id="f600d-136">Überprüfen Sie, ob sich die Aufgabe in der Liste der bereits registrierten Hintergrundaufgaben befindet.</span><span class="sxs-lookup"><span data-stu-id="f600d-136">Check to see if the task was found in the list of existing background task registrations.</span></span> <span data-ttu-id="f600d-137">Geben Sie in diesem Fall diese Instanz der Aufgabe zurück.</span><span class="sxs-lookup"><span data-stu-id="f600d-137">If so, return that instance of the task.</span></span>

<span data-ttu-id="f600d-138">Registrieren Sie die Aufgabe dann mithilfe eines neuen [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="f600d-138">Then, register the task using a new [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) object.</span></span> <span data-ttu-id="f600d-139">Der Code sollte überprüfen, ob der Parameter für die Bedingung null ist, und andernfalls die Bedingung an das Registrierungsobjekt anfügen.</span><span class="sxs-lookup"><span data-stu-id="f600d-139">This code should check whether the condition parameter is null, and if not, add the condition to the registration object.</span></span> <span data-ttu-id="f600d-140">Geben Sie die von der [**BackgroundTaskBuilder.Register**](https://msdn.microsoft.com/library/windows/apps/br224772)-Methode zurückgegebene [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786) zurück.</span><span class="sxs-lookup"><span data-stu-id="f600d-140">Return the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786) returned by the [**BackgroundTaskBuilder.Register**](https://msdn.microsoft.com/library/windows/apps/br224772) method.</span></span>

> <span data-ttu-id="f600d-141">**Hinweis:** Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="f600d-141">**Note**Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="f600d-142">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f600d-142">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="f600d-143">Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="f600d-143">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>
> <span data-ttu-id="f600d-144">**Hinweis** Wenn Sie eine Hintergrundaufgabe registrieren, die im gleichen Prozess wie Ihre-App ausgeführt wird, senden Sie `String.Empty` oder `null` als `taskEntryPoint`-Parameter.</span><span class="sxs-lookup"><span data-stu-id="f600d-144">**Note** If you are registering a background task that runs in the same process as your app, send `String.Empty` or `null` for the `taskEntryPoint` parameter.</span></span>

<span data-ttu-id="f600d-145">Im folgenden Beispiel wird entweder die vorhandene Aufgabe zurückgegeben, oder es wird Code hinzugefügt, mit dem die Hintergrundaufgabe registriert wird (ggf. einschließlich der Systembedingung):</span><span class="sxs-lookup"><span data-stu-id="f600d-145">The following example either returns the existing task, or adds code that registers the background task (including the optional system condition if present):</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> public static BackgroundTaskRegistration RegisterBackgroundTask(
>                                                 string taskEntryPoint,
>                                                 string name,
>                                                 IBackgroundTrigger trigger,
>                                                 IBackgroundCondition condition)
> {
>     //
>     // Check for existing registrations of this background task.
>     //
>
>     foreach (var cur in BackgroundTaskRegistration.AllTasks)
>     {
>
>         if (cur.Value.Name == taskName)
>         {
>             //
>             // The task is already registered.
>             //
>
>             return (BackgroundTaskRegistration)(cur.Value);
>         }
>     }
>
>     //
>     // Register the background task.
>     //
>
>     var builder = new BackgroundTaskBuilder();
>
>     builder.Name = name;
>
>     // in-process background tasks don't set TaskEntryPoint
>     if ( taskEntryPoint != null && taskEntryPoint != String.Empty)
>     {
>         builder.TaskEntryPoint = taskEntryPoint;
>     }
>     builder.SetTrigger(trigger);
>
>     if (condition != null)
>     {
>         builder.AddCondition(condition);
>     }
>
>     BackgroundTaskRegistration task = builder.Register();
>
>     return task;
> }
> ```
> ``` cpp
> BackgroundTaskRegistration^ MainPage::RegisterBackgroundTask(
>                                              Platform::String ^ taskEntryPoint,
>                                              Platform::String ^ taskName,
>                                              IBackgroundTrigger ^ trigger,
>                                              IBackgroundCondition ^ condition)
> {
>
>     //
>     // Check for existing registrations of this background task.
>     //
>
>     auto iter   = BackgroundTaskRegistration::AllTasks->First();
>     auto hascur = iter->HasCurrent;
>
>     while (hascur)
>     {
>         auto cur = iter->Current->Value;
>
>         if(cur->Name == name)
>         {
>             //
>             // The task is registered.
>             //
>
>             return (BackgroundTaskRegistration ^)(cur);
>         }
>
>         hascur = iter->MoveNext();
>     }
>
>     //
>     // Register the background task.
>     //
>
>     auto builder = ref new BackgroundTaskBuilder();
>
>     builder->Name = name;
>     builder->TaskEntryPoint = taskEntryPoint;
>     builder->SetTrigger(trigger);
>
>     if (condition != nullptr) {
>         
>         builder->AddCondition(condition);
>     }
>
>     BackgroundTaskRegistration ^ task = builder->Register();
>
>     return task;
> }
> ```

## <a name="complete-background-task-registration-utility-function"></a><span data-ttu-id="f600d-146">Hilfsfunktion zur Registrierung der abgeschlossenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-146">Complete background task registration utility function</span></span>

<span data-ttu-id="f600d-147">Dieses Beispiel zeigt die Hilfsfunktion zur Registrierung der abgeschlossenen Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="f600d-147">This example shows the completed background task registration function.</span></span> <span data-ttu-id="f600d-148">Diese Funktion kann zum Registrieren der meisten Hintergrundaufgaben mit Ausnahme von Hintergrundaufgaben im Netzwerk verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f600d-148">This function can be used to register most background tasks, with the exception of networking background tasks.</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> //
> // Register a background task with the specified taskEntryPoint, name, trigger,
> // and condition (optional).
> //
> // taskEntryPoint: Task entry point for the background task.
> // taskName: A name for the background task.
> // trigger: The trigger for the background task.
> // condition: Optional parameter. A conditional event that must be true for the task to fire.
> //
> public static BackgroundTaskRegistration RegisterBackgroundTask(string taskEntryPoint,
>                                                                 string taskName,
>                                                                 IBackgroundTrigger trigger,
>                                                                 IBackgroundCondition condition)
> {
>     //
>     // Check for existing registrations of this background task.
>     //
>
>     foreach (var cur in BackgroundTaskRegistration.AllTasks)
>     {
>
>         if (cur.Value.Name == taskName)
>         {
>             //
>             // The task is already registered.
>             //
>
>             return (BackgroundTaskRegistration)(cur.Value);
>         }
>     }
>
>     //
>     // Register the background task.
>     //
>
>     var builder = new BackgroundTaskBuilder();
>
>     builder.Name = taskName;
>     builder.TaskEntryPoint = taskEntryPoint;
>     builder.SetTrigger(trigger);
>
>     if (condition != null)
>     {
>
>         builder.AddCondition(condition);
>     }
>
>     BackgroundTaskRegistration task = builder.Register();
>
>     return task;
> }
> ```
> ``` cpp
> //
> // Register a background task with the specified taskEntryPoint, name, trigger,
> // and condition (optional).
> //
> // taskEntryPoint: Task entry point for the background task.
> // taskName: A name for the background task.
> // trigger: The trigger for the background task.
> // condition: Optional parameter. A conditional event that must be true for the task to fire.
> //
> BackgroundTaskRegistration^ MainPage::RegisterBackgroundTask(Platform::String ^ taskEntryPoint,
>                                                              Platform::String ^ taskName,
>                                                              IBackgroundTrigger ^ trigger,
>                                                              IBackgroundCondition ^ condition)
> {
>
>     //
>     // Check for existing registrations of this background task.
>     //
>
>     auto iter   = BackgroundTaskRegistration::AllTasks->First();
>     auto hascur = iter->HasCurrent;
>
>     while (hascur)
>     {
>         auto cur = iter->Current->Value;
>
>         if(cur->Name == name)
>         {
>             //
>             // The task is registered.
>             //
>
>             return (BackgroundTaskRegistration ^)(cur);
>         }
>
>         hascur = iter->MoveNext();
>     }
>
>
>     //
>     // Register the background task.
>     //
>
>     auto builder = ref new BackgroundTaskBuilder();
>
>     builder->Name = name;
>     builder->TaskEntryPoint = taskEntryPoint;
>     builder->SetTrigger(trigger);
>
>     if (condition != nullptr) {
>
>         builder->AddCondition(condition);
>     }
>
>     BackgroundTaskRegistration ^ task = builder->Register();
>
>     return task;
> }
> ```

## <a name="related-topics"></a><span data-ttu-id="f600d-149">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f600d-149">Related topics</span></span>

* [<span data-ttu-id="f600d-150">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="f600d-150">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="f600d-151">Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="f600d-151">Create and register an in-process background task</span></span>](create-and-register-an-inproc-background-task.md)
* [<span data-ttu-id="f600d-152">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="f600d-152">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="f600d-153">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-153">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="f600d-154">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="f600d-154">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="f600d-155">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="f600d-155">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="f600d-156">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-156">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="f600d-157">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-157">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="f600d-158">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="f600d-158">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="f600d-159">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="f600d-159">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* [<span data-ttu-id="f600d-160">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="f600d-160">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="f600d-161">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="f600d-161">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="f600d-162">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="f600d-162">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)