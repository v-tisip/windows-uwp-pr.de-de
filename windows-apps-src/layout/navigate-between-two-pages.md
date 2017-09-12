---
author: Jwmsft
Description: "Hier erfahren Sie, wie Sie in einer einfachen Peer-zu-Peer-App für die Universelle Windows-Plattform (UWP) mit zwei Seiten navigieren."
title: Peer-zu-Peer-Navigation zwischen zwei Seiten
ms.assetid: 0A364C8B-715F-4407-9426-92267E8FB525
label: Peer-to-peer navigation between two pages
template: detail.hbs
op-migration-status: ready
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: e5d0b0303218415d529b60e2dcaf28a21a28e430
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="implement-navigation-between-two-pages"></a><span data-ttu-id="19f24-104">Implementieren der Navigation zwischen zwei Seiten</span><span class="sxs-lookup"><span data-stu-id="19f24-104">Implement navigation between two pages</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="19f24-105">Hier erfahren Sie, wie Sie einen Rahmen und Seiten verwenden, um eine grundlegende Navigation in Ihrer App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="19f24-105">Learn how to use a frame and pages to enable basic navigation in your app.</span></span> 
<p></p>
<table>
    <tr>
        <td><span data-ttu-id="19f24-106">Wichtige APIs:</span><span class="sxs-lookup"><span data-stu-id="19f24-106">Important APIs:</span></span></td><td><span data-ttu-id="19f24-107">[**Windows.UI.Xaml.Controls.Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Klasse, [**Windows.UI.Xaml.Controls.Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Klasse, [**Windows.UI.Xaml.Navigation**](https://msdn.microsoft.com/library/windows/apps/br243300)-Namespace</span><span class="sxs-lookup"><span data-stu-id="19f24-107">[**Windows.UI.Xaml.Controls.Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) class, [**Windows.UI.Xaml.Controls.Page**](https://msdn.microsoft.com/library/windows/apps/br227503) class, [**Windows.UI.Xaml.Navigation**](https://msdn.microsoft.com/library/windows/apps/br243300) namespace</span></span></td>
    </tr>
</table>

## <a name="1-create-a-blank-app"></a><span data-ttu-id="19f24-108">1. Erstellen einer leeren App</span><span class="sxs-lookup"><span data-stu-id="19f24-108">1. Create a blank app</span></span>


1.  <span data-ttu-id="19f24-109">Klicken Sie im Microsoft Visual Studio-Menü auf **Datei &gt; Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="19f24-109">On the Microsoft Visual Studio menu, choose **File &gt; New Project**.</span></span>
2.  <span data-ttu-id="19f24-110">Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Knoten **Visual C# -&gt; Windows -&gt; Universell** oder **Visual C++ -&gt; Windows -&gt; Universell**.</span><span class="sxs-lookup"><span data-stu-id="19f24-110">In the left pane of the **New Project** dialog box, choose the **Visual C# -&gt; Windows -&gt; Universal** or the **Visual C++ -&gt; Windows -&gt; Universal** node.</span></span>
3.  <span data-ttu-id="19f24-111">Wählen Sie im mittleren Bereich die Option **Leere App** aus.</span><span class="sxs-lookup"><span data-stu-id="19f24-111">In the center pane, choose **Blank App**.</span></span>
4.  <span data-ttu-id="19f24-112">Geben Sie in das Feld **Name** den Wert **NavApp1** ein, und klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="19f24-112">In the **Name** box, enter **NavApp1**, and then choose the **OK** button.</span></span>

    <span data-ttu-id="19f24-113">Die Projektmappe wird erstellt, und die Projektdateien werden im **Projektmappen-Explorer** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19f24-113">The solution is created and the project files appear in **Solution Explorer**.</span></span>

5.  <span data-ttu-id="19f24-114">Klicken Sie zum Ausführen des Programms im Menü auf **Debuggen** &gt; **Debugging starten**, oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="19f24-114">To run the program, choose **Debug** &gt; **Start Debugging** from the menu, or press F5.</span></span>

    <span data-ttu-id="19f24-115">Es wird eine leere Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19f24-115">A blank page is displayed.</span></span>

6.  <span data-ttu-id="19f24-116">Drücken Sie UMSCHALT+F5, um das Debuggen zu beenden und zu Visual Studio zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="19f24-116">Press Shift+F5 to stop debugging and return to Visual Studio.</span></span>

## <a name="2-add-basic-pages"></a><span data-ttu-id="19f24-117">2. Hinzufügen von Standardseiten</span><span class="sxs-lookup"><span data-stu-id="19f24-117">2. Add basic pages</span></span>

<span data-ttu-id="19f24-118">Fügen Sie im nächsten Schritt zwei Inhaltsseiten zum Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-118">Next, add two content pages to the project.</span></span>

<span data-ttu-id="19f24-119">Führen Sie die folgenden Schritte zweimal aus, um zwei Seiten zum Navigieren hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="19f24-119">Do the following steps two times to add two pages to navigate between.</span></span>

1.  <span data-ttu-id="19f24-120">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten **BlankApp**, um das Kontextmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="19f24-120">In **Solution Explorer**, right-click the **BlankApp** project node to open the shortcut menu.</span></span>
2.  <span data-ttu-id="19f24-121">Wählen Sie im Kontextmenü **Hinzufügen** &gt; **Neues Element** aus.</span><span class="sxs-lookup"><span data-stu-id="19f24-121">Choose **Add** &gt; **New Item** from the shortcut menu.</span></span>
3.  <span data-ttu-id="19f24-122">Wählen Sie im Dialogfeld **Neues Element hinzufügen** im mittleren Bereich die Option **Leere Seite** aus.</span><span class="sxs-lookup"><span data-stu-id="19f24-122">In the **Add New Item** dialog box, choose **Blank Page** in the middle pane.</span></span>
4.  <span data-ttu-id="19f24-123">Geben Sie in das Feld **Name** den Wert **Page1** (oder **Page2**) ein, und wählen Sie anschließend **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="19f24-123">In the **Name** box, enter **Page1** (or **Page2**) and press the **Add** button.</span></span>

<span data-ttu-id="19f24-124">Diese Dateien sollten nun als Teil des Projekts „NavApp1“ aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="19f24-124">These files should now be listed as part of your NavApp1 project.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="19f24-125">C#</span><span class="sxs-lookup"><span data-stu-id="19f24-125">C#</span></span></th>
<th align="left"><span data-ttu-id="19f24-126">C++</span><span class="sxs-lookup"><span data-stu-id="19f24-126">C++</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="19f24-127">Page1.xaml</span><span class="sxs-lookup"><span data-stu-id="19f24-127">Page1.xaml</span></span></li>
<li><span data-ttu-id="19f24-128">Page1.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="19f24-128">Page1.xaml.cs</span></span></li>
<li><span data-ttu-id="19f24-129">Page2.xaml</span><span class="sxs-lookup"><span data-stu-id="19f24-129">Page2.xaml</span></span></li>
<li><span data-ttu-id="19f24-130">Page2.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="19f24-130">Page2.xaml.cs</span></span></li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="19f24-131">Page1.xaml</span><span class="sxs-lookup"><span data-stu-id="19f24-131">Page1.xaml</span></span></li>
<li><span data-ttu-id="19f24-132">Page1.xaml.cpp</span><span class="sxs-lookup"><span data-stu-id="19f24-132">Page1.xaml.cpp</span></span></li>
<li><span data-ttu-id="19f24-133">Page1.xaml.h</span><span class="sxs-lookup"><span data-stu-id="19f24-133">Page1.xaml.h</span></span></li>
<li><span data-ttu-id="19f24-134">Page2.xaml</span><span class="sxs-lookup"><span data-stu-id="19f24-134">Page2.xaml</span></span></li>
<li><span data-ttu-id="19f24-135">Page2.xaml.cpp</span><span class="sxs-lookup"><span data-stu-id="19f24-135">Page2.xaml.cpp</span></span></li>
<li><span data-ttu-id="19f24-136">Page2.xaml.h</span><span class="sxs-lookup"><span data-stu-id="19f24-136">Page2.xaml.h</span></span>

</li>
</ul></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="19f24-137">Fügen Sie der Benutzeroberfläche von „Page1.xaml“ folgenden Inhalt hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-137">Add the following content to the UI of Page1.xaml.</span></span>

-   <span data-ttu-id="19f24-138">Fügen Sie ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element mit der Bezeichnung `pageTitle` als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-138">Add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element named `pageTitle` as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span> <span data-ttu-id="19f24-139">Ändern Sie die [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676)-Eigenschaft in `Page 1`.</span><span class="sxs-lookup"><span data-stu-id="19f24-139">Change the [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676) property to `Page 1`.</span></span>

```xaml
<TextBlock x:Name="pageTitle" Text="Page 1" />
```

-   <span data-ttu-id="19f24-140">Fügen Sie das folgende [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Element als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements und nach dem `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-140">Add the following [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) element as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) and after the `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element.</span></span>

    
```xaml
<HyperlinkButton Content="Click to go to page 2"
                 Click="HyperlinkButton_Click"
                 HorizontalAlignment="Center"/>
```

<span data-ttu-id="19f24-141">Fügen Sie den folgenden Code zur `Page1`-Klasse in der CodeBehind-Datei „Page1.xaml“ hinzu, um das `Click`-Ereignis des zuvor hinzugefügten [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Elements zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="19f24-141">Add the following code to the `Page1` class in the Page1.xaml code-behind file to handle the `Click` event of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) you added previously.</span></span> <span data-ttu-id="19f24-142">Hier navigieren wir zu „Page2.xaml“.</span><span class="sxs-lookup"><span data-stu-id="19f24-142">Here, we navigate to Page2.xaml.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page2));
}
```
```cpp
void Page1::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page2::typeid));
}
```

<span data-ttu-id="19f24-143">Nehmen Sie die folgenden Änderungen an der UI von „Page2.xaml“ vor.</span><span class="sxs-lookup"><span data-stu-id="19f24-143">Make the following changes to the UI of Page2.xaml.</span></span>

-   <span data-ttu-id="19f24-144">Fügen Sie ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element mit der Bezeichnung `pageTitle` als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-144">Add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element named `pageTitle` as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span> <span data-ttu-id="19f24-145">Ändern Sie den Wert der [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676)-Eigenschaft in `Page 2`:</span><span class="sxs-lookup"><span data-stu-id="19f24-145">Change the value of the [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676) property to `Page 2`.</span></span>

```xaml
<TextBlock x:Name="pageTitle" Text="Page 2" />
```

-   <span data-ttu-id="19f24-146">Fügen Sie das folgende [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Element als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements und nach dem `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-146">Add the following [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) element as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) and after the `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element.</span></span>

```xaml
<HyperlinkButton Content="Click to go to page 1" 
                 Click="HyperlinkButton_Click"
                 HorizontalAlignment="Center"/>
```

<span data-ttu-id="19f24-147">Fügen Sie der `Page2`-Klasse in der CodeBehind-Datei „Page2.xaml“ den folgenden Code hinzu, um das `Click`-Ereignis des zuvor hinzugefügten [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Elements zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="19f24-147">Add the following code to the `Page2` class in the Page2.xaml code-behind file to handle the `Click` event of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) you added previously.</span></span> <span data-ttu-id="19f24-148">Nun wird die Navigation zu „Page1.xaml“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="19f24-148">Here, we navigate to Page1.xaml.</span></span>

> [!NOTE]
> <span data-ttu-id="19f24-149">Im Fall von C++-Projekten müssen Sie in der Headerdatei jeder Seite, die auf eine andere Seite verweist, eine `#include`-Anweisung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19f24-149">For C++ projects, you must add a `#include` directive in the header file of each page that references another page.</span></span> <span data-ttu-id="19f24-150">Für das hier gezeigte Beispiel für die seitenübergreifende Navigation enthält die Datei „page1.xaml.h“ `#include "Page2.xaml.h"`, und die Datei „page2.xaml.h“ wiederum enthält `#include "Page1.xaml.h"`.</span><span class="sxs-lookup"><span data-stu-id="19f24-150">For the inter-page navigation example presented here, page1.xaml.h file contains `#include "Page2.xaml.h"`, in turn, page2.xaml.h contains `#include "Page1.xaml.h"`.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page1));
}
```
```cpp
void Page2::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page1::typeid));
}
```

<span data-ttu-id="19f24-151">Da wir die Inhaltsseiten nun vorbereitet haben, müssen wir festlegen, dass „Page1.xaml“ beim Starten der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="19f24-151">Now that we've prepared the content pages, we need to make Page1.xaml display when the app starts.</span></span>

<span data-ttu-id="19f24-152">Öffnen Sie die CodeBehind-Datei „app.xaml“, und ändern Sie den `OnLaunched`-Handler.</span><span class="sxs-lookup"><span data-stu-id="19f24-152">Open the app.xaml code-behind file and change the `OnLaunched` handler.</span></span>

<span data-ttu-id="19f24-153">Hier geben wir `Page1` im Aufruf von [**Frame.Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) anstelle von `MainPage` an.</span><span class="sxs-lookup"><span data-stu-id="19f24-153">Here, we specify `Page1` in the call to [**Frame.Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) instead of `MainPage`.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> protected override void OnLaunched(LaunchActivatedEventArgs e)
> {
>     Frame rootFrame = Window.Current.Content as Frame;
> 
>     // Do not repeat app initialization when the Window already has content,
>     // just ensure that the window is active
>     if (rootFrame == null)
>     {
>         // Create a Frame to act as the navigation context and navigate to the first page
>         rootFrame = new Frame();
> 
>         rootFrame.NavigationFailed += OnNavigationFailed;
> 
>         if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
>         {
>             //TODO: Load state from previously suspended application
>         }
> 
>         // Place the frame in the current Window
>         Window.Current.Content = rootFrame;
>     }
> 
>     if (rootFrame.Content == null)
>     {
>         // When the navigation stack isn't restored navigate to the first page,
>         // configuring the new page by passing required information as a navigation
>         // parameter
>         rootFrame.Navigate(typeof(Page1), e.Arguments);
>     }
>     // Ensure the current window is active
>     Window.Current.Activate();
> }
> ```
> ```cpp
> void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e)
> {
>     auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);
> 
>     // Do not repeat app initialization when the Window already has content,
>     // just ensure that the window is active
>     if (rootFrame == nullptr)
>     {
>         // Create a Frame to act as the navigation context and associate it with
>         // a SuspensionManager key
>         rootFrame = ref new Frame();
> 
>         rootFrame->NavigationFailed += 
>             ref new Windows::UI::Xaml::Navigation::NavigationFailedEventHandler(
>                 this, &App::OnNavigationFailed);
> 
>         if (e->PreviousExecutionState == ApplicationExecutionState::Terminated)
>         {
>             // TODO: Load state from previously suspended application
>         }
>         
>         // Place the frame in the current Window
>         Window::Current->Content = rootFrame;
>     }
> 
>     if (rootFrame->Content == nullptr)
>     {
>         // When the navigation stack isn't restored navigate to the first page,
>         // configuring the new page by passing required information as a navigation
>         // parameter
>         rootFrame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page1::typeid), e->Arguments);
>     }
> 
>     // Ensure the current window is active
>     Window::Current->Activate();
> }
> ```

<span data-ttu-id="19f24-154">**Hinweis**  In diesem Beispielcode wird der Rückgabewert von [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) verwendet, um eine App-Ausnahme auszulösen, wenn die Navigation zum anfänglichen Fensterframe der App einen Fehler verursacht.</span><span class="sxs-lookup"><span data-stu-id="19f24-154">**Note**  The code here uses the return value of [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) to throw an app exception if the navigation to the app's initial window frame fails.</span></span> <span data-ttu-id="19f24-155">Wenn **Navigate** den Wert **true** zurückgibt, findet die Navigation statt.</span><span class="sxs-lookup"><span data-stu-id="19f24-155">When **Navigate** returns **true**, the navigation happens.</span></span>

<span data-ttu-id="19f24-156">Erstellen Sie nun die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="19f24-156">Now, build and run the app.</span></span> <span data-ttu-id="19f24-157">Klicken Sie auf den Link „Click to go to page 2“.</span><span class="sxs-lookup"><span data-stu-id="19f24-157">Click the link that says "Click to go to page 2".</span></span> <span data-ttu-id="19f24-158">Die zweite Seite mit der Bezeichnung „Seite 2“ wird geladen und im Frame angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19f24-158">The second page that says "Page 2" at the top should be loaded and displayed in the frame.</span></span>

## <a name="about-the-frame-and-page-classes"></a><span data-ttu-id="19f24-159">Über die Rahmen- und Seitenklassen</span><span class="sxs-lookup"><span data-stu-id="19f24-159">About the Frame and Page classes</span></span>

<span data-ttu-id="19f24-160">Bevor wir der App weitere Funktionen hinzufügen, betrachten wir zunächst, inwiefern die hinzugefügten Seiten Navigationsunterstützung für die App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="19f24-160">Before we add more functionality to our app, let's look at how the pages we added provide navigation support for the app.</span></span>

<span data-ttu-id="19f24-161">Zuerst wird ein [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) (`rootFrame`) für die App in der `App.OnLaunched`-Methode der CodeBehind-Datei „App.xaml“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="19f24-161">First, a [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) (`rootFrame`) is created for the app in the `App.OnLaunched` method of the App.xaml code-behind file.</span></span> <span data-ttu-id="19f24-162">Die [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694)-Methode wird zum Anzeigen von Inhalt im **Frame** verwendet.</span><span class="sxs-lookup"><span data-stu-id="19f24-162">The [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) method is used to display content in this **Frame**.</span></span>

**<span data-ttu-id="19f24-163">Hinweis</span><span class="sxs-lookup"><span data-stu-id="19f24-163">Note</span></span>**  
<span data-ttu-id="19f24-164">Die [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Klasse unterstützt verschiedene Navigationsmethoden, z. B. [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694), [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) oder [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693) und Eigenschaften wie [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543), [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547) oder [**BackStackDepth**](https://msdn.microsoft.com/library/windows/apps/hh967995).</span><span class="sxs-lookup"><span data-stu-id="19f24-164">The [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) class supports various navigation methods such as [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694), [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568), and [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693), and properties such as [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543), [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547), and [**BackStackDepth**](https://msdn.microsoft.com/library/windows/apps/hh967995).</span></span>

 
<span data-ttu-id="19f24-165">In unserem Beispiel wird `Page1` an die [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694)-Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="19f24-165">In our example, `Page1` is passed to the [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) method.</span></span> <span data-ttu-id="19f24-166">Mit dieser Methode wird der Inhalt des aktuellen Fensters der App auf [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) festgelegt und der Inhalt der angegebenen Seite in **Frame** (in unserem Beispiel „Page1.xaml“ oder standardmäßig „MainPage.xaml“) geladen.</span><span class="sxs-lookup"><span data-stu-id="19f24-166">This method sets the content of the app's current window to the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) and loads the content of the page you specify into the **Frame** (Page1.xaml in our example, or MainPage.xaml, by default).</span></span>

`Page1` <span data-ttu-id="19f24-167">ist eine Unterklasse der [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="19f24-167">is a subclass of the [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503) class.</span></span> <span data-ttu-id="19f24-168">Die **Page**-Klasse hat eine schreibgeschützte [**Frame**](https://msdn.microsoft.com/library/windows/apps/br227504)-Eigenschaft, die den [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) mit der **Page**-Klasse abruft.</span><span class="sxs-lookup"><span data-stu-id="19f24-168">The **Page** class has a read-only [**Frame**](https://msdn.microsoft.com/library/windows/apps/br227504) property that gets the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) containing the **Page**.</span></span> <span data-ttu-id="19f24-169">Wenn der [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737)-Ereignishandler der [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Klasse ` Frame.Navigate(typeof(Page2))` aufruft, wird im **Frame** des App-Fensters der Inhalt von „Page2.xaml“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19f24-169">When the [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737) event handler of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) calls` Frame.Navigate(typeof(Page2))`, the **Frame** in the app's window displays the content of Page2.xaml.</span></span>

<span data-ttu-id="19f24-170">Wenn eine Seite in den Frame geladen wird, wird diese Seite als [**PageStackEntry**](https://msdn.microsoft.com/library/windows/apps/dn298572)-Klasse der [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543)- oder [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547)-Eigenschaft der [**Frame**](https://msdn.microsoft.com/library/windows/apps/br227504)-Klasse hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19f24-170">Whenever a page is loaded into the frame, that page is added as a [**PageStackEntry**](https://msdn.microsoft.com/library/windows/apps/dn298572) to the [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543) or [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547) of the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br227504).</span></span>

## <a name="3-pass-information-between-pages"></a><span data-ttu-id="19f24-171">3. Übergeben von Informationen zwischen Seiten</span><span class="sxs-lookup"><span data-stu-id="19f24-171">3. Pass information between pages</span></span>

<span data-ttu-id="19f24-172">Unsere App navigiert zwischen zwei Seiten, sie bietet jedoch noch keine interessanten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="19f24-172">Our app navigates between two pages, but it really doesn't do anything interesting yet.</span></span> <span data-ttu-id="19f24-173">Bei vielen Apps mit mehreren Seiten müssen die Seiten Informationen freigeben.</span><span class="sxs-lookup"><span data-stu-id="19f24-173">Often, when an app has multiple pages, the pages need to share information.</span></span> <span data-ttu-id="19f24-174">Übergeben wir also einige Informationen der ersten Seite an die zweite Seite.</span><span class="sxs-lookup"><span data-stu-id="19f24-174">Let's pass some information from the first page to the second page.</span></span>

<span data-ttu-id="19f24-175">Ersetzen Sie in „Page1.xaml“ das zuvor hinzugefügte [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Element mit der folgenden [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="19f24-175">In Page1.xaml, replace the the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) you added earlier with the following [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635).</span></span>

<span data-ttu-id="19f24-176">Hier werden eine [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Bezeichnung und ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683)-Element (`name`) zum Eingeben einer Textzeichenfolge hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19f24-176">Here, we add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) label and a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) (`name`) for entering a text string.</span></span>

```xaml
<StackPanel>
    <TextBlock HorizontalAlignment="Center" Text="Enter your name"/>
    <TextBox HorizontalAlignment="Center" Width="200" Name="name"/>
    <HyperlinkButton Content="Click to go to page 2" 
                     Click="HyperlinkButton_Click"
                     HorizontalAlignment="Center"/>
</StackPanel>
```

<span data-ttu-id="19f24-177">Fügen Sie im `HyperlinkButton_Click`-Ereignishandler der CodeBehind-Datei „Page1.xaml“ einen Parameter hinzu, der die `Text`-Eigenschaft von `name` [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) auf die `Navigate`-Methode verweist.</span><span class="sxs-lookup"><span data-stu-id="19f24-177">In the `HyperlinkButton_Click` event handler of the Page1.xaml code-behind file, add a parameter referencing the `Text` property of the `name` [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) to the `Navigate` method.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page2), name.Text);
}
```
```cpp
void Page1::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page2::typeid), name->Text);
}
```

<span data-ttu-id="19f24-178">Ersetzen Sie in „Page2.xaml“ das zuvor hinzugefügte [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Element mit der folgenden [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="19f24-178">In Page2.xaml, replace the the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) you added earlier with the following [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635).</span></span>

<span data-ttu-id="19f24-179">Hier fügen wir einen [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) für das Anzeigen einer von Seite 1 übergebenen Textzeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="19f24-179">Here, we add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) for displaying a text string passed from Page1.</span></span>

```xaml
<StackPanel>
    <TextBlock HorizontalAlignment="Center" Name="greeting"/>
    <HyperlinkButton Content="Click to go to page 1" 
                     Click="HyperlinkButton_Click"
                     HorizontalAlignment="Center"/>
</StackPanel>
```

<span data-ttu-id="19f24-180">Überschreiben Sie in der CodeBehind-Datei „Page2.xaml“ die `OnNavigatedTo`-Methode durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="19f24-180">In the Page2.xaml code-behind file, override the `OnNavigatedTo` method with the following:</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    if (e.Parameter is string && !string.IsNullOrWhiteSpace((string)e.Parameter))
    {
        greeting.Text = $"Hi, {e.Parameter.ToString()}";
    }
    else
    {
        greeting.Text = "Hi!";
    }
    base.OnNavigatedTo(e);
}
```
```cpp
void Page2::OnNavigatedTo(NavigationEventArgs^ e)
{
    if (dynamic_cast<Platform::String^>(e->Parameter) != nullptr)
    {
        greeting->Text = "Hi," + e->Parameter->ToString();
    }
    else
    {
        greeting->Text = "Hi!";
    }
    ::Windows::UI::Xaml::Controls::Page::OnNavigatedTo(e);
}
```

<span data-ttu-id="19f24-181">Führen Sie die App aus, geben Sie Ihren Namen in das Textfeld ein, und klicken Sie auf den Link **Click to go to page 2**.</span><span class="sxs-lookup"><span data-stu-id="19f24-181">Run the app, type your name in the text box, and then click the link that says **Click to go to page 2**.</span></span> <span data-ttu-id="19f24-182">Beim Aufruf von `this.Frame.Navigate(typeof(Page2), name.Text)` im [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737)-Ereignis des [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)-Elements wird die `name.Text`-Eigenschaft an `Page2` übergeben. Der Wert der Ereignisdaten wird zum Anzeigen der Nachricht auf der Seite verwendet.</span><span class="sxs-lookup"><span data-stu-id="19f24-182">When you called `this.Frame.Navigate(typeof(Page2), name.Text)` in the [**Click**](https://msdn.microsoft.com/library/windows/apps/br227737) event of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739), the `name.Text` property was passed to `Page2` and the value from the event data is used for the message displayed on the page.</span></span>

## <a name="4-cache-a-page"></a><span data-ttu-id="19f24-183">4. Zwischenspeichern einer Seite</span><span class="sxs-lookup"><span data-stu-id="19f24-183">4. Cache a page</span></span>

<span data-ttu-id="19f24-184">Inhalt und Zustand einer Seite werden nicht standardmäßig zwischengespeichert, sondern müssen auf jeder Seite der App aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="19f24-184">Page content and state is not cached by default, you must enable it in each page of your app.</span></span>

<span data-ttu-id="19f24-185">In unserem einfachen Peer-zu-Peer-Beispiel gibt es keine Zurück-Schaltfläche (Infos zur Rückwärtsnavigation unter [Navigation per Zurück-Schaltfläche](navigation-history-and-backwards-navigation.md)). Würden Sie aber auf `Page2` auf eine Zurück-Schaltfläche klicken, würden das [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683)-Element (und alle anderen Felder) auf `Page1` auf den Standardzustand zurückgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="19f24-185">In our basic peer-to-peer example, there is no back button (we demonstrate back navigation in [Back button navigation](navigation-history-and-backwards-navigation.md)), but if you did click a back button on `Page2`, the [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) (and any other field) on `Page1` would be set to its default state.</span></span> <span data-ttu-id="19f24-186">Eine Möglichkeit zur Umgehung dieses Problems ist die Verwendung der [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506)-Eigenschaft, um anzugeben, dass eine Seite zum Seitencache des Frames hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="19f24-186">One way to work around this is to use the [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) property to specify that a page be added to the frame's page cache.</span></span>

<span data-ttu-id="19f24-187">Legen Sie im Konstruktor von `Page1` die [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506)-Eigenschaft auf [**Enabled**](https://msdn.microsoft.com/library/windows/apps/br243284) fest.</span><span class="sxs-lookup"><span data-stu-id="19f24-187">In the constructor of `Page1`, set [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) to [**Enabled**](https://msdn.microsoft.com/library/windows/apps/br243284).</span></span> <span data-ttu-id="19f24-188">Hierdurch werden alle Inhalts- und-Zustandswerte für die Seite zurückbehalten, bis der Höchstwert für den Seitencache des Frames überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="19f24-188">This retains all content and state values for the page until the page cache for the frame is exceeded.</span></span>

<span data-ttu-id="19f24-189">Legen Sie [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) auf [**Required**](https://msdn.microsoft.com/library/windows/apps/br243284) fest, wenn Cachegrößenbeschränkungen für den Frame ignoriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="19f24-189">Set [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) to [**Required**](https://msdn.microsoft.com/library/windows/apps/br243284) if you want to ignore cache size limits for the frame.</span></span> <span data-ttu-id="19f24-190">Einschränkungen der Cachegröße können je nach der Arbeitsspeichergrenze eines Geräts jedoch äußerst wichtig sein.</span><span class="sxs-lookup"><span data-stu-id="19f24-190">However, cache size limits might be crucial, depending on the memory limits of a device.</span></span>

> [!NOTE]
> <span data-ttu-id="19f24-191">Die Eigenschaft [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683) gibt die Anzahl der Seiten im Navigationsverlauf an, die für den Frame zwischengespeichert werden können.</span><span class="sxs-lookup"><span data-stu-id="19f24-191">The [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683) property specifies the number of pages in the navigation history that can be cached for the frame.</span></span>

> [!div class="tabbedCodeSnippets"]
```csharp
public Page1()
{
    this.InitializeComponent();
    this.NavigationCacheMode = Windows.UI.Xaml.Navigation.NavigationCacheMode.Enabled;
}
```
```cpp
Page1::Page1()
{
    this->InitializeComponent();
    this->NavigationCacheMode = Windows::UI::Xaml::Navigation::NavigationCacheMode::Enabled;
}
```

## <a name="related-articles"></a><span data-ttu-id="19f24-192">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="19f24-192">Related articles</span></span>

* [<span data-ttu-id="19f24-193">Navigationsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="19f24-193">Navigation design basics for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958438)
* [<span data-ttu-id="19f24-194">Richtlinien für Registerkarten und Pivots</span><span class="sxs-lookup"><span data-stu-id="19f24-194">Guidelines for tabs and pivots</span></span>](https://msdn.microsoft.com/library/windows/apps/dn997788)
* [<span data-ttu-id="19f24-195">Richtlinien für Navigationsbereiche</span><span class="sxs-lookup"><span data-stu-id="19f24-195">Guidelines for navigation panes</span></span>](https://msdn.microsoft.com/library/windows/apps/dn997766)
 

 




