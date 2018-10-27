---
author: normesta
Description: Enhance your desktop application for Windows 10 users by using Universal Windows Platform (UWP) APIs.
Search.Product: eADQiWindows 10XVcnh
title: Verbessern Ihrer Desktopanwendung für Windows10
ms.author: normesta
ms.date: 10/15/2018
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5e76d3d517be73417777eb31dfc3994f92186522
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5685949"
---
# <a name="enhance-your-desktop-application-for-windows-10"></a><span data-ttu-id="c99fb-103">Verbessern Sie Ihre Desktopanwendung für Windows10</span><span class="sxs-lookup"><span data-stu-id="c99fb-103">Enhance your desktop application for Windows 10</span></span>

<span data-ttu-id="c99fb-104">Sie können Windows-Runtime-APIs verwenden, moderne Funktionen hinzufügen, die für Windows 10-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c99fb-104">You can use Windows Runtime APIs to add modern experiences that light up for Windows 10 users.</span></span>

<span data-ttu-id="c99fb-105">Richten Sie zuerst Ihr Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="c99fb-105">First, set up your project.</span></span> <span data-ttu-id="c99fb-106">Dann fügen Sie Windows10-Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="c99fb-106">Then, add Windows 10 experiences.</span></span> <span data-ttu-id="c99fb-107">Sie können separate Builds für Windows10-Benutzer erstellen oder die gleichen Binärdateien für alle Benutzer verteilen – unabhängig davon, welche Version von Windows sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-107">You can build separately for Windows 10 users or distribute the same exact binaries to all users regardless of which version of Windows they run.</span></span>

## <a name="first-set-up-your-project"></a><span data-ttu-id="c99fb-108">Einrichten Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="c99fb-108">First, set up your project</span></span>

<span data-ttu-id="c99fb-109">Sie müssen einige Änderungen am Projekt vornehmen, um UWP-APIs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c99fb-109">You'll have to make a few changes to your project to use UWP APIs.</span></span>

### <a name="modify-a-net-project-to-use-windows-runtime-apis"></a><span data-ttu-id="c99fb-110">Ändern eines .NET-Projekts für Windows Runtime-APIs</span><span class="sxs-lookup"><span data-stu-id="c99fb-110">Modify a .NET project to use Windows Runtime APIs</span></span>

<span data-ttu-id="c99fb-111">Öffnen Sie das **Verweis-Manager**-Dialogfeld, wählen Sie die **Durchsuchen**-Schaltfläche, und wählen Sie dann **Alle Dateien** aus.</span><span class="sxs-lookup"><span data-stu-id="c99fb-111">Open the **Reference Manager** dialog box, choose the **Browse** button, and then select  **All Files**.</span></span>

![Dialogfeld „Verweis hinzufügen“](images/desktop-to-uwp/browse-references.png)

<span data-ttu-id="c99fb-113">Fügen Sie dann einen Verweis auf diese Dateien hinzu.</span><span class="sxs-lookup"><span data-stu-id="c99fb-113">Then, add a reference to these files.</span></span>

|<span data-ttu-id="c99fb-114">Datei</span><span class="sxs-lookup"><span data-stu-id="c99fb-114">File</span></span>|<span data-ttu-id="c99fb-115">Speicherort</span><span class="sxs-lookup"><span data-stu-id="c99fb-115">Location</span></span>|
|--|--|
|<span data-ttu-id="c99fb-116">System.Runtime.WindowsRuntime</span><span class="sxs-lookup"><span data-stu-id="c99fb-116">System.Runtime.WindowsRuntime</span></span>|<span data-ttu-id="c99fb-117">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="c99fb-117">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="c99fb-118">System.Runtime.WindowsRuntime.UI.Xaml</span><span class="sxs-lookup"><span data-stu-id="c99fb-118">System.Runtime.WindowsRuntime.UI.Xaml</span></span>|<span data-ttu-id="c99fb-119">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="c99fb-119">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="c99fb-120">System.Runtime.InteropServices.WindowsRuntime</span><span class="sxs-lookup"><span data-stu-id="c99fb-120">System.Runtime.InteropServices.WindowsRuntime</span></span>|<span data-ttu-id="c99fb-121">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span><span class="sxs-lookup"><span data-stu-id="c99fb-121">C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5</span></span>|
|<span data-ttu-id="c99fb-122">Windows.winmd</span><span class="sxs-lookup"><span data-stu-id="c99fb-122">Windows.winmd</span></span>|<span data-ttu-id="c99fb-123">C:\Program Files (x86)\Windows Kits\10\UnionMetadata\Facade</span><span class="sxs-lookup"><span data-stu-id="c99fb-123">C:\Program Files (x86)\Windows Kits\10\UnionMetadata\Facade</span></span>|
|<span data-ttu-id="c99fb-124">Windows.Foundation.UniversalApiContract.winmd</span><span class="sxs-lookup"><span data-stu-id="c99fb-124">Windows.Foundation.UniversalApiContract.winmd</span></span>|<span data-ttu-id="c99fb-125">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.UniversalApiContract\<*version*></span><span class="sxs-lookup"><span data-stu-id="c99fb-125">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.UniversalApiContract\<*version*></span></span>|
|<span data-ttu-id="c99fb-126">Windows.Foundation.FoundationContract.winmd</span><span class="sxs-lookup"><span data-stu-id="c99fb-126">Windows.Foundation.FoundationContract.winmd</span></span>|<span data-ttu-id="c99fb-127">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.FoundationContract\<*version*></span><span class="sxs-lookup"><span data-stu-id="c99fb-127">C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.FoundationContract\<*version*></span></span>|

<span data-ttu-id="c99fb-128">Legen Sie im Dialogfeld **Eigenschaften** die **lokale Kopie** jeder *winmd*-Datei auf **Falsch** fest.</span><span class="sxs-lookup"><span data-stu-id="c99fb-128">In the **Properties** window, set the **Copy Local** field of each *.winmd* file to **False**.</span></span>

![„Lokal kopieren“-Feld](images/desktop-to-uwp/copy-local-field.png)

### <a name="modify-a-c-project-to-use-windows-runtime-apis"></a><span data-ttu-id="c99fb-130">Ändern eines C++ Projekts für Windows-Runtime-APIs verwenden</span><span class="sxs-lookup"><span data-stu-id="c99fb-130">Modify a C++ project to use Windows Runtime APIs</span></span>

<span data-ttu-id="c99fb-131">Verwendung [C++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) Windows-Runtime-APIs nutzen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-131">Use [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) to consume Windows Runtime APIs.</span></span> <span data-ttu-id="c99fb-132">C++/WinRT ist eine vollständig standardisierte, moderne C++17-Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet.</span><span class="sxs-lookup"><span data-stu-id="c99fb-132">C++/WinRT is an entirely standard modern C++17 language projection for Windows Runtime (WinRT) APIs, implemented as a header-file-based library, and designed to provide you with first-class access to the modern Windows API.</span></span>

<span data-ttu-id="c99fb-133">Zum Konfigurieren des Projekts für C++ / WinRT, siehe [Ändern Sie ein Projekt Windows-Desktop-Anwendung zum Hinzufügen von C++ / WinRT-Unterstützung](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/get-started#modify-a-windows-desktop-application-project-to-add-cwinrt-support).</span><span class="sxs-lookup"><span data-stu-id="c99fb-133">To configure your project for C++/WinRT, See [Modify a Windows Desktop application project to add C++/WinRT support](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/get-started#modify-a-windows-desktop-application-project-to-add-cwinrt-support).</span></span>

## <a name="add-windows-10-experiences"></a><span data-ttu-id="c99fb-134">Windows10-Funktionen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="c99fb-134">Add Windows 10 experiences</span></span>

<span data-ttu-id="c99fb-135">Jetzt können Sie moderner Funktionen für Benutzer der Anwendung unter Windows10 Hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-135">Now you're ready to add modern experiences that light up when users run your application on Windows 10.</span></span> <span data-ttu-id="c99fb-136">Verwenden Sie diesen Designfluss.</span><span class="sxs-lookup"><span data-stu-id="c99fb-136">Use this design flow.</span></span>

<span data-ttu-id="c99fb-137">:white_check_mark: **Entscheiden Sie zunächst, welche Funktionen Sie hinzufügen möchten**</span><span class="sxs-lookup"><span data-stu-id="c99fb-137">:white_check_mark: **First, decide what experiences you want to add**</span></span>

<span data-ttu-id="c99fb-138">Es gibt viele zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="c99fb-138">There's lots to choose from.</span></span> <span data-ttu-id="c99fb-139">Beispielsweise können Sie Ihre Purchase Reihenfolge Fluss mithilfe von monetisierungs-APIs oder mehr Aufmerksamkeit für Ihre Anwendung beim stehen Ihnen interessante, z. B. ein neues Bild mit Teilen kaufablauf vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-139">For example, you can simplify your purchase order flow by using monetization APIs, or direct attention to your application when you have something interesting to share, such as a new picture that another user has posted.</span></span>

![Popup](images/desktop-to-uwp/toast.png)

<span data-ttu-id="c99fb-141">Auch dann, wenn Benutzer Ihre Nachricht ignorieren oder schließen, können sie diese im Info-Center anzeigen und dann auf die Nachricht klicken, um Ihre App zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-141">Even if users ignore or dismiss your message, they can see it again in the action center, and then click on the message to open your app.</span></span> <span data-ttu-id="c99fb-142">Dies erhöht die Interaktion mit Ihrer Anwendung und hat den zusätzlichen Vorteil, Ihre Anwendung tief in das Betriebssystem integrieren.</span><span class="sxs-lookup"><span data-stu-id="c99fb-142">This increases engagement with your application and has the added bonus of making your application appear deeply integrated with the operating system.</span></span> <span data-ttu-id="c99fb-143">Wir zeigen Ihnen den Code für diese Funktion weiter unten.</span><span class="sxs-lookup"><span data-stu-id="c99fb-143">We'll show you the code for that experience a bit later.</span></span>

<span data-ttu-id="c99fb-144">Besuchen Sie unsere [Developer Center](https://developer.microsoft.com/windows) mit weiteren Ideen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-144">Visit our [developer center](https://developer.microsoft.com/windows) for ideas.</span></span>

<span data-ttu-id="c99fb-145">:white_check_mark: **Entscheiden Sie, ob Sie die App verbessern oder erweitern möchten**</span><span class="sxs-lookup"><span data-stu-id="c99fb-145">:white_check_mark: **Decide whether to enhance or extend**</span></span>

<span data-ttu-id="c99fb-146">Wir verwenden häufig die Begriffe „verbessern“ und „Erweitern“. Daher möchten wir erklären, was diese Begriffe bedeuten.</span><span class="sxs-lookup"><span data-stu-id="c99fb-146">You'll often hear us use the terms "enhance" and "extend" so we'll take a moment to explain exactly what each of these terms mean.</span></span>

<span data-ttu-id="c99fb-147">Wir verwenden den Begriff "verbessern" Windows-Runtime-APIs zu beschreiben, die Sie direkt aus Ihrer Desktopanwendung aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="c99fb-147">We use the term "enhance" to describe Windows Runtime APIs that you can call directly from your desktop application.</span></span> <span data-ttu-id="c99fb-148">Wenn Sie eine Windows10-Funktion ausgewählt haben, identifizieren Sie die APIs, die Sie benötigen, um sie zu erstellen. Überprüfen Sie dann, ob die API in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c99fb-148">When you've chosen a Windows 10 experience, identify the APIs that you need to create it, and then see if that API appears in this [list](desktop-to-uwp-supported-api.md).</span></span> <span data-ttu-id="c99fb-149">Hierbei handelt es sich um eine Liste der APIs, die Sie direkt aus Ihrer Desktopanwendung aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="c99fb-149">This is a list of APIs that you can call directly from your desktop application.</span></span> <span data-ttu-id="c99fb-150">Wenn Ihre API nicht in dieser Liste angezeigt wird, kann die Funktionalität der zugeordneten API nur in einem UWP-Prozess ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c99fb-150">If your API does not appear in this list, that's because the functionality associated with that API can run only within a UWP process.</span></span> <span data-ttu-id="c99fb-151">Häufig sind dies APIs, die moderne Benutzeroberflächenelemente wie z.B. ein UWP-Karten-Steuerelement oder ein Windows Hello-Anmeldung nutzen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-151">Often times, these include APIs that show modern UIs such as a UWP map control or a Windows Hello security prompt.</span></span>

<span data-ttu-id="c99fb-152">Dies bedeutet, wenn Sie diese Funktionen in der Anwendung nutzen möchten, „erweitern“ sie einfach die Anwendung, indem Sie ein UWP-Projekt zur Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-152">That said, if you want to include those experiences in your application, just "extend" the application by adding a UWP project to your solution.</span></span> <span data-ttu-id="c99fb-153">Das Desktop-Projekt ist immer noch den Einstiegspunkt der Anwendung, aber das UWP-Projekt ermöglicht den Zugriff auf alle APIs, die nicht in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="c99fb-153">The desktop project is still the entry point of your application, but the UWP project gives you access to all of the APIs that do not appear in this [list](desktop-to-uwp-supported-api.md).</span></span> <span data-ttu-id="c99fb-154">Der Desktopanwendung kann mithilfe eines App-Dienstes mit dem UWP-Prozess kommunizieren. Wir stellen zahlreiche Anleitungen zum Einrichten dieser Kommunikation bereit.</span><span class="sxs-lookup"><span data-stu-id="c99fb-154">The desktop application can communicate with the UWP process by using a an app service and we have lots of guidance on how to set that up.</span></span> <span data-ttu-id="c99fb-155">Wenn Sie eine Umgebung hinzufügen möchten, die ein UWP-Projekt erfordert finden Sie unter [Erweitern mit UWP](desktop-to-uwp-extend.md) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-155">If you want to add an experience that requires a UWP project, see [Extend with UWP](desktop-to-uwp-extend.md).</span></span>

<span data-ttu-id="c99fb-156">:white_check_mark: **Referenz-API-Verträge**</span><span class="sxs-lookup"><span data-stu-id="c99fb-156">:white_check_mark: **Reference API contracts**</span></span>

<span data-ttu-id="c99fb-157">Wenn Sie die API direkt aus Ihrer Desktopanwendung aufrufen können, öffnen Sie einen Browser und suchen Sie nach dem Referenzthema für diese API.</span><span class="sxs-lookup"><span data-stu-id="c99fb-157">If you can call the API directly from your desktop application, open a browser and search for the reference topic for that API.</span></span>
<span data-ttu-id="c99fb-158">Unterhalb der Zusammenfassung der API finden Sie eine Tabelle, die die API-Vertrag für diese API beschreibt.</span><span class="sxs-lookup"><span data-stu-id="c99fb-158">Beneath the summary of the API, you'll find a table that describes the API contract for that API.</span></span> <span data-ttu-id="c99fb-159">Dies ist ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="c99fb-159">Here's an example of that table:</span></span>

![API-Vertrag-Tabelle](images/desktop-to-uwp/contract-table.png)

<span data-ttu-id="c99fb-161">Wenn Sie eine .NET-basierte Desktop-App haben, fügen Sie einen Verweis auf den API-Vertrag hinzu und legen Sie die **Lokale Kopie** Eigenschaft dieser Datei auf **Falsch** fest.</span><span class="sxs-lookup"><span data-stu-id="c99fb-161">If you have a .NET-based desktop app, add a reference to that API contract, and then set the **Copy Local** property of that file to **False**.</span></span> <span data-ttu-id="c99fb-162">Wenn Sie ein C++-basiertes Projekt haben, fügen Sie **Zusätzliche Include-Verzeichnisse** einen Pfad zu dem Ordner hinzu, der diesen Vertrag enthält.</span><span class="sxs-lookup"><span data-stu-id="c99fb-162">If you have a C++-based project, add to your **Additional Include Directories**, a path to the folder that contains this contract.</span></span>

<span data-ttu-id="c99fb-163">:white_check_mark: **Aufrufen der APIs, um die Funktion hinzuzufügen**</span><span class="sxs-lookup"><span data-stu-id="c99fb-163">:white_check_mark: **Call the APIs to add your experience**</span></span>

<span data-ttu-id="c99fb-164">Dies ist der Code, den Sie verwenden würden, um dem Benachrichtigungsfenster anzuzeigen, dass wir weiter oben behandelt haben.</span><span class="sxs-lookup"><span data-stu-id="c99fb-164">Here's the code that you'd use to show the notification window that we looked at earlier.</span></span> <span data-ttu-id="c99fb-165">Diese APIs werden in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt. Sie können diesen Code sofort in Ihrer Desktopanwendung nutzen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-165">These APIs appear in this [list](desktop-to-uwp-supported-api.md) so you can add this code to your desktop application and run it right now.</span></span>

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
    string image = "https://picsum.photos/360/180?image=104";
    string logo = "https://picsum.photos/64?image=883";

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
    Platform::String ^image = "https://picsum.photos/360/180?image=104";
    Platform::String ^logo = "https://picsum.photos/64?image=883";

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
<span data-ttu-id="c99fb-166">Weitere Informationen zu Benachrichtigungen finden Sie unter [Adaptive und interaktive Popupbenachrichtigungen](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/adaptive-interactive-toasts).</span><span class="sxs-lookup"><span data-stu-id="c99fb-166">To learn more about notifications, see [Adaptive and Interactive toast notifications](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/adaptive-interactive-toasts).</span></span>

## <a name="support-windows-xp-windows-vista-and-windows-78-install-bases"></a><span data-ttu-id="c99fb-167">Unterstützung der Windows XP-, Windows Vista- und Windows7/8-Installationsbasis</span><span class="sxs-lookup"><span data-stu-id="c99fb-167">Support Windows XP, Windows Vista, and Windows 7/8 install bases</span></span>

<span data-ttu-id="c99fb-168">Sie können Ihre Anwendung für Windows 10 modernisieren, ohne dass eine neue Verzweigung zu erstellen und eine separate Codebasis verwalten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-168">You can modernize your application for Windows 10 without having to create a new branch and maintain separate code bases.</span></span>

<span data-ttu-id="c99fb-169">Wenn Sie separate Binärdateien für Windows10-Benutzer erstellen möchten, verwenden Sie die bedingten Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="c99fb-169">If you want to build separate binaries for Windows 10 users, use conditional compilation.</span></span> <span data-ttu-id="c99fb-170">Wenn Sie einen Satz von Binärdateien für alle Windows-Benutzer erstellen möchten, verwenden Sie Laufzeitprüfungen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-170">If you'd prefer to build one set of binaries that you deploy to all Windows users, use runtime checks.</span></span>

<span data-ttu-id="c99fb-171">Schauen wir uns die Optionen an.</span><span class="sxs-lookup"><span data-stu-id="c99fb-171">Let's take a quick look at each option.</span></span>

### <a name="conditional-compilation"></a><span data-ttu-id="c99fb-172">Bedingte Kompilierung</span><span class="sxs-lookup"><span data-stu-id="c99fb-172">Conditional compilation</span></span>

<span data-ttu-id="c99fb-173">Sie können eine Codebasis beibehalten und einen Satz Binärdateien nur für Windows10-Benutzer kompilieren.</span><span class="sxs-lookup"><span data-stu-id="c99fb-173">You can keep one code base and compile a set of binaries just for Windows 10 users.</span></span>

<span data-ttu-id="c99fb-174">Fügen Sie Ihrem Projekt zuerst eine neue Buildkonfiguration hinzu.</span><span class="sxs-lookup"><span data-stu-id="c99fb-174">First, add a new build configuration to your project.</span></span>

![Buildkonfiguration](images/desktop-to-uwp/build-config.png)

<span data-ttu-id="c99fb-176">Erstellen Sie für diese Buildkonfiguration eine Konstante, um den Code zu identifizieren, die Windows-Runtime-APIs aufruft.</span><span class="sxs-lookup"><span data-stu-id="c99fb-176">For that build configuration, create a constant that to identify code that calls Windows Runtime APIs.</span></span>  

<span data-ttu-id="c99fb-177">Für .NET-basierte Projekte heißt die Konstante **Bedingte Kompilierungskonstante**.</span><span class="sxs-lookup"><span data-stu-id="c99fb-177">For .NET-based projects, the constant is called a **Conditional Compilation Constant**.</span></span>

![Preprozessor](images/desktop-to-uwp/compilation-constants.png)

<span data-ttu-id="c99fb-179">Für C++ basierte Projekte heißt die Konstante **Preprozessordefinition**.</span><span class="sxs-lookup"><span data-stu-id="c99fb-179">For C++-based projects, the constant is called a **Preprocessor Definition**.</span></span>

![Preprozessor](images/desktop-to-uwp/pre-processor.png)

<span data-ttu-id="c99fb-181">Fügen Sie die Konstanten vor jedem UWP-Codeblock hinzu.</span><span class="sxs-lookup"><span data-stu-id="c99fb-181">Add that constant before any block of UWP code.</span></span>

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

<span data-ttu-id="c99fb-182">Der Compiler erstellt den Code nur dann, wenn die Konstante in der aktiven Buildkonfiguration definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c99fb-182">The compiler builds that code only if that constant is defined in your active build configuration.</span></span>

### <a name="runtime-checks"></a><span data-ttu-id="c99fb-183">Laufzeitprüfungen</span><span class="sxs-lookup"><span data-stu-id="c99fb-183">Runtime checks</span></span>

<span data-ttu-id="c99fb-184">Sie können einen Satz von Binärdateien für alle Windows-Benutzer kompilieren, unabhängig davon, welche Version von Windows sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-184">You can compile one set of binaries for all of your Windows users regardless of which version of Windows they run.</span></span> <span data-ttu-id="c99fb-185">Ihre Anwendung ruft Windows-Runtime-APIs nur dann, wenn der Benutzer ausgeführt wird die Anwendung als verpackten Anwendung unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c99fb-185">Your application calls Windows Runtime APIs only if the user is runs your application as a packaged application on Windows 10.</span></span>

<span data-ttu-id="c99fb-186">Die einfachste Möglichkeit zum Hinzufügen von laufzeitprüfungen zum Code ist zum Installieren von Nuget-Pakets: [Desktop Bridge Helpers](https://www.nuget.org/packages/DesktopBridge.Helpers/) und verwenden Sie dann die ``IsRunningAsUWP()`` -Methode auf, um alle Code, der Windows-Runtime-APIs aufruft abzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="c99fb-186">The easiest way to add runtime checks to your code is to install this Nuget package: [Desktop Bridge Helpers](https://www.nuget.org/packages/DesktopBridge.Helpers/) and then use the ``IsRunningAsUWP()`` method to gate off all code that calls Windows Runtime APIs.</span></span> <span data-ttu-id="c99fb-187">Weitere Detail finden Sie in diesem Blogbeitrag: [Desktop-Brücke - Identifizieren des Anwendungskontexts](https://blogs.msdn.microsoft.com/appconsult/2016/11/03/desktop-bridge-identify-the-applications-context/).</span><span class="sxs-lookup"><span data-stu-id="c99fb-187">see this blog post for more details: [Desktop Bridge - Identify the application's context](https://blogs.msdn.microsoft.com/appconsult/2016/11/03/desktop-bridge-identify-the-applications-context/).</span></span>

## <a name="related-video"></a><span data-ttu-id="c99fb-188">Verwandte Videos</span><span class="sxs-lookup"><span data-stu-id="c99fb-188">Related Video</span></span>

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Use-UWP-APIs-in-Your-Code-3d78c6WhD_9506218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="related-samples"></a><span data-ttu-id="c99fb-189">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="c99fb-189">Related Samples</span></span>

* [<span data-ttu-id="c99fb-190">„Hello world“-Beispiel</span><span class="sxs-lookup"><span data-stu-id="c99fb-190">Hello World Sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/HelloWorldSample)
* [<span data-ttu-id="c99fb-191">Sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="c99fb-191">Secondary Tile</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [<span data-ttu-id="c99fb-192">Store-API-Beispiel</span><span class="sxs-lookup"><span data-stu-id="c99fb-192">Store API Sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/StoreSample)
* [<span data-ttu-id="c99fb-193">WinForms-Anwendung, die eine UWP-UpdateTask implementiert.</span><span class="sxs-lookup"><span data-stu-id="c99fb-193">WinForms application that implements a UWP UpdateTask</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinFormsUpdateTaskSample)
* [<span data-ttu-id="c99fb-194">Beispiele für Desktop-App-Brücke zu UWP</span><span class="sxs-lookup"><span data-stu-id="c99fb-194">Desktop app bridge to UWP Samples</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)


## <a name="support-and-feedback"></a><span data-ttu-id="c99fb-195">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="c99fb-195">Support and feedback</span></span>

**<span data-ttu-id="c99fb-196">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="c99fb-196">Find answers to your questions</span></span>**

<span data-ttu-id="c99fb-197">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="c99fb-197">Have questions?</span></span> <span data-ttu-id="c99fb-198">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="c99fb-198">Ask us on Stack Overflow.</span></span> <span data-ttu-id="c99fb-199">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="c99fb-199">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="c99fb-200">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="c99fb-200">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="c99fb-201">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="c99fb-201">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="c99fb-202">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="c99fb-202">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
