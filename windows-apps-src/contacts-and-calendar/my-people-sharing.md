---
title: „Meine Kontakte” freigeben
description: Erläutert das Hinzufügen von Support für das Freigeben von „Meine Kontakte”
author: muhsinking
ms.author: mukin
ms.date: 06/28/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7084c4dde7bdf2d59842a04fe9fd52bc029c264a
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5823696"
---
# <a name="my-people-sharing"></a><span data-ttu-id="3ddc9-104">„Meine Kontakte” freigeben</span><span class="sxs-lookup"><span data-stu-id="3ddc9-104">My People sharing</span></span>

<span data-ttu-id="3ddc9-105">Die Feature „Meine Kontakte” ermöglicht Benutzern das Anheften von Kontakten an die Taskleiste, damit sie überall über Windows in Kontakt bleiben können unabhängig von der Anwendung, durch die sie verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-105">The My People feature allows users to pin contacts to their taskbar, enabling them to stay in touch easily from anywhere in Windows, no matter what application they are connected by.</span></span> <span data-ttu-id="3ddc9-106">Jetzt können Benutzer Inhalte für ihre angeheftete Kontakte freigeben, indem sie Dateien aus dem Datei-Explorer auf die Startseite von „Meine Kontakte” anheften.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-106">Now users can share content with their pinned contacts by dragging files from the File Explorer to their My People pin.</span></span> <span data-ttu-id="3ddc9-107">Sie können Inhalte ebenfalls für alle Kontakte im Kontaktspeicher von Windows über den standardmäßigen Charms "Teilen" freigeben.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-107">They can also share to any contacts in the Windows contact store via the standard share charm.</span></span> <span data-ttu-id="3ddc9-108">Nachfolgend erhalten Sie weitere Informationen zum Aktivieren Ihrer Anwendung als Freigabeziel für Meine Kontakte.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-108">Keep reading to learn how to enable your application as a My People sharing target.</span></span>

![„Meine Kontakte”-Freigabecenter](images/my-people-sharing.png)

## <a name="requirements"></a><span data-ttu-id="3ddc9-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3ddc9-110">Requirements</span></span>

+ <span data-ttu-id="3ddc9-111">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="3ddc9-111">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="3ddc9-112">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-112">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="3ddc9-113">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-113">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="3ddc9-114">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-114">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="overview"></a><span data-ttu-id="3ddc9-115">Übersicht</span><span class="sxs-lookup"><span data-stu-id="3ddc9-115">Overview</span></span>

<span data-ttu-id="3ddc9-116">Es gibt drei Schritte, die Sie ausführen müssen, um die Anwendung als Freigabeziel für „Meine Kontakte” zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="3ddc9-116">There are three steps you must take to enable your application as a My People sharing target:</span></span>

1. [<span data-ttu-id="3ddc9-117">Unterstützung für den „ShareTarget”-Aktivierungsvertrag im Anwendungsmanifest bekannt geben.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-117">Declare support for the shareTarget activation contract in your application manifest.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#declaring-support-for-the-share-contract)
2. [<span data-ttu-id="3ddc9-118">Versehen Sie die Kontakte, die der Benutzer auf Ihre freigeben kann mit Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-118">Annotate the contacts that the users can share to using your app.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#annotating-contacts)
3. <span data-ttu-id="3ddc9-119">Unterstützen Sie mehrere Instanzen der Anwendung, die zur gleichen Zeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-119">Support multiple instances of the application running at the same time.</span></span>  <span data-ttu-id="3ddc9-120">Benutzer müssen mit einer vollständigen Version Ihrer Anwendung interagieren und diese auch für andere Personen freigeben können.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-120">Users must be able to interact with a full version of your application while also using it to share with others.</span></span> <span data-ttu-id="3ddc9-121">Sie können diese in mehreren Freigabefenstern gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-121">They may use it in multiple share windows at once.</span></span> <span data-ttu-id="3ddc9-122">Um dies zu unterstützen, muss Ihre Anwendung mehrere Ansichten gleichzeitig ausführen können.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-122">To support this, your application needs to be able to run multiple views simultaneously.</span></span> <span data-ttu-id="3ddc9-123">Weitere Informationen hierzu finden Sie im Artikel ["Anzeigen mehrerer Ansichten für eine App"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-123">To learn how to do this, see the article ["show multiple views for an app"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span></span>

<span data-ttu-id="3ddc9-124">Wenn Sie dies getan haben, wird die Anwendung als Freigabeziel im Freigabefenster „Meine Kontakte” angezeigt, das auf zwei Arten gestartet werden kann:</span><span class="sxs-lookup"><span data-stu-id="3ddc9-124">When you’ve done this, your application will appear as a share target in the My People share window, which can be launched in two ways:</span></span>
1. <span data-ttu-id="3ddc9-125">Ein Kontakt wird über den Charm "Freigabe" ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-125">A contact is chosen via the share charm.</span></span>
2. <span data-ttu-id="3ddc9-126">Dateien werden über Drag & Drop auf einen Kontakt an die Taskleiste angeheftet.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-126">File(s) are dragged and dropped on a contact pinned to the taskbar.</span></span>

## <a name="declaring-support-for-the-share-contract"></a><span data-ttu-id="3ddc9-127">Deklarieren von Support für den Freigabe-Vertrag</span><span class="sxs-lookup"><span data-stu-id="3ddc9-127">Declaring support for the share contract</span></span>

<span data-ttu-id="3ddc9-128">Um Unterstützung für die Anwendung als Freigabeziel zu deklarieren, öffnen Sie die Anwendung zunächst in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-128">To declare support for your application as a share target, first open your application in Visual Studio.</span></span> <span data-ttu-id="3ddc9-129">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei **Package.appxmanifest** und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-129">From the **Solution Explorer**, right click **Package.appxmanifest** and select **Open With**.</span></span> <span data-ttu-id="3ddc9-130">Wählen Sie aus dem Menü anschließend **XML (Text)-Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-130">From the menu, select **XML (Text) Editor** and click **OK**.</span></span> <span data-ttu-id="3ddc9-131">Nehmen Sie danach folgenden Änderungen am Manifest vor.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-131">Then, make the following changes to the manifest:</span></span>


**<span data-ttu-id="3ddc9-132">Vorher</span><span class="sxs-lookup"><span data-stu-id="3ddc9-132">Before</span></span>**
```xml
<Applications>
    <Application Id="MyApp"
      Executable="$targetnametoken$.exe"
      EntryPoint="My.App">
    </Application>
</Applications>
```

**<span data-ttu-id="3ddc9-133">Nachher</span><span class="sxs-lookup"><span data-stu-id="3ddc9-133">After</span></span>**

```xml
<Applications>
    <Application Id="MyApp"
      Executable="$targetnametoken$.exe"
      EntryPoint="My.App">
        <Extensions>
            <uap:Extension Category="windows.shareTarget">
                <uap:ShareTarget Description="Share with MyApp">
                    <uap:SupportedFileTypes>
                        <uap:SupportsAnyFileType/>
                    </uap:SupportedFileTypes>
                    <uap:DataFormat>Text</uap:DataFormat>
                    <uap:DataFormat>Bitmap</uap:DataFormat>
                    <uap:DataFormat>Html</uap:DataFormat>
                    <uap:DataFormat>StorageItems</uap:DataFormat>
                    <uap:DataFormat>URI</uap:DataFormat>
                </uap:ShareTarget>
            </uap:Extension>
         </Extensions>
    </Application>
</Applications>
```

<span data-ttu-id="3ddc9-134">Dieser Code fügt Unterstützung für alle Dateien und Daten-Formate hinzu. Sie können allerdings auch angeben, welche Arten von Dateien und Datenformate unterstützt werden (weitere Details finden Sie unter [ShareTarget Klassendokumentation](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget)).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-134">This code adds support for all files and data formats, but you can choose to specify what files types and data formats are supported (see [ShareTarget class documentation](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget) for more details).</span></span>

## <a name="annotating-contacts"></a><span data-ttu-id="3ddc9-135">Kontakte mit Kommentaren versehen</span><span class="sxs-lookup"><span data-stu-id="3ddc9-135">Annotating contacts</span></span>

<span data-ttu-id="3ddc9-136">Um zuzulassen, dass das Freigabefenster für „Meine Kontakte” Ihre Anwendung als Freigabeziel für Ihre Kontakte angibt, müssen Sie diese auf den Windows-Kontaktspeicher schreiben.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-136">To allow the My People share window to show your application as a share target for your contacts, you need to write them to the Windows contact store.</span></span> <span data-ttu-id="3ddc9-137">Weitere Informationen zum Schreiben von Kontakten finden Sie unter [Beispiel für die Visitenkartenintegration](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-137">To learn how to write contacts, see the [Contact Card Integration sample](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span></span> 

<span data-ttu-id="3ddc9-138">Damit Ihre Anwendung als Freigabeziel für „Meine Kontakte” angezeigt werden kann, wenn Sie zu einen Kontakt freigeben, müssen sie eine Anmerkung darauf schreiben.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-138">For your application to appear as a My People share target when sharing to a contact, it must write an annotation to that contact.</span></span> <span data-ttu-id="3ddc9-139">Kommentare sind Datenteile von Ihrer Anwendung, die mit einem Kontakt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-139">Annotations are pieces of data from your application that are associated with a contact.</span></span> <span data-ttu-id="3ddc9-140">Die Anmerkung muss die aktivierbare Klassen für die gewünschte Ansicht in seinem Element **ProviderProperties** und Support für den **Freigabe**-Vorgang deklarieren.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-140">The annotation must contain the activatable class corresponding to your desired view in its **ProviderProperties** member, and declare support for the **Share** operation.</span></span>

<span data-ttu-id="3ddc9-141">Sie können Kontakten jederzeit einen Kommentar hinzufügen, während die App ausgeführt wird, aber in der Regel sollten Sie Kontakte sofort kommentieren, wenn sie dem Windows-Kontaktspeicher hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-141">You can annotate contacts at any point while your app is running, but generally you should annotate contacts as soon as they are added to the Windows contact store.</span></span>

```Csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    // Create a new contact annotation
    ContactAnnotation annotation = new ContactAnnotation();
    annotation.ContactId = myContact.Id;

    // Add appId and Share support to the annotation
    String appId = "MyApp_vqvv5s4y3scbg!App";
    annotation.ProviderProperties.Add("ContactShareAppID", appId);
    annotation.SupportedOperations = ContactAnnotationOperations::Share;

    // Save annotation to contact annotation list
    // Windows.ApplicationModel.Contacts.ContactAnnotationList 
    await contactAnnotationList.TrySaveAnnotationAsync(annotation);
}
```

<span data-ttu-id="3ddc9-142">Die “appId” ist der Paketfamilienname, gefolgt von ‘!’</span><span class="sxs-lookup"><span data-stu-id="3ddc9-142">The “appId” is the Package Family Name, followed by ‘!’</span></span> <span data-ttu-id="3ddc9-143">und einer aktivierbaren Klassen-ID.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-143">and the Activatable Class ID.</span></span> <span data-ttu-id="3ddc9-144">Um den Paketfamiliennamen zu suchen, öffnen Sie **"Package.appxmanifest"** mithilfe des Standard-Editors und suchen Sie auf der Registerkarte "Verpacken". Hier ist "App" die aktivierbare Klasse, die der zielfreigabeansicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-144">To find your Package Family Name, open **Package.appxmanifest** using the default editor, and look in the “Packaging” tab. Here, “App” is the Activatable Class corresponding to the Share Target view.</span></span>

## <a name="running-as-a-my-people-share-target"></a><span data-ttu-id="3ddc9-145">Ausführung als Freigabeziel für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="3ddc9-145">Running as a My People share target</span></span>

<span data-ttu-id="3ddc9-146">Zum Ausführen der App müssen Sie die [OnShareTargetActivated](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Application#Windows_UI_Xaml_Application_OnShareTargetActivated_Windows_ApplicationModel_Activation_ShareTargetActivatedEventArgs_)-Methode in der App-Hauptklasse außer Kraft setzen, um die Zielfreigabeaktivierung behandeln zu können.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-146">Finally, to run the app, override the [OnShareTargetActivated](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Application#Windows_UI_Xaml_Application_OnShareTargetActivated_Windows_ApplicationModel_Activation_ShareTargetActivatedEventArgs_) method in your app’s main class to handle the share target activation.</span></span> <span data-ttu-id="3ddc9-147">Die [ShareTargetActivatedEventArgs.ShareOperation.Contacts](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.datatransfer.sharetarget.shareoperation#Properties)-Eigenschaft enthält die Kontakte, die freigegeben werden, oder leer bleiben, wenn es sich um einen standardmäßigen Freigabevorgang handelt (und nicht eine Freigabe für „Meine Kontakte”).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-147">The [ShareTargetActivatedEventArgs.ShareOperation.Contacts](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.datatransfer.sharetarget.shareoperation#Properties) property will contain the contact(s) that are being shared to, or will be empty if this is a standard share operation (not a My People share).</span></span>

```Csharp
protected override void OnShareTargetActivated(ShareTargetActivatedEventArgs args)
{
    bool isPeopleShare = false;
    if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
    {
        // Make sure the current OS version includes the My People feature before
        // accessing the ShareOperation.Contacts property
        isPeopleShare = (args.ShareOperation.Contacts.Count > 0);
    }

    if (isPeopleShare)
    {
        // Show share UI for MyPeople contact(s)
    }
    else
    {
        // Show standard share UI for unpinned contacts
    }
}
```

## <a name="see-also"></a><span data-ttu-id="3ddc9-148">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="3ddc9-148">See also</span></span>
+ [<span data-ttu-id="3ddc9-149">Hinzufügen von Support für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="3ddc9-149">Adding My People support</span></span>](my-people-support.md)
+ [<span data-ttu-id="3ddc9-150">ShareTarget-Klasse</span><span class="sxs-lookup"><span data-stu-id="3ddc9-150">ShareTarget Class</span></span>](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget)
+ [<span data-ttu-id="3ddc9-151">Beispiel für die Visitenkartenintegration</span><span class="sxs-lookup"><span data-stu-id="3ddc9-151">Contact Card Integration sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration)
