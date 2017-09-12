---
title: "„Meine Kontakte” freigeben"
description: "Erläutert das Hinzufügen von Support für das Freigeben von „Meine Kontakte”"
author: mukin
ms.author: mukin
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 1f841c0c58e209f1dfb318d31108b6fe8fc66b4f
ms.sourcegitcommit: 214a1dcb24e0811811bd7a4a07bfe707ecd93b18
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2017
---
# <a name="my-people-sharing"></a><span data-ttu-id="319e2-104">„Meine Kontakte” freigeben</span><span class="sxs-lookup"><span data-stu-id="319e2-104">My People sharing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="319e2-105">**VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen als Ziel [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) angeben und [Insider-Builds 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) oder höher ausführen, um die API „Meine Kontakte” zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="319e2-105">**PRERELEASE | Requires Fall Creators Update**: You must target [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) and be running [Insider build 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) or higher to use the My People APIs.</span></span>

<span data-ttu-id="319e2-106">Die Feature „Meine Kontakte” ermöglicht Benutzern das Anheften von Kontakten an die Taskleiste, damit sie überall über Windows in Kontakt bleiben können unabhängig von der Anwendung, durch die sie verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="319e2-106">The My People feature allows users to pin contacts to their taskbar, enabling them to stay in touch easily from anywhere in Windows, no matter what application they are connected by.</span></span> <span data-ttu-id="319e2-107">Jetzt können Benutzer Inhalte für ihre angeheftete Kontakte freigeben, indem sie Dateien aus dem Datei-Explorer auf die Startseite von „Meine Kontakte” anheften.</span><span class="sxs-lookup"><span data-stu-id="319e2-107">Now users can share content with their pinned contacts by dragging files from the File Explorer to their My People pin.</span></span> <span data-ttu-id="319e2-108">Sie können Inhalte ebenfalls für alle Kontakte im Kontaktspeicher von Windows über den standardmäßigen Charms "Teilen" freigeben.</span><span class="sxs-lookup"><span data-stu-id="319e2-108">They can also share to any contacts in the Windows contact store via the standard share charm.</span></span> <span data-ttu-id="319e2-109">Nachfolgend erhalten Sie weitere Informationen zum Aktivieren Ihrer Anwendung als Freigabeziel für Meine Kontakte.</span><span class="sxs-lookup"><span data-stu-id="319e2-109">Keep reading to learn how to enable your application as a My People sharing target.</span></span>

![„Meine Kontakte”-Freigabecenter](images/my-people-sharing.png)

## <a name="requirements"></a><span data-ttu-id="319e2-111">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="319e2-111">Requirements</span></span>

+ <span data-ttu-id="319e2-112">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="319e2-112">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="319e2-113">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="319e2-113">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="319e2-114">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="319e2-114">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="319e2-115">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="319e2-115">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="overview"></a><span data-ttu-id="319e2-116">Übersicht</span><span class="sxs-lookup"><span data-stu-id="319e2-116">Overview</span></span>

<span data-ttu-id="319e2-117">Es gibt drei Schritte, die Sie ausführen müssen, um die Anwendung als Freigabeziel für „Meine Kontakte” zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="319e2-117">There are three steps you must take to enable your application as a My People sharing target:</span></span>

1. [<span data-ttu-id="319e2-118">Unterstützung für den „ShareTarget”-Aktivierungsvertrag im Anwendungsmanifest bekannt geben.</span><span class="sxs-lookup"><span data-stu-id="319e2-118">Declare support for the shareTarget activation contract in your application manifest.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#declaring-support-for-the-share-contract)
2. [<span data-ttu-id="319e2-119">Versehen Sie die Kontakte, die der Benutzer auf Ihre freigeben kann mit Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="319e2-119">Annotate the contacts that the users can share to using your app.</span></span>](https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-sharing#annotating-contacts)
3. <span data-ttu-id="319e2-120">Unterstützen Sie mehrere Instanzen der Anwendung, die zur gleichen Zeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="319e2-120">Support multiple instances of the application running at the same time.</span></span>  <span data-ttu-id="319e2-121">Benutzer müssen mit einer vollständigen Version Ihrer Anwendung interagieren und diese auch für andere Personen freigeben können.</span><span class="sxs-lookup"><span data-stu-id="319e2-121">Users must be able to interact with a full version of your application while also using it to share with others.</span></span> <span data-ttu-id="319e2-122">Sie können diese in mehreren Freigabefenstern gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="319e2-122">They may use it in multiple share windows at once.</span></span> <span data-ttu-id="319e2-123">Um dies zu unterstützen, muss Ihre Anwendung mehrere Ansichten gleichzeitig ausführen können.</span><span class="sxs-lookup"><span data-stu-id="319e2-123">To support this, your application needs to be able to run multiple views simultaneously.</span></span> <span data-ttu-id="319e2-124">Weitere Informationen hierzu finden Sie im Artikel ["Anzeigen mehrerer Ansichten für eine App"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span><span class="sxs-lookup"><span data-stu-id="319e2-124">To learn how to do this, see the article ["show multiple views for an app"](https://docs.microsoft.com/en-us/windows/uwp/layout/show-multiple-views).</span></span>

<span data-ttu-id="319e2-125">Wenn Sie dies getan haben, wird die Anwendung als Freigabeziel im Freigabefenster „Meine Kontakte” angezeigt, das auf zwei Arten gestartet werden kann:</span><span class="sxs-lookup"><span data-stu-id="319e2-125">When you’ve done this, your application will appear as a share target in the My People share window, which can be launched in two ways:</span></span>
1. <span data-ttu-id="319e2-126">Ein Kontakt wird über den Charm "Freigabe" ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="319e2-126">A contact is chosen via the share charm.</span></span>
2. <span data-ttu-id="319e2-127">Dateien werden über Drag & Drop auf einen Kontakt an die Taskleiste angeheftet.</span><span class="sxs-lookup"><span data-stu-id="319e2-127">File(s) are dragged and dropped on a contact pinned to the taskbar.</span></span>

## <a name="declaring-support-for-the-share-contract"></a><span data-ttu-id="319e2-128">Deklarieren von Support für den Freigabe-Vertrag</span><span class="sxs-lookup"><span data-stu-id="319e2-128">Declaring support for the share contract</span></span>

<span data-ttu-id="319e2-129">Um Unterstützung für die Anwendung als Freigabeziel zu deklarieren, öffnen Sie die Anwendung zunächst in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="319e2-129">To declare support for your application as a share target, first open your application in Visual Studio.</span></span> <span data-ttu-id="319e2-130">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei **Package.appxmanifest** und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="319e2-130">From the **Solution Explorer**, right click **Package.appxmanifest** and select **Open With**.</span></span> <span data-ttu-id="319e2-131">Wählen Sie aus dem Menü anschließend **XML (Text)-Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="319e2-131">From the menu, select **XML (Text) Editor** and click **OK**.</span></span> <span data-ttu-id="319e2-132">Nehmen Sie danach folgenden Änderungen am Manifest vor.</span><span class="sxs-lookup"><span data-stu-id="319e2-132">Then, make the following changes to the manifest:</span></span>


**<span data-ttu-id="319e2-133">Vorher</span><span class="sxs-lookup"><span data-stu-id="319e2-133">Before</span></span>**
```xml
<Applications>
    <Application Id="MyApp"
      Executable="$targetnametoken$.exe"
      EntryPoint="My.App">
    </Application>
</Applications>
```

**<span data-ttu-id="319e2-134">Nachher</span><span class="sxs-lookup"><span data-stu-id="319e2-134">After</span></span>**

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

<span data-ttu-id="319e2-135">Dieser Code fügt Unterstützung für alle Dateien und Daten-Formate hinzu. Sie können allerdings auch angeben, welche Arten von Dateien und Datenformate unterstützt werden (weitere Details finden Sie unter [ShareTarget Klassendokumentation](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget)).</span><span class="sxs-lookup"><span data-stu-id="319e2-135">This code adds support for all files and data formats, but you can choose to specify what files types and data formats are supported (see [ShareTarget class documentation](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget) for more details).</span></span>

## <a name="annotating-contacts"></a><span data-ttu-id="319e2-136">Kontakte mit Kommentaren versehen</span><span class="sxs-lookup"><span data-stu-id="319e2-136">Annotating contacts</span></span>

<span data-ttu-id="319e2-137">Um zuzulassen, dass das Freigabefenster für „Meine Kontakte” Ihre Anwendung als Freigabeziel für Ihre Kontakte angibt, müssen Sie diese auf den Windows-Kontaktspeicher schreiben.</span><span class="sxs-lookup"><span data-stu-id="319e2-137">To allow the My People share window to show your application as a share target for your contacts, you need to write them to the Windows contact store.</span></span> <span data-ttu-id="319e2-138">Weitere Informationen zum Schreiben von Kontakten finden Sie unter [Beispiel für die Visitenkartenintegration](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span><span class="sxs-lookup"><span data-stu-id="319e2-138">To learn how to write contacts, see the [Contact Card Integration sample](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration).</span></span> 

<span data-ttu-id="319e2-139">Damit Ihre Anwendung als Freigabeziel für „Meine Kontakte” angezeigt werden kann, wenn Sie zu einen Kontakt freigeben, müssen sie eine Anmerkung darauf schreiben.</span><span class="sxs-lookup"><span data-stu-id="319e2-139">For your application to appear as a My People share target when sharing to a contact, it must write an annotation to that contact.</span></span> <span data-ttu-id="319e2-140">Kommentare sind Datenteile von Ihrer Anwendung, die mit einem Kontakt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="319e2-140">Annotations are pieces of data from your application that are associated with a contact.</span></span> <span data-ttu-id="319e2-141">Die Anmerkung muss die aktivierbare Klassen für die gewünschte Ansicht in seinem Element **ProviderProperties** und Support für den **Freigabe**-Vorgang deklarieren.</span><span class="sxs-lookup"><span data-stu-id="319e2-141">The annotation must contain the activatable class corresponding to your desired view in its **ProviderProperties** member, and declare support for the **Share** operation.</span></span>

<span data-ttu-id="319e2-142">Sie können Kontakten jederzeit einen Kommentar hinzufügen, während die App ausgeführt wird, aber in der Regel sollten Sie Kontakte sofort kommentieren, wenn sie dem Windows-Kontaktspeicher hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="319e2-142">You can annotate contacts at any point while your app is running, but generally you should annotate contacts as soon as they are added to the Windows contact store.</span></span>

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

<span data-ttu-id="319e2-143">Die “appId” ist der Paketfamilienname, gefolgt von ‘!’</span><span class="sxs-lookup"><span data-stu-id="319e2-143">The “appId” is the Package Family Name, followed by ‘!’</span></span> <span data-ttu-id="319e2-144">und einer aktivierbaren Klassen-ID.</span><span class="sxs-lookup"><span data-stu-id="319e2-144">and the Activatable Class ID.</span></span> <span data-ttu-id="319e2-145">Um den Paketfamiliennamen zu such, öffnen Sie **Package.appxmanifest** mithilfe des Standard-Editors und suchen Sie auf der Registerkarte "Verpacken".</span><span class="sxs-lookup"><span data-stu-id="319e2-145">To find your Package Family Name, open **Package.appxmanifest** using the default editor, and look in the “Packaging” tab.</span></span> <span data-ttu-id="319e2-146">Hier ist "App" die aktivierbare Klasse, die der Zielfreigabeansicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="319e2-146">Here, “App” is the Activatable Class corresponding to the Share Target view.</span></span>

## <a name="running-as-a-my-people-share-target"></a><span data-ttu-id="319e2-147">Ausführung als Freigabeziel für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="319e2-147">Running as a My People share target</span></span>

<span data-ttu-id="319e2-148">Zum Ausführen der App müssen Sie die [OnShareTargetActivated](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Application#Windows_UI_Xaml_Application_OnShareTargetActivated_Windows_ApplicationModel_Activation_ShareTargetActivatedEventArgs_)-Methode in der App-Hauptklasse außer Kraft setzen, um die Zielfreigabeaktivierung behandeln zu können.</span><span class="sxs-lookup"><span data-stu-id="319e2-148">Finally, to run the app, override the [OnShareTargetActivated](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Application#Windows_UI_Xaml_Application_OnShareTargetActivated_Windows_ApplicationModel_Activation_ShareTargetActivatedEventArgs_) method in your app’s main class to handle the share target activation.</span></span> <span data-ttu-id="319e2-149">Die [ShareTargetActivatedEventArgs.ShareOperation.Contacts](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.datatransfer.sharetarget.shareoperation#properties_)-Eigenschaft enthält die Kontakte, die freigegeben werden, oder leer bleiben, wenn es sich um einen standardmäßigen Freigabevorgang handelt (und nicht eine Freigabe für „Meine Kontakte”).</span><span class="sxs-lookup"><span data-stu-id="319e2-149">The [ShareTargetActivatedEventArgs.ShareOperation.Contacts](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.datatransfer.sharetarget.shareoperation#properties_) property will contain the contact(s) that are being shared to, or will be empty if this is a standard share operation (not a My People share).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="319e2-150">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="319e2-150">See also</span></span>
+ [<span data-ttu-id="319e2-151">Hinzufügen von Support für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="319e2-151">Adding My People support</span></span>](my-people-support.md)
+ [<span data-ttu-id="319e2-152">ShareTarget-Klasse</span><span class="sxs-lookup"><span data-stu-id="319e2-152">ShareTarget Class</span></span>](https://docs.microsoft.com/en-us/uwp/schemas/appxpackage/appxmanifestschema/element-sharetarget)
+ [<span data-ttu-id="319e2-153">Beispiel für die Visitenkartenintegration</span><span class="sxs-lookup"><span data-stu-id="319e2-153">Contact Card Integration sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/ContactCardIntegration)
