---
author: normesta
Description: "Optimieren Sie Ihre Desktop-App für Windows10-Benutzer mithilfe von UWP-APIs (Universal Windows Platform)."
Search.Product: eADQiWindows 10XVcnh
title: "Verbessern Sie Ihre Desktopanwendung für Windows10"
ms.author: normesta
ms.date: 07/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 9f1522527825d6580ddf4fc36599352a9ca8a243
ms.sourcegitcommit: f93e887fbab6c1f824a8f762ba848f64c7f77c49
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="enhance-your-desktop-application-for-windows-10"></a><span data-ttu-id="20d62-104">Verbessern Sie Ihre Desktopanwendung für Windows10</span><span class="sxs-lookup"><span data-stu-id="20d62-104">Enhance your desktop application for Windows 10</span></span>

<span data-ttu-id="20d62-105">Sie können UWP-APIs verwenden, um moderner Funktionen für Windows10-Benutzer hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="20d62-105">You can use UWP APIs to add modern experiences that light up for Windows 10 users.</span></span>

<span data-ttu-id="20d62-106">Richten Sie zuerst Ihr Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="20d62-106">First, set up your project.</span></span> <span data-ttu-id="20d62-107">Dann fügen Sie Windows10-Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="20d62-107">Then, add Windows 10 experiences.</span></span> <span data-ttu-id="20d62-108">Sie können separate Builds für Windows10-Benutzer erstellen oder die gleichen Binärdateien für alle Benutzer verteilen – unabhängig davon, welche Version von Windows sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="20d62-108">You can build separately for Windows 10 users or distribute the same exact binaries to all users regardless of which version of Windows they run.</span></span>

## <a name="first-set-up-your-project"></a><span data-ttu-id="20d62-109">Einrichten Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="20d62-109">First, set up your project</span></span>

<span data-ttu-id="20d62-110">Sie müssen einige Änderungen am Projekt vornehmen, um UWP-APIs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="20d62-110">You'll have to make a few changes to your project to use UWP APIs.</span></span>

### <a name="modify-a-net-project-to-use-uwp-apis"></a><span data-ttu-id="20d62-111">Ändern eines .NET-Projekts für UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="20d62-111">Modify a .NET project to use UWP APIs</span></span>

<span data-ttu-id="20d62-112">Öffnen Sie das **Verweis-Manager**-Dialogfeld, wählen Sie die **Durchsuchen**-Schaltfläche, und wählen Sie dann **Alle Dateien** aus.</span><span class="sxs-lookup"><span data-stu-id="20d62-112">Open the **Reference Manager** dialog box, choose the **Browse** button, and then select  **All Files**.</span></span>

![Dialogfeld „Verweis hinzufügen“](images/desktop-to-uwp/browse-references.png)

<span data-ttu-id="20d62-114">Fügen Sie dann einen Verweis auf diese Dateien hinzu.</span><span class="sxs-lookup"><span data-stu-id="20d62-114">Then, add a reference to these files.</span></span>

|<span data-ttu-id="20d62-115">Datei</span><span class="sxs-lookup"><span data-stu-id="20d62-115">File</span></span>|<span data-ttu-id="20d62-116">Speicherort</span><span class="sxs-lookup"><span data-stu-id="20d62-116">Location</span></span>|
|--|--|
|<span data-ttu-id="20d62-117">System.Runtime.WindowsRuntime</span><span class="sxs-lookup"><span data-stu-id="20d62-117">System.Runtime.WindowsRuntime</span></span>|<span data-ttu-id="20d62-118">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="20d62-118">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="20d62-119">System.Runtime.WindowsRuntime.UI.Xaml</span><span class="sxs-lookup"><span data-stu-id="20d62-119">System.Runtime.WindowsRuntime.UI.Xaml</span></span>|<span data-ttu-id="20d62-120">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="20d62-120">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="20d62-121">System.Runtime.InteropServices.WindowsRuntime</span><span class="sxs-lookup"><span data-stu-id="20d62-121">System.Runtime.InteropServices.WindowsRuntime</span></span>|<span data-ttu-id="20d62-122">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="20d62-122">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="20d62-123">Windows.winmd</span><span class="sxs-lookup"><span data-stu-id="20d62-123">Windows.winmd</span></span>|<span data-ttu-id="20d62-124">C:\Program Files (x86)\Windows Kits\10\UnionMetadata\Facade</span><span class="sxs-lookup"><span data-stu-id="20d62-124">C:\Program Files (x86)\Windows Kits\10\UnionMetadata\Facade</span></span>|
|<span data-ttu-id="20d62-125">Windows.Foundation.UniversalApiContract.winmd</span><span class="sxs-lookup"><span data-stu-id="20d62-125">Windows.Foundation.UniversalApiContract.winmd</span></span>|<span data-ttu-id="20d62-126">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.UniversalApiContract\<*version*></span><span class="sxs-lookup"><span data-stu-id="20d62-126">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.UniversalApiContract\<*version*></span></span>|
|<span data-ttu-id="20d62-127">Windows.Foundation.FoundationContract.winmd</span><span class="sxs-lookup"><span data-stu-id="20d62-127">Windows.Foundation.FoundationContract.winmd</span></span>|<span data-ttu-id="20d62-128">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.FoundationContract\<*version*></span><span class="sxs-lookup"><span data-stu-id="20d62-128">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.FoundationContract\<*version*></span></span>|

<span data-ttu-id="20d62-129">Im Fenster **Eigenschaften** legen Sie das **Lokale Kopie** Feld für **Windows.winmd** und **Windows.Foundation.FoundationContract.winmd** auf **Falsch** fest.</span><span class="sxs-lookup"><span data-stu-id="20d62-129">In the **Properties** window, set the **Copy Local** field of the **Windows.winmd** and **Windows.Foundation.FoundationContract.winmd** files to **False**.</span></span>

![„Lokal kopieren“-Feld](images/desktop-to-uwp/copy-local-field.png)

### <a name="modify-a-c-project-to-use-uwp-apis"></a><span data-ttu-id="20d62-131">Ändern eines C++ Projekts für UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="20d62-131">Modify a C++ project to use UWP APIs</span></span>

<span data-ttu-id="20d62-132">Öffnen Sie die Eigenschaftenseiten des Projekts.</span><span class="sxs-lookup"><span data-stu-id="20d62-132">Open the property pages of your project.</span></span>

<span data-ttu-id="20d62-133">Legen Sie in den **Allgemeinen** Einstellungen der **C/C++** Einstellungsgruppe das Feld **Windows-Runtime-Erweiterung verwenden** auf **Ja(/ZW)** fest.</span><span class="sxs-lookup"><span data-stu-id="20d62-133">In the **General** settings of the **C/C++** settings group, set the **Consume Windows Runtime Extension** field to **Yes(/ZW)**.</span></span>

   ![Windows-Runtime-Erweiterung verwenden](images/desktop-to-uwp/enable-winrt-objects.png)

<span data-ttu-id="20d62-135">Öffnen Sie das **Zusätzliche #using-Verzeichnisse** Dialogfeld und fügen Sie diese Verzeichnisse hinzu.</span><span class="sxs-lookup"><span data-stu-id="20d62-135">Open the **Additional #using Directories** dialog box, and add these directories.</span></span>

* <span data-ttu-id="20d62-136">C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcpackages</span><span class="sxs-lookup"><span data-stu-id="20d62-136">C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcpackages</span></span>
* <span data-ttu-id="20d62-137">C:\Program Files (x86)\Windows Kits\10\UnionMetadata</span><span class="sxs-lookup"><span data-stu-id="20d62-137">C:\Program Files (x86)\Windows Kits\10\UnionMetadata</span></span>
* <span data-ttu-id="20d62-138">C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.UniversalApiContract\<*latest version*></span><span class="sxs-lookup"><span data-stu-id="20d62-138">C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.UniversalApiContract\<*latest version*></span></span>
* <span data-ttu-id="20d62-139">C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.FoundationContract\<*latest version*></span><span class="sxs-lookup"><span data-stu-id="20d62-139">C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.FoundationContract\<*latest version*></span></span>

![Zusätzliche Using-Verzeichnisse](images/desktop-to-uwp/additional-using.png)

<span data-ttu-id="20d62-141">Öffnen Sie das **Zusätzliche Include-Verzeichnisse**-Dialogfeld und fügen Sie dieses Verzeichnis hinzu: „C:\Program Files“ (x86) \Windows Kits\10\Include\ <*neueste Version*> \um</span><span class="sxs-lookup"><span data-stu-id="20d62-141">Open the **Additional Include Directories** dialog box, and add this directory: C:\Program Files (x86)\Windows Kits\10\Include\<*latest version*>\um</span></span>

![Zusätzliche Include-Verzeichnisse](images/desktop-to-uwp/additional-include.png)

<span data-ttu-id="20d62-143">In den **Codegenerierung**-Einstellungen der **C/C++** Einstellungsgruppe legen die **Minimales Neuerstellen aktivieren** auf **Nein(/GM)** fest.</span><span class="sxs-lookup"><span data-stu-id="20d62-143">In the **Code Generation** settings of the **C/C++** settings group, set the **Enable Minimal Rebuild** setting to **No(/GM-)**.</span></span>

![Minimales Neuerstellen aktivieren](images/desktop-to-uwp/disable-min-build.png)


## <a name="add-windows-10-experiences"></a><span data-ttu-id="20d62-145">Windows10-Funktionen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="20d62-145">Add Windows 10 experiences</span></span>

<span data-ttu-id="20d62-146">Jetzt können Sie moderner Funktionen für Benutzer der Anwendung unter Windows10 Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="20d62-146">Now you're ready to add modern experiences that light up when users run your application on Windows 10.</span></span> <span data-ttu-id="20d62-147">Verwenden Sie diesen Designfluss.</span><span class="sxs-lookup"><span data-stu-id="20d62-147">Use this design flow.</span></span>

<span data-ttu-id="20d62-148">:white_check_mark: **Entscheiden Sie zunächst, welche Funktionen Sie hinzufügen möchten**</span><span class="sxs-lookup"><span data-stu-id="20d62-148">:white_check_mark: **First, decide what experiences you want to add**</span></span>

<span data-ttu-id="20d62-149">Es gibt viele zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="20d62-149">There's lots to choose from.</span></span> <span data-ttu-id="20d62-150">Beispielsweise können Sie mithilfe von Monetisierungs-APIs den Kaufablauf vereinfachen oder mehr Aufmerksamkeit für Ihre App generieren.</span><span class="sxs-lookup"><span data-stu-id="20d62-150">For example, you can simplify your purchase order flow by using monetization APIs, or direct attention to your app when you have something interesting to share, such as a new picture that another user has posted.</span></span>

![Popup](images/desktop-to-uwp/toast.png)

<span data-ttu-id="20d62-152">Auch dann, wenn Benutzer Ihre Nachricht ignorieren oder schließen, können sie diese im Info-Center anzeigen und dann auf die Nachricht klicken, um Ihre App zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="20d62-152">Even if users ignore or dismiss your message, they can see it again in the action center, and then click on the message to open your app.</span></span> <span data-ttu-id="20d62-153">Dies erhöht die Interaktion mit Ihrer App und hat den zusätzlichen Vorteil, das Sie die App tief in das Betriebssystem integrieren.</span><span class="sxs-lookup"><span data-stu-id="20d62-153">This increases engagement with your app and has the added bonus of making your app appear deeply integrated with the operating system.</span></span> <span data-ttu-id="20d62-154">Wir zeigen Ihnen den Code für diese Funktion weiter unten.</span><span class="sxs-lookup"><span data-stu-id="20d62-154">We'll show you the code for that experience a bit later.</span></span>

<span data-ttu-id="20d62-155">Besuchen Sie unsere [Developer Center](https://developer.microsoft.com/windows) mit weiteren Ideen.</span><span class="sxs-lookup"><span data-stu-id="20d62-155">Visit our [developer center](https://developer.microsoft.com/windows) for ideas.</span></span>

<span data-ttu-id="20d62-156">:white_check_mark: **Entscheiden Sie, ob Sie die App verbessern oder erweitern möchten**</span><span class="sxs-lookup"><span data-stu-id="20d62-156">:white_check_mark: **Decide whether to enhance or extend**</span></span>

<span data-ttu-id="20d62-157">Wir verwenden häufig die Begriffe „verbessern“ und „Erweitern“. Daher möchten wir erklären, was diese Begriffe bedeuten.</span><span class="sxs-lookup"><span data-stu-id="20d62-157">You'll often hear us use the terms "enhance" and "extend" so we'll take a moment to explain exactly what each of these terms mean.</span></span>

<span data-ttu-id="20d62-158">Wir verwenden den Begriff „Verbessern“ für UWP-APIs, die Sie direkt aus Ihrer Desktopanwendung aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="20d62-158">We use the term "enhance" to describe UWP APIs that you can call directly from your desktop application.</span></span> <span data-ttu-id="20d62-159">Wenn Sie eine Windows10-Funktion ausgewählt haben, identifizieren Sie die APIs, die Sie benötigen, um sie zu erstellen. Überprüfen Sie dann, ob die API in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="20d62-159">When you've chosen a Windows 10 experience, identify the APIs that you need to create it, and then see if that API appears in this [list](desktop-to-uwp-supported-api.md).</span></span> <span data-ttu-id="20d62-160">Hierbei handelt es sich um eine Liste der APIs, die Sie direkt aus Ihrer Desktopanwendung aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="20d62-160">This is a list of APIs that you can call directly from your desktop application.</span></span> <span data-ttu-id="20d62-161">Wenn Ihre API nicht in dieser Liste angezeigt wird, kann die Funktionalität der zugeordneten API nur in einem UWP-Prozess ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="20d62-161">If your API does not appear in this list, that's because the functionality associated with that API can run only within a UWP process.</span></span> <span data-ttu-id="20d62-162">Häufig sind dies APIs, die moderne Benutzeroberflächenelemente wie z.B. ein UWP-Karten-Steuerelement oder ein Windows Hello-Anmeldung nutzen.</span><span class="sxs-lookup"><span data-stu-id="20d62-162">Often times, these include APIs that show modern UIs such as a UWP map control or a Windows Hello security prompt.</span></span>

<span data-ttu-id="20d62-163">Dies bedeutet, wenn Sie diese Funktionen in der Anwendung nutzen möchten, „erweitern“ sie einfach die Anwendung, indem Sie ein UWP-Projekt zur Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="20d62-163">That said, if you want to include those experiences in your application, just "extend" the application by adding a UWP project to your solution.</span></span> <span data-ttu-id="20d62-164">Das Desktop-Projekt ist immer noch den Einstiegspunkt der Anwendung, aber das UWP-Projekt ermöglicht den Zugriff auf alle APIs, die nicht in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="20d62-164">The desktop project is still the entry point of your application, but the UWP project gives you access to all of the APIs that do not appear in this [list](desktop-to-uwp-supported-api.md).</span></span> <span data-ttu-id="20d62-165">Der Desktopanwendung kann mithilfe eines App-Dienstes mit dem UWP-Prozess kommunizieren. Wir stellen zahlreiche Anleitungen zum Einrichten dieser Kommunikation bereit.</span><span class="sxs-lookup"><span data-stu-id="20d62-165">The desktop application can communicate with the UWP process by using a an app service and we have lots of guidance on how to set that up.</span></span> <span data-ttu-id="20d62-166">Wenn Sie eine Umgebung hinzufügen möchten, die ein UWP-Projekt erfordert finden Sie unter [Erweitern mit UWP](desktop-to-uwp-extend.md) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="20d62-166">If you want to add an experience that requires a UWP project, see [Extend with UWP](desktop-to-uwp-extend.md).</span></span>

<span data-ttu-id="20d62-167">:white_check_mark: **Referenz-API-Verträge**</span><span class="sxs-lookup"><span data-stu-id="20d62-167">:white_check_mark: **Reference API contracts**</span></span>

<span data-ttu-id="20d62-168">Wenn Sie die API direkt aus Ihrer Desktopanwendung aufrufen können, öffnen Sie einen Browser und suchen Sie nach dem Referenzthema für diese API.</span><span class="sxs-lookup"><span data-stu-id="20d62-168">If you can call the API directly from your desktop application, open a browser and search for the reference topic for that API.</span></span>
<span data-ttu-id="20d62-169">Unterhalb der Zusammenfassung der API finden Sie eine Tabelle, die die API-Vertrag für diese API beschreibt.</span><span class="sxs-lookup"><span data-stu-id="20d62-169">Beneath the summary of the API, you'll find a table that describes the API contract for that API.</span></span> <span data-ttu-id="20d62-170">Dies ist ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="20d62-170">Here's an example of that table:</span></span>

![API-Vertrag-Tabelle](images/desktop-to-uwp/contract-table.png)

<span data-ttu-id="20d62-172">Wenn Sie eine .NET-basierte Desktop-App haben, fügen Sie einen Verweis auf den API-Vertrag hinzu und legen Sie die **Lokale Kopie** Eigenschaft dieser Datei auf **Falsch** fest.</span><span class="sxs-lookup"><span data-stu-id="20d62-172">If you have a .NET-based desktop app, add a reference to that API contract, and then set the **Copy Local** property of that file to **False**.</span></span> <span data-ttu-id="20d62-173">Wenn Sie ein C++-basiertes Projekt haben, fügen Sie **Zusätzliche Include-Verzeichnisse** einen Pfad zu dem Ordner hinzu, der diesen Vertrag enthält.</span><span class="sxs-lookup"><span data-stu-id="20d62-173">If you have a C++-based project, add to your **Additional Include Directories**, a path to the folder that contains this contract.</span></span>

<span data-ttu-id="20d62-174">:white_check_mark: **Aufrufen der APIs, um die Funktion hinzuzufügen**</span><span class="sxs-lookup"><span data-stu-id="20d62-174">:white_check_mark: **Call the APIs to add your experience**</span></span>

<span data-ttu-id="20d62-175">Dies ist der Code, den Sie verwenden würden, um dem Benachrichtigungsfenster anzuzeigen, dass wir weiter oben behandelt haben.</span><span class="sxs-lookup"><span data-stu-id="20d62-175">Here's the code that you'd use to show the notification window that we looked at earlier.</span></span> <span data-ttu-id="20d62-176">Diese APIs werden in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt. Sie können diesen Code sofort in Ihrer Desktopanwendung nutzen.</span><span class="sxs-lookup"><span data-stu-id="20d62-176">These APIs appear in this [list](desktop-to-uwp-supported-api.md) so you can add this code to your desktop application and run it right now.</span></span>

```csharp
using Windows.Foundation;
using Windows.System;
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;
...

private void ShowToast()
{
    string title = "featured picture of the day";
    string content = "beautiful scenery";
    string image = "https://unsplash.it/360/180?image=104";
    string logo = "https://unsplash.it/64?image=883";

    string xmlString =
    $@"<toast><visual>
       <binding template='ToastGeneric'>
       <text>{title}</text>
       <text>{content}</text>
       <image src='{image}'/>
       <image src='{logo}' placement='appLogoOverride' hint-crop='circle'/>
       </binding>
      </visual></toast>";

    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);

    ToastNotification toast = new ToastNotification(toastXml);

    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

```C++
using namespace Windows::Foundation;
using namespace Windows::System;
using namespace Windows::UI::Notifications;
using namespace Windows::Data::Xml::Dom;

void UWP::ShowToast()
{
    Platform::String ^title = "featured picture of the day";
    Platform::String ^content = "beautiful scenery";
    Platform::String ^image = "https://unsplash.it/360/180?image=104";
    Platform::String ^logo = "https://unsplash.it/64?image=883";

    Platform::String ^xmlString =
        L"<toast><visual><binding template='ToastGeneric'>" +
        L"<text>" + title + "</text>" +
        L"<text>"+ content + "</text>" +
        L"<image src='" + image + "'/>" +
        L"<image src='" + logo + "'" +
        L" placement='appLogoOverride' hint-crop='circle'/>" +
        L"</binding></visual></toast>";

    XmlDocument ^toastXml = ref new XmlDocument();

    toastXml->LoadXml(xmlString);

    ToastNotificationManager::CreateToastNotifier()->Show(ref new ToastNotification(toastXml));
}
```
<span data-ttu-id="20d62-177">Weitere Informationen zu Benachrichtigungen finden Sie unter [Adaptive und interaktive Popupbenachrichtigungen](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts).</span><span class="sxs-lookup"><span data-stu-id="20d62-177">To learn more about notifications, see [Adaptive and Interactive toast notifications](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts).</span></span>

## <a name="support-windows-xp-windows-vista-and-windows-78-install-bases"></a><span data-ttu-id="20d62-178">Unterstützung der Windows XP-, Windows Vista- und Windows7/8-Installationsbasis</span><span class="sxs-lookup"><span data-stu-id="20d62-178">Support Windows XP, Windows Vista, and Windows 7/8 install bases</span></span>

<span data-ttu-id="20d62-179">Sie können Ihre App für Windows10 modernisieren, ohne eine neue Verzweigung zu erstellen und eine separate Codebasis verwalten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="20d62-179">You can modernize your app for Windows 10 without having to create a new branch and maintain separate code bases.</span></span>

<span data-ttu-id="20d62-180">Wenn Sie separate Binärdateien für Windows10-Benutzer erstellen möchten, verwenden Sie die bedingten Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="20d62-180">If you want to build separate binaries for Windows 10 users, use conditional compilation.</span></span> <span data-ttu-id="20d62-181">Wenn Sie einen Satz von Binärdateien für alle Windows-Benutzer erstellen möchten, verwenden Sie Laufzeitprüfungen.</span><span class="sxs-lookup"><span data-stu-id="20d62-181">If you'd prefer to build one set of binaries that you deploy to all Windows users, use runtime checks.</span></span>

<span data-ttu-id="20d62-182">Schauen wir uns die Optionen an.</span><span class="sxs-lookup"><span data-stu-id="20d62-182">Let's take a quick look at each option.</span></span>

### <a name="conditional-compilation"></a><span data-ttu-id="20d62-183">Bedingte Kompilierung</span><span class="sxs-lookup"><span data-stu-id="20d62-183">Conditional compilation</span></span>

<span data-ttu-id="20d62-184">Sie können eine Codebasis beibehalten und einen Satz Binärdateien nur für Windows10-Benutzer kompilieren.</span><span class="sxs-lookup"><span data-stu-id="20d62-184">You can keep one code base and compile a set of binaries just for Windows 10 users.</span></span>

<span data-ttu-id="20d62-185">Fügen Sie Ihrem Projekt zuerst eine neue Buildkonfiguration hinzu.</span><span class="sxs-lookup"><span data-stu-id="20d62-185">First, add a new build configuration to your project.</span></span>

![Buildkonfiguration](images/desktop-to-uwp/build-config.png)

<span data-ttu-id="20d62-187">Erstellen Sie für diese Buildkonfiguration eine Konstante, um den Code zu identifizieren, der UWP-APIs aufruft.</span><span class="sxs-lookup"><span data-stu-id="20d62-187">For that build configuration, create a constant that to identify code that calls UWP APIs.</span></span>  

<span data-ttu-id="20d62-188">Für .NET-basierte Projekte heißt die Konstante **Bedingte Kompilierungskonstante**.</span><span class="sxs-lookup"><span data-stu-id="20d62-188">For .NET-based projects, the constant is called a **Conditional Compilation Constant**.</span></span>

![Preprozessor](images/desktop-to-uwp/compilation-constants.png)

<span data-ttu-id="20d62-190">Für C++ basierte Projekte heißt die Konstante **Preprozessordefinition**.</span><span class="sxs-lookup"><span data-stu-id="20d62-190">For C++-based projects, the constant is called a **Preprocessor Definition**.</span></span>

![Preprozessor](images/desktop-to-uwp/pre-processor.png)

<span data-ttu-id="20d62-192">Fügen Sie die Konstanten vor jedem UWP-Codeblock hinzu.</span><span class="sxs-lookup"><span data-stu-id="20d62-192">Add that constant before any block of UWP code.</span></span>

```csharp

[System.Diagnostics.Conditional("_UWP")]
private void ShowToast()
{
 ...
}

```

```C++

#if _UWP
void UWP::ShowToast()
{
 ...
}
#endif

```

<span data-ttu-id="20d62-193">Der Compiler erstellt den Code nur dann, wenn die Konstante in der aktiven Buildkonfiguration definiert ist.</span><span class="sxs-lookup"><span data-stu-id="20d62-193">The compiler builds that code only if that constant is defined in your active build configuration.</span></span>

### <a name="runtime-checks"></a><span data-ttu-id="20d62-194">Laufzeitprüfungen</span><span class="sxs-lookup"><span data-stu-id="20d62-194">Runtime checks</span></span>

<span data-ttu-id="20d62-195">Sie können einen Satz von Binärdateien für alle Windows-Benutzer kompilieren, unabhängig davon, welche Version von Windows sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="20d62-195">You can compile one set of binaries for all of your Windows users regardless of which version of Windows they run.</span></span> <span data-ttu-id="20d62-196">Ihre App ruft UWP-APIs nur dann auf, wenn der Benutzer Ihre App als verpackte App für Windows10 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="20d62-196">Your app calls UWP APIs only if the user is runs your app as a packaged app on Windows 10.</span></span>

<span data-ttu-id="20d62-197">Die einfachste Methode zum Hinzufügen von Laufzeitprüfungen zum Code ist die Installation des Nuget-Pakets [Desktop Bridge Helpers](https://www.nuget.org/packages/DesktopBridge.Helpers/) und die Verwendung der ``IsRunningAsUWP()``-Methode, um den ganzen UWP-Code abzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="20d62-197">The easiest way to add runtime checks to your code is to install this Nuget package: [Desktop Bridge Helpers](https://www.nuget.org/packages/DesktopBridge.Helpers/) and then use the ``IsRunningAsUWP()`` method to gate off all UWP code.</span></span> <span data-ttu-id="20d62-198">Weitere Detail finden Sie in diesem Blogbeitrag: [Desktop-Brücke - Identifizieren des Anwendungskontexts](https://blogs.msdn.microsoft.com/appconsult/2016/11/03/desktop-bridge-identify-the-applications-context/).</span><span class="sxs-lookup"><span data-stu-id="20d62-198">see this blog post for more details: [Desktop Bridge - Identify the application's context](https://blogs.msdn.microsoft.com/appconsult/2016/11/03/desktop-bridge-identify-the-applications-context/).</span></span>

## <a name="related-video"></a><span data-ttu-id="20d62-199">Verwandte Videos</span><span class="sxs-lookup"><span data-stu-id="20d62-199">Related Video</span></span>

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Use-UWP-APIs-in-Your-Code-3d78c6WhD_9506218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="related-samples"></a><span data-ttu-id="20d62-200">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="20d62-200">Related Samples</span></span>

* [<span data-ttu-id="20d62-201">„Hello world“-Beispiel</span><span class="sxs-lookup"><span data-stu-id="20d62-201">Hello World Sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/HelloWorldSample)
* [<span data-ttu-id="20d62-202">Sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="20d62-202">Secondary Tile</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [<span data-ttu-id="20d62-203">Store-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="20d62-203">Store API Sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/StoreSample)
* [<span data-ttu-id="20d62-204">WinForms-App, die einen UWP-UpdateTask implementiert.</span><span class="sxs-lookup"><span data-stu-id="20d62-204">WinForms app that implements a UWP UpdateTask</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinFormsUpdateTaskSample)
* [<span data-ttu-id="20d62-205">Beispiele für Desktop-App-Brücke zu UWP</span><span class="sxs-lookup"><span data-stu-id="20d62-205">Desktop app bridge to UWP Samples</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)


## <a name="support-and-feedback"></a><span data-ttu-id="20d62-206">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="20d62-206">Support and feedback</span></span>

**<span data-ttu-id="20d62-207">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="20d62-207">Find answers to specific questions</span></span>**

<span data-ttu-id="20d62-208">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="20d62-208">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="20d62-209">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="20d62-209">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="20d62-210">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="20d62-210">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial)</span></span>

**<span data-ttu-id="20d62-211">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="20d62-211">Give feedback about this article</span></span>**

<span data-ttu-id="20d62-212">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="20d62-212">Use the comments section below.</span></span>
