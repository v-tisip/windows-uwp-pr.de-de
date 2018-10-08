---
author: TylerMSFT
title: Benutzeraktivitäten geräteübergreifend fortsetzen
description: In diesem Thema wird beschrieben, wie Benutzer fortsetzen können, was sie in ihrer App erledigt haben, auch über mehrere Geräte hinweg.
keywords: benutzeraktivität, benutzeraktivitäten, zeitachse, cortana aufgaben weiterführen, cortana begonnene aufgaben bearbeiten, project rome
ms.author: twhitney
ms.date: 04/27/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 53aac2375d60df3cd9493f315b20431961378fe8
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4420194"
---
# <a name="continue-user-activity-even-across-devices"></a><span data-ttu-id="762b0-104">Benutzeraktivitäten geräteübergreifend fortsetzen</span><span class="sxs-lookup"><span data-stu-id="762b0-104">Continue user activity, even across devices</span></span>

<span data-ttu-id="762b0-105">In diesem Thema wird beschrieben, wie Benutzer fortsetzen können, was sie in ihrer App, auf ihrem PC und anderen Geräten erledigt haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-105">This topic describes how to help users resume what they were doing in your app on their PC, and across devices.</span></span>

## <a name="user-activities-and-timeline"></a><span data-ttu-id="762b0-106">Benutzeraktivitäten und die Zeitachse</span><span class="sxs-lookup"><span data-stu-id="762b0-106">User Activities and Timeline</span></span>

<span data-ttu-id="762b0-107">Jeden Tag verbringen wir viel Zeit an unterschiedlichen Geräten.</span><span class="sxs-lookup"><span data-stu-id="762b0-107">Our time each day is spread across multiple devices.</span></span> <span data-ttu-id="762b0-108">Im Bus benutzen wir unser Telefon, tagsüber im Büro den PC und abends surfen wir auf dem Smartphone oder dem Tablet.</span><span class="sxs-lookup"><span data-stu-id="762b0-108">We might use our phone while on the bus, a PC during the day, then a phone or tablet in the evening.</span></span> <span data-ttu-id="762b0-109">Wenn Sie in Windows10, Build 1803 oder höher, eine [Benutzeraktivität](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) erstellen, wird diese Aktivität in der Windows-Zeitachse und in der Funktion „Dort fortfahren, wo Sie aufgehört haben” in Cortana angezeigt.</span><span class="sxs-lookup"><span data-stu-id="762b0-109">Starting in Windows 10 Build 1803 or higher, creating a [User Activity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) makes that activity appear in Windows Timeline and in Cortana's Pick up where I left off feature.</span></span> <span data-ttu-id="762b0-110">Die Zeitachse bietet eine umfassende Aufgabenansicht, die Ihnen über Benutzeraktivitäten in einer chronologischen Ansicht anzeigt, woran Sie bisher gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-110">Timeline is a rich task view that takes advantage of User Activities to show a chronological view of what you’ve been working on.</span></span> <span data-ttu-id="762b0-111">Hier kann auch aufgezeichnet werden, woran Sie auf unterschiedlichen Geräten gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-111">It can also include what you were working on across devices.</span></span>

![Bild der Windows-Zeitachse](images/timeline.png)

<span data-ttu-id="762b0-113">Wenn Sie Ihr Smartphone mit Ihrem Windows-PC verbinden, können Sie an den Aufgaben weiterarbeiten, die Sie auf Ihrem iOS- oder Android-Gerät begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-113">Likewise, linking your phone to your Windows PC allows you to continue what you were doing previously on your iOS or Android device.</span></span>

<span data-ttu-id="762b0-114">Bei einer **UserActivity** handelt es sich um eine bestimmte Aufgabe, die der Nutzer in Ihrer App bearbeitet hat.</span><span class="sxs-lookup"><span data-stu-id="762b0-114">Think of a **UserActivity** as something specific the user was working on within your app.</span></span> <span data-ttu-id="762b0-115">Ein Beispiel für eine **UserActivity** könnte ein Feed Ihres RSS-Readers sein, den Sie kürzlich gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-115">For example, if you are using a RSS reader, a **UserActivity** could be the feed that you are reading.</span></span> <span data-ttu-id="762b0-116">Wenn Sie ein Spiel spielen, ist die **UserActivity** möglicherweise das Level, das Sie erreicht haben.</span><span class="sxs-lookup"><span data-stu-id="762b0-116">If you are playing a game, the **UserActivity** could be the level that you are playing.</span></span> <span data-ttu-id="762b0-117">Ein anderes Beispiel für eine **UserActivity** könnte eine Playlist in Ihrer Musik-App sein.</span><span class="sxs-lookup"><span data-stu-id="762b0-117">If you are listening to a music app, the **UserActivity** could be the playlist that you are listening to.</span></span> <span data-ttu-id="762b0-118">Wenn Sie an einem Dokument arbeiten, stellt die **UserActivity** unter Umständen die Stelle dar, an der Sie aufgehört haben zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="762b0-118">If you are working on a document, the **UserActivity** could be where you left off working on it, and so on.</span></span>  <span data-ttu-id="762b0-119">Kurz gesagt: Bei einer **UserActivity** handelt es sich um ein Ziel in Ihrer App, das ein Nutzer erreichen und an dem er später weiter die Arbeit wieder aufnehmen kann.</span><span class="sxs-lookup"><span data-stu-id="762b0-119">In short, a **UserActivity** represents a destination within your app so that enables the user to resume what they were doing.</span></span>

<span data-ttu-id="762b0-120">Wenn Sie mit einer **UserActivity** interagieren, indem Sie [UserActivity.CreateSession](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.createsession) aufrufen, erstellt das System einen Verlaufsdatensatz, der die Start- und Endzeit der **UserActivity** angibt.</span><span class="sxs-lookup"><span data-stu-id="762b0-120">When you engage with a **UserActivity** by calling [UserActivity.CreateSession](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.createsession), the system creates a history record indicating the start and end time for that **UserActivity**.</span></span> <span data-ttu-id="762b0-121">Wie Sie mit der **UserActivity** im Laufe der Zeit mehrmals interagieren, werden mehrere Verlaufsdatensätze für sie aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="762b0-121">As you re-engage with that **UserActivity** over time, multiple history records are recorded for it.</span></span>

## <a name="add-user-activities-to-your-app"></a><span data-ttu-id="762b0-122">Benutzeraktivitäten zur App hinzufügen</span><span class="sxs-lookup"><span data-stu-id="762b0-122">Add User Activities to your app</span></span>

<span data-ttu-id="762b0-123">Über die [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) wird die Benutzerbindung in Windows gemessen.</span><span class="sxs-lookup"><span data-stu-id="762b0-123">A [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) is the unit of user engagement in Windows.</span></span> <span data-ttu-id="762b0-124">Sie besteht aus drei Teilen: einem URI zur Aktivierung der App, zu der die Aktivität gehört, visuelle Elemente sowie Metadaten, die die Aktivität beschreiben.</span><span class="sxs-lookup"><span data-stu-id="762b0-124">It has three parts: a URI used to activate the app the activity belongs to, visuals, and metadata that describes the activity.</span></span>

1. <span data-ttu-id="762b0-125">Der [ActivationUri](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activationuri#Windows_ApplicationModel_UserActivities_UserActivity_ActivationUri) wird verwendet, um die Anwendung in einem bestimmten Kontext fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="762b0-125">The [ActivationUri](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activationuri#Windows_ApplicationModel_UserActivities_UserActivity_ActivationUri) is used to resume the application with a specific context.</span></span> <span data-ttu-id="762b0-126">Normalerweise wird dieser Link in Form eines Protokollhandlers für ein Schema (z.B. "my-App://page2?action=edit") oder eines App-URI-Handlers (z. B. http://constoso.com/page2?action=edit) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="762b0-126">Typically, this link takes the form of protocol handler for a scheme (e.g. “my-app://page2?action=edit”) or of an AppUriHandler (e.g. http://constoso.com/page2?action=edit).</span></span>
2. <span data-ttu-id="762b0-127">[VisualElements](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.visualelements) stellt eine Klasse bereit, die es dem Benutzer ermöglicht, eine Aktivität visuell mit einem Titel, einer Beschreibung oder Adaptive Karten-Elementen zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="762b0-127">[VisualElements](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.visualelements) exposes a class that allows the user to visually identify an activity with a title, description, or Adaptive Card elements.</span></span>
3. <span data-ttu-id="762b0-128">In [Content](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityvisualelements.content#Windows_ApplicationModel_UserActivities_UserActivityVisualElements_Content) können Sie Metadaten für die Aktivität speichern, die zum Gruppieren und Abrufen von Aktivitäten in einem bestimmten Kontext verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="762b0-128">Finally, [Content](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityvisualelements.content#Windows_ApplicationModel_UserActivities_UserActivityVisualElements_Content) is where you can store metadata for the activity that can be used to group and retrieve activities under a specific context.</span></span> <span data-ttu-id="762b0-129">Häufig handelt es sich hierbei um [http://schema.org](http://schema.org)-Daten.</span><span class="sxs-lookup"><span data-stu-id="762b0-129">Often, this takes the form of [http://schema.org](http://schema.org) data.</span></span>

<span data-ttu-id="762b0-130">So fügen Sie Ihrer App eine **UserActivity** hinzu:</span><span class="sxs-lookup"><span data-stu-id="762b0-130">To add a **UserActivity** to your app:</span></span>

1. <span data-ttu-id="762b0-131">Wenn der Kontext des Benutzers innerhalb der App geändert wird (z.B. Seitennavigation, neues Spiellevel etc.), erstellen Sie **UserActivity**-Objekte.</span><span class="sxs-lookup"><span data-stu-id="762b0-131">Generate **UserActivity** objects when your user’s context changes within the app (such as page navigation, new game level, etc.)</span></span>
2. <span data-ttu-id="762b0-132">Füllen Sie **UserActivity**-Objekte mit den mindestens erforderlichen Feldern: [ActivityId](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activityid#Windows_ApplicationModel_UserActivities_UserActivity_ActivityId), [ActivationUri](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activationuri) und [UserActivity.VisualElements.DisplayText ](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityvisualelements.displaytext#Windows_ApplicationModel_UserActivities_UserActivityVisualElements_DisplayText).</span><span class="sxs-lookup"><span data-stu-id="762b0-132">Populate **UserActivity** objects with the minimum set of required fields: [ActivityId](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activityid#Windows_ApplicationModel_UserActivities_UserActivity_ActivityId), [ActivationUri](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.activationuri), and [UserActivity.VisualElements.DisplayText](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityvisualelements.displaytext#Windows_ApplicationModel_UserActivities_UserActivityVisualElements_DisplayText).</span></span>
3. <span data-ttu-id="762b0-133">Fügen Sie Ihrer App einen benutzerdefinierten Schema-Handler hinzu, damit er erneut durch eine **UserActivity** aktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="762b0-133">Add a custom scheme handler to your app so it can be re-activated by a **UserActivity**.</span></span>

<span data-ttu-id="762b0-134">Eine **UserActivity** kann mit nur wenigen Codezeilen in eine App integriert werden.</span><span class="sxs-lookup"><span data-stu-id="762b0-134">A **UserActivity** can be integrated into an app with just a few lines of code.</span></span> <span data-ttu-id="762b0-135">Angenommen, dieser Code befindet sich in „MainPage.xaml.cs” in der MainPage-Klasse (Hinweis: es wird von `using Windows.ApplicationModel.UserActivities;` ausgegangen):</span><span class="sxs-lookup"><span data-stu-id="762b0-135">For example, imagine this code in MainPage.xaml.cs, inside the MainPage class (note: assumes `using Windows.ApplicationModel.UserActivities;`):</span></span>

```csharp
UserActivitySession _currentActivity;
private async Task GenerateActivityAsync()
{
    // Get the default UserActivityChannel and query it for our UserActivity. If the activity doesn't exist, one is created.
    UserActivityChannel channel = UserActivityChannel.GetDefault();
    UserActivity userActivity = await channel.GetOrCreateUserActivityAsync("MainPage");
 
    // Populate required properties
    userActivity.VisualElements.DisplayText = "Hello Activities";
    userActivity.ActivationUri = new Uri("my-app://page2?action=edit");
     
    //Save
    await userActivity.SaveAsync(); //save the new metadata
 
    // Dispose of any current UserActivitySession, and create a new one.
    _currentActivity?.Dispose();
    _currentActivity = userActivity.CreateSession();
}
```

<span data-ttu-id="762b0-136">Die erste Zeile in der oben genannten `GenerateActivityAsync()`-Methode ruft [UserActivityChannel ](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitychannel) eines Benutzers auf.</span><span class="sxs-lookup"><span data-stu-id="762b0-136">The first line in the `GenerateActivityAsync()` method above gets a user’s [UserActivityChannel](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitychannel).</span></span> <span data-ttu-id="762b0-137">Hierbei handelt es sich um den Feed, in dem die Aktivitäten dieser App veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="762b0-137">This is the feed that this app’s activities will be published to.</span></span> <span data-ttu-id="762b0-138">Die nächste Zeile fragt den Kanal einer Aktivität namens `MainPage` an.</span><span class="sxs-lookup"><span data-stu-id="762b0-138">The next line queries the channel of an activity called `MainPage`.</span></span>

* <span data-ttu-id="762b0-139">Ihre App sollte Aktivitäten so benennen, dass jedes Mal dieselbe ID generiert wird, wenn der Benutzer sich an einer bestimmten Stelle in der App befindet.</span><span class="sxs-lookup"><span data-stu-id="762b0-139">Your app should name activities in such a way that same ID is generated each time the user is in a particular location in the app.</span></span> <span data-ttu-id="762b0-140">Wenn die App beispielsweise seitenbasiert ist, verwenden Sie einen Bezeichner für die Seite. Wenn sie dokumentbasiert ist, verwenden Sie den Dokumentnamen (oder ein Hash des Namens).</span><span class="sxs-lookup"><span data-stu-id="762b0-140">For example, if your app is page-based, use an identifier for the page; if its document based, use the name of the doc (or a hash of the name).</span></span>
* <span data-ttu-id="762b0-141">Wenn im Feed eine vorhandene Aktivität mit derselben ID vorhanden ist, wird die Aktivität vom Kanal so zurückgegeben, dass `UserActivity.State`den Status [Veröffentlicht](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitystate)) hat.</span><span class="sxs-lookup"><span data-stu-id="762b0-141">If there is an existing activity in the feed with the same ID, that activity will be returned from the channel with `UserActivity.State` set to [Published](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitystate)).</span></span> <span data-ttu-id="762b0-142">Wenn keine Aktivität mit diesem Namen vorhanden ist, wird neue Aktivität mit dem `UserActivity.State` \*\*Neu \*\* zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="762b0-142">If there is no activity with that name, and new activity is returned with `UserActivity.State` set to **New**.</span></span>
* <span data-ttu-id="762b0-143">Aktivitäten sind auf Ihre App beschränkt.</span><span class="sxs-lookup"><span data-stu-id="762b0-143">Activities are scoped to your app.</span></span> <span data-ttu-id="762b0-144">Es gibt keine Konflikte zwischen Ihrer Aktivitäts-ID und Aktivitäts-IDs in anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="762b0-144">You do not need to worry about your activity ID colliding with IDs in other apps.</span></span>

<span data-ttu-id="762b0-145">Nach dem Abrufen oder Erstellen der **UserActivity**, geben Sie die beiden anderen erforderlichen Felder an: `UserActivity.VisualElements.DisplayText`und `UserActivity.ActivationUri`.</span><span class="sxs-lookup"><span data-stu-id="762b0-145">After getting or creating the **UserActivity**, specify the other two required fields:  `UserActivity.VisualElements.DisplayText`and `UserActivity.ActivationUri`.</span></span>

<span data-ttu-id="762b0-146">Speichern Sie anschließend die **UserActivity**-Metadaten durch Aufrufen von [SaveAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.saveasync) und schließlich [CreateSession](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.createsession), die eine [UserActivitySession ](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitysession) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="762b0-146">Next, save the **UserActivity** metadata by calling [SaveAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.saveasync), and finally [CreateSession](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity.createsession), which returns a [UserActivitySession](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitysession).</span></span> <span data-ttu-id="762b0-147">Mit dem Objekt **UserActivitySession** können wir verwalten, wann der Benutzer tatsächlich mit der \*\*UserActivity \*\* beschäftigt ist.</span><span class="sxs-lookup"><span data-stu-id="762b0-147">The **UserActivitySession** is the object that we can use to manage when the user is actually engaged with the **UserActivity**.</span></span> <span data-ttu-id="762b0-148">Wir sollten z.B. `Dispose()` in der **UserActivitySession** aufrufen, wenn der Benutzer die Seite verlässt.</span><span class="sxs-lookup"><span data-stu-id="762b0-148">For example, we should call `Dispose()` on the **UserActivitySession** when the user leaves the page.</span></span> <span data-ttu-id="762b0-149">Im obigen Beispiel rufen wir auch `Dispose()` in `_currentActivity` auf, bevor wir `CreateSession()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="762b0-149">In the example above, we also call `Dispose()` on `_currentActivity` before calling `CreateSession()`.</span></span> <span data-ttu-id="762b0-150">Dies ist der Fall, weil wir `_currentActivity` zu einem Mitgliedsfeld unserer Seite gemacht haben und alle vorhandenen Aktivität beenden möchten, bevor wir die neue starten (Hinweis: `?`ist der [Operator mit NULL-Bedingung](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-conditional-operators), der auf Null testet, bevor der Member-Zugriff durchgeführt wird).</span><span class="sxs-lookup"><span data-stu-id="762b0-150">This is because we made `_currentActivity` a member field of our page, and we want to stop any existing activity before we start the new one (note: the `?` is the [null-conditional operator](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-conditional-operators) which tests for null before performing the member access).</span></span>

<span data-ttu-id="762b0-151">Da es sich in diesem Fall beim `ActivationUri` um ein benutzerdefiniertes Schema handelt, müssen wir außerdem das Protokoll im Anwendungsmanifest registrieren.</span><span class="sxs-lookup"><span data-stu-id="762b0-151">Since, in this case, the `ActivationUri` is a custom scheme, we also need to register the protocol in the application manifest.</span></span> <span data-ttu-id="762b0-152">Dies erfolgt in der Package.appmanifest XML-Datei oder mithilfe des Designers.</span><span class="sxs-lookup"><span data-stu-id="762b0-152">This is done in the Package.appmanifest XML file, or by using the designer.</span></span>

<span data-ttu-id="762b0-153">Wenn Sie die Änderung mit dem Designer durchführen möchten, doppelklicken Sie auf die Datei „Package.appmanifest” in Ihrem Projekt, um den Designer zu starten. Wählen Sie dann die Registerkarte **Deklarationen** und fügen Sie eine **Protokoll**-Definition hinzu.</span><span class="sxs-lookup"><span data-stu-id="762b0-153">To make the change with the designer, double-click the Package.appmanifest file in your project to launch the designer, select the **Declarations** tab and add a **Protocol** definition.</span></span> <span data-ttu-id="762b0-154">Die einzige Eigenschaft, die ausgefüllt werden muss, ist **Name**.</span><span class="sxs-lookup"><span data-stu-id="762b0-154">The only property that needs to be filled out, for now, is **Name**.</span></span> <span data-ttu-id="762b0-155">Sie sollte mit dem URI übereinstimmen, den wir oben angegeben haben – `my-app`.</span><span class="sxs-lookup"><span data-stu-id="762b0-155">It should match the URI we specified above, `my-app`.</span></span>

<span data-ttu-id="762b0-156">Nun müssen wir etwas Code schreiben, um der App mitzuteilen, was passiert, wenn sie von einem Protokoll aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="762b0-156">Now we need to write some code to tell the app what to do when it’s been activated by a protocol.</span></span> <span data-ttu-id="762b0-157">Wir überschreiben die `OnActivated`-Methode in „App.xaml.cs” wie folgt, sodass der URI an die Hauptseite übergeben wird:</span><span class="sxs-lookup"><span data-stu-id="762b0-157">We’ll override the `OnActivated` method in App.xaml.cs to pass the URI on to the main page, like so:</span></span>

```csharp
protected override void OnActivated(IActivatedEventArgs e)
{
    if (e.Kind == ActivationKind.Protocol)
    {
        var uriArgs = e as ProtocolActivatedEventArgs;
        if (uriArgs != null)
        {
            if (uriArgs.Uri.Host == "page2")
            {
                // Navigate to the 2nd page of the  app
            }
        }
    }
    Window.Current.Activate();
}
```

<span data-ttu-id="762b0-158">Der Code bewirkt, dass erkannt wird, ob die App über ein Protokoll aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="762b0-158">What this code does is detect whether the app was activated via a protocol.</span></span> <span data-ttu-id="762b0-159">Wenn dem so ist, wird ermittelt, wie die App den Vorgang fortsetzen kann, für den sie aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="762b0-159">If it was, then it looks to see what the app should do to resume the task it is being activated for.</span></span> <span data-ttu-id="762b0-160">Da es sich um eine einfache App handelt, setzt sie nur eine einzige Aktivität fort: Wenn die App eingeblendet wird, befinden Sie sich auf der sekundären Seite.</span><span class="sxs-lookup"><span data-stu-id="762b0-160">Being a simple app, the only activity this app resumes is putting you on on the secondary page when the app comes up.</span></span>

## <a name="use-adaptive-cards-to-improve-the-timeline-experience"></a><span data-ttu-id="762b0-161">Adaptive Karten verwenden, um die Zeitachse zu verbessern</span><span class="sxs-lookup"><span data-stu-id="762b0-161">Use Adaptive Cards to improve the Timeline experience</span></span>

<span data-ttu-id="762b0-162">Aktivitäten des Benutzers werden in Cortana und der Zeitachse angezeigt.</span><span class="sxs-lookup"><span data-stu-id="762b0-162">User Activities appear in Cortana and Timeline.</span></span> <span data-ttu-id="762b0-163">Wenn Aktivitäten in der Zeitachse angezeigt werden, geschieht dies über das [Adaptive Karten](http://adaptivecards.io/)-Framework.</span><span class="sxs-lookup"><span data-stu-id="762b0-163">When activities appear in Timeline, we display them using the [Adaptive Card](http://adaptivecards.io/) framework.</span></span> <span data-ttu-id="762b0-164">Wenn Sie nicht für jede Aktivität eine adaptive Karte angeben, erstellt die Zeitachse automatisch eine einfache Aktivitätskarte basierend auf dem App-Namen und -Symbol, dem Titelfeld und optional auf der Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="762b0-164">If you do not provide an adaptive card for each activity, Timeline will automatically create a simple activity card based on your application name and icon, the title field and optional description field.</span></span> <span data-ttu-id="762b0-165">Es folgt ein Beispiel für die Nutzlast einer adaptiven Karte sowie die Karte, die produziert wird.</span><span class="sxs-lookup"><span data-stu-id="762b0-165">Below is an example Adaptive Card payload and the card it produces.</span></span>

![Eine adaptive Karte](images/adaptivecard.png)<span data-ttu-id="762b0-167">]</span><span class="sxs-lookup"><span data-stu-id="762b0-167">]</span></span>

<span data-ttu-id="762b0-168">Beispiel für die Nutzlast einer adaptiven Karte mit JSON-Zeichenfolge:</span><span class="sxs-lookup"><span data-stu-id="762b0-168">Example adaptive card payload JSON string:</span></span>

```json
{ 
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json", 
  "type": "AdaptiveCard", 
  "version": "1.0",
  "backgroundImage": "https://winblogs.azureedge.net/win/2017/11/eb5d872c743f8f54b957ff3f5ef3066b.jpg", 
  "body": [ 
    { 
      "type": "Container", 
      "items": [ 
        { 
          "type": "TextBlock", 
          "text": "Windows Blog", 
          "weight": "bolder", 
          "size": "large", 
          "wrap": true, 
          "maxLines": 3 
        }, 
        { 
          "type": "TextBlock", 
          "text": "Training Haiti’s radiologists: St. Louis doctor takes her teaching global", 
          "size": "default", 
          "wrap": true, 
          "maxLines": 3 
        } 
      ] 
    } 
  ]
}
```

<span data-ttu-id="762b0-169">Fügen Sie die Nutzlast einer adaptiven Karte mit JSON-Zeichenfolge wie folgt zur **UserActivity** hinzu:</span><span class="sxs-lookup"><span data-stu-id="762b0-169">Add the Adaptive Cards payload as a JSON string to the **UserActivity** like this:</span></span>

```csharp
activity.VisualElements.Content = 
Windows.UI.Shell.AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonCardText); // where jsonCardText is a JSON string that represents the card
```

## <a name="cross-platform-and-service-to-service-integration"></a><span data-ttu-id="762b0-170">Plattformübergreifende Integration und Integration zwischen Diensten</span><span class="sxs-lookup"><span data-stu-id="762b0-170">Cross-platform and Service-to-service integration</span></span>

<span data-ttu-id="762b0-171">Wenn Ihre App plattformübergreifend ausgeführt wird (z.B. auf Android und iOS) oder der Benutzerzustand in der Cloud verwaltet wird, können Sie UserActivities über [Microsoft Graph](https://developer.microsoft.com/graph/) veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="762b0-171">If your app runs cross-platform (for example on Android and iOS), or maintains user state in the cloud, you can publish UserActivities via [Microsoft Graph](https://developer.microsoft.com/graph/).</span></span>
<span data-ttu-id="762b0-172">Nachdem Ihre App oder Ihr Dienst mit einem Microsoft-Konto authentifiziert wurde, sind lediglich zwei einfache REST-Aufrufe erforderlich, um anhand der gleichen Daten wie weiter oben beschrieben [Aktivitäts](https://developer.microsoft.com/graph/docs/api-reference/beta/api/projectrome_put_activity)- und [Verlaufs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/projectrome_historyitem)-Objekte zu generieren.</span><span class="sxs-lookup"><span data-stu-id="762b0-172">Once your application or service is authenticated with a Microsoft Account, it just takes two simple REST calls to generate [Activity](https://developer.microsoft.com/graph/docs/api-reference/beta/api/projectrome_put_activity) and [History](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/projectrome_historyitem) objects, using the same data as described above.</span></span>

## <a name="summary"></a><span data-ttu-id="762b0-173">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="762b0-173">Summary</span></span>

<span data-ttu-id="762b0-174">Sie können die [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities)-API verwenden, um Ihre App in der Zeitachse und Cortana anzeigen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="762b0-174">You can use the [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities) API to make your app appear in Timeline and Cortana.</span></span>
* <span data-ttu-id="762b0-175">Weitere Informationen zur **UserActivity**-API finden Sie im [Windows Dev Center](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities)</span><span class="sxs-lookup"><span data-stu-id="762b0-175">Learn more about the **UserActivity** API on the [Windows Dev Center](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities)</span></span>
* <span data-ttu-id="762b0-176">Sehen Sie sich den [Beispielcode](https://github.com/Microsoft/project-rome) an.</span><span class="sxs-lookup"><span data-stu-id="762b0-176">Check out the [sample code](https://github.com/Microsoft/project-rome).</span></span>
* <span data-ttu-id="762b0-177">Hier finden Sie [weitere ausgeklügelte adaptive Karten](http://adaptivecards.io/).</span><span class="sxs-lookup"><span data-stu-id="762b0-177">See [more sophisticated Adaptive Cards](http://adaptivecards.io/).</span></span>
* <span data-ttu-id="762b0-178">Veröffentlichen Sie eine **UserActivity** von iOS, Android oder Ihrem Webdienst über [Microsoft Graph](https://developer.microsoft.com/graph/).</span><span class="sxs-lookup"><span data-stu-id="762b0-178">Publish a **UserActivity** from iOS, Android or your web service via [Microsoft Graph](https://developer.microsoft.com/graph/).</span></span>
* <span data-ttu-id="762b0-179">Erfahren Sie mehr zu [Project Rome auf GitHub](https://github.com/Microsoft/project-rome).</span><span class="sxs-lookup"><span data-stu-id="762b0-179">Learn more about [Project Rome on GitHub](https://github.com/Microsoft/project-rome).</span></span>

## <a name="key-apis"></a><span data-ttu-id="762b0-180">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="762b0-180">Key APIs</span></span>

* [<span data-ttu-id="762b0-181">UserActivities-namespace</span><span class="sxs-lookup"><span data-stu-id="762b0-181">UserActivities namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities)

## <a name="related-topics"></a><span data-ttu-id="762b0-182">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="762b0-182">Related topics</span></span>

* [<span data-ttu-id="762b0-183">Benutzeraktivitäten (Projekt "ROME" Dokumente)</span><span class="sxs-lookup"><span data-stu-id="762b0-183">User Activities (Project Rome docs)</span></span>](https://docs.microsoft.com/windows/project-rome/user-activities/)
* [<span data-ttu-id="762b0-184">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="762b0-184">Adaptive cards</span></span>](https://docs.microsoft.com/adaptive-cards/)
* [<span data-ttu-id="762b0-185">Adaptive Karten, Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="762b0-185">Adaptive cards visualizer, samples</span></span>](http://adaptivecards.io/)
* [<span data-ttu-id="762b0-186">Behandeln der URI-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="762b0-186">Handle URI activation</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
* [<span data-ttu-id="762b0-187">Mit Ihren Kunden auf jeder Plattform mit Microsoft Graph, Aktivitätenfeed und adaptiven Karten kommunizieren</span><span class="sxs-lookup"><span data-stu-id="762b0-187">Engaging with your customers on any platform using the Microsoft Graph, Activity Feed, and Adaptive Cards</span></span>](https://channel9.msdn.com/Events/Connect/2017/B111)
* [<span data-ttu-id="762b0-188">Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="762b0-188">Microsoft Graph</span></span>](https://developer.microsoft.com/graph/)