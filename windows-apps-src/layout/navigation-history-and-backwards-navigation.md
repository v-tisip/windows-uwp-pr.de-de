---
author: mijacobs
Description: "Die Navigation in UWP-Apps (Apps für die Universelle Windows-Plattform) basiert auf einem flexiblen Modell aus Navigationsstrukturen, Navigationselementen und Funktionen auf Systemebene."
title: "Navigationsverlauf und Rückwärtsnavigation (Windows-Apps)"
ms.assetid: e9876b4c-242d-402d-a8ef-3487398ed9b3
isNew: True
label: History and backwards navigation
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: cd3184ebe5e94c410d55a725129a38907aa6a01e
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
#  <a name="navigation-history-and-backwards-navigation-for-uwp-apps"></a><span data-ttu-id="14125-104">Navigationsverlauf und Rückwärtsnavigation für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="14125-104">Navigation history and backwards navigation for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="14125-105">Im Internet stellen die einzelnen Websites eigene Navigationssysteme bereit, beispielsweise Inhaltsverzeichnis, Schaltflächen, Menüs, einfache Listen mit Links usw.</span><span class="sxs-lookup"><span data-stu-id="14125-105">On the Web, individual web sites provide their own navigation systems, such as tables of contents, buttons, menus, simple lists of links, and so on.</span></span> <span data-ttu-id="14125-106">Die Navigationsfunktionalität kann je nach Website stark variieren.</span><span class="sxs-lookup"><span data-stu-id="14125-106">The navigation experience can vary wildly from website to website.</span></span> <span data-ttu-id="14125-107">Es gibt jedoch eine konsistente Navigationsfunktion: Zurück.</span><span class="sxs-lookup"><span data-stu-id="14125-107">However, there is one consistent navigation experience: back.</span></span> <span data-ttu-id="14125-108">Die meisten Browser bieten eine Zurück-Schaltfläche, die unabhängig von der Website das gleiche Verhalten aufweist.</span><span class="sxs-lookup"><span data-stu-id="14125-108">Most browsers provide a back button that behaves the same way regardless of the website.</span></span>

> <span data-ttu-id="14125-109">**Wichtige APIs**: [SystemNavigationManager-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager), [BackRequested-Ereignis](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager#Windows_UI_Core_SystemNavigationManager_BackRequested), [OnNavigatedTo](https://msdn.microsoft.com/library/windows/apps/br227508)</span><span class="sxs-lookup"><span data-stu-id="14125-109">**Important APIs**: [SystemNavigationManager class](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager), [BackRequested event](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager#Windows_UI_Core_SystemNavigationManager_BackRequested), [OnNavigatedTo](https://msdn.microsoft.com/library/windows/apps/br227508)</span></span>

<span data-ttu-id="14125-110">Ähnlichen Gründen enthält die universelle Windows-Plattform (UWP) ein einheitliches System zur Rückwärtsnavigation, mit dem der Navigationsverlauf des Benutzers innerhalb einer App und je nach Gerät von App zu App durchlaufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="14125-110">For similar reasons, the Universal Windows Platform (UWP) provides a consistent back navigation system for traversing the user's navigation history within an app and, depending on the device, from app to app.</span></span>

<span data-ttu-id="14125-111">Die Benutzeroberfläche für die Systemschaltfläche "Zurück" ist für jeden Formfaktor und Eingabegerätetyp optimiert. Die Navigationsfunktionalität hingegen ist auf allen Geräten und UWP-Apps global und einheitlich gültig.</span><span class="sxs-lookup"><span data-stu-id="14125-111">The UI for the system back button is optimized for each form factor and input device type, but the navigation experience is global and consistent across devices and UWP apps.</span></span>

<span data-ttu-id="14125-112">Im Folgenden sind die primären Formfaktoren für die Zurück-Schaltfläche der Benutzeroberfläche aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="14125-112">Here are the primary form factors with the back button UI:</span></span>


<table>
    <tr>
        <td colspan="2"><span data-ttu-id="14125-113">Geräte</span><span class="sxs-lookup"><span data-stu-id="14125-113">Devices</span></span></td>
        <td style="vertical-align:top;"><span data-ttu-id="14125-114">Verhalten der Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="14125-114">Back button behavior</span></span></td>
     </tr>
    <tr>
        <td style="vertical-align:top;"><span data-ttu-id="14125-115">Telefon</span><span class="sxs-lookup"><span data-stu-id="14125-115">Phone</span></span></td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Smartphone](images/back-systemback-phone.png)</td>
        <td style="vertical-align:top;">
        <ul>
<li><span data-ttu-id="14125-117">Immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="14125-117">Always present.</span></span></li>
<li><span data-ttu-id="14125-118">Eine Software- oder Hardwareschaltfläche am unteren Rand des Geräts.</span><span class="sxs-lookup"><span data-stu-id="14125-118">A software or hardware button at the bottom of the device.</span></span></li>
<li><span data-ttu-id="14125-119">Globale Rückwärtsnavigation innerhalb der App und zwischen Apps.</span><span class="sxs-lookup"><span data-stu-id="14125-119">Global back navigation within the app and between apps.</span></span></li>
</ul>
</td>
     </tr>
     <tr>
        <td style="vertical-align:top;"><span data-ttu-id="14125-120">Tablet</span><span class="sxs-lookup"><span data-stu-id="14125-120">Tablet</span></span></td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Tablet (im Tablet-Modus)](images/back-systemback-tablet.png)</td>
        <td style="vertical-align:top;">
<ul>
<li><span data-ttu-id="14125-122">Im Tablet-Modus immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="14125-122">Always present in Tablet mode.</span></span> <span data-ttu-id="14125-123">In Desktopmodus nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14125-123">Not available in Desktop mode.</span></span> <span data-ttu-id="14125-124">Stattdessen kann die Zurück-Schaltfläche in der Titelleiste aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="14125-124">Title bar back button can be enabled, instead.</span></span> <span data-ttu-id="14125-125">Weitere Infos finden Sie unter [PC, Laptop, Tablet](#PC).</span><span class="sxs-lookup"><span data-stu-id="14125-125">See [PC, Laptop, Tablet](#PC).</span></span>
<span data-ttu-id="14125-126">Benutzer können zwischen dem Tablet- und dem Desktopmodus wechseln, indem sie unter **Einstellungen &gt; System &gt; Tablet-Modus** die Option **Durch die Verwendung des Geräts als Tablet wird die Toucheingabe in Windows verbessert** aktivieren.</span><span class="sxs-lookup"><span data-stu-id="14125-126">Users can switch between running in Tablet mode and Desktop mode by going to **Settings &gt; System &gt; Tablet mode** and setting **Make Windows more touch-friendly when using your device as a tablet**.</span></span></li>
<li> <span data-ttu-id="14125-127">Eine Softwareschaltfläche in der Navigationsleiste am unteren Rand des Geräts.</span><span class="sxs-lookup"><span data-stu-id="14125-127">A software button in the navigation bar at the bottom of the device.</span></span></li>
<li><span data-ttu-id="14125-128">Globale Rückwärtsnavigation innerhalb der App und zwischen Apps.</span><span class="sxs-lookup"><span data-stu-id="14125-128">Global back navigation within the app and between apps.</span></span></li></ul>        
        </td>
     </tr>
    <tr>
        <td style="vertical-align:top;"><span data-ttu-id="14125-129">PC, Laptop, Tablet</span><span class="sxs-lookup"><span data-stu-id="14125-129">PC, Laptop, Tablet</span></span></td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem PC oder Laptop](images/back-systemback-pc.png)</td>
        <td style="vertical-align:top;">
<ul>
<li><span data-ttu-id="14125-131">Optional im Desktopmodus.</span><span class="sxs-lookup"><span data-stu-id="14125-131">Optional in Desktop mode.</span></span> <span data-ttu-id="14125-132">Im Tablet-Modus nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14125-132">Not available in Tablet mode.</span></span> <span data-ttu-id="14125-133">Weitere Infos finden Sie unter [Tablet](#Tablet).</span><span class="sxs-lookup"><span data-stu-id="14125-133">See [Tablet](#Tablet).</span></span> <span data-ttu-id="14125-134">Standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="14125-134">Disabled by default.</span></span> <span data-ttu-id="14125-135">Muss zur Verwendung aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="14125-135">Must opt in to enable it.</span></span>
<span data-ttu-id="14125-136">Benutzer können zwischen dem Tablet- und dem Desktopmodus wechseln, indem sie unter **Einstellungen &gt; System &gt; Tablet-Modus** die Option **Durch die Verwendung des Geräts als Tablet wird die Toucheingabe in Windows verbessert** aktivieren.</span><span class="sxs-lookup"><span data-stu-id="14125-136">Users can switch between running in Tablet mode and Desktop mode by going to **Settings &gt; System &gt; Tablet mode** and setting **Make Windows more touch-friendly when using your device as a tablet**.</span></span></li>
<li><span data-ttu-id="14125-137">Eine Softwareschaltfläche in der Titelleiste der App.</span><span class="sxs-lookup"><span data-stu-id="14125-137">A software button in the title bar of the app.</span></span></li>
<li><span data-ttu-id="14125-138">Ermöglicht die Rückwärtsnavigation nur innerhalb der App.</span><span class="sxs-lookup"><span data-stu-id="14125-138">Back navigation within the app only.</span></span> <span data-ttu-id="14125-139">Unterstützt keine App-zu-App-Navigation.</span><span class="sxs-lookup"><span data-stu-id="14125-139">Does not support app-to-app navigation.</span></span></li></ul>        
        </td>
     </tr>
    <tr>
        <td style="vertical-align:top;"><span data-ttu-id="14125-140">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="14125-140">Surface Hub</span></span></td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Surface Hub](images/nav/nav-back-surfacehub.png)</td>
        <td style="vertical-align:top;">
<ul>
<li><span data-ttu-id="14125-142">Optional.</span><span class="sxs-lookup"><span data-stu-id="14125-142">Optional.</span></span></li>
<li><span data-ttu-id="14125-143">Standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="14125-143">Disabled by default.</span></span> <span data-ttu-id="14125-144">Muss zur Verwendung aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="14125-144">Must opt in to enable it.</span></span></li>
<li><span data-ttu-id="14125-145">Eine Softwareschaltfläche in der Titelleiste der App.</span><span class="sxs-lookup"><span data-stu-id="14125-145">A software button in the title bar of the app.</span></span></li>
<li><span data-ttu-id="14125-146">Ermöglicht die Rückwärtsnavigation nur innerhalb der App.</span><span class="sxs-lookup"><span data-stu-id="14125-146">Back navigation within the app only.</span></span> <span data-ttu-id="14125-147">Unterstützt keine App-zu-App-Navigation.</span><span class="sxs-lookup"><span data-stu-id="14125-147">Does not support app-to-app navigation.</span></span></li></ul>        
        </td>
     </tr>     
<table>


<span data-ttu-id="14125-148">Hier sind einige alternative Eingabetypen, die keine Zurück-Schaltfläche auf der Benutzeroberfläche erfordern, aber dieselbe Funktionalität bieten.</span><span class="sxs-lookup"><span data-stu-id="14125-148">Here are some alternative input types that don't rely on a back button UI, but still provide the exact same functionality.</span></span>


<table>
<tr><td colspan="3"><span data-ttu-id="14125-149">Eingabegeräte</span><span class="sxs-lookup"><span data-stu-id="14125-149">Input devices</span></span></td></tr>
<tr><td style="vertical-align:top;"><span data-ttu-id="14125-150">Tastatur</span><span class="sxs-lookup"><span data-stu-id="14125-150">Keyboard</span></span></td><td style="vertical-align:top;">![Tastatur](images/keyboard-wireframe.png)</td><td style="vertical-align:top;"><span data-ttu-id="14125-152">Windows-Taste + RÜCKTASTE</span><span class="sxs-lookup"><span data-stu-id="14125-152">Windows key + Backspace</span></span></td></tr>
<tr><td style="vertical-align:top;"><span data-ttu-id="14125-153">Cortana</span><span class="sxs-lookup"><span data-stu-id="14125-153">Cortana</span></span></td><td style="vertical-align:top;">![Spracherkennung](images/speech-wireframe.png)</td><td style="vertical-align:top;"><span data-ttu-id="14125-155">Sagen Sie „Hey Cortana, zurück.“</span><span class="sxs-lookup"><span data-stu-id="14125-155">Say, "Hey Cortana, go back"</span></span></td></tr>
</table>
 

<span data-ttu-id="14125-156">Wenn Ihre App auf einem Smartphone, Tablet, oder einem PC bzw. Laptop mit aktivierter Zurück-Funktion des Systems ausgeführt wird, informiert das System Ihre App darüber, wenn die Zurück-Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="14125-156">When your app runs on a phone, tablet, or on a PC or laptop that has system back enabled, the system notifies your app when the back button is pressed.</span></span> <span data-ttu-id="14125-157">Der Benutzer erwartet, dass durch Drücken der Zurück-Schaltfläche die vorherige Seite im Navigationsverlauf der App aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="14125-157">The user expects the back button to navigate to the previous location in the app's navigation history.</span></span> <span data-ttu-id="14125-158">Sie können entscheiden, welche Navigationsaktionen dem Navigationsverlauf hinzugefügt werden sollen und wie auf das Drücken der Zurück-Schaltfläche reagiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="14125-158">It's up to you to decide which navigation actions to add to the navigation history and how to respond to the back button press.</span></span>


## <a name="how-to-enable-system-back-navigation-support"></a><span data-ttu-id="14125-159">Aktivieren der Unterstützung für die System-Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="14125-159">How to enable system back navigation support</span></span>


<span data-ttu-id="14125-160">Apps müssen die Rückwärtsnavigation für alle Hardware- und Software-Zurück-Systemschaltflächen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="14125-160">Apps must enable back navigation for all hardware and software system back buttons.</span></span> <span data-ttu-id="14125-161">Dazu registrieren Sie einen Listener für das [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignis und definieren einen entsprechenden Handler.</span><span class="sxs-lookup"><span data-stu-id="14125-161">Do this by registering a listener for the [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596) event and defining a corresponding handler.</span></span>

<span data-ttu-id="14125-162">Hier registrieren wir einen globalen Listener für das [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignis in der CodeBehind-Datei für App.xaml.</span><span class="sxs-lookup"><span data-stu-id="14125-162">Here we register a global listener for the [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596) event in the App.xaml code-behind file.</span></span> <span data-ttu-id="14125-163">Sie können sich für dieses Ereignis auf jeder Seite registrieren, wenn Sie bestimmte Seiten aus der Rückwärtsnavigation ausschließen oder vor dem Anzeigen der Seite Seitenebenencode ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="14125-163">You can register for this event in each page if you want to exclude specific pages from back navigation, or you want to execute page-level code before displaying the page.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += 
    App_BackRequested;
```
```cpp
Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->
    BackRequested += ref new Windows::Foundation::EventHandler<
    Windows::UI::Core::BackRequestedEventArgs^>(
        this, &App::App_BackRequested);
```

<span data-ttu-id="14125-164">Das ist der entsprechende [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignishandler, der [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) im Stammframe der App aufruft.</span><span class="sxs-lookup"><span data-stu-id="14125-164">Here's the corresponding [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596) event handler that calls [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) on the root frame of the app.</span></span>

<span data-ttu-id="14125-165">Dieser Handler wird für ein globales Zurück-Ereignis aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="14125-165">This handler is invoked on a global back event.</span></span> <span data-ttu-id="14125-166">Wenn der In-App-Zurück-Stapel leer ist, navigiert das System ggf. zur vorherigen App im App-Stapel oder zum Startbildschirm zurück.</span><span class="sxs-lookup"><span data-stu-id="14125-166">If the in-app back stack is empty, the system might navigate to the previous app in the app stack or to the Start screen.</span></span> <span data-ttu-id="14125-167">Im Desktopmodus gibt es keinen App-Zurück-Stapel, und der Benutzer bleibt selbst dann in der App, wenn der In-App-Zurück-Stapel leer ist.</span><span class="sxs-lookup"><span data-stu-id="14125-167">There is no app back stack in Desktop mode and the user stays in the app even when the in-app back stack is depleted.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
>private void App_BackRequested(object sender, 
>    Windows.UI.Core.BackRequestedEventArgs e)
>{
>    Frame rootFrame = Window.Current.Content as Frame;
>    if (rootFrame == null)
>        return;
>
>    // Navigate back if possible, and if the event has not 
>    // already been handled .
>    if (rootFrame.CanGoBack && e.Handled == false)
>    {
>        e.Handled = true;
>        rootFrame.GoBack();
>    }
>}
```
```cpp
>void App::App_BackRequested(
>    Platform::Object^ sender, 
>    Windows::UI::Core::BackRequestedEventArgs^ e)
>{
>    Frame^ rootFrame = dynamic_cast<Frame^>(Window::Current->Content);
>    if (rootFrame == nullptr)
>        return;
>
>    // Navigate back if possible, and if the event has not
>    // already been handled.
>    if (rootFrame->CanGoBack && e->Handled == false)
>    {
>        e->Handled = true;
>        rootFrame->GoBack();
>    }
>}
```

## <a name="how-to-enable-the-title-bar-back-button"></a><span data-ttu-id="14125-168">Aktivieren der Schaltfläche „Zurück“ auf der Titelleiste</span><span class="sxs-lookup"><span data-stu-id="14125-168">How to enable the title bar back button</span></span>


<span data-ttu-id="14125-169">Geräte, die den Desktopmodus unterstützen (in der Regel PCs und Laptops, aber auch einige Tablets) und auf denen die Einstellung (**Einstellungen &gt; System &gt; Tablet-Modus**) aktiviert ist, bieten keine globale Navigationsleiste mit der Systemschaltfläche „Zurück“.</span><span class="sxs-lookup"><span data-stu-id="14125-169">Devices that support Desktop mode (typically PCs and laptops, but also some tablets) and have the setting enabled (**Settings &gt; System &gt; Tablet mode**), do not provide a global navigation bar with the system back button.</span></span>

<span data-ttu-id="14125-170">Im Desktopmodus wird jede App in einem Fenster mit Titelleiste ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="14125-170">In Desktop mode, every app runs in a window with a title bar.</span></span> <span data-ttu-id="14125-171">Sie können eine alternative Zurück-Schaltfläche für Ihre App bereitstellen, die in dieser Titelleiste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="14125-171">You can provide an alternative back button for your app that is displayed in this title bar.</span></span>

<span data-ttu-id="14125-172">Die Titelleisten-Zurück-Schaltfläche ist nur in Apps verfügbar, die auf Geräten im Desktop-Modus ausgeführt werden. Sie unterstützt nur den In-App-Navigationsverlauf. Der App-zu-App-Navigationsverlauf wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14125-172">The title bar back button is only available in apps running on devices in Desktop mode, and only supports in-app navigation history—it does not support app-to-app navigation history.</span></span>

<span data-ttu-id="14125-173">**Wichtig**  Die Schaltfläche „Zurück“ der Titelleiste wird standardmäßig nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="14125-173">**Important**  The title bar back button is not displayed by default.</span></span> <span data-ttu-id="14125-174">Sie müssen sie aktivieren.</span><span class="sxs-lookup"><span data-stu-id="14125-174">You must opt in.</span></span>

 

|                                                             |                                                        |
|-------------------------------------------------------------|--------------------------------------------------------|
| ![Keine Zurück-Systemschaltfläche im Desktopmodus](images/nav-noback-pc.png) | ![Zurück-Systemschaltfläche im Desktopmodus](images/nav-back-pc.png) |
| <span data-ttu-id="14125-177">Desktopmodus, keine Rückwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="14125-177">Desktop mode, no back navigation.</span></span>                           | <span data-ttu-id="14125-178">Desktopmodus, Rückwärtsnavigation aktiviert.</span><span class="sxs-lookup"><span data-stu-id="14125-178">Desktop mode, back navigation enabled.</span></span>                 |

 

<span data-ttu-id="14125-179">Überschreiben Sie das [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Ereignis, und legen Sie [**AppViewBackButtonVisibility**](https://msdn.microsoft.com/library/windows/apps/dn986448) in der CodeBehind-Datei für jede Seite in Ihrer App auf [**Visible**](https://msdn.microsoft.com/library/windows/apps/dn986276) fest, für die Sie die Titelleisten-Zurück-Schaltfläche aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="14125-179">Override the [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508) event and set [**AppViewBackButtonVisibility**](https://msdn.microsoft.com/library/windows/apps/dn986448) to [**Visible**](https://msdn.microsoft.com/library/windows/apps/dn986276) in the code-behind file for each page that you want to enable the title bar back button.</span></span>

<span data-ttu-id="14125-180">Für dieses Beispiel wird jede Seite im Zurück-Stapel aufgelistet und die Zurück-Schaltfläche aktiviert, wenn die [**CanGoBack**](https://msdn.microsoft.com/library/windows/apps/br242685)-Eigenschaft des Frames den Wert **true** aufweist.</span><span class="sxs-lookup"><span data-stu-id="14125-180">For this example, we list each page in the back stack and enable the back button if the [**CanGoBack**](https://msdn.microsoft.com/library/windows/apps/br242685) property of the frame has a value of **true**.</span></span>

> [!div class="tabbedCodeSnippets"]
>```csharp
>protected override void OnNavigatedTo(NavigationEventArgs e)
>{
>    Frame rootFrame = Window.Current.Content as Frame;
>
>    string myPages = "";
>    foreach (PageStackEntry page in rootFrame.BackStack)
>    {
>        myPages += page.SourcePageType.ToString() + "\n";
>    }
>    stackCount.Text = myPages;
>
>    if (rootFrame.CanGoBack)
>    {
>        // Show UI in title bar if opted-in and in-app backstack is not empty.
>        SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
>            AppViewBackButtonVisibility.Visible;
>    }
>    else
>    {
>        // Remove the UI from the title bar if in-app back stack is empty.
>        SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
>            AppViewBackButtonVisibility.Collapsed;
>    }
>}
>```
>```cpp
>void StartPage::OnNavigatedTo(NavigationEventArgs^ e)
>{
>    auto rootFrame = dynamic_cast<Windows::UI::Xaml::Controls::Frame^>(Window::Current->Content);
>
>    Platform::String^ myPages = "";
>
>    if (rootFrame == nullptr)
>        return;
>
>    for each (PageStackEntry^ page in rootFrame->BackStack)
>    {
>        myPages += page->SourcePageType.ToString() + "\n";
>    }
>    stackCount->Text = myPages;
>
>    if (rootFrame->CanGoBack)
>    {
>        // If we have pages in our in-app backstack and have opted in to showing back, do so
>        Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->AppViewBackButtonVisibility =
>            Windows::UI::Core::AppViewBackButtonVisibility::Visible;
>    }
>    else
>    {
>        // Remove the UI from the title bar if there are no pages in our in-app back stack
>        Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->AppViewBackButtonVisibility =
>            Windows::UI::Core::AppViewBackButtonVisibility::Collapsed;
>    }
>}
>```


### <a name="guidelines-for-custom-back-navigation-behavior"></a><span data-ttu-id="14125-181">Richtlinien für das benutzerdefinierte Verhalten der Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="14125-181">Guidelines for custom back navigation behavior</span></span>

<span data-ttu-id="14125-182">Wenn Sie Ihre eigene Zurück-Stapelnavigation bereitstellen möchten, sollte die Benutzeroberfläche mit anderen Apps konsistent sein.</span><span class="sxs-lookup"><span data-stu-id="14125-182">If you choose to provide your own back stack navigation, the experience should be consistent with other apps.</span></span> <span data-ttu-id="14125-183">Wir empfehlen, die folgenden Muster für Navigationsaktionen zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="14125-183">We recommend that you follow the following patterns for navigation actions:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="14125-184">Navigationsaktion</span><span class="sxs-lookup"><span data-stu-id="14125-184">Navigation action</span></span></th>
<th align="left"><span data-ttu-id="14125-185">Zum Navigationsverlauf hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="14125-185">Add to navigation history?</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-186">Seite zu Seite, verschiedene Peer-Gruppen</span><span class="sxs-lookup"><span data-stu-id="14125-186">Page to page, different peer groups</span></span></strong></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-187">Ja</span><span class="sxs-lookup"><span data-stu-id="14125-187">Yes</span></span></strong>
<p><span data-ttu-id="14125-188">In der folgenden Abbildung navigiert der Benutzer von Ebene 1 der App zu Ebene 2. Dabei werden Peer-Gruppen durchlaufen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="14125-188">In this illustration, the user navigates from level 1 of the app to level 2, crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/nav/nav-pagetopage-diffpeers-imageonly1.png" alt="Navigation across peer groups" /></p>
<p><span data-ttu-id="14125-189">In der nächsten Abbildung navigiert der Benutzer zwischen zwei Peer-Gruppen derselben Ebene. Er durchläuft erneut Peer-Gruppen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="14125-189">In the next illustration, the user navigates between two peer groups at the same level, again crossing peer groups, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/nav/nav-pagetopage-diffpeers-imageonly2.png" alt="Navigation across peer groups" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-190">Seite zu Seite, gleiche Peer-Gruppe, kein Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="14125-190">Page to page, same peer group, no on-screen navigation element</span></span></strong>
<p><span data-ttu-id="14125-191">Der Benutzer navigiert von einer Seite zu einer anderen mit derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="14125-191">The user navigates from one page to another with the same peer group.</span></span> <span data-ttu-id="14125-192">Es gibt kein Navigationselement, das immer vorhanden ist (wie Registerkarten/Pivots oder ein angedockter Navigationsbereich) und das eine direkte Navigation zu beiden Seiten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="14125-192">There is no navigation element that is always present (such as tabs/pivots or a docked navigation pane) that provides direct navigation to both pages.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-193">Ja</span><span class="sxs-lookup"><span data-stu-id="14125-193">Yes</span></span></strong>
<p><span data-ttu-id="14125-194">In der folgenden Abbildung navigiert der Benutzer zwischen zwei Seiten in derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="14125-194">In the following illustration, the user navigates between two pages in the same peer group.</span></span> <span data-ttu-id="14125-195">Die Seiten verwenden keine Registerkarten oder angedockten Navigationsbereich, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="14125-195">The pages don't use tabs or a docked navigation pane, so the navigation is added to the navigation history.</span></span></p>
<p><img src="images/nav/nav-pagetopage-samepeer-noosnavelement.png" alt="Navigation within a peer group" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-196">Seite zu Seite, gleiche Peer-Gruppe, mit einem Bildschirmnavigationselement</span><span class="sxs-lookup"><span data-stu-id="14125-196">Page to page, same peer group, with an on-screen navigation element</span></span></strong>
<p><span data-ttu-id="14125-197">Der Benutzer navigiert von einer Seite zu einer anderen in derselben Peer-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="14125-197">The user navigates from one page to another in the same peer group.</span></span> <span data-ttu-id="14125-198">Beide Seiten werden im gleichen Navigationselement angezeigt.</span><span class="sxs-lookup"><span data-stu-id="14125-198">Both pages are shown in the same navigation element.</span></span> <span data-ttu-id="14125-199">Beide Seiten verwenden beispielsweise das gleiche Registerkarten/Pivots-Element, oder beide Seiten werden in einem angedockten Navigationsbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="14125-199">For example, both pages use the same tabs/pivots element, or both pages appear in a docked navigation pane.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-200">Nein</span><span class="sxs-lookup"><span data-stu-id="14125-200">No</span></span></strong>
<p><span data-ttu-id="14125-201">Wenn der Benutzer die Zurück-Schaltfläche drückt, wird wieder die letzte Seite aufgerufen, die geöffnet war, bevor der Benutzer zur aktuellen Peer-Gruppe navigierte.</span><span class="sxs-lookup"><span data-stu-id="14125-201">When the user presses back, go back to the last page before the user navigated to the current peer group.</span></span></p>
<p><img src="images/nav/nav-pagetopage-samepeer-yesosnavelement.png" alt="Navigation across peer groups when a navigation element is present" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-202">Anzeigen einer vorübergehenden Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="14125-202">Show a transient UI</span></span></strong>
<p><span data-ttu-id="14125-203">Die App zeigt ein Popupfenster oder ein untergeordnetes Fenster an, z. B. ein Dialogfeld, einen Begrüßungsbildschirm oder eine Bildschirmtastatur. Anderenfalls wechselt die App in einen speziellen Modus, z. B. den Mehrfachauswahlmodus.</span><span class="sxs-lookup"><span data-stu-id="14125-203">The app displays a pop-up or child window, such as a dialog, splash screen, or on-screen keyboard, or the app enters a special mode, such as multiple selection mode.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-204">Nein</span><span class="sxs-lookup"><span data-stu-id="14125-204">No</span></span></strong>
<p><span data-ttu-id="14125-205">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte die vorübergehende Benutzeroberfläche geschlossen werden (durch Ausblenden der Bildschirmtastatur, Abbrechen des Dialogfelds usw.) und zur Seite zurückgekehrt werden, die die vorübergehende Benutzeroberfläche aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="14125-205">When the user presses the back button, dismiss the transient UI (hide the on-screen keyboard, cancel the dialog, etc) and return to the page that spawned the transient UI.</span></span></p>
<p><img src="images/back-transui.png" alt="Showing a transient UI" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-206">Aufzählen von Elementen</span><span class="sxs-lookup"><span data-stu-id="14125-206">Enumerate items</span></span></strong>
<p><span data-ttu-id="14125-207">Die App zeigt die Inhalte für ein Bildschirmelement an, z. B. die Details für das ausgewählte Element in der Master/Details-Liste.</span><span class="sxs-lookup"><span data-stu-id="14125-207">The app displays content for an on-screen item, such as the details for the selected item in master/details list.</span></span></p></td>
<td style="vertical-align:top;"><strong><span data-ttu-id="14125-208">Nein</span><span class="sxs-lookup"><span data-stu-id="14125-208">No</span></span></strong>
<p><span data-ttu-id="14125-209">Das Aufzählen von Elementen ist mit der Navigation innerhalb einer Peer-Gruppe vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="14125-209">Enumerating items is similar to navigating within a peer group.</span></span> <span data-ttu-id="14125-210">Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte zu der Seite navigiert werden, die vor der aktuellen Seite angezeigt wurde, die die Elementenaufzählung enthält.</span><span class="sxs-lookup"><span data-stu-id="14125-210">When the user presses back, navigate to the page that preceded the current page that has the item enumeration.</span></span></p>
<img src="images/nav/nav-enumerate.png" alt="Iterm enumeration" /></td>
</tr>
</tbody>
</table>


### <a name="resuming"></a><span data-ttu-id="14125-211">Fortsetzen</span><span class="sxs-lookup"><span data-stu-id="14125-211">Resuming</span></span>

<span data-ttu-id="14125-212">Wenn der Benutzer zu einer anderen App wechselt und zu Ihrer App zurückkehrt, wird empfohlen, zur letzten Seite im Navigationsverlauf zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="14125-212">When the user switches to another app and returns to your app, we recommend returning to the last page in the navigation history.</span></span>


## <a name="get-the-samples"></a><span data-ttu-id="14125-213">Beispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="14125-213">Get the samples</span></span>
*   [<span data-ttu-id="14125-214">Beispiel für die Zurück-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="14125-214">Back button sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackButton)<br/>
    <span data-ttu-id="14125-215">Zeigt, wie Sie einen Ereignishandler für das Ereignis Zurück-Schaltfläche einrichten und die Titelleisten-Zurück-Schaltfläche aktivieren, wenn sich die App im Fensterdesktopmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="14125-215">Shows how to set up an event handler for the back button event and how to enable the title bar back button for when the app is in windowed Desktop mode.</span></span>

## <a name="related-articles"></a><span data-ttu-id="14125-216">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="14125-216">Related articles</span></span>
* [<span data-ttu-id="14125-217">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="14125-217">Navigation basics</span></span>](navigation-basics.md)

 




