---
author: stevewhims
description: Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *Observable*-Eigenschaft bezeichnet. Dieses Thema zeigt, wie man eine Observable-Eigenschaft implementiert und nutzt und wie man ein XAML-Steuerelement daran bindet.
title: XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, binden, eigenschaft
ms.localizationpriority: medium
ms.openlocfilehash: 367bf5d5d554bd094ce3d5b726b818c8c388d398
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "2787157"
---
# <a name="xaml-controls-bind-to-a-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-property"></a><span data-ttu-id="ae400-105">XAML-Steuerelemente; Binden an eine [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ae400-105">XAML controls; bind to a [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) property</span></span>
<span data-ttu-id="ae400-106">Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *observable*-Eigenschaft bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ae400-106">A property that can be effectively bound to a XAML control is known as an *observable* property.</span></span> <span data-ttu-id="ae400-107">Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="ae400-107">This idea is based on the software design pattern known as the *observer pattern*.</span></span> <span data-ttu-id="ae400-108">Dieses Thema zeigt, wie man Observable-Eigenschaften in C++/WinRT implementiert und wie man XAML-Steuerelemente an diese bindet.</span><span class="sxs-lookup"><span data-stu-id="ae400-108">This topic shows how to implement observable properties in C++/WinRT, and how to bind XAML controls to them.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae400-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="ae400-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="what-does-observable-mean-for-a-property"></a><span data-ttu-id="ae400-110">Was bedeutet *observable* für eine Eigenschaft?</span><span class="sxs-lookup"><span data-stu-id="ae400-110">What does *observable* mean for a property?</span></span>
<span data-ttu-id="ae400-111">Angenommen, eine Laufzeitklasse namens **BookSku** hat eine Eigenschaft namens **Title**.</span><span class="sxs-lookup"><span data-stu-id="ae400-111">Let's say that a runtime class named **BookSku** has a property named **Title**.</span></span> <span data-ttu-id="ae400-112">Wenn **BookSku** das Ereignis [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) auslöst, wenn sich der Wert von **Title** ändert, dann ist **Title** eine Observable-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-112">If **BookSku** chooses to raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event whenever the value of **Title** changes, then **Title** is an observable property.</span></span> <span data-ttu-id="ae400-113">Es ist das Verhalten von **BookSku** (Auslösen oder nicht Auslösen des Ereignisses), das bestimmt, welche seiner Eigenschaften Observable-Eigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="ae400-113">It's the behavior of **BookSku** (raising or not raising the event) that determines which, if any, of its properties are observable.</span></span>

<span data-ttu-id="ae400-114">Ein XAML-Textelement oder -Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es den/die aktualisierten Wert(e) abruft und dann eine Aktualisierung durchführt, um den neuen Wert anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ae400-114">A XAML text element, or control, can bind to, and handle, these events by retrieving the updated value(s) and then updating itself to show the new value.</span></span>

> [!NOTE]
> <span data-ttu-id="ae400-115">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="ae400-115">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="create-a-blank-app-bookstore"></a><span data-ttu-id="ae400-116">Erstellen einer leeren App (Bookstore)</span><span class="sxs-lookup"><span data-stu-id="ae400-116">Create a Blank App (Bookstore)</span></span>
<span data-ttu-id="ae400-117">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae400-117">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="ae400-118">Erstellen Sie ein **Visual C++ Blank App (C++/WinRT)**-Projekt und nennen Sie es *Bookstore*.</span><span class="sxs-lookup"><span data-stu-id="ae400-118">Create a **Visual C++ Blank App (C++/WinRT)** project, and name it *Bookstore*.</span></span>

<span data-ttu-id="ae400-119">Wir werden eine neue Klasse schreiben, um ein Buch mit einer Observable-Eigenschaft namens „Titel” darzustellen.</span><span class="sxs-lookup"><span data-stu-id="ae400-119">We're going to author a new class to represent a book that has an observable title property.</span></span> <span data-ttu-id="ae400-120">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="ae400-120">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="ae400-121">Aber wir wollen in der Lage sein, aus XAML eine Bindung an diese Klasse zu nutzen. Daher wird es eine Laufzeitklasse sein.</span><span class="sxs-lookup"><span data-stu-id="ae400-121">But we want to be able to bind to this class from XAML, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="ae400-122">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="ae400-122">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="ae400-123">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ae400-123">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="ae400-124">Nennen Sie es `BookSku.idl`.</span><span class="sxs-lookup"><span data-stu-id="ae400-124">Name it `BookSku.idl`.</span></span> <span data-ttu-id="ae400-125">Löschen Sie den Standardinhalt von `BookSku.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="ae400-125">Delete the default contents of `BookSku.idl`, and paste in this runtime class declaration.</span></span>

```idl
// BookSku.idl
namespace Bookstore
{
    runtimeclass BookSku : Windows.UI.Xaml.DependencyObject, Windows.UI.Xaml.Data.INotifyPropertyChanged
    {
        String Title;
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="ae400-126">Für eine Anwendung an das [Windows App Zertifizierungskit](../debug-test-perf/windows-app-certification-kit.md) übergeben Tests, die vom Microsoft Store zum Überprüfen von Übermittlungen verwendet, und daher um erfolgreich in Microsoft Store aufgenommen werden, die oberste Basisklasse für jede Klasse Runtime *in deklariert die Anwendung* muss einen Typ, die in einem Windows.\*-Namespace stammen.</span><span class="sxs-lookup"><span data-stu-id="ae400-126">For an application to pass the [Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md) tests used by the Microsoft Store to validate submissions, and therefore to be successfully ingested into the Microsoft Store, the ultimate base class of each runtime class *declared in the application* must be a type originating in a Windows.\* namespace.</span></span>

<span data-ttu-id="ae400-127">Um diese Anforderung zu erfüllen, leiten Sie Ihre Ansichtsmodell-Klassen von [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject) ab.</span><span class="sxs-lookup"><span data-stu-id="ae400-127">To fulfil that requirement, derive your view model classes from [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject).</span></span> <span data-ttu-id="ae400-128">Alternativ können Sie eine von **DependencyObject** abgeleitete bindbare Basisklasse deklarieren und daraus Ihre Ansichtsmodelle ableiten.</span><span class="sxs-lookup"><span data-stu-id="ae400-128">Alternatively, declare a bindable base class derived from **DependencyObject**, and derive your view models from that.</span></span> <span data-ttu-id="ae400-129">Sie können Ihre Datenmodelle als C++ Strukturen deklarieren. Sie müssen nicht in MIDL deklariert werden (solange Sie sie nur in Ihren Ansichtsmodellen nutzen und XAML nicht direkt an sie binden – in diesem Fall wären sie allerdings per Definition sowieso Ansichtsmodelle).</span><span class="sxs-lookup"><span data-stu-id="ae400-129">You can declare your data models as C++ structs; they don't need to be declared in MIDL (as long as you're consuming them only from your view models and not binding XAML directly to them; in which case they'd arguably be view models by definition, anyway).</span></span>

<span data-ttu-id="ae400-130">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="ae400-130">Save the file and build the project.</span></span> <span data-ttu-id="ae400-131">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ae400-131">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) describing the runtime class.</span></span> <span data-ttu-id="ae400-132">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ae400-132">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="ae400-133">Diese Dateien enthalten Stubs, um mit der Implementierung der **BookSku**-Laufzeitklasse zu beginnen, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="ae400-133">These files include stubs to get you started implementing the **BookSku** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="ae400-134">Diese Stubs sind `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` und `BookSku.cpp`.</span><span class="sxs-lookup"><span data-stu-id="ae400-134">Those stubs are `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` and `BookSku.cpp`.</span></span>

<span data-ttu-id="ae400-135">Kopieren Sie die Stub-Dateien `BookSku.h` und `BookSku.cpp` von `\Bookstore\Bookstore\Generated Files\sources\` in den Projektordner `\Bookstore\Bookstore\`.</span><span class="sxs-lookup"><span data-stu-id="ae400-135">Copy the stub files `BookSku.h` and `BookSku.cpp` from `\Bookstore\Bookstore\Generated Files\sources\` into the project folder, which is `\Bookstore\Bookstore\`.</span></span> <span data-ttu-id="ae400-136">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ae400-136">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="ae400-137">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="ae400-137">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-booksku"></a><span data-ttu-id="ae400-138">Implementieren von **BookSku**</span><span class="sxs-lookup"><span data-stu-id="ae400-138">Implement **BookSku**</span></span>
<span data-ttu-id="ae400-139">Nun öffnen wir `\Bookstore\Bookstore\BookSku.h` und `BookSku.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="ae400-139">Now, let's open `\Bookstore\Bookstore\BookSku.h` and `BookSku.cpp` and implement our runtime class.</span></span> <span data-ttu-id="ae400-140">Fügen Sie in `BookSku.h` einen Konstruktor hinzu, der ein [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Argument (ein privates Mitglied zum Speichern des Titels) und eine weiteres für das bei einer Titeländerung ausgelöste Ereignis entgegen nimmt.</span><span class="sxs-lookup"><span data-stu-id="ae400-140">In `BookSku.h`, add a constructor that takes a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring), a private member to store the title string, and another for the event that we'll raise when the title changes.</span></span> <span data-ttu-id="ae400-141">Nachdem Sie diese hinzugefügt haben, sieht Ihr `BookSku.h` so aus.</span><span class="sxs-lookup"><span data-stu-id="ae400-141">After adding those, your `BookSku.h` will look like this.</span></span>

```cppwinrt
// BookSku.h
#pragma once

#include "BookSku.g.h"

namespace winrt::Bookstore::implementation
{
    struct BookSku : BookSkuT<BookSku>
    {
        BookSku() = delete;
        BookSku(winrt::hstring const& title);

        hstring Title();
        void Title(winrt::hstring const& value);
        event_token PropertyChanged(Windows::UI::Xaml::Data::PropertyChangedEventHandler const& value);
        void PropertyChanged(winrt::event_token const& token);
    
    private:
        hstring m_title;
        event<Windows::UI::Xaml::Data::PropertyChangedEventHandler> m_propertyChanged;
    };
}
```

<span data-ttu-id="ae400-142">Implementieren Sie in `BookSku.cpp` die Funktionen wie folgt.</span><span class="sxs-lookup"><span data-stu-id="ae400-142">In `BookSku.cpp`, implement the functions like this.</span></span>

```cppwinrt
// BookSku.cpp
#include "pch.h"
#include "BookSku.h"

namespace winrt::Bookstore::implementation
{
    hstring BookSku::Title()
    {
        return m_title;
    }

    BookSku::BookSku(winrt::hstring const& title)
    {
        Title(title);
    }

    void BookSku::Title(winrt::hstring const& value)
    {
        if (m_title != value)
        {
            m_title = value;
            m_propertyChanged(*this, Windows::UI::Xaml::Data::PropertyChangedEventArgs{ L"Title" });
        }
    }

    event_token BookSku::PropertyChanged(Windows::UI::Xaml::Data::PropertyChangedEventHandler const& handler)
    {
        return m_propertyChanged.add(handler);
    }

    void BookSku::PropertyChanged(winrt::event_token const& token)
    {
        m_propertyChanged.remove(token);
    }
}
```

<span data-ttu-id="ae400-143">In der **Title**-Zugriffsfunktion prüfen wir, ob ein anderer Wert gesetzt wird, und wenn ja, aktualisieren wir den Titel und lösen außerdem das Ereignis [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) mit einem Argument aus, das dem Namen der geänderten Eigenschaft entspricht.</span><span class="sxs-lookup"><span data-stu-id="ae400-143">In the **Title** mutator function, we check whether a different value is being set and, if so, we update the title and also raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event with an argument equal to the name of the property that has changed.</span></span> <span data-ttu-id="ae400-144">Dies dient dazu, dass die Benutzeroberfläche (UI) erkennt, welcher Eigenschaftswert erneut abgefragt werden muss.</span><span class="sxs-lookup"><span data-stu-id="ae400-144">This is so that the user-interface (UI) will know which property's value to re-query.</span></span>

## <a name="declare-and-implement-bookstoreviewmodel"></a><span data-ttu-id="ae400-145">**BookstoreViewModel** deklarieren und implementieren</span><span class="sxs-lookup"><span data-stu-id="ae400-145">Declare and implement **BookstoreViewModel**</span></span>
<span data-ttu-id="ae400-146">Unsere XAML-Hauptseite wird sich an ein Hauptansichtsmodell gebunden.</span><span class="sxs-lookup"><span data-stu-id="ae400-146">Our main XAML page is going to bind to a main view model.</span></span> <span data-ttu-id="ae400-147">Dieses Ansichtsmodell wird mehrere Eigenschaften haben, darunter eine vom Typ **BookSku**.</span><span class="sxs-lookup"><span data-stu-id="ae400-147">And that view model is going to have several properties, including one of type **BookSku**.</span></span> <span data-ttu-id="ae400-148">In diesem Schritt deklarieren und implementieren wir unsere Hauptansichtsmodell-Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="ae400-148">In this step, we'll declare and implement our main view model runtime class.</span></span>

<span data-ttu-id="ae400-149">Fügen Sie eine neue **Midl-Datei (.idl)** mit dem Namen `BookstoreViewModel.idl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae400-149">Add a new **Midl File (.idl)** item named `BookstoreViewModel.idl`.</span></span>

```idl
// BookstoreViewModel.idl
import "BookSku.idl";

namespace Bookstore
{
    runtimeclass BookstoreViewModel : Windows.UI.Xaml.DependencyObject
    {
        BookSku BookSku{ get; };
    }
}
```

<span data-ttu-id="ae400-150">Speichern und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="ae400-150">Save and build.</span></span> <span data-ttu-id="ae400-151">Kopieren Sie `BookstoreViewModel.h` und `BookstoreViewModel.cpp` aus dem `Generated Files`-Ordner in den Projektordner und nehmen Sie sie in das Projekt auf.</span><span class="sxs-lookup"><span data-stu-id="ae400-151">Copy `BookstoreViewModel.h` and `BookstoreViewModel.cpp` from the `Generated Files` folder into the project folder, and include them in the project.</span></span> <span data-ttu-id="ae400-152">Öffnen Sie diese Dateien und implementieren Sie die Laufzeitklasse wie folgt.</span><span class="sxs-lookup"><span data-stu-id="ae400-152">Open those files and implement the runtime class like this.</span></span>

```cppwinrt
// BookstoreViewModel.h
#pragma once

#include "BookstoreViewModel.g.h"
#include "BookSku.h"

namespace winrt::Bookstore::implementation
{
    struct BookstoreViewModel : BookstoreViewModelT<BookstoreViewModel>
    {
        BookstoreViewModel();
        Bookstore::BookSku BookSku();

    private:
        Bookstore::BookSku m_bookSku{ nullptr };
    };
}
```

```cppwinrt
// BookstoreViewModel.cpp
#include "pch.h"
#include "BookstoreViewModel.h"

namespace winrt::Bookstore::implementation
{
    BookstoreViewModel::BookstoreViewModel()
    {
        m_bookSku = make<Bookstore::implementation::BookSku>(L"Atticus");
    }

    Bookstore::BookSku BookstoreViewModel::BookSku()
    {
        return m_bookSku;
    }
}
```

> [!NOTE]
> <span data-ttu-id="ae400-153">Der Typ von `m_bookSku` ist der projizierte Typ (**winrt::Bookstore::BookSku**), und der Template-Parameter, den Sie mit **make** verwenden, ist der Implementierungstyp (**winrt::Bookstore::implementation::BookSku**).</span><span class="sxs-lookup"><span data-stu-id="ae400-153">The type of `m_bookSku` is the projected type (**winrt::Bookstore::BookSku**), and the template parameter that you use with **make** is the implementation type (**winrt::Bookstore::implementation::BookSku**).</span></span> <span data-ttu-id="ae400-154">Dennoch gibt **make** eine Instanz des projizierten Typs zurück.</span><span class="sxs-lookup"><span data-stu-id="ae400-154">Even so, **make** returns an instance of the projected type.</span></span>

## <a name="add-a-property-of-type-bookstoreviewmodel-to-mainpage"></a><span data-ttu-id="ae400-155">Hinzufügen einer Eigenschaft vom Typ **BookstoreViewModel** zu **MainPage**</span><span class="sxs-lookup"><span data-stu-id="ae400-155">Add a property of type **BookstoreViewModel** to **MainPage**</span></span>
<span data-ttu-id="ae400-156">Öffnen Sie `MainPage.idl` (unsere Haupt-UI-Seite) mit der Deklaration der Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="ae400-156">Open `MainPage.idl`, which declares the runtime class that represents our main UI page.</span></span> <span data-ttu-id="ae400-157">Fügen Sie eine Import-Anweisung zum Import von `BookstoreViewModel.idl` hinzu und fügen Sie eine schreibgeschützte Eigenschaft namens MainViewModel vom Typ **BookstoreViewModel** hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae400-157">Add an import statement to import `BookstoreViewModel.idl`, and add a read-only property named MainViewModel of type **BookstoreViewModel**.</span></span> <span data-ttu-id="ae400-158">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-158">Also remove the **MyProperty** property.</span></span> <span data-ttu-id="ae400-159">Beachten Sie außerdem die Richtlinie **Importieren** in der Liste unten.</span><span class="sxs-lookup"><span data-stu-id="ae400-159">Also note the **import** directive in the listing below.</span></span>

```idl
// MainPage.idl
import "BookstoreViewModel.idl";

namespace Bookstore
{
    runtimeclass MainPage : Windows.UI.Xaml.Controls.Page
    {
        MainPage();
        BookstoreViewModel MainViewModel{ get; };
    }
}
```

<span data-ttu-id="ae400-160">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="ae400-160">Save the file.</span></span> <span data-ttu-id="ae400-161">Erstellen Sie das Projekt wird nicht erfolgreich abgeschlossen, in dem Moment, aber jetzt erstellen, ist ein sinnvoll, da es die Quellcodedateien generiert in der **MainPage** -Runtime-Klasse implementiert wird (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` und `MainPage.cpp`).</span><span class="sxs-lookup"><span data-stu-id="ae400-161">The project won't build to completion at the moment, but building now is a useful thing to do because it regenerates the source code files in which the **MainPage** runtime class is implemented (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` and `MainPage.cpp`).</span></span> <span data-ttu-id="ae400-162">Also nun und jetzt erstellen.</span><span class="sxs-lookup"><span data-stu-id="ae400-162">So go ahead and build now.</span></span> <span data-ttu-id="ae400-163">Ist der Fehler beim Erstellen Sie erwarten können, in dieser Phase finden Sie unter **'MainViewModel': ist kein Mitglied von 'Winrt::Bookstore::implementation::MainPage'**.</span><span class="sxs-lookup"><span data-stu-id="ae400-163">The build error you can expect to see at this stage is **'MainViewModel': is not a member of 'winrt::Bookstore::implementation::MainPage'**.</span></span>

<span data-ttu-id="ae400-164">Wenn Sie die einschließen von weglassen `BookstoreViewModel.idl` (finden Sie in der Liste der `MainPage.idl` oben), und klicken Sie dann die Fehlermeldung angezeigt wird **erwartet \ < near "MainViewModel"**.</span><span class="sxs-lookup"><span data-stu-id="ae400-164">If you omit the include of `BookstoreViewModel.idl` (see the listing of `MainPage.idl` above), then you'll see the error **expecting \< near "MainViewModel"**.</span></span> <span data-ttu-id="ae400-165">Ein weiterer Tipp ist, um sicherzustellen, dass Sie alle Typen im gleichen Namespace lassen: der Namespace, der in der Codebeispiele angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ae400-165">Another tip is to make sure that you leave all types in the same namespace: the namespace that's shown in the code listings.</span></span>

<span data-ttu-id="ae400-166">Zum Beheben des Fehlers, die wir finden Sie unter erwarten Sie jetzt müssen die Accessor Stubs für die **MainViewModel** -Eigenschaft aus dem generierten Dateien und in kopieren `\Bookstore\Bookstore\MainPage.h` und `MainPage.cpp`.</span><span class="sxs-lookup"><span data-stu-id="ae400-166">To resolve the error that we expect to see, you'll now need to copy the accessor stubs for the **MainViewModel** property out of the generated files and into `\Bookstore\Bookstore\MainPage.h` and `MainPage.cpp`.</span></span>

<span data-ttu-id="ae400-167">Fügen Sie zu `\Bookstore\Bookstore\MainPage.h` ein privates Mitglied hinzu, um das Ansichtsmodell zu speichern.</span><span class="sxs-lookup"><span data-stu-id="ae400-167">To `\Bookstore\Bookstore\MainPage.h`, add a private member to store the view model.</span></span> <span data-ttu-id="ae400-168">Beachten Sie, dass die Zugriffsfunktion für die Eigenschaft (und das Mitglied m_mainViewModel) als **Bookstore::BookstoreViewModel** (dem projizierten Typ) implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="ae400-168">Note that the property accessor function (and the member m_mainViewModel) is implemented in terms of **Bookstore::BookstoreViewModel**, which is the projected type.</span></span> <span data-ttu-id="ae400-169">Der Implementierungstyp befindet sich im selben Projekt (Kompilierungseinheit), so dass wir m_mainViewModel über die Konstruktorüberladung mit `nullptr_t` konstruieren.</span><span class="sxs-lookup"><span data-stu-id="ae400-169">The implementation type is in the same project (compilation unit), so we construct m_mainViewModel via the constructor overload that takes `nullptr_t`.</span></span> <span data-ttu-id="ae400-170">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-170">Also remove the **MyProperty** property.</span></span>

```cppwinrt
// MainPage.h
...
namespace winrt::Bookstore::implementation
{
    struct MainPage : MainPageT<MainPage>
    {
        MainPage();

        Bookstore::BookstoreViewModel MainViewModel();

        void ClickHandler(Windows::Foundation::IInspectable const& sender, Windows::UI::Xaml::RoutedEventArgs const& args);

    private:
        Bookstore::BookstoreViewModel m_mainViewModel{ nullptr };
    };
}
...
```

<span data-ttu-id="ae400-171">Nehmen Sie `BookstoreViewModel.h` (Deklaration des Implementierungstyps) in `\Bookstore\Bookstore\MainPage.cpp` auf.</span><span class="sxs-lookup"><span data-stu-id="ae400-171">In `\Bookstore\Bookstore\MainPage.cpp`, include `BookstoreViewModel.h`, which declares the implementation type.</span></span> <span data-ttu-id="ae400-172">Rufen Sie [**winrt::make**](/uwp/cpp-ref-for-winrt/make) auf (mit dem Implementierungstyp), um m_mainViewModel eine neue Instanz des projizierten Typs zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="ae400-172">Call [**winrt::make**](/uwp/cpp-ref-for-winrt/make) (with the implementation type) to assign a new instance of the projected type to m_mainViewModel.</span></span> <span data-ttu-id="ae400-173">Weisen Sie einen Initialwert für den Titel des Buches zu.</span><span class="sxs-lookup"><span data-stu-id="ae400-173">Assign an initial value for the book's title.</span></span> <span data-ttu-id="ae400-174">Implementieren Sie die Zugriffsfunktion für die MainViewModel-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-174">Implement the accessor for the MainViewModel property.</span></span> <span data-ttu-id="ae400-175">Aktualisieren Sie zum Schluss den Titel des Buches im Event-Handler der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ae400-175">And finally, update the book's title in the button's event handler.</span></span> <span data-ttu-id="ae400-176">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-176">Also remove the **MyProperty** property.</span></span>

```cppwinrt
// MainPage.cpp
#include "pch.h"
#include "MainPage.h"
#include "BookstoreViewModel.h"

using namespace winrt;
using namespace Windows::UI::Xaml;

namespace winrt::Bookstore::implementation
{
    MainPage::MainPage()
    {
        m_mainViewModel = make<Bookstore::implementation::BookstoreViewModel>();
        InitializeComponent();
    }

    void MainPage::ClickHandler(IInspectable const&, RoutedEventArgs const&)
    {
        MainViewModel().BookSku().Title(L"To Kill a Mockingbird");
    }

    Bookstore::BookstoreViewModel MainPage::MainViewModel()
    {
        return m_mainViewModel;
    }
}
```

## <a name="bind-the-button-to-the-title-property"></a><span data-ttu-id="ae400-177">Binden Sie die Schaltfläche an die **Title**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ae400-177">Bind the button to the **Title** property</span></span>
<span data-ttu-id="ae400-178">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="ae400-178">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="ae400-179">Entfernen Sie den Namen von der Schaltfläche und ändern Sie den Wert der **Content**-Eigenschaft von einem Literal in einen Bindungsausdruck.</span><span class="sxs-lookup"><span data-stu-id="ae400-179">Remove the name from the button, and change its **Content** property value from a literal to a binding expression.</span></span> <span data-ttu-id="ae400-180">Beachten Sie die Eigenschaft `Mode=OneWay` des Bindungsausdrucks (einseitig vom Ansichtsmodell zum UI).</span><span class="sxs-lookup"><span data-stu-id="ae400-180">Note the `Mode=OneWay` property on the binding expression (one-way from the view model to the UI).</span></span> <span data-ttu-id="ae400-181">Ohne diese Eigenschaft reagiert die Benutzeroberfläche nicht auf Ereignisse zu Eigenschaftsänderungen.</span><span class="sxs-lookup"><span data-stu-id="ae400-181">Without that property, the UI will not respond to property changed events.</span></span>

```xaml
<Button Click="ClickHandler" Content="{x:Bind MainViewModel.BookSku.Title, Mode=OneWay}"/>
```

<span data-ttu-id="ae400-182">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="ae400-182">Now build and run the project.</span></span> <span data-ttu-id="ae400-183">Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ae400-183">Click the button to execute the **Click** event handler.</span></span> <span data-ttu-id="ae400-184">Dieser Handler ruft die Zugriffsfunktion des Buches auf; diese Zugriffsfunktion löst ein Ereignis aus, um die Benutzeroberfläche wissen zu lassen, dass sich die **Title**-Eigenschaft geändert hat; die Schaltfläche fragt den Wert dieser Eigenschaft erneut ab, um ihren eigenen **Content**-Wert zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ae400-184">That handler calls the book's title mutator function; that mutator raises an event to let the UI know that the **Title** property has changed; and the button re-queries that property's value to update its own **Content** value.</span></span>

## <a name="using-the-binding-markup-extension-with-cwinrt"></a><span data-ttu-id="ae400-185">Verwenden die Erweiterung {Binding} Markup mit C + / WinRT</span><span class="sxs-lookup"><span data-stu-id="ae400-185">Using the {Binding} markup extension with C++/WinRT</span></span>
<span data-ttu-id="ae400-186">Für die derzeit endgültige Produktversion von C + / WinRT, damit werden die {Binding} Markup-Erweiterung verwenden, Sie die [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) und [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) Schnittstellen implementieren müssen, können.</span><span class="sxs-lookup"><span data-stu-id="ae400-186">For the currently released version of C++/WinRT, in order to be able to use the {Binding} markup extension you'll need to implement the [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) and [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) interfaces.</span></span>

## <a name="important-apis"></a><span data-ttu-id="ae400-187">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="ae400-187">Important APIs</span></span>
* [<span data-ttu-id="ae400-188">INotifyPropertyChanged::PropertyChanged</span><span class="sxs-lookup"><span data-stu-id="ae400-188">INotifyPropertyChanged::PropertyChanged</span></span>](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged)
* [<span data-ttu-id="ae400-189">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="ae400-189">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a><span data-ttu-id="ae400-190">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ae400-190">Related topics</span></span>
* [<span data-ttu-id="ae400-191">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="ae400-191">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="ae400-192">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="ae400-192">Author APIs with C++/WinRT</span></span>](author-apis.md)
