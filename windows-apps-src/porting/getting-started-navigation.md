---
author: stevewhims
title: Erste Schritte mit der Navigation
description: Erste Schritte mit der Navigation
ms.assetid: F4DF5C5F-C886-4483-BBDA-498C4E2C1BAF
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9cb4550a7da3b9b547a1d723d5ae8da260149ba2
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5597974"
---
# <a name="getting-started-navigation"></a><span data-ttu-id="5c300-104">Erste Schritte: Navigation</span><span class="sxs-lookup"><span data-stu-id="5c300-104">Getting started: Navigation</span></span>


## <a name="adding-navigation"></a><span data-ttu-id="5c300-105">Hinzufügen von Navigation</span><span class="sxs-lookup"><span data-stu-id="5c300-105">Adding navigation</span></span>

<span data-ttu-id="5c300-106">iOS bietet die **UINavigationController**-Klasse als In-App-Navigationshilfe: Sie erstellen eine Hierarchie von **UIViewControllers**, die Ihre App definieren, durch das Drücken und Aufklappen von Ansichten.</span><span class="sxs-lookup"><span data-stu-id="5c300-106">iOS provides the **UINavigationController** class to help with in-app navigation: you can push and pop views to create the hierarchy of **UIViewControllers** that define your app.</span></span>

<span data-ttu-id="5c300-107">In orientierten eine Windows 10-app mit mehreren Ansichten holt mehr von einer Website Ansatz zur Navigation.</span><span class="sxs-lookup"><span data-stu-id="5c300-107">In contrast, a Windows10 app containing multiple views takes more of a web-site approach to navigation.</span></span> <span data-ttu-id="5c300-108">Sie können sich vorstellen, wie Benutzer von Seite zu Seite wechseln, indem Sie auf Steuerelemente klicken, um durch die App zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="5c300-108">You can imagine your users hopping from page to page as they click on controls to work their way through the app.</span></span> <span data-ttu-id="5c300-109">Weitere Informationen finden Sie unter [Navigationsdesigngrundlagen](https://msdn.microsoft.com/library/windows/apps/dn958438).</span><span class="sxs-lookup"><span data-stu-id="5c300-109">For more info, see [Navigation design basics](https://msdn.microsoft.com/library/windows/apps/dn958438).</span></span>

<span data-ttu-id="5c300-110">Eine der Methoden zum Verwalten dieser Navigation in einer Windows 10-app ist die Verwendung die [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="5c300-110">One of the ways to manage this navigation in a Windows10 app is to use the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) class.</span></span> <span data-ttu-id="5c300-111">Die folgende exemplarische Vorgehensweise veranschaulicht, wie Sie dies ausprobieren können.</span><span class="sxs-lookup"><span data-stu-id="5c300-111">The following walkthrough shows you how to try this out.</span></span>

<span data-ttu-id="5c300-112">Fahren Sie mit der Lösung aus früheren Schritten fort, öffnen Sie die **MainPage.xaml**-Datei, und fügen Sie eine Schaltfläche in der Ansicht **Entwurf** hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-112">Continuing with the solution you started earlier, open the **MainPage.xaml** file, and add a button in the **Design** view.</span></span> <span data-ttu-id="5c300-113">Ändern Sie die **Content**-Eigenschaft der Schaltfläche von „Button“ in „Go To Page“.</span><span class="sxs-lookup"><span data-stu-id="5c300-113">Change the button's **Content** property from "Button" to "Go To Page".</span></span> <span data-ttu-id="5c300-114">Erstellen Sie anschließend einen Handler für das **Click**-Ereignis der Schaltfläche, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5c300-114">Then, create a handler for the button's **Click** event, as shown in the following figure.</span></span> <span data-ttu-id="5c300-115">Wenn Sie nicht mehr wissen, wie das geht, schlagen Sie unter der exemplarischen Vorgehensweise im vorherigen Abschnitt nach (Hinweis: Doppelklicken Sie auf die Schaltfläche in der Ansicht **Entwurf**).</span><span class="sxs-lookup"><span data-stu-id="5c300-115">If you don't remember how to do this, review the walkthrough in the previous section (Hint: double-click the button in the **Design** view).</span></span>

![Hinzufügen einer Schaltfläche und des zugehörigen Click-Ereignisses in Visual Studio](images/ios-to-uwp/vs-go-to-page.png)

<span data-ttu-id="5c300-117">Als Nächstes fügen wir eine neue Seite hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-117">Let's add a new page.</span></span> <span data-ttu-id="5c300-118">Tippen Sie in der Ansicht **Lösung** auf das Menü **Projekt**, und tippen Sie auf **Neues Element hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5c300-118">In the **Solution** view, tap the **Project** menu, and tap **Add New Item**.</span></span> <span data-ttu-id="5c300-119">Tippen Sie wie in der folgenden Abbildung dargestellt auf **Leere Seite** und dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5c300-119">Tap **Blank Page** as shown in the following figure, and then tap **Add**.</span></span>

![Hinzufügen einer neuen Seite in Visual Studio](images/ios-to-uwp/vs-add-new-page.png)

<span data-ttu-id="5c300-121">Fügen Sie als Nächstes der Datei „BlankPage.xaml“ eine Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-121">Next, add a button to the BlankPage.xaml file.</span></span> <span data-ttu-id="5c300-122">Nun wird das AppBarButton-Steuerelement verwendet und soll ein Bild mit einem Zurück-Pfeil erhalten: Fügen Sie hierzu in der **XAML**-Ansicht ` <AppBarButton Icon="Back"/>` zwischen den `<Grid> </Grid>`-Elementen hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-122">Let's use the AppBarButton control, and let's give it a back arrow image: in the **XAML** view, add ` <AppBarButton Icon="Back"/>` between the `<Grid> </Grid>` elements.</span></span>

<span data-ttu-id="5c300-123">Nun fügen wir der Schaltfläche einen Ereignishandler hinzu: Doppelklicken Sie in der Ansicht **Entwurf** auf das Steuerelement, und Microsoft Visual Studio fügt dem Feld **Click** wie in der folgenden Abbildung dargestellt den Text „AppBarButton\_Click“ hinzu. Anschließend wird der entsprechende Ereignishandler der Datei „BlankPage.xaml.cs“ hinzugefügt und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5c300-123">Now, let's add an event handler to the button: double-click the control in the **Design** view and Microsoft Visual Studio adds the text "AppBarButton\_Click" to the **Click** box, as shown in the following figure, and then adds and displays the corresponding event handler in the BlankPage.xaml.cs file.</span></span>

![Hinzufügen einer Zurück-Schaltfläche und des zugehörigen Click-Ereignisses in Visual Studio](images/ios-to-uwp/vs-add-back-button.png)

<span data-ttu-id="5c300-125">Wenn Sie zur **XAML**-Ansicht der Datei „BlankPage.xaml“ zurückkehren, sollte der Extensible Application Markup Language (XAML)-Code des `<AppBarButton>`-Elements nun wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="5c300-125">If you return to the BlankPage.xaml file's **XAML** view, the `<AppBarButton>` element's Extensible Application Markup Language (XAML) code should now look like this:</span></span>

` <AppBarButton Icon="Back" Click="AppBarButton_Click"/>`

<span data-ttu-id="5c300-126">Kehren Sie zur Datei „BlankPage.xaml.cs“ zurück, und fügen Sie diesen Code hinzu, damit der Benutzer zur vorherigen Seite zurückkehrt, nachdem er auf die Schaltfläche getippt hat.</span><span class="sxs-lookup"><span data-stu-id="5c300-126">Return to the BlankPage.xaml.cs file, and add this code to go to the previous page after the user taps the button.</span></span>

```csharp
private void AppBarButton_Click(object sender, RoutedEventArgs e)
{
    // Add the following line of code.    
    Frame.GoBack();
}
```

<span data-ttu-id="5c300-127">Öffnen Sie zum Schluss die Datei „MainPage.xaml.cs“, und fügen Sie diesen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-127">Finally, open the MainPage.xaml.cs file and add this code.</span></span> <span data-ttu-id="5c300-128">Mithilfe dieses Codes wird BlankPage geöffnet, nachdem der Benutzer auf die Schaltfläche getippt hat.</span><span class="sxs-lookup"><span data-stu-id="5c300-128">It opens BlankPage after the user taps the button.</span></span>

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    // Add the following line of code.
    Frame.Navigate(typeof(BlankPage1));
}
```

<span data-ttu-id="5c300-129">Führen Sie nun das Programm aus.</span><span class="sxs-lookup"><span data-stu-id="5c300-129">Now, run the program.</span></span> <span data-ttu-id="5c300-130">Tippen Sie auf die Schaltfläche „Go To Page“, um zu der anderen Seite zu wechseln, und tippen Sie dann auf die Schaltfläche mit dem Zurück-Pfeil, um zur vorherigen Seite zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="5c300-130">Tap the "Go To Page" button to go to the other page, and then tap the back-arrow button to return to the previous page.</span></span>

<span data-ttu-id="5c300-131">Die Seitennavigation wird mithilfe der [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682)-Klasse verwaltet.</span><span class="sxs-lookup"><span data-stu-id="5c300-131">Page navigation is managed by the [**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) class.</span></span> <span data-ttu-id="5c300-132">Wie die **UINavigationController** -Klasse in iOS **PushViewController** und **PopViewController** Methoden verwendet wird, bietet die **Frame** -Klasse für UWP-apps [**Navigieren**](https://msdn.microsoft.com/library/windows/apps/br242694) und [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) -Methode.</span><span class="sxs-lookup"><span data-stu-id="5c300-132">As the **UINavigationController** class in iOS uses **pushViewController** and **popViewController** methods, the **Frame** class for UWP apps provides [**Navigate**](https://msdn.microsoft.com/library/windows/apps/br242694) and [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) methods.</span></span> <span data-ttu-id="5c300-133">Die **Frame**-Klasse verfügt außerdem über eine Methode mit dem Namen [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693), die genau das tut, was Sie vermutlich erwartet haben.</span><span class="sxs-lookup"><span data-stu-id="5c300-133">The **Frame** class also has a method called [**GoForward**](https://msdn.microsoft.com/library/windows/apps/br242693), which does what you might expect.</span></span>

<span data-ttu-id="5c300-134">Bei dieser exemplarischen Vorgehensweise wird immer dann eine neue Instanz von BlankPage erstellt, wenn Sie zu dieser Seite navigieren.</span><span class="sxs-lookup"><span data-stu-id="5c300-134">This walkthrough creates a new instance of BlankPage each time you navigate to it.</span></span> <span data-ttu-id="5c300-135">(Die vorherige Instanz wird automatisch *freigegeben*.)</span><span class="sxs-lookup"><span data-stu-id="5c300-135">(The previous instance will be freed, or *released*, automatically).</span></span> <span data-ttu-id="5c300-136">Wenn nicht jedes Mal eine neue Instanz erstellt werden soll, fügen Sie dem Konstruktor der BlankPage-Klasse in der Datei „BlankPage.xaml.cs“ den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c300-136">If you don't want a new instance to be created each time, add the following code to the BlankPage class's constructor in the BlankPage.xaml.cs file.</span></span> <span data-ttu-id="5c300-137">Dadurch wird das [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506)-Verhalten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5c300-137">This will enable the [**NavigationCacheMode**](https://msdn.microsoft.com/library/windows/apps/br227506) behavior.</span></span>

```csharp
public BlankPage()
{
    this.InitializeComponent();
    // Add the following line of code.
    this.NavigationCacheMode = Windows.UI.Xaml.Navigation.NavigationCacheMode.Enabled;
}
```

<span data-ttu-id="5c300-138">Sie können auch die [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683)-Eigenschaft der **Frame**-Klasse abrufen oder festlegen, um zu definieren, wie viele Seiten im Navigationsverlauf zwischengespeichert werden können.</span><span class="sxs-lookup"><span data-stu-id="5c300-138">You can also get or set the **Frame** class's [**CacheSize**](https://msdn.microsoft.com/library/windows/apps/br242683) property to manage how many pages in the navigation history can be cached.</span></span>

<span data-ttu-id="5c300-139">Weitere Informationen zur Navigation finden Sie unter [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) und unter [XAML-Beispiel für Charakteranimationen](http://go.microsoft.com/fwlink/p/?LinkID=242401).</span><span class="sxs-lookup"><span data-stu-id="5c300-139">For more info about navigation, see [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) and [XAML personality animations sample](http://go.microsoft.com/fwlink/p/?LinkID=242401).</span></span>

<span data-ttu-id="5c300-140">**Hinweis:** Informationen zur Navigation für UWP-apps mit JavaScript und HTML finden Sie unter [Schnellstart: Verwenden der einzelseitennavigation](https://msdn.microsoft.com/library/windows/apps/hh452768).</span><span class="sxs-lookup"><span data-stu-id="5c300-140">**Note**For info about navigation for UWP apps using JavaScript and HTML, see [Quickstart: Using single-page navigation](https://msdn.microsoft.com/library/windows/apps/hh452768).</span></span>
 
### <a name="next-step"></a><span data-ttu-id="5c300-141">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="5c300-141">Next step</span></span>

[<span data-ttu-id="5c300-142">Erste Schritte: Animation</span><span class="sxs-lookup"><span data-stu-id="5c300-142">Getting started: Animation</span></span>](getting-started-animation.md)

