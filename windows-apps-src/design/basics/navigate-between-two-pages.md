---
author: Jwmsft
Description: Learn how to enable peer-to-peer navigation between two basic pages in an Universal Windows Platform (UWP) app.
title: Peer-zu-Peer-Navigation zwischen zwei Seiten
ms.assetid: 0A364C8B-715F-4407-9426-92267E8FB525
label: Peer-to-peer navigation between two pages
template: detail.hbs
op-migration-status: ready
ms.author: jimwalk
ms.date: 07/13/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 91a1ca0ee99833280aaa41ca4d9c94d043a78e0a
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6195971"
---
# <a name="implement-navigation-between-two-pages"></a><span data-ttu-id="58848-103">Implementieren der Navigation zwischen zwei Seiten</span><span class="sxs-lookup"><span data-stu-id="58848-103">Implement navigation between two pages</span></span>

<span data-ttu-id="58848-104">Hier erfahren Sie, wie Sie einen Rahmen und Seiten verwenden, um eine grundlegende Peer-to-Peer-Navigation in Ihrer App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="58848-104">Learn how to use a frame and pages to enable basic peer-to-peer navigation in your app.</span></span> 

> <span data-ttu-id="58848-105">**Wichtige APIS**: [**Windows.UI.Xaml.Controls.Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Klasse, [**Windows.UI.Xaml.Controls.Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Klasse, [**Windows.UI.Xaml.Navigation**](https://msdn.microsoft.com/library/windows/apps/br243300)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="58848-105">**Important APIs**: [**Windows.UI.Xaml.Controls.Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) class, [**Windows.UI.Xaml.Controls.Page**](https://msdn.microsoft.com/library/windows/apps/br227503) class, [**Windows.UI.Xaml.Navigation**](https://msdn.microsoft.com/library/windows/apps/br243300) namespace</span></span>

![Peer-to-Peer-Navigation](images/peertopeer.png)

## <a name="1-create-a-blank-app"></a><span data-ttu-id="58848-107">1. Erstellen einer leeren App</span><span class="sxs-lookup"><span data-stu-id="58848-107">1. Create a blank app</span></span>

1.  <span data-ttu-id="58848-108">Klicken Sie im Microsoft Visual Studio-Menü auf **Datei** > **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="58848-108">On the Microsoft Visual Studio menu, choose **File** > **New Project**.</span></span>
2.  <span data-ttu-id="58848-109">Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Knoten **Visual C#** > **Windows** > **Universell** oder **Visual C++** > **Windows** > **Universell**.</span><span class="sxs-lookup"><span data-stu-id="58848-109">In the left pane of the **New Project** dialog box, choose the **Visual C#** > **Windows** > **Universal** or the **Visual C++** > **Windows** > **Universal** node.</span></span>
3.  <span data-ttu-id="58848-110">Wählen Sie im mittleren Bereich die Option **Leere App** aus.</span><span class="sxs-lookup"><span data-stu-id="58848-110">In the center pane, choose **Blank App**.</span></span>
4.  <span data-ttu-id="58848-111">Geben Sie in das Feld **Name** den Wert **NavApp1** ein, und klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="58848-111">In the **Name** box, enter **NavApp1**, and then choose the **OK** button.</span></span>
    <span data-ttu-id="58848-112">Die Projektmappe wird erstellt, und die Projektdateien werden im **Projektmappen-Explorer** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="58848-112">The solution is created, and the project files appear in **Solution Explorer**.</span></span>
5.  <span data-ttu-id="58848-113">Wählen Sie zum Ausführen des Programms im Menü **Debugging** > **Debugging starten**, oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="58848-113">To run the program, choose **Debug** > **Start Debugging** from the menu, or press F5.</span></span>
    <span data-ttu-id="58848-114">Es wird eine leere Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="58848-114">A blank page is displayed.</span></span>
6.  <span data-ttu-id="58848-115">Um das Debuggen zu beenden und zu Visual Studio zurückzukehren, beenden Sie die App oder klicken Sie im Menü auf **Debuggen beenden**.</span><span class="sxs-lookup"><span data-stu-id="58848-115">To stop debugging and return to Visual Studio, exit the app, or click **Stop Debugging** from the menu.</span></span>

## <a name="2-add-basic-pages"></a><span data-ttu-id="58848-116">2. Hinzufügen von Standardseiten</span><span class="sxs-lookup"><span data-stu-id="58848-116">2. Add basic pages</span></span>

<span data-ttu-id="58848-117">Fügen Sie im nächsten Schritt zwei Seiten zum Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="58848-117">Next, add two pages to the project.</span></span>

1.  <span data-ttu-id="58848-118">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten **BlankApp**, um das Kontextmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="58848-118">In **Solution Explorer**, right-click the **BlankApp** project node to open the shortcut menu.</span></span>
2.  <span data-ttu-id="58848-119">Wählen Sie im Kontextmenü **Hinzufügen** > **Neues Element**.</span><span class="sxs-lookup"><span data-stu-id="58848-119">Choose **Add** > **New Item** from the shortcut menu.</span></span>
3.  <span data-ttu-id="58848-120">Wählen Sie im Dialogfeld **Neues Element hinzufügen** im mittleren Bereich die Option **Leere Seite** aus.</span><span class="sxs-lookup"><span data-stu-id="58848-120">In the **Add New Item** dialog box, choose **Blank Page** in the middle pane.</span></span>
4.  <span data-ttu-id="58848-121">Geben Sie in das Feld **Name** den Wert **Page1** (oder **Page2**) ein, und wählen Sie anschließend **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="58848-121">In the **Name** box, enter **Page1** (or **Page2**) and press the **Add** button.</span></span>
5. <span data-ttu-id="58848-122">Wiederholen Sie die Schritte 1-4, um die zweite Seite hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="58848-122">Repeat steps 1-4 to add the second page.</span></span>

<span data-ttu-id="58848-123">Diese Dateien sollten nun als Teil des Projekts „NavApp1“ aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="58848-123">Now, these files should be listed as part of your NavApp1 project.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="58848-124">C#</span><span class="sxs-lookup"><span data-stu-id="58848-124">C#</span></span></th>
<th align="left"><span data-ttu-id="58848-125">C++</span><span class="sxs-lookup"><span data-stu-id="58848-125">C++</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="58848-126">Page1.xaml</span><span class="sxs-lookup"><span data-stu-id="58848-126">Page1.xaml</span></span></li>
<li><span data-ttu-id="58848-127">Page1.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="58848-127">Page1.xaml.cs</span></span></li>
<li><span data-ttu-id="58848-128">Page2.xaml</span><span class="sxs-lookup"><span data-stu-id="58848-128">Page2.xaml</span></span></li>
<li><span data-ttu-id="58848-129">Page2.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="58848-129">Page2.xaml.cs</span></span></li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li><span data-ttu-id="58848-130">Page1.xaml</span><span class="sxs-lookup"><span data-stu-id="58848-130">Page1.xaml</span></span></li>
<li><span data-ttu-id="58848-131">Page1.xaml.cpp</span><span class="sxs-lookup"><span data-stu-id="58848-131">Page1.xaml.cpp</span></span></li>
<li><span data-ttu-id="58848-132">Page1.xaml.h</span><span class="sxs-lookup"><span data-stu-id="58848-132">Page1.xaml.h</span></span></li>
<li><span data-ttu-id="58848-133">Page2.xaml</span><span class="sxs-lookup"><span data-stu-id="58848-133">Page2.xaml</span></span></li>
<li><span data-ttu-id="58848-134">Page2.xaml.cpp</span><span class="sxs-lookup"><span data-stu-id="58848-134">Page2.xaml.cpp</span></span></li>
<li><span data-ttu-id="58848-135">Page2.xaml.h</span><span class="sxs-lookup"><span data-stu-id="58848-135">Page2.xaml.h</span></span>

</li>
</ul></td>
</tr>
</tbody>
</table>

<span data-ttu-id="58848-136">Fügen Sie in Page1.xaml den folgenden Inhalt hinzu:</span><span class="sxs-lookup"><span data-stu-id="58848-136">In Page1.xaml, add the following content:</span></span>

-   <span data-ttu-id="58848-137">Ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element mit der Bezeichnung `pageTitle` als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements.</span><span class="sxs-lookup"><span data-stu-id="58848-137">A [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element named `pageTitle` as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span> <span data-ttu-id="58848-138">Ändern Sie die [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676)-Eigenschaft in `Page 1`.</span><span class="sxs-lookup"><span data-stu-id="58848-138">Change the [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676) property to `Page 1`.</span></span>
```xaml
<TextBlock x:Name="pageTitle" Text="Page 1" />
```

-   <span data-ttu-id="58848-139">Ein [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) -Element als untergeordnetes Element des Stamms [**Raster**](https://msdn.microsoft.com/library/windows/apps/br242704) und nach der `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) -Element.</span><span class="sxs-lookup"><span data-stu-id="58848-139">A [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) element as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) and after the `pageTitle`[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element.</span></span>
```xaml
<HyperlinkButton Content="Click to go to page 2"
                 Click="HyperlinkButton_Click"
                 HorizontalAlignment="Center"/>
```

<span data-ttu-id="58848-140">Fügen Sie in der Datei Page1.xaml Code-Behind den folgenden Code hinzu, um das `Click`-Ereignis des [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)s zu behandeln, den Sie hinzugefügt haben, um zu Page2.xaml zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="58848-140">In the Page1.xaml code-behind file, add the following code to handle the `Click` event of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) you added to navigate to Page2.xaml.</span></span>

```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page2));
}
```

```cppwinrt
void Page1::HyperlinkButton_Click(Windows::Foundation::IInspectable const& sender, Windows::UI::Xaml::RoutedEventArgs const& args)
{
    Frame().Navigate(winrt::xaml_typename<NavApp1::Page2>());
}
```

```cpp
void Page1::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page2::typeid));
}
```

<span data-ttu-id="58848-141">Fügen Sie in Page2.xaml den folgenden Inhalt hinzu:</span><span class="sxs-lookup"><span data-stu-id="58848-141">In Page2.xaml, add the following content:</span></span>

-   <span data-ttu-id="58848-142">Ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element mit der Bezeichnung `pageTitle` als untergeordnetes Element des [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704)-Stammelements.</span><span class="sxs-lookup"><span data-stu-id="58848-142">A [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element named `pageTitle` as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704).</span></span> <span data-ttu-id="58848-143">Ändern Sie den Wert der [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676)-Eigenschaft in `Page 2`:</span><span class="sxs-lookup"><span data-stu-id="58848-143">Change the value of the [**Text**](https://msdn.microsoft.com/library/windows/apps/br209676) property to `Page 2`.</span></span>
```xaml
<TextBlock x:Name="pageTitle" Text="Page 2" />
```

-   <span data-ttu-id="58848-144">Ein [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) -Element als untergeordnetes Element des Stamms [**Raster**](https://msdn.microsoft.com/library/windows/apps/br242704) und nach der `pageTitle` [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) -Element.</span><span class="sxs-lookup"><span data-stu-id="58848-144">A [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) element as a child element of the root [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) and after the `pageTitle`[**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element.</span></span>
```xaml
<HyperlinkButton Content="Click to go to page 1" 
                 Click="HyperlinkButton_Click"
                 HorizontalAlignment="Center"/>
```

<span data-ttu-id="58848-145">Fügen Sie in der Datei Page2.xaml Code-Behind den folgenden Code hinzu, um das `Click`-Ereignis des [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739)s zu behandeln, den Sie hinzugefügt haben, um zu Page1.xaml zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="58848-145">In the Page2.xaml code-behind file, add the following code to handle the `Click` event of the [**HyperlinkButton**](https://msdn.microsoft.com/library/windows/apps/br242739) to navigate to Page1.xaml.</span></span>

```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page1));
}
```

```cppwinrt
void Page2::HyperlinkButton_Click(Windows::Foundation::IInspectable const& sender, Windows::UI::Xaml::RoutedEventArgs const& args)
{
    Frame().Navigate(winrt::xaml_typename<NavApp1::Page1>());
}
```

```cpp
void Page2::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page1::typeid));
}
```

> [!NOTE]
> <span data-ttu-id="58848-146">Im Fall von C++ Projekten müssen Sie in der Headerdatei jeder Seite, die auf eine andere Seite verweist, eine `#include`-Anweisung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58848-146">For C++ projects, you must add a `#include` directive in the header file of each page that references another page.</span></span> <span data-ttu-id="58848-147">Für das hier gezeigte Beispiel für die seitenübergreifende Navigation enthält die Datei „page1.xaml.h“ `#include "Page2.xaml.h"`, und die Datei „page2.xaml.h“ wiederum enthält `#include "Page1.xaml.h"`.</span><span class="sxs-lookup"><span data-stu-id="58848-147">For the inter-page navigation example presented here, page1.xaml.h file contains `#include "Page2.xaml.h"`, in turn, page2.xaml.h contains `#include "Page1.xaml.h"`.</span></span>

<span data-ttu-id="58848-148">Da wir die Seiten nun vorbereitet haben, müssen wir festlegen, dass „Page1.xaml“ beim Starten der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="58848-148">Now that we've prepared the pages, we need to make Page1.xaml display when the app starts.</span></span>

<span data-ttu-id="58848-149">Öffnen Sie die Code-Behind-Datei App.xaml, und ändern Sie den `OnLaunched`-Handler.</span><span class="sxs-lookup"><span data-stu-id="58848-149">Open the App.xaml code-behind file and change the `OnLaunched` handler.</span></span>

<span data-ttu-id="58848-150">Hier geben wir `Page1` im Aufruf von [**Frame.Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) anstelle von `MainPage` an.</span><span class="sxs-lookup"><span data-stu-id="58848-150">Here, we specify `Page1` in the call to [**Frame.Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) instead of `MainPage`.</span></span>

```csharp
protected override void OnLaunched(LaunchActivatedEventArgs e)
{
    Frame rootFrame = Window.Current.Content as Frame;
 
    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == null)
    {
        // Create a Frame to act as the navigation context and navigate to the first page
        rootFrame = new Frame();
        rootFrame.NavigationFailed += OnNavigationFailed;
 
        if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
        {
            //TODO: Load state from previously suspended application
        }
 
        // Place the frame in the current Window
        Window.Current.Content = rootFrame;
    }
 
    if (rootFrame.Content == null)
    {
        // When the navigation stack isn't restored navigate to the first page,
        // configuring the new page by passing required information as a navigation
        // parameter
        rootFrame.Navigate(typeof(Page1), e.Arguments);
    }
    // Ensure the current window is active
    Window.Current.Activate();
}
```

```cppwinrt
void App::OnLaunched(LaunchActivatedEventArgs const& e)
{
    Frame rootFrame{ nullptr };
    auto content = Window::Current().Content();
    if (content)
    {
        rootFrame = content.try_as<Frame>();
    }

    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = Frame();

        rootFrame.NavigationFailed({ this, &App::OnNavigationFailed });

        if (e.PreviousExecutionState() == ApplicationExecutionState::Terminated)
        {
            // Restore the saved session state only when appropriate, scheduling the
            // final launch steps after the restore is complete
        }

        if (e.PrelaunchActivated() == false)
        {
            if (rootFrame.Content() == nullptr)
            {
                // When the navigation stack isn't restored navigate to the first page,
                // configuring the new page by passing required information as a navigation
                // parameter
                rootFrame.Navigate(xaml_typename<NavApp1::Page1>(), box_value(e.Arguments()));
            }
            // Place the frame in the current Window
            Window::Current().Content(rootFrame);
            // Ensure the current window is active
            Window::Current().Activate();
        }
    }
    else
    {
        if (e.PrelaunchActivated() == false)
        {
            if (rootFrame.Content() == nullptr)
            {
                // When the navigation stack isn't restored navigate to the first page,
                // configuring the new page by passing required information as a navigation
                // parameter
                rootFrame.Navigate(xaml_typename<NavApp1::Page1>(), box_value(e.Arguments()));
            }
            // Ensure the current window is active
            Window::Current().Activate();
        }
    }
}
```

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the Window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();

        rootFrame->NavigationFailed += 
            ref new Windows::UI::Xaml::Navigation::NavigationFailedEventHandler(
                this, &App::OnNavigationFailed);

        if (e->PreviousExecutionState == ApplicationExecutionState::Terminated)
        {
            // TODO: Load state from previously suspended application
        }
        
        // Place the frame in the current Window
        Window::Current->Content = rootFrame;
    }

    if (rootFrame->Content == nullptr)
    {
        // When the navigation stack isn't restored navigate to the first page,
        // configuring the new page by passing required information as a navigation
        // parameter
        rootFrame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page1::typeid), e->Arguments);
    }

    // Ensure the current window is active
    Window::Current->Activate();
}
```

> [!NOTE]
> <span data-ttu-id="58848-151">Der Code hier verwendet den Rückgabewert der [**Navigieren**](https://msdn.microsoft.com/library/windows/apps/br242694) , um eine app-Ausnahme auszulösen, wenn die Navigation zum anfänglichen fensterframe der app einen Fehler verursacht.</span><span class="sxs-lookup"><span data-stu-id="58848-151">The code here uses the return value of [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) to throw an app exception if the navigation to the app's initial window frame fails.</span></span> <span data-ttu-id="58848-152">Wenn **Navigate** den Wert **true** zurückgibt, findet die Navigation statt.</span><span class="sxs-lookup"><span data-stu-id="58848-152">When **Navigate** returns **true**, the navigation happens.</span></span>

<span data-ttu-id="58848-153">Erstellen Sie nun die App, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="58848-153">Now, build and run the app.</span></span> <span data-ttu-id="58848-154">Klicken Sie auf den Link „Click to go to page 2“.</span><span class="sxs-lookup"><span data-stu-id="58848-154">Click the link that says "Click to go to page 2".</span></span> <span data-ttu-id="58848-155">Die zweite Seite mit der Bezeichnung „Seite 2“ wird geladen und im Frame angezeigt.</span><span class="sxs-lookup"><span data-stu-id="58848-155">The second page that says "Page 2" at the top should be loaded and displayed in the frame.</span></span>

### <a name="about-the-frame-and-page-classes"></a><span data-ttu-id="58848-156">Über die Rahmen- und Seitenklassen</span><span class="sxs-lookup"><span data-stu-id="58848-156">About the Frame and Page classes</span></span>

<span data-ttu-id="58848-157">Bevor wir der App weitere Funktionen hinzufügen, betrachten wir zunächst, inwiefern die hinzugefügten Seiten Navigationsunterstützung für die App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="58848-157">Before we add more functionality to our app, let's look at how the pages we added provide navigation within our app.</span></span>

<span data-ttu-id="58848-158">Zuerst wird ein [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) (`rootFrame`) für die App in der `App.OnLaunched`-Methode der Code-Behind-Datei „App.xaml“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="58848-158">First, a [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) called `rootFrame` is created for the app in the `App.OnLaunched` method in the App.xaml code-behind file.</span></span> <span data-ttu-id="58848-159">Die **Frame**-Klasse unterstützt verschiedene Navigationsmethoden, z. B. [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694), [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) oder [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693) und Eigenschaften wie [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543), [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547) oder [**BackStackDepth**](https://msdn.microsoft.com/library/windows/apps/hh967995).</span><span class="sxs-lookup"><span data-stu-id="58848-159">The **Frame** class supports various navigation methods such as [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694), [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568), and [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693), and properties such as [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543), [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547), and [**BackStackDepth**](https://msdn.microsoft.com/library/windows/apps/hh967995).</span></span>
 
<span data-ttu-id="58848-160">Die [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694)-Methode wird zum Anzeigen von Inhalt im **Frame** verwendet.</span><span class="sxs-lookup"><span data-stu-id="58848-160">The [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) method is used to display content in this **Frame**.</span></span> <span data-ttu-id="58848-161">Standardmäßig lädt diese Methode MainPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="58848-161">By default, this method loads MainPage.xaml.</span></span> <span data-ttu-id="58848-162">In unserem Beispiel wird `Page1` an die Methode **Navigate** übergeben, so dass die Methode `Page1` in den **Frame** geladen wird.</span><span class="sxs-lookup"><span data-stu-id="58848-162">In our example, `Page1` is passed to the **Navigate** method, so the method loads `Page1` in the **Frame**.</span></span> 

`Page1` <span data-ttu-id="58848-163">ist eine Unterklasse der [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="58848-163">is a subclass of the [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503) class.</span></span> <span data-ttu-id="58848-164">Die **Page**-Klasse hat eine schreibgeschützte **Frame**-Eigenschaft, die den **Frame** mit der **Page**-Klasse abruft.</span><span class="sxs-lookup"><span data-stu-id="58848-164">The **Page** class has a read-only **Frame** property that gets the **Frame** containing the **Page**.</span></span> <span data-ttu-id="58848-165">Wenn der **Click**-Ereignis-Handler des **HyperlinkButton**s in `Page1` `this.Frame.Navigate(typeof(Page2))` aufruft, zeigt das **Frame** den Inhalt von Page2.xaml an.</span><span class="sxs-lookup"><span data-stu-id="58848-165">When the **Click** event handler of the **HyperlinkButton** in `Page1` calls `this.Frame.Navigate(typeof(Page2))`, the **Frame** displays the content of Page2.xaml.</span></span>

<span data-ttu-id="58848-166">Wenn eine Seite in das Frame geladen wird, wird diese Seite als [**PageStackEntry**](https://msdn.microsoft.com/library/windows/apps/dn298572) zum [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543) oder [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547) des [**Frames**](https://msdn.microsoft.com/library/windows/apps/br227504) hinzugefügt, was eine [Historie und Rückwärtsnavigation ermöglicht](navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="58848-166">Finally, whenever a page is loaded into the frame, that page is added as a [**PageStackEntry**](https://msdn.microsoft.com/library/windows/apps/dn298572) to the [**BackStack**](https://msdn.microsoft.com/library/windows/apps/dn279543) or [**ForwardStack**](https://msdn.microsoft.com/library/windows/apps/dn279547) of the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br227504), allowing for [history and backwards navigation](navigation-history-and-backwards-navigation.md).</span></span>

## <a name="3-pass-information-between-pages"></a><span data-ttu-id="58848-167">3. Übergeben von Informationen zwischen Seiten</span><span class="sxs-lookup"><span data-stu-id="58848-167">3. Pass information between pages</span></span>

<span data-ttu-id="58848-168">Unsere App navigiert zwischen zwei Seiten, sie bietet jedoch noch keine interessanten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="58848-168">Our app navigates between two pages, but it really doesn't do anything interesting yet.</span></span> <span data-ttu-id="58848-169">Bei vielen Apps mit mehreren Seiten müssen die Seiten Informationen freigeben.</span><span class="sxs-lookup"><span data-stu-id="58848-169">Often, when an app has multiple pages, the pages need to share information.</span></span> <span data-ttu-id="58848-170">Übergeben wir also einige Informationen der ersten Seite an die zweite Seite.</span><span class="sxs-lookup"><span data-stu-id="58848-170">Let's pass some information from the first page to the second page.</span></span>

<span data-ttu-id="58848-171">Ersetzen Sie in "Page1.xaml" zuvor **HyperlinkButton** Sie hinzugefügt haben, mit dem folgenden [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635).</span><span class="sxs-lookup"><span data-stu-id="58848-171">In Page1.xaml, replace the **HyperlinkButton** you added earlier with the following [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/br209635).</span></span>

<span data-ttu-id="58848-172">Hier werden eine [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Bezeichnung und ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683)-Element (`name`) zum Eingeben einer Textzeichenfolge hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="58848-172">Here, we add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) label and a [**TextBox**](https://msdn.microsoft.com/library/windows/apps/br209683) `name` for entering a text string.</span></span>

```xaml
<StackPanel>
    <TextBlock HorizontalAlignment="Center" Text="Enter your name"/>
    <TextBox HorizontalAlignment="Center" Width="200" Name="name"/>
    <HyperlinkButton Content="Click to go to page 2" 
                     Click="HyperlinkButton_Click"
                     HorizontalAlignment="Center"/>
</StackPanel>
```

<span data-ttu-id="58848-173">In der `HyperlinkButton_Click` -Ereignishandler der CodeBehind-Datei "Page1.xaml" Hinzufügen einer Parameter einen Verweis auf die `Text` Eigenschaft der `name` **TextBox** , die `Navigate` Methode.</span><span class="sxs-lookup"><span data-stu-id="58848-173">In the `HyperlinkButton_Click` event handler of the Page1.xaml code-behind file, add a parameter referencing the `Text` property of the `name`**TextBox** to the `Navigate` method.</span></span>

```csharp
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page2), name.Text);
}
```

```cppwinrt
void Page1::HyperlinkButton_Click(Windows::Foundation::IInspectable const& sender, Windows::UI::Xaml::RoutedEventArgs const& args)
{
    Frame().Navigate(winrt::xaml_typename<NavApp1::Page2>(), winrt::box_value(name().Text()));
}
```

```cpp
void Page1::HyperlinkButton_Click(Platform::Object^ sender, RoutedEventArgs^ e)
{
    this->Frame->Navigate(Windows::UI::Xaml::Interop::TypeName(Page2::typeid), name->Text);
}
```

<span data-ttu-id="58848-174">Ersetzen Sie in „Page2.xaml“ das zuvor hinzugefügte **HyperlinkButton**-Element mit der folgenden **StackPanel**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="58848-174">In Page2.xaml, replace the **HyperlinkButton** you added earlier with the following **StackPanel**.</span></span>

<span data-ttu-id="58848-175">Hier fügen wir einen [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) für das Anzeigen einer von Seite 1 übergebenen Textzeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="58848-175">Here, we add a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) for displaying the text string passed from Page1.</span></span>

```xaml
<StackPanel>
    <TextBlock HorizontalAlignment="Center" Name="greeting"/>
    <HyperlinkButton Content="Click to go to page 1" 
                     Click="HyperlinkButton_Click"
                     HorizontalAlignment="Center"/>
</StackPanel>
```

<span data-ttu-id="58848-176">Fügen Sie im Code-Behind der Datei Page2.xaml folgendes hinzu, um die `OnNavigatedTo`-Methode zu überschreiben:</span><span class="sxs-lookup"><span data-stu-id="58848-176">In the Page2.xaml code-behind file, add the following to override the `OnNavigatedTo` method:</span></span>

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

```cppwinrt
void Page2::OnNavigatedTo(Windows::UI::Xaml::Navigation::NavigationEventArgs const& e)
{
    auto propertyValue{ e.Parameter().as<Windows::Foundation::IPropertyValue>() };
    if (propertyValue.Type() == Windows::Foundation::PropertyType::String)
    {
        greeting().Text(L"Hi, " + winrt::unbox_value<winrt::hstring>(e.Parameter()));
    }
    else
    {
        greeting().Text(L"Hi!");
    }
    __super::OnNavigatedTo(e);
}
```

```cpp
void Page2::OnNavigatedTo(NavigationEventArgs^ e)
{
    if (dynamic_cast<Platform::String^>(e->Parameter) != nullptr)
    {
        greeting->Text = "Hi, " + e->Parameter->ToString();
    }
    else
    {
        greeting->Text = "Hi!";
    }
    ::Windows::UI::Xaml::Controls::Page::OnNavigatedTo(e);
}
```

<span data-ttu-id="58848-177">Führen Sie die App aus, geben Sie Ihren Namen in das Textfeld ein, und klicken Sie auf den Link **Click to go to page 2**.</span><span class="sxs-lookup"><span data-stu-id="58848-177">Run the app, type your name in the text box, and then click the link that says **Click to go to page 2**.</span></span> 

<span data-ttu-id="58848-178">Wenn das **Click**-Ereignis des **HyperlinkButton**s in `Page1` `this.Frame.Navigate(typeof(Page2), name.Text)` aufruft, wird die `name.Text`-Eigenschaft an `Page2` übergeben und der Wert aus den Ereignisdaten wird für die auf der Seite angezeigte Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="58848-178">When the **Click** event of the **HyperlinkButton** in `Page1` calls `this.Frame.Navigate(typeof(Page2), name.Text)`, the `name.Text` property is passed to `Page2`, and the value from the event data is used for the message displayed on the page.</span></span>

## <a name="4-cache-a-page"></a><span data-ttu-id="58848-179">4. Zwischenspeichern einer Seite</span><span class="sxs-lookup"><span data-stu-id="58848-179">4. Cache a page</span></span>

<span data-ttu-id="58848-180">Seiteninhalt und -status werden standardmäßig nicht zwischengespeichert. Wenn Sie also Informationen zwischenspeichern möchten, müssen Sie diese in jeder Seite Ihrer App aktivieren.</span><span class="sxs-lookup"><span data-stu-id="58848-180">Page content and state is not cached by default, so if you'd like to cache information, you must enable it in each page of your app.</span></span>

<span data-ttu-id="58848-181">In unserem einfachen Peer-zu-Peer-Beispiel gibt es keine Zurück-Schaltfläche (Infos zur Rückwärtsnavigation finden Sie unter [Rückwärtsnavigation](navigation-history-and-backwards-navigation.md)). Würden Sie aber auf `Page2` auf eine Zurück-Schaltfläche klicken, würden das **TextBox**-Element (und alle anderen Felder) auf `Page1` auf den Standardzustand zurückgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="58848-181">In our basic peer-to-peer example, there is no back button (we demonstrate back navigation in [backwards navigation](navigation-history-and-backwards-navigation.md)), but if you did click a back button on `Page2`, the **TextBox** (and any other field) on `Page1` would be set to its default state.</span></span> <span data-ttu-id="58848-182">Eine Möglichkeit zur Umgehung dieses Problems ist die Verwendung der [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506)-Eigenschaft, um anzugeben, dass eine Seite zum Seitencache des Frames hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="58848-182">One way to work around this is to use the [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) property to specify that a page be added to the frame's page cache.</span></span> 

<span data-ttu-id="58848-183">Im Konstruktor von `Page1` können Sie **NavigationCacheMode** auf **Enabled** setzen, um alle Inhalte und Statuswerte für die Seite beizubehalten, bis der Seiten-Cache für den Frame überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="58848-183">In the constructor of `Page1`, you can set **NavigationCacheMode** to **Enabled** to retains all content and state values for the page until the page cache for the frame is exceeded.</span></span> <span data-ttu-id="58848-184">Setzen Sie [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) auf [**Required**](https://msdn.microsoft.com/library/windows/apps/br243284), wenn Sie [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683)-Limits ignorieren wollen (gibt die Anzahl der Seiten in der Navigationshistorie an, die für den Frame zwischengespeichert werden können).</span><span class="sxs-lookup"><span data-stu-id="58848-184">Set [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) to [**Required**](https://msdn.microsoft.com/library/windows/apps/br243284) if you want to ignore [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683) limits, which specify the number of pages in the navigation history that can be cached for the frame.</span></span> <span data-ttu-id="58848-185">Einschränkungen der Cachegröße können je nach der Arbeitsspeichergrenze eines Geräts jedoch äußerst wichtig sein.</span><span class="sxs-lookup"><span data-stu-id="58848-185">However, keep in mind that cache size limits might be crucial, depending on the memory limits of a device.</span></span>

```csharp
public Page1()
{
    this.InitializeComponent();
    this.NavigationCacheMode = Windows.UI.Xaml.Navigation.NavigationCacheMode.Enabled;
}
```

```cppwinrt
Page1::Page1()
{
    InitializeComponent();
    NavigationCacheMode(Windows::UI::Xaml::Navigation::NavigationCacheMode::Enabled);
}
```

```cpp
Page1::Page1()
{
    this->InitializeComponent();
    this->NavigationCacheMode = Windows::UI::Xaml::Navigation::NavigationCacheMode::Enabled;
}
```

## <a name="related-articles"></a><span data-ttu-id="58848-186">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="58848-186">Related articles</span></span>
* [<span data-ttu-id="58848-187">Navigationsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="58848-187">Navigation design basics for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958438)
* [<span data-ttu-id="58848-188">Richtlinien für Registerkarten und Pivots</span><span class="sxs-lookup"><span data-stu-id="58848-188">Guidelines for tabs and pivots</span></span>](https://msdn.microsoft.com/library/windows/apps/dn997788)
* [<span data-ttu-id="58848-189">Richtlinien für Navigationsbereiche</span><span class="sxs-lookup"><span data-stu-id="58848-189">Guidelines for navigation panes</span></span>](https://msdn.microsoft.com/library/windows/apps/dn997766)
