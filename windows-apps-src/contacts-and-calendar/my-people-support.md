---
title: "Support für Meine Kontakte zu einer Anwendung hinzufügen"
description: "Erläutert, wie Sie einer Anwendung Support für „Meine Kontakte” hinzufügen, und wie Sie Kontakte auf der Startseite anheften und entfernen"
author: mukin
ms.author: mukin
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 61f73fd2fc0d14d0d1d478d67763c9b0e252cd36
ms.sourcegitcommit: ec18e10f750f3f59fbca2f6a41bf1892072c3692
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2017
---
# <a name="adding-my-people-support-to-an-application"></a><span data-ttu-id="07f15-104">Support für Meine Kontakte zu einer Anwendung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="07f15-104">Adding My People support to an application</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07f15-105">**VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen als Ziel [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) angeben und [Insider-Builds 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) oder höher ausführen, um die API „Meine Kontakte” zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="07f15-105">**PRERELEASE | Requires Fall Creators Update**: You must target [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) and be running [Insider build 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) or higher to use the My People APIs.</span></span>

<span data-ttu-id="07f15-106">Die Feature „Meine Kontakte” ermöglicht Benutzern das Anheften von Kontakten an die Taskleiste, um neue Kontaktobjekt zu erstellen, die auf unterschiedliche Weise miteinander interagieren können.</span><span class="sxs-lookup"><span data-stu-id="07f15-106">The My People feature allows users to pin contacts from an application directly to their taskbar, which creates a new contact object that they can interact with in several ways.</span></span> <span data-ttu-id="07f15-107">In diesem Artikel wird gezeigt, wie Sie Support für dieses Feature hinzufügen können, damit Benutzer Kontakte direkt in der App anheften können.</span><span class="sxs-lookup"><span data-stu-id="07f15-107">This article shows how you can add support for this feature, allowing users to pin contacts directly from your app.</span></span> <span data-ttu-id="07f15-108">Wenn Kontakte angeheftet sind, werden neue Arten an Benutzerinteraktionen verfügbar, z.B. [Meine Kontakte freigeben](my-people-sharing.md) und [Benachrichtigungen ](my-people-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="07f15-108">When contacts are pinned, new types of user interaction become available, such as [My People sharing](my-people-sharing.md) and [notifications](my-people-notifications.md).</span></span>

![Chat für Meine Kontakte](images/my-people-chat.png)

## <a name="requirements"></a><span data-ttu-id="07f15-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="07f15-110">Requirements</span></span>

+ <span data-ttu-id="07f15-111">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="07f15-111">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="07f15-112">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="07f15-112">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="07f15-113">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="07f15-113">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="07f15-114">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="07f15-114">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="overview"></a><span data-ttu-id="07f15-115">Übersicht</span><span class="sxs-lookup"><span data-stu-id="07f15-115">Overview</span></span>

<span data-ttu-id="07f15-116">Es gibt drei Dinge, die durchgeführt werden müssen, damit die Anwendung das Feature„ Meine Kontakte” verwenden kann:</span><span class="sxs-lookup"><span data-stu-id="07f15-116">There are three things you need to do to enable your application to use the My People feature:</span></span>

1. [<span data-ttu-id="07f15-117">Unterstützung für den „ShareTarget”-Aktivierungsvertrag im Anwendungsmanifest bekannt geben.</span><span class="sxs-lookup"><span data-stu-id="07f15-117">Declare support for the shareTarget activation contract in your application manifest.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#declaring-support-for-the-share-contract)
2. [<span data-ttu-id="07f15-118">Versehen Sie die Kontakte, die der Benutzer auf Ihre freigeben kann mit Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="07f15-118">Annotate the contacts that the users can share to using your app.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#annotating-contacts)
3.  <span data-ttu-id="07f15-119">Unterstützen Sie mehrere Instanzen Ihrer Anwendung, die zur gleichen Zeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="07f15-119">Support multiple instances of your application running at the same time.</span></span> <span data-ttu-id="07f15-120">Benutzer müssen mit einer vollständigen Version Ihrer Anwendung interagieren, während Sie diese im Kontaktbereich verwenden.</span><span class="sxs-lookup"><span data-stu-id="07f15-120">Users must be able to interact with a full version of your application while using it in a contact panel.</span></span>  <span data-ttu-id="07f15-121">Sie können diese sogar in mehreren Kontaktlisten gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="07f15-121">They may even use it in multiple contact panels at once.</span></span>  <span data-ttu-id="07f15-122">Um dies zu unterstützen, muss Ihre Anwendung mehrere Ansichten gleichzeitig ausführen können.</span><span class="sxs-lookup"><span data-stu-id="07f15-122">To support this, your application needs to be able to run multiple views simultaneously.</span></span> <span data-ttu-id="07f15-123">Weitere Informationen hierzu finden Sie im Artikel ["Anzeigen mehrerer Ansichten für eine App"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span><span class="sxs-lookup"><span data-stu-id="07f15-123">To learn how to do this, see the article ["show multiple views for an app"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span></span>

<span data-ttu-id="07f15-124">Wenn Sie dies getan haben, wird die Anwendung in der Kontaktliste für Kontakte mit Kommentaren angezeigt.</span><span class="sxs-lookup"><span data-stu-id="07f15-124">When you’ve done this, your application will appear in the contact panel for annotated contacts.</span></span>

## <a name="declaring-support-for-the-contract"></a><span data-ttu-id="07f15-125">Deklarieren von Support für den Vertrag</span><span class="sxs-lookup"><span data-stu-id="07f15-125">Declaring support for the contract</span></span>

<span data-ttu-id="07f15-126">Um Unterstützung für den Vertrag „Meine Kontakte” zu deklarieren, öffnen Sie die Anwendung in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07f15-126">To declare support for the My People contract, open your application in Visual Studio.</span></span> <span data-ttu-id="07f15-127">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei **Package.appxmanifest** und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="07f15-127">From the **Solution Explorer**, right click **Package.appxmanifest** and select **Open With**.</span></span> <span data-ttu-id="07f15-128">Wählen Sie aus dem Menü anschließend **XML (Text)-Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="07f15-128">From the menu, select **XML (Text) Editor)** and click **OK**.</span></span> <span data-ttu-id="07f15-129">Nehmen Sie danach folgenden Änderungen am Manifest vor.</span><span class="sxs-lookup"><span data-stu-id="07f15-129">Make the following changes to the manifest:</span></span>

**<span data-ttu-id="07f15-130">Vorher</span><span class="sxs-lookup"><span data-stu-id="07f15-130">Before</span></span>**

```xml
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">

    <Applications>
        <Application Id="MyApp"
          Executable="$targetnametoken$.exe"
          EntryPoint="My.App">
        </Application>
    </Applications>

```

**<span data-ttu-id="07f15-131">Nachher</span><span class="sxs-lookup"><span data-stu-id="07f15-131">After</span></span>**

```xml
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4">

    <Applications>
        <Application Id="MyApp"
          Executable="$targetnametoken$.exe"
          EntryPoint="My.App">
          <Extensions>
            <uap4:Extension Category="windows.contactPanel" />
          </Extensions>
        </Application>
    </Applications>

```

<span data-ttu-id="07f15-132">Durch diesen Zusatz kann Ihre Anwendung jetzt über den Vertrag **Windows. ContactPanel** gestartet werden, die Sie mit mit Kontakten in der Kontaktliste interagieren können.</span><span class="sxs-lookup"><span data-stu-id="07f15-132">With this addition, your application can now be launched through the **windows.ContactPanel** contract, which allows you to interact with contact panels.</span></span>

## <a name="annotating-contacts"></a><span data-ttu-id="07f15-133">Kontakte mit Kommentaren versehen</span><span class="sxs-lookup"><span data-stu-id="07f15-133">Annotating contacts</span></span>

<span data-ttu-id="07f15-134">Um Kontakte von Ihrer Anwendung über den Bereich „Meine Kontakte” in der Taskleiste anzuzueigen, müssen Sie diese auf den Windows-Kontaktspeicher schreiben.</span><span class="sxs-lookup"><span data-stu-id="07f15-134">To allow contacts from your application to appear in the taskbar via the My People pane, you need to write them to the Windows contact store.</span></span>  <span data-ttu-id="07f15-135">Weitere Informationen zum Schreiben von Kontakten finden Sie unter [Beispiel für die Visitenkarte](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span><span class="sxs-lookup"><span data-stu-id="07f15-135">To learn how to write contacts, see the [Contact Card sample](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span></span>

<span data-ttu-id="07f15-136">Ihre Anwendung muss ebenfalls eine Anmerkung für jeden Kontakt schreiben.</span><span class="sxs-lookup"><span data-stu-id="07f15-136">Your application must also write an annotation to each contact.</span></span> <span data-ttu-id="07f15-137">Kommentare sind Datenteile von Ihrer Anwendung, die mit einem Kontakt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="07f15-137">Annotations are pieces of data from your application that are associated with a contact.</span></span> <span data-ttu-id="07f15-138">Die Anmerkung muss die aktivierbare Klassen für die gewünschte Ansicht in seinem Element **ProviderProperties** und Support für den **ContactProfile**-Vorgang deklarieren.</span><span class="sxs-lookup"><span data-stu-id="07f15-138">The annotation must contain the activatable class corresponding to your desired view in its **ProviderProperties** member, and declare support for the **ContactProfile** operation.</span></span>

<span data-ttu-id="07f15-139">Sie können Kontakten jederzeit einen Kommentar hinzufügen, während die App ausgeführt wird, aber in der Regel sollten Sie Kontakte sofort kommentieren, wenn sie dem Windows-Kontaktspeicher hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="07f15-139">You can annotate contacts at any point while your app is running, but generally you should annotate contacts as soon as they are added to the Windows contact store.</span></span>

```Csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    // Create a new contact annotation
    ContactAnnotation annotation = new ContactAnnotation();
    annotation.ContactId = myContact.Id;

    // Add appId and contact panel support to the annotation
    String appId = "MyApp_vqvv5s4y3scbg!App";
    annotation.ProviderProperties.Add("ContactPanelAppID", appId);
    annotation.SupportedOperations = ContactAnnotationOperations::ContactProfile;

    // Save annotation to contact annotation list
    // Windows.ApplicationModel.Contacts.ContactAnnotationList 
    await contactAnnotationList.TrySaveAnnotationAsync(annotation));
}
```

<span data-ttu-id="07f15-140">Die “appId” ist der Paketfamilienname, gefolgt von ‘!’</span><span class="sxs-lookup"><span data-stu-id="07f15-140">The “appId” is the Package Family Name, followed by ‘!’</span></span> <span data-ttu-id="07f15-141">und einer aktivierbaren Klassen-ID.</span><span class="sxs-lookup"><span data-stu-id="07f15-141">and the activatable class ID.</span></span> <span data-ttu-id="07f15-142">Um den Paketfamiliennamen zu such, öffnen Sie **Package.appxmanifest** mithilfe des Standard-Editors und suchen Sie auf der Registerkarte "Verpacken".</span><span class="sxs-lookup"><span data-stu-id="07f15-142">To find your Package Family Name, open **Package.appxmanifest** using the default editor, and look in the “Packaging” tab.</span></span> <span data-ttu-id="07f15-143">Hier ist "App" die aktivierbare Klasse, die der Anwendungsstart-Ansicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="07f15-143">Here, “App” is the activatable class corresponding to the application startup view.</span></span>

## <a name="allow-contacts-to-invite-new-potential-users"></a><span data-ttu-id="07f15-144">Kontakten die Einladung von neuen potenziellen Benutzern ermöglichen</span><span class="sxs-lookup"><span data-stu-id="07f15-144">Allow contacts to invite new potential users</span></span>

<span data-ttu-id="07f15-145">Standardmäßig wird die Anwendung nur für Kontakte in der Kontaktliste angezeigt, die Sie speziell kommentiert haben.</span><span class="sxs-lookup"><span data-stu-id="07f15-145">By default, your application will only appear in the contact panel for contacts that you have specifically annotated.</span></span>  <span data-ttu-id="07f15-146">Dies vermeidet eine Verwechslungen mit Kontakten, die nicht mit Ihnen durch die App interagiert können.</span><span class="sxs-lookup"><span data-stu-id="07f15-146">This is to avoid confusion with contacts that can’t be interacted with through your app.</span></span>  <span data-ttu-id="07f15-147">Wenn Sie möchten, dass Ihre Anwendung für Kontakte angezeigt wird, deren Ihre Anwendung nicht bekannt ist (z.B. um Benutzer dazu aufzufordern, ihrem Konto Kontakte hinzuzufügen), können Sie Ihrem Manifest Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="07f15-147">If you want your application to appear for contacts that your application doesn’t know about (to invite users to add that contact to their account, for instance), you can add the following to your manifest:</span></span>

**<span data-ttu-id="07f15-148">Vorher</span><span class="sxs-lookup"><span data-stu-id="07f15-148">Before</span></span>**

```Csharp
<Applications>
    <Application Id="MyApp"
      Executable="$targetnametoken$.exe"
      EntryPoint="My.App">
      <Extensions>
        <uap4:Extension Category="windows.contactPanel" />
      </Extensions>
    </Application>
</Applications>
```

**<span data-ttu-id="07f15-149">Nachher</span><span class="sxs-lookup"><span data-stu-id="07f15-149">After</span></span>**

```Csharp
<Applications>
    <Application Id="MyApp"
      Executable="$targetnametoken$.exe"
      EntryPoint="My.App">
      <Extensions>
        <uap4:Extension Category="windows.contactPanel">
            <uap4:ContactPanel SupportsUnknownContacts="true" />
        </uap4:Extension>
      </Extensions>
    </Application>
</Applications>
```

<span data-ttu-id="07f15-150">Aufgrund dieser Änderung wird die Anwendung als verfügbare Option für alle Kontakte in der Kontaktliste angezeigt, die der Benutzer angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="07f15-150">With this change, your application will appear as an available option in the contact panel for all contacts that the user has pinned.</span></span>  <span data-ttu-id="07f15-151">Wenn Ihre Anwendung durch den Kontaktlisten-Vertrag aktiviert ist, sollten Sie überprüfen, ob der Kontakt Ihrer Anwendung bereits bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="07f15-151">When your application is activated using the contact panel contract, you should check to see if the contact is one your application knows about.</span></span>  <span data-ttu-id="07f15-152">Wenn dies nicht der Fall ist, sollten Sie die Benutzerfreundlichkeit Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="07f15-152">If not, you should show your app’s new user experience.</span></span>

![„Meine Kontakte”-Kontaktliste](images/my-people.png)

## <a name="support-for-email-apps"></a><span data-ttu-id="07f15-154">Unterstützung für E-Mail-Apps</span><span class="sxs-lookup"><span data-stu-id="07f15-154">Support for email apps</span></span>

<span data-ttu-id="07f15-155">Wenn Sie eine E-Mail-App schreiben, müssen Sie nicht jeden Kontakt manuell kommentieren.</span><span class="sxs-lookup"><span data-stu-id="07f15-155">If you are writing an email app, you don’t need to annotate every contact manually.</span></span>  <span data-ttu-id="07f15-156">Wenn Sie Unterstützung für die Kontaktliste und das „mailto: protocol” deklarieren, erscheint Ihre Anwendung automatisch für Benutzer mit einer E-Mail-Adresse.</span><span class="sxs-lookup"><span data-stu-id="07f15-156">If you declare support for the contact pane and for the mailto: protocol, your application will automatically appear for users with an email address.</span></span>

## <a name="running-in-the-contact-panel"></a><span data-ttu-id="07f15-157">Ausführen in der Kontaktliste</span><span class="sxs-lookup"><span data-stu-id="07f15-157">Running in the contact panel</span></span>

<span data-ttu-id="07f15-158">Jetzt, wo Ihre Anwendung in der Kontaktliste für einige oder alle Benutzer angezeigt wird, müssen Sie diese mit dem Kontaktlisten-Vertrag aktivieren.</span><span class="sxs-lookup"><span data-stu-id="07f15-158">Now that your application appears in the contact panel for some or all users, you need to handle activation with the contact panel contract.</span></span>

```Csharp
override protected void OnActivated(IActivatedEventArgs e)
{
    if (e.Kind == ActivationKind.ContactPanel)
    {
        // Create a Frame to act as the navigation context and navigate to the first page
        var rootFrame = new Frame();

        // Place the frame in the current Window
        Window.Current.Content = rootFrame;

        // Navigate to the page that shows the Contact UI.
        rootFrame.Navigate(typeof(ContactPage), e);

        // Ensure the current window is active
        Window.Current.Activate();
    }
}
```

<span data-ttu-id="07f15-159">Wenn Ihre Anwendung mit diesem Vertrag aktiviert ist, erhält sie ein [ContactPanelActivatedEventArgs-Objekt](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.contactpanelactivatedeventargs).</span><span class="sxs-lookup"><span data-stu-id="07f15-159">When your application is activated with this contract, it will receive a [ContactPanelActivatedEventArgs object](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.contactpanelactivatedeventargs).</span></span>  <span data-ttu-id="07f15-160">Dieses enthält die ID des Kontakts, mit dem Ihre Anwendung zu interagieren versucht und ein [ContactPanel](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactpanel)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="07f15-160">This contains the ID of the Contact that your application is trying to interact with on launch, and a [ContactPanel](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactpanel) object.</span></span> <span data-ttu-id="07f15-161">Sie sollten einen Verweis auf dieses ContactPanel-Objekt beibehalten, der die Interaktion mit der Liste ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="07f15-161">You should keep a reference to this ContactPanel object, which will allow you to interact with the panel.</span></span>

<span data-ttu-id="07f15-162">Das ContactPanel-Objekt verfügt über zwei Ereignisse, auf die Ihre Anwendung hören soll:</span><span class="sxs-lookup"><span data-stu-id="07f15-162">The ContactPanel object has two events your application should listen for:</span></span>
+ <span data-ttu-id="07f15-163">Das **LaunchFullAppRequested**-Ereignis wird gesendet, wenn der Benutzer das Element der Benutzeroberfläche aufgerufen hat, das anfordert, dass die vollständige Anwendung in einem eigenen Fenster gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="07f15-163">The **LaunchFullAppRequested** event is sent when the user has invoked the UI element that requests that your full application be launched in its own window.</span></span>  <span data-ttu-id="07f15-164">Ihre Anwendung ist für ihren Start verantwortlich und übergibt dabei alle erforderlichen Kontexte.</span><span class="sxs-lookup"><span data-stu-id="07f15-164">Your application is responsible for launching itself, passing along all necessary context.</span></span>  <span data-ttu-id="07f15-165">Sie können nach Ihren eigenen Wünschen durchführen (z.B. per Protokollstart).</span><span class="sxs-lookup"><span data-stu-id="07f15-165">You are free to do this however you’d like (for example, via protocol launch).</span></span>
+ <span data-ttu-id="07f15-166">Die **Closing-Ereignis** wird gesendet, wenn Ihre Anwendung im Begriff ist, beendet zu werden, sodass Sie den Kontext speichern können.</span><span class="sxs-lookup"><span data-stu-id="07f15-166">The **Closing event** is sent when your application is about to be closed, allowing you to save any context.</span></span>

<span data-ttu-id="07f15-167">Mit dem ContactPanel-Objekt können Sie ebenfalls die Hintergrundfarbe des Headers der Kontaktliste festlegen (wenn er nicht festgelegt ist, wird das Systemdesign standardmäßig verwendet) und die Kontaktliste programmgesteuert schließen.</span><span class="sxs-lookup"><span data-stu-id="07f15-167">The ContactPanel object also allows you to set the background color of the contact panel header (if not set, it will default to the system theme) and to programmatically close the contact panel.</span></span>



## <a name="the-pinnedcontactmanager-class"></a><span data-ttu-id="07f15-168">Die PinnedContactManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="07f15-168">The PinnedContactManager class</span></span>

<span data-ttu-id="07f15-169">Der [PinnedContactManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager) verwaltet, welche Kontakte an die Taskleiste angeheftet werden.</span><span class="sxs-lookup"><span data-stu-id="07f15-169">The [PinnedContactManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager) is used to manage which contacts are pinned to the taskbar.</span></span> <span data-ttu-id="07f15-170">Mit dieser Klasse können Sie Kontakte anheften und lösen, bestimmen, ob der Kontakt hinzugefügt wird und ob das Anheften auf eine bestimmte Fläche vom System unterstützt wird, auf dem die Anwendung zurzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="07f15-170">This class lets you pin and unpin contacts, determine whether a contact is pinned, and determine if pinning on a particular surface is supported by the system your application is currently running on.</span></span>

<span data-ttu-id="07f15-171">Sie können das Objekt mit PinnedContactManager mithilfe der **GetDefault**- Methode abrufen:</span><span class="sxs-lookup"><span data-stu-id="07f15-171">You can retrieve the PinnedContactManager object using the **GetDefault** method:</span></span>

```Csharp
PinnedContactManager pinnedContactManager = PinnedContactManager.GetDefault();
```

## <a name="pinning-and-unpinning-contacts"></a><span data-ttu-id="07f15-172">Anheften und Loslösen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="07f15-172">Pinning and unpinning contacts</span></span>
<span data-ttu-id="07f15-173">Sie können jetzt Kontakte, die Sie gerade erstellt haben, über die PinnedContactManager anheften und lösen.</span><span class="sxs-lookup"><span data-stu-id="07f15-173">You can now pin and unpin contacts using the PinnedContactManager you just created.</span></span> <span data-ttu-id="07f15-174">Die **RequestPinContactAsync** und **RequestUnpinContactAsync**-Methoden bieten dem Benutzer Bestätigungsdialogfelder, damit sie vom Anwendungsthread für Single-Threaded Apartment (ASTA, or UI) aufgerufen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="07f15-174">The **RequestPinContactAsync** and **RequestUnpinContactAsync** methods provide the user with confirmation dialogs, so they must be called from your Application Single-Threaded Apartment (ASTA, or UI) thread.</span></span>

```Csharp
async void PinContact (Contact contact)
{
    await pinnedContactManager.RequestPinContactAsync(contact,
                                                      PinnedContactSurface.Taskbar);
}

async void UnpinContact (Contact contact)
{
    await pinnedContactManager.RequestUnpinContactAsync(contact,
                                                        PinnedContactSurface.Taskbar);
}
```

<span data-ttu-id="07f15-175">Sie können ebenfalls mehrere Kontakte gleichzeitig anheften:</span><span class="sxs-lookup"><span data-stu-id="07f15-175">You can also pin multiple contacts at the same time:</span></span>

```Csharp
async Task PinMultipleContacts(Contact[] contacts)
{
    await pinnedContactManager.RequestPinContactsAsync(
        contacts, PinnedContactSurface.Taskbar);
}
```

> [!Note]
> <span data-ttu-id="07f15-176">Zurzeit besteht keine Batchvorgang zum Lösen von Kontakten.</span><span class="sxs-lookup"><span data-stu-id="07f15-176">There is currently no batch operation for unpinning contacts.</span></span>

**<span data-ttu-id="07f15-177">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="07f15-177">Note:</span></span>** 

## <a name="see-also"></a><span data-ttu-id="07f15-178">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="07f15-178">See also</span></span>
+ [<span data-ttu-id="07f15-179">„Meine Kontakte” freigeben</span><span class="sxs-lookup"><span data-stu-id="07f15-179">My People sharing</span></span>](my-people-sharing.md)
+ [<span data-ttu-id="07f15-180">Meine Kontakte – Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="07f15-180">My People notificatons</span></span>](my-people-notifications.md)
+ [<span data-ttu-id="07f15-181">Beispiel für Visitenkarten</span><span class="sxs-lookup"><span data-stu-id="07f15-181">Contact Card sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration)
+ [<span data-ttu-id="07f15-182">Dokumentation zur PinnedContactManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="07f15-182">PinnedContactManager class documentation</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager)
