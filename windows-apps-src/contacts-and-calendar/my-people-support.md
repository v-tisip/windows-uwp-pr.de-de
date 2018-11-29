---
title: Support für Meine Kontakte zu einer Anwendung hinzufügen
description: Erläutert, wie Sie einer Anwendung Support für „Meine Kontakte” hinzufügen, und wie Sie Kontakte auf der Startseite anheften und entfernen
ms.date: 06/28/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9a486f27d390a651cec0dcad82246a858bab2f33
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8193089"
---
# <a name="adding-my-people-support-to-an-application"></a><span data-ttu-id="f9369-104">Support für Meine Kontakte zu einer Anwendung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="f9369-104">Adding My People support to an application</span></span>

<span data-ttu-id="f9369-105">Die Feature „Meine Kontakte” ermöglicht Benutzern das Anheften von Kontakten an die Taskleiste, um neue Kontaktobjekt zu erstellen, die auf unterschiedliche Weise miteinander interagieren können.</span><span class="sxs-lookup"><span data-stu-id="f9369-105">The My People feature allows users to pin contacts from an application directly to their taskbar, which creates a new contact object that they can interact with in several ways.</span></span> <span data-ttu-id="f9369-106">In diesem Artikel wird gezeigt, wie Sie Support für dieses Feature hinzufügen können, damit Benutzer Kontakte direkt in der App anheften können.</span><span class="sxs-lookup"><span data-stu-id="f9369-106">This article shows how you can add support for this feature, allowing users to pin contacts directly from your app.</span></span> <span data-ttu-id="f9369-107">Wenn Kontakte angeheftet sind, werden neue Arten an Benutzerinteraktionen verfügbar, z.B. [Meine Kontakte freigeben](my-people-sharing.md) und [Benachrichtigungen ](my-people-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="f9369-107">When contacts are pinned, new types of user interaction become available, such as [My People sharing](my-people-sharing.md) and [notifications](my-people-notifications.md).</span></span>

![Chat für Meine Kontakte](images/my-people-chat.png)

## <a name="requirements"></a><span data-ttu-id="f9369-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f9369-109">Requirements</span></span>

+ <span data-ttu-id="f9369-110">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="f9369-110">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="f9369-111">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="f9369-111">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="f9369-112">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="f9369-112">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="f9369-113">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="f9369-113">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="overview"></a><span data-ttu-id="f9369-114">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f9369-114">Overview</span></span>

<span data-ttu-id="f9369-115">Es gibt drei Dinge, die durchgeführt werden müssen, damit die Anwendung das Feature„ Meine Kontakte” verwenden kann:</span><span class="sxs-lookup"><span data-stu-id="f9369-115">There are three things you need to do to enable your application to use the My People feature:</span></span>

1. [<span data-ttu-id="f9369-116">Unterstützung für den „ShareTarget”-Aktivierungsvertrag im Anwendungsmanifest bekannt geben.</span><span class="sxs-lookup"><span data-stu-id="f9369-116">Declare support for the shareTarget activation contract in your application manifest.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#declaring-support-for-the-share-contract)
2. [<span data-ttu-id="f9369-117">Versehen Sie die Kontakte, die der Benutzer auf Ihre freigeben kann mit Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="f9369-117">Annotate the contacts that the users can share to using your app.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#annotating-contacts)
3.  <span data-ttu-id="f9369-118">Unterstützen Sie mehrere Instanzen Ihrer Anwendung, die zur gleichen Zeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f9369-118">Support multiple instances of your application running at the same time.</span></span> <span data-ttu-id="f9369-119">Benutzer müssen mit einer vollständigen Version Ihrer Anwendung interagieren, während Sie diese im Kontaktbereich verwenden.</span><span class="sxs-lookup"><span data-stu-id="f9369-119">Users must be able to interact with a full version of your application while using it in a contact panel.</span></span>  <span data-ttu-id="f9369-120">Sie können diese sogar in mehreren Kontaktlisten gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="f9369-120">They may even use it in multiple contact panels at once.</span></span>  <span data-ttu-id="f9369-121">Um dies zu unterstützen, muss Ihre Anwendung mehrere Ansichten gleichzeitig ausführen können.</span><span class="sxs-lookup"><span data-stu-id="f9369-121">To support this, your application needs to be able to run multiple views simultaneously.</span></span> <span data-ttu-id="f9369-122">Weitere Informationen hierzu finden Sie im Artikel ["Anzeigen mehrerer Ansichten für eine App"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span><span class="sxs-lookup"><span data-stu-id="f9369-122">To learn how to do this, see the article ["show multiple views for an app"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span></span>

<span data-ttu-id="f9369-123">Wenn Sie dies getan haben, wird die Anwendung in der Kontaktliste für Kontakte mit Kommentaren angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f9369-123">When you’ve done this, your application will appear in the contact panel for annotated contacts.</span></span>

## <a name="declaring-support-for-the-contract"></a><span data-ttu-id="f9369-124">Deklarieren von Support für den Vertrag</span><span class="sxs-lookup"><span data-stu-id="f9369-124">Declaring support for the contract</span></span>

<span data-ttu-id="f9369-125">Um Unterstützung für den Vertrag „Meine Kontakte” zu deklarieren, öffnen Sie die Anwendung in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9369-125">To declare support for the My People contract, open your application in Visual Studio.</span></span> <span data-ttu-id="f9369-126">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei **Package.appxmanifest** und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="f9369-126">From the **Solution Explorer**, right click **Package.appxmanifest** and select **Open With**.</span></span> <span data-ttu-id="f9369-127">Wählen Sie aus dem Menü anschließend **XML (Text)-Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9369-127">From the menu, select **XML (Text) Editor)** and click **OK**.</span></span> <span data-ttu-id="f9369-128">Nehmen Sie danach folgenden Änderungen am Manifest vor.</span><span class="sxs-lookup"><span data-stu-id="f9369-128">Make the following changes to the manifest:</span></span>

**<span data-ttu-id="f9369-129">Vorher</span><span class="sxs-lookup"><span data-stu-id="f9369-129">Before</span></span>**

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

**<span data-ttu-id="f9369-130">Nachher</span><span class="sxs-lookup"><span data-stu-id="f9369-130">After</span></span>**

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

<span data-ttu-id="f9369-131">Durch diesen Zusatz kann Ihre Anwendung jetzt über den Vertrag **Windows. ContactPanel** gestartet werden, die Sie mit mit Kontakten in der Kontaktliste interagieren können.</span><span class="sxs-lookup"><span data-stu-id="f9369-131">With this addition, your application can now be launched through the **windows.ContactPanel** contract, which allows you to interact with contact panels.</span></span>

## <a name="annotating-contacts"></a><span data-ttu-id="f9369-132">Kontakte mit Kommentaren versehen</span><span class="sxs-lookup"><span data-stu-id="f9369-132">Annotating contacts</span></span>

<span data-ttu-id="f9369-133">Um Kontakte von Ihrer Anwendung über den Bereich „Meine Kontakte” in der Taskleiste anzuzueigen, müssen Sie diese auf den Windows-Kontaktspeicher schreiben.</span><span class="sxs-lookup"><span data-stu-id="f9369-133">To allow contacts from your application to appear in the taskbar via the My People pane, you need to write them to the Windows contact store.</span></span>  <span data-ttu-id="f9369-134">Weitere Informationen zum Schreiben von Kontakten finden Sie unter [Beispiel für die Visitenkarte](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span><span class="sxs-lookup"><span data-stu-id="f9369-134">To learn how to write contacts, see the [Contact Card sample](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span></span>

<span data-ttu-id="f9369-135">Ihre Anwendung muss ebenfalls eine Anmerkung für jeden Kontakt schreiben.</span><span class="sxs-lookup"><span data-stu-id="f9369-135">Your application must also write an annotation to each contact.</span></span> <span data-ttu-id="f9369-136">Kommentare sind Datenteile von Ihrer Anwendung, die mit einem Kontakt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="f9369-136">Annotations are pieces of data from your application that are associated with a contact.</span></span> <span data-ttu-id="f9369-137">Die Anmerkung muss die aktivierbare Klassen für die gewünschte Ansicht in seinem Element **ProviderProperties** und Support für den **ContactProfile**-Vorgang deklarieren.</span><span class="sxs-lookup"><span data-stu-id="f9369-137">The annotation must contain the activatable class corresponding to your desired view in its **ProviderProperties** member, and declare support for the **ContactProfile** operation.</span></span>

<span data-ttu-id="f9369-138">Sie können Kontakten jederzeit einen Kommentar hinzufügen, während die App ausgeführt wird, aber in der Regel sollten Sie Kontakte sofort kommentieren, wenn sie dem Windows-Kontaktspeicher hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f9369-138">You can annotate contacts at any point while your app is running, but generally you should annotate contacts as soon as they are added to the Windows contact store.</span></span>

```Csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    // Create a new contact annotation
    ContactAnnotation annotation = new ContactAnnotation();
    annotation.ContactId = myContact.Id;

    // Add appId and contact panel support to the annotation
    String appId = "MyApp_vqvv5s4y3scbg!App";
    annotation.ProviderProperties.Add("ContactPanelAppID", appId);
    annotation.SupportedOperations = ContactAnnotationOperations.ContactProfile;

    // Save annotation to contact annotation list
    // Windows.ApplicationModel.Contacts.ContactAnnotationList 
    await contactAnnotationList.TrySaveAnnotationAsync(annotation));
}
```

<span data-ttu-id="f9369-139">Die “appId” ist der Paketfamilienname, gefolgt von ‘!’</span><span class="sxs-lookup"><span data-stu-id="f9369-139">The “appId” is the Package Family Name, followed by ‘!’</span></span> <span data-ttu-id="f9369-140">und einer aktivierbaren Klassen-ID.</span><span class="sxs-lookup"><span data-stu-id="f9369-140">and the activatable class ID.</span></span> <span data-ttu-id="f9369-141">Um Ihren Paketfamilienname zu suchen, öffnen Sie **Package.appxmanifest** mithilfe des Standard-Editors, und suchen Sie den Namen auf der Registerkarte "Verpacken". Hier entspricht "App" der aktivierbaren Klassen der Anwendungsstart-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="f9369-141">To find your Package Family Name, open **Package.appxmanifest** using the default editor, and look in the “Packaging” tab. Here, “App” is the activatable class corresponding to the application startup view.</span></span>

## <a name="allow-contacts-to-invite-new-potential-users"></a><span data-ttu-id="f9369-142">Kontakten die Einladung von neuen potenziellen Benutzern ermöglichen</span><span class="sxs-lookup"><span data-stu-id="f9369-142">Allow contacts to invite new potential users</span></span>

<span data-ttu-id="f9369-143">Standardmäßig wird die Anwendung nur für Kontakte in der Kontaktliste angezeigt, die Sie speziell kommentiert haben.</span><span class="sxs-lookup"><span data-stu-id="f9369-143">By default, your application will only appear in the contact panel for contacts that you have specifically annotated.</span></span>  <span data-ttu-id="f9369-144">Dies vermeidet eine Verwechslungen mit Kontakten, die nicht mit Ihnen durch die App interagiert können.</span><span class="sxs-lookup"><span data-stu-id="f9369-144">This is to avoid confusion with contacts that can’t be interacted with through your app.</span></span>  <span data-ttu-id="f9369-145">Wenn Sie möchten, dass Ihre Anwendung für Kontakte angezeigt wird, deren Ihre Anwendung nicht bekannt ist (z.B. um Benutzer dazu aufzufordern, ihrem Konto Kontakte hinzuzufügen), können Sie Ihrem Manifest Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="f9369-145">If you want your application to appear for contacts that your application doesn’t know about (to invite users to add that contact to their account, for instance), you can add the following to your manifest:</span></span>

**<span data-ttu-id="f9369-146">Vorher</span><span class="sxs-lookup"><span data-stu-id="f9369-146">Before</span></span>**

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

**<span data-ttu-id="f9369-147">Nachher</span><span class="sxs-lookup"><span data-stu-id="f9369-147">After</span></span>**

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

<span data-ttu-id="f9369-148">Aufgrund dieser Änderung wird die Anwendung als verfügbare Option für alle Kontakte in der Kontaktliste angezeigt, die der Benutzer angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="f9369-148">With this change, your application will appear as an available option in the contact panel for all contacts that the user has pinned.</span></span>  <span data-ttu-id="f9369-149">Wenn Ihre Anwendung durch den Kontaktlisten-Vertrag aktiviert ist, sollten Sie überprüfen, ob der Kontakt Ihrer Anwendung bereits bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="f9369-149">When your application is activated using the contact panel contract, you should check to see if the contact is one your application knows about.</span></span>  <span data-ttu-id="f9369-150">Wenn dies nicht der Fall ist, sollten Sie die Benutzerfreundlichkeit Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f9369-150">If not, you should show your app’s new user experience.</span></span>

![„Meine Kontakte”-Kontaktliste](images/my-people.png)

## <a name="support-for-email-apps"></a><span data-ttu-id="f9369-152">Unterstützung für E-Mail-Apps</span><span class="sxs-lookup"><span data-stu-id="f9369-152">Support for email apps</span></span>

<span data-ttu-id="f9369-153">Wenn Sie eine E-Mail-App schreiben, müssen Sie nicht jeden Kontakt manuell kommentieren.</span><span class="sxs-lookup"><span data-stu-id="f9369-153">If you are writing an email app, you don’t need to annotate every contact manually.</span></span>  <span data-ttu-id="f9369-154">Wenn Sie Unterstützung für die Kontaktliste und das „mailto: protocol” deklarieren, erscheint Ihre Anwendung automatisch für Benutzer mit einer E-Mail-Adresse.</span><span class="sxs-lookup"><span data-stu-id="f9369-154">If you declare support for the contact pane and for the mailto: protocol, your application will automatically appear for users with an email address.</span></span>

## <a name="running-in-the-contact-panel"></a><span data-ttu-id="f9369-155">Ausführen in der Kontaktliste</span><span class="sxs-lookup"><span data-stu-id="f9369-155">Running in the contact panel</span></span>

<span data-ttu-id="f9369-156">Jetzt, wo Ihre Anwendung in der Kontaktliste für einige oder alle Benutzer angezeigt wird, müssen Sie diese mit dem Kontaktlisten-Vertrag aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f9369-156">Now that your application appears in the contact panel for some or all users, you need to handle activation with the contact panel contract.</span></span>

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

<span data-ttu-id="f9369-157">Wenn Ihre Anwendung mit diesem Vertrag aktiviert ist, erhält sie ein [ContactPanelActivatedEventArgs-Objekt](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.contactpanelactivatedeventargs).</span><span class="sxs-lookup"><span data-stu-id="f9369-157">When your application is activated with this contract, it will receive a [ContactPanelActivatedEventArgs object](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.activation.contactpanelactivatedeventargs).</span></span>  <span data-ttu-id="f9369-158">Dieses enthält die ID des Kontakts, mit dem Ihre Anwendung zu interagieren versucht und ein [ContactPanel](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactpanel)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f9369-158">This contains the ID of the Contact that your application is trying to interact with on launch, and a [ContactPanel](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactpanel) object.</span></span> <span data-ttu-id="f9369-159">Sie sollten einen Verweis auf dieses ContactPanel-Objekt beibehalten, der die Interaktion mit der Liste ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f9369-159">You should keep a reference to this ContactPanel object, which will allow you to interact with the panel.</span></span>

<span data-ttu-id="f9369-160">Das ContactPanel-Objekt verfügt über zwei Ereignisse, auf die Ihre Anwendung hören soll:</span><span class="sxs-lookup"><span data-stu-id="f9369-160">The ContactPanel object has two events your application should listen for:</span></span>
+ <span data-ttu-id="f9369-161">Das **LaunchFullAppRequested**-Ereignis wird gesendet, wenn der Benutzer das Element der Benutzeroberfläche aufgerufen hat, das anfordert, dass die vollständige Anwendung in einem eigenen Fenster gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f9369-161">The **LaunchFullAppRequested** event is sent when the user has invoked the UI element that requests that your full application be launched in its own window.</span></span>  <span data-ttu-id="f9369-162">Ihre Anwendung ist für ihren Start verantwortlich und übergibt dabei alle erforderlichen Kontexte.</span><span class="sxs-lookup"><span data-stu-id="f9369-162">Your application is responsible for launching itself, passing along all necessary context.</span></span>  <span data-ttu-id="f9369-163">Sie können nach Ihren eigenen Wünschen durchführen (z.B. per Protokollstart).</span><span class="sxs-lookup"><span data-stu-id="f9369-163">You are free to do this however you’d like (for example, via protocol launch).</span></span>
+ <span data-ttu-id="f9369-164">Die **Closing-Ereignis** wird gesendet, wenn Ihre Anwendung im Begriff ist, beendet zu werden, sodass Sie den Kontext speichern können.</span><span class="sxs-lookup"><span data-stu-id="f9369-164">The **Closing event** is sent when your application is about to be closed, allowing you to save any context.</span></span>

<span data-ttu-id="f9369-165">Mit dem ContactPanel-Objekt können Sie ebenfalls die Hintergrundfarbe des Headers der Kontaktliste festlegen (wenn er nicht festgelegt ist, wird das Systemdesign standardmäßig verwendet) und die Kontaktliste programmgesteuert schließen.</span><span class="sxs-lookup"><span data-stu-id="f9369-165">The ContactPanel object also allows you to set the background color of the contact panel header (if not set, it will default to the system theme) and to programmatically close the contact panel.</span></span>

## <a name="supporting-notification-badging"></a><span data-ttu-id="f9369-166">Unterstützung von Benachrichtigungssignalen</span><span class="sxs-lookup"><span data-stu-id="f9369-166">Supporting notification badging</span></span>

<span data-ttu-id="f9369-167">Wenn Sie möchten, dass auf der Taskleiste angeheftete Kontakte ein Signal erhalten, wenn neue Benachrichtigungen von Ihrer App für diese Person eintreffen, müssen die **Hint-Personen**-Parameter in den [Popupbenachrichtigungen](https://docs.microsoft.com/en-us/windows/uwp/shell/tiles-and-notifications/adaptive-interactive-toasts) und [Meine Kontakte – Benachrichtigungen](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-notifications) einbezogen werden.</span><span class="sxs-lookup"><span data-stu-id="f9369-167">If you want contacts pinned to the taskbar to be badged when new notifications arrive from your app that are related to that person, then you must include the **hint-people** parameter in your [toast notifications](https://docs.microsoft.com/en-us/windows/uwp/shell/tiles-and-notifications/adaptive-interactive-toasts) and expressive [My People notifications](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-notifications).</span></span>

![Benachrichtigung für „Meine Kontakte”](images/my-people-badging.png)

<span data-ttu-id="f9369-169">Um einen Kontakt zu benachrichtigen, muss der Knoten der obersten Ebene Popups hint-people-Parameter enthalten, um den Absender-Kontakt oder andere Kontakte anzugeben.</span><span class="sxs-lookup"><span data-stu-id="f9369-169">To badge a contact, the top-level toast node must include the hint-people parameter to indicate the sending or related contact.</span></span> <span data-ttu-id="f9369-170">Dieser Parameter kann folgende Werte haben:</span><span class="sxs-lookup"><span data-stu-id="f9369-170">This parameter can have any of the following values:</span></span>
+ **<span data-ttu-id="f9369-171">E-Mail-Adresse</span><span class="sxs-lookup"><span data-stu-id="f9369-171">Email address</span></span>** 
    + <span data-ttu-id="f9369-172">z.B.</span><span class="sxs-lookup"><span data-stu-id="f9369-172">E.g.</span></span> <span data-ttu-id="f9369-173">mailto:johndoe@mydomain.com</span><span class="sxs-lookup"><span data-stu-id="f9369-173">mailto:johndoe@mydomain.com</span></span>
+ **<span data-ttu-id="f9369-174">Telefonnummer</span><span class="sxs-lookup"><span data-stu-id="f9369-174">Telephone number</span></span>** 
    + <span data-ttu-id="f9369-175">z.B.</span><span class="sxs-lookup"><span data-stu-id="f9369-175">E.g.</span></span> <span data-ttu-id="f9369-176">Tel:888-888-8888</span><span class="sxs-lookup"><span data-stu-id="f9369-176">tel:888-888-8888</span></span>
+ **<span data-ttu-id="f9369-177">Remote-ID</span><span class="sxs-lookup"><span data-stu-id="f9369-177">Remote ID</span></span>** 
    + <span data-ttu-id="f9369-178">z.B.</span><span class="sxs-lookup"><span data-stu-id="f9369-178">E.g.</span></span> <span data-ttu-id="f9369-179">remoteid:1234</span><span class="sxs-lookup"><span data-stu-id="f9369-179">remoteid:1234</span></span>

<span data-ttu-id="f9369-180">Hier ist ein Beispiel, wie Sie eine Popupbenachrichtigung für eine bestimmte Person identifizieren:</span><span class="sxs-lookup"><span data-stu-id="f9369-180">Here is an example of how to identify a toast notification is related to a specific person:</span></span>
```XML
<toast hint-people="mailto:johndoe@mydomain.com">
    <visual lang="en-US">
        <binding template="ToastText01">
            <text>John Doe posted a comment.</text>
        </binding>
    </visual>
</toast>
```

> [!NOTE]
> <span data-ttu-id="f9369-181">Falls Ihre App die [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) verwendet und auf dem Smartphone gespeicherte Kontakte mithilfe der [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact.RemoteId)-Eigenschaft mit remote gespeicherten Kontakten verknüpft, muss der Wert für die RemoteId-Eigenschaft unbedingt stabil und eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="f9369-181">If your app uses the [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) and uses the [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact.RemoteId) property to link contacts stored on the PC with contacts stored remotely, it is essential that the value for the RemoteId property is both stable and unique.</span></span> <span data-ttu-id="f9369-182">Die Remote-ID muss also durchweg ein einzelnes Benutzerkonto identifizieren und ein eindeutiges Tag enthalten, um zu verhindern, dass sich Konflikte mit den Remote-IDs anderer Kontakte auf dem PC ergeben. Hierzu zählen auch Kontakte von anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="f9369-182">This means that the remote ID must consistently identify a single user account and should contain a unique tag to guarantee that it does not conflict with the remote IDs of other contacts on the PC, including contacts that are owned by other apps.</span></span>
> <span data-ttu-id="f9369-183">Falls die Stabilität und Eindeutigkeit der von Ihrer App verwendeten Remote-IDs nicht gewährleistet ist, können Sie allen Ihren RemoteIdHelper mithilfe der später in diesem Thema beschriebenen -Klasse ein eindeutiges Tag hinzufügen, bevor Sie die Remote-IDs dem System hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f9369-183">If the remote IDs used by your app are not guaranteed to be stable and unique, you can use the RemoteIdHelper class shown later in this topic in order to add a unique tag to all of your remote IDs before you add them to the system.</span></span> <span data-ttu-id="f9369-184">Alternativ können Sie auch ganz auf die Verwendung der RemoteId-Eigenschaft verzichten und stattdessen eine benutzerdefinierte erweiterte Eigenschaft erstellen, um die Remote-IDs für Ihre Kontakte zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f9369-184">Or you can choose to not use the RemoteId property at all and instead you create a custom extended property in which to store remote IDs for your contacts.</span></span>

## <a name="the-pinnedcontactmanager-class"></a><span data-ttu-id="f9369-185">Die PinnedContactManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f9369-185">The PinnedContactManager class</span></span>

<span data-ttu-id="f9369-186">Der [PinnedContactManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager) verwaltet, welche Kontakte an die Taskleiste angeheftet werden.</span><span class="sxs-lookup"><span data-stu-id="f9369-186">The [PinnedContactManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager) is used to manage which contacts are pinned to the taskbar.</span></span> <span data-ttu-id="f9369-187">Mit dieser Klasse können Sie Kontakte anheften und lösen, bestimmen, ob der Kontakt hinzugefügt wird und ob das Anheften auf eine bestimmte Fläche vom System unterstützt wird, auf dem die Anwendung zurzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f9369-187">This class lets you pin and unpin contacts, determine whether a contact is pinned, and determine if pinning on a particular surface is supported by the system your application is currently running on.</span></span>

<span data-ttu-id="f9369-188">Sie können das Objekt mit PinnedContactManager mithilfe der **GetDefault**- Methode abrufen:</span><span class="sxs-lookup"><span data-stu-id="f9369-188">You can retrieve the PinnedContactManager object using the **GetDefault** method:</span></span>

```Csharp
PinnedContactManager pinnedContactManager = PinnedContactManager.GetDefault();
```

## <a name="pinning-and-unpinning-contacts"></a><span data-ttu-id="f9369-189">Anheften und Loslösen von Kontakten</span><span class="sxs-lookup"><span data-stu-id="f9369-189">Pinning and unpinning contacts</span></span>
<span data-ttu-id="f9369-190">Sie können jetzt Kontakte, die Sie gerade erstellt haben, über die PinnedContactManager anheften und lösen.</span><span class="sxs-lookup"><span data-stu-id="f9369-190">You can now pin and unpin contacts using the PinnedContactManager you just created.</span></span> <span data-ttu-id="f9369-191">Die **RequestPinContactAsync** und **RequestUnpinContactAsync**-Methoden bieten dem Benutzer Bestätigungsdialogfelder, damit sie vom Anwendungsthread für Single-Threaded Apartment (ASTA, or UI) aufgerufen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f9369-191">The **RequestPinContactAsync** and **RequestUnpinContactAsync** methods provide the user with confirmation dialogs, so they must be called from your Application Single-Threaded Apartment (ASTA, or UI) thread.</span></span>

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

<span data-ttu-id="f9369-192">Sie können ebenfalls mehrere Kontakte gleichzeitig anheften:</span><span class="sxs-lookup"><span data-stu-id="f9369-192">You can also pin multiple contacts at the same time:</span></span>

```Csharp
async Task PinMultipleContacts(Contact[] contacts)
{
    await pinnedContactManager.RequestPinContactsAsync(
        contacts, PinnedContactSurface.Taskbar);
}
```

> [!Note]
> <span data-ttu-id="f9369-193">Zurzeit besteht keine Batchvorgang zum Lösen von Kontakten.</span><span class="sxs-lookup"><span data-stu-id="f9369-193">There is currently no batch operation for unpinning contacts.</span></span>

**<span data-ttu-id="f9369-194">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="f9369-194">Note:</span></span>** 

## <a name="see-also"></a><span data-ttu-id="f9369-195">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f9369-195">See also</span></span>
+ [<span data-ttu-id="f9369-196">„Meine Kontakte” freigeben</span><span class="sxs-lookup"><span data-stu-id="f9369-196">My People sharing</span></span>](my-people-sharing.md)
+ [<span data-ttu-id="f9369-197">Meine Kontakte – Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f9369-197">My People notificatons</span></span>](my-people-notifications.md)
+ [<span data-ttu-id="f9369-198">Channel 9-Video zum Hinzufügen von „Meine Kontakte” zu einer Anwendung</span><span class="sxs-lookup"><span data-stu-id="f9369-198">Channel 9 video on adding My People support to an application</span></span>](https://channel9.msdn.com/Events/Build/2017/P4056)
+ [<span data-ttu-id="f9369-199">Beispiel zur „Meine Kontakte”-Integration</span><span class="sxs-lookup"><span data-stu-id="f9369-199">My People integration sample</span></span>](http://aka.ms/mypeoplebuild2017)
+ [<span data-ttu-id="f9369-200">Beispiel für Visitenkarten</span><span class="sxs-lookup"><span data-stu-id="f9369-200">Contact Card sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration)
+ [<span data-ttu-id="f9369-201">Dokumentation zur PinnedContactManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f9369-201">PinnedContactManager class documentation</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.pinnedcontactmanager)
+ [<span data-ttu-id="f9369-202">Verbinden der App mit Aktionen auf einer Visitenkarte</span><span class="sxs-lookup"><span data-stu-id="f9369-202">Connect your app to actions on a contact card</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/integrating-with-contacts)
