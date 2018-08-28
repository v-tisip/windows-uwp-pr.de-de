---
author: stevewhims
description: Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *Observable*-Eigenschaft bezeichnet. Dieses Thema zeigt, wie man eine Observable-Eigenschaft implementiert und nutzt und wie man ein XAML-Steuerelement daran bindet.
title: XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft
ms.author: stwhi
ms.date: 08/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, binden, eigenschaft
ms.localizationpriority: medium
ms.openlocfilehash: 31913ae162bfe541d04f304db87b4dff962a8af4
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2884186"
---
# <a name="xaml-controls-bind-to-a-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-property"></a><span data-ttu-id="dde11-105">XAML-Steuerelemente; Binden an eine [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="dde11-105">XAML controls; bind to a [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) property</span></span>
<span data-ttu-id="dde11-106">Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *observable*-Eigenschaft bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="dde11-106">A property that can be effectively bound to a XAML control is known as an *observable* property.</span></span> <span data-ttu-id="dde11-107">Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="dde11-107">This idea is based on the software design pattern known as the *observer pattern*.</span></span> <span data-ttu-id="dde11-108">Dieses Thema zeigt, wie man Observable-Eigenschaften in C++/WinRT implementiert und wie man XAML-Steuerelemente an diese bindet.</span><span class="sxs-lookup"><span data-stu-id="dde11-108">This topic shows how to implement observable properties in C++/WinRT, and how to bind XAML controls to them.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dde11-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="dde11-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="what-does-observable-mean-for-a-property"></a><span data-ttu-id="dde11-110">Was bedeutet *observable* für eine Eigenschaft?</span><span class="sxs-lookup"><span data-stu-id="dde11-110">What does *observable* mean for a property?</span></span>
<span data-ttu-id="dde11-111">Angenommen, eine Laufzeitklasse namens **BookSku** hat eine Eigenschaft namens **Title**.</span><span class="sxs-lookup"><span data-stu-id="dde11-111">Let's say that a runtime class named **BookSku** has a property named **Title**.</span></span> <span data-ttu-id="dde11-112">Wenn **BookSku** das Ereignis [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) auslöst, wenn sich der Wert von **Title** ändert, dann ist **Title** eine Observable-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-112">If **BookSku** chooses to raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event whenever the value of **Title** changes, then **Title** is an observable property.</span></span> <span data-ttu-id="dde11-113">Es ist das Verhalten von **BookSku** (Auslösen oder nicht Auslösen des Ereignisses), das bestimmt, welche seiner Eigenschaften Observable-Eigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="dde11-113">It's the behavior of **BookSku** (raising or not raising the event) that determines which, if any, of its properties are observable.</span></span>

<span data-ttu-id="dde11-114">Ein XAML-Textelement oder -Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es den/die aktualisierten Wert(e) abruft und dann eine Aktualisierung durchführt, um den neuen Wert anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="dde11-114">A XAML text element, or control, can bind to, and handle, these events by retrieving the updated value(s) and then updating itself to show the new value.</span></span>

> [!NOTE]
> <span data-ttu-id="dde11-115">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="dde11-115">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="create-a-blank-app-bookstore"></a><span data-ttu-id="dde11-116">Erstellen einer leeren App (Bookstore)</span><span class="sxs-lookup"><span data-stu-id="dde11-116">Create a Blank App (Bookstore)</span></span>
<span data-ttu-id="dde11-117">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dde11-117">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="dde11-118">Erstellen Sie ein **Visual C++ Blank App (C++/WinRT)**-Projekt und nennen Sie es *Bookstore*.</span><span class="sxs-lookup"><span data-stu-id="dde11-118">Create a **Visual C++ Blank App (C++/WinRT)** project, and name it *Bookstore*.</span></span>

<span data-ttu-id="dde11-119">Wir werden eine neue Klasse schreiben, um ein Buch mit einer Observable-Eigenschaft namens „Titel” darzustellen.</span><span class="sxs-lookup"><span data-stu-id="dde11-119">We're going to author a new class to represent a book that has an observable title property.</span></span> <span data-ttu-id="dde11-120">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="dde11-120">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="dde11-121">Aber wir wollen in der Lage sein, aus XAML eine Bindung an diese Klasse zu nutzen. Daher wird es eine Laufzeitklasse sein.</span><span class="sxs-lookup"><span data-stu-id="dde11-121">But we want to be able to bind to this class from XAML, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="dde11-122">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="dde11-122">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="dde11-123">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="dde11-123">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="dde11-124">Nennen Sie es `BookSku.idl`.</span><span class="sxs-lookup"><span data-stu-id="dde11-124">Name it `BookSku.idl`.</span></span> <span data-ttu-id="dde11-125">Löschen Sie den Standardinhalt von `BookSku.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="dde11-125">Delete the default contents of `BookSku.idl`, and paste in this runtime class declaration.</span></span>

```idl
// BookSku.idl
namespace Bookstore
{
    runtimeclass BookSku : Windows.UI.Xaml.Data.INotifyPropertyChanged
    {
        String Title;
    }
}
```

> [!NOTE]
> <span data-ttu-id="dde11-126">Ihre Ansicht Modellklassen&mdash;tatsächlich jede Laufzeitklasse, die Sie in der Anwendung deklarieren&mdash;müssen nicht von einer Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="dde11-126">Your view model classes&mdash;in fact, any runtime class that you declare in your application&mdash;need not derive from a base class.</span></span> <span data-ttu-id="dde11-127">Die oben deklarierte **BookSku** -Klasse ist ein Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="dde11-127">The **BookSku** class declared above is an example of that.</span></span> <span data-ttu-id="dde11-128">Eine Schnittstelle implementiert, aber sie nicht von einer Basisklasse abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="dde11-128">It implements an interface, but it doesn't derive from any base class.</span></span>
>
> <span data-ttu-id="dde11-129">Jede Laufzeitklasse, die Sie in der Anwendung zu deklarieren, *wird* von abgeleitet, einer Basis Klasse wird als bezeichnet ein *zusammensetzbares* Klasse.</span><span class="sxs-lookup"><span data-stu-id="dde11-129">Any runtime class that you declare in the application that *does* derive from a base class is known as a *composable* class.</span></span> <span data-ttu-id="dde11-130">Und Einschränkungen um zusammensetzbare Klassen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="dde11-130">And there are constraints around composable classes.</span></span> <span data-ttu-id="dde11-131">Für eine Anwendung, die von Visual Studio und Microsoft Store Übermittlungen überprüfen verwendet [Windows App Zertifizierungskit](../debug-test-perf/windows-app-certification-kit.md) Tests zu übergeben (und somit die Anwendung erfolgreich in Microsoft Store aufgenommen werden), muss eine zusammensetzbare-Klasse letztlich von einer Windows-Basisklasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="dde11-131">For an application to pass the [Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md) tests used by Visual Studio and by the Microsoft Store to validate submissions (and therefore for the application to be successfully ingested into the Microsoft Store), a composable class must ultimately derive from a Windows base class.</span></span> <span data-ttu-id="dde11-132">Was bedeutet, dass die Klasse sehr Stamm der Vererbungshierarchie einen Typ, der in einem Namespace Windows.\* sein muss.</span><span class="sxs-lookup"><span data-stu-id="dde11-132">Meaning that the class at the very root of the inheritance hierarchy must be a type originating in a Windows.\* namespace.</span></span> <span data-ttu-id="dde11-133">Wenn Sie eine Basisklasse Runtime-Klasse abgeleitet benötigen&mdash;beispielsweise implementieren eine **BindableBase** -Klasse für alle Ihre Modelle anzeigen Ableiten von&mdash;dann [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject)abgeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="dde11-133">If you do need to derive a runtime class from a base class&mdash;for example, to implement a **BindableBase** class for all of your view models to derive from&mdash;then you can derive from [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject).</span></span>
>
> <span data-ttu-id="dde11-134">Ein Ansichtsmodell ist eine Abstraktion einer Ansicht, und es ist also direkt auf die Ansicht (XAML-Markup) gebunden.</span><span class="sxs-lookup"><span data-stu-id="dde11-134">A view model is an abstraction of a view, and so it's bound directly to the view (the XAML markup).</span></span> <span data-ttu-id="dde11-135">Ein Datenmodell ist eine Abstraktion des Daten, und nur von Ansichtsmodellen verwendet und nicht direkt in XAML gebunden.</span><span class="sxs-lookup"><span data-stu-id="dde11-135">A data model is an abstraction of data, and it's consumed only from your view models, and not bound directly to XAML.</span></span> <span data-ttu-id="dde11-136">Daher können Sie Ihre Datenmodelle nicht als Runtime-Klassen, sondern als C++ Strukturen oder Klassen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="dde11-136">So, you can declare your data models not as runtime classes, but as C++ structs or classes.</span></span> <span data-ttu-id="dde11-137">Sie brauchen in MIDL deklariert werden, und Sie können unabhängig Vererbungshierarchie verwenden Sie wie folgt.</span><span class="sxs-lookup"><span data-stu-id="dde11-137">They don't need to be declared in MIDL, and you're free to use whatever inheritance hierarchy you like.</span></span>

<span data-ttu-id="dde11-138">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="dde11-138">Save the file and build the project.</span></span> <span data-ttu-id="dde11-139">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="dde11-139">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) describing the runtime class.</span></span> <span data-ttu-id="dde11-140">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dde11-140">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="dde11-141">Diese Dateien enthalten Stubs, um mit der Implementierung der **BookSku**-Laufzeitklasse zu beginnen, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="dde11-141">These files include stubs to get you started implementing the **BookSku** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="dde11-142">Diese Stubs sind `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` und `BookSku.cpp`.</span><span class="sxs-lookup"><span data-stu-id="dde11-142">Those stubs are `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` and `BookSku.cpp`.</span></span>

<span data-ttu-id="dde11-143">Kopieren Sie die Stub-Dateien `BookSku.h` und `BookSku.cpp` von `\Bookstore\Bookstore\Generated Files\sources\` in den Projektordner `\Bookstore\Bookstore\`.</span><span class="sxs-lookup"><span data-stu-id="dde11-143">Copy the stub files `BookSku.h` and `BookSku.cpp` from `\Bookstore\Bookstore\Generated Files\sources\` into the project folder, which is `\Bookstore\Bookstore\`.</span></span> <span data-ttu-id="dde11-144">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="dde11-144">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="dde11-145">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="dde11-145">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-booksku"></a><span data-ttu-id="dde11-146">Implementieren von **BookSku**</span><span class="sxs-lookup"><span data-stu-id="dde11-146">Implement **BookSku**</span></span>
<span data-ttu-id="dde11-147">Nun öffnen wir `\Bookstore\Bookstore\BookSku.h` und `BookSku.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="dde11-147">Now, let's open `\Bookstore\Bookstore\BookSku.h` and `BookSku.cpp` and implement our runtime class.</span></span> <span data-ttu-id="dde11-148">Fügen Sie in `BookSku.h` einen Konstruktor hinzu, der ein [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Argument (ein privates Mitglied zum Speichern des Titels) und eine weiteres für das bei einer Titeländerung ausgelöste Ereignis entgegen nimmt.</span><span class="sxs-lookup"><span data-stu-id="dde11-148">In `BookSku.h`, add a constructor that takes a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring), a private member to store the title string, and another for the event that we'll raise when the title changes.</span></span> <span data-ttu-id="dde11-149">Nachdem Sie diese Änderungen vorgenommen haben Ihre `BookSku.h` wird wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="dde11-149">After making these changes, your `BookSku.h` will look like this.</span></span>

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

        winrt::hstring Title();
        void Title(winrt::hstring const& value);
        winrt::event_token PropertyChanged(Windows::UI::Xaml::Data::PropertyChangedEventHandler const& value);
        void PropertyChanged(winrt::event_token const& token);
    
    private:
        winrt::hstring m_title;
        winrt::event<Windows::UI::Xaml::Data::PropertyChangedEventHandler> m_propertyChanged;
    };
}
```

<span data-ttu-id="dde11-150">Implementieren Sie in `BookSku.cpp` die Funktionen wie folgt.</span><span class="sxs-lookup"><span data-stu-id="dde11-150">In `BookSku.cpp`, implement the functions like this.</span></span>

```cppwinrt
// BookSku.cpp
#include "pch.h"
#include "BookSku.h"

namespace winrt::Bookstore::implementation
{
    BookSku::BookSku(winrt::hstring const& title) : m_title{ title }
    {
    }

    winrt::hstring BookSku::Title()
    {
        return m_title;
    }

    void BookSku::Title(winrt::hstring const& value)
    {
        if (m_title != value)
        {
            m_title = value;
            m_propertyChanged(*this, Windows::UI::Xaml::Data::PropertyChangedEventArgs{ L"Title" });
        }
    }

    winrt::event_token BookSku::PropertyChanged(Windows::UI::Xaml::Data::PropertyChangedEventHandler const& handler)
    {
        return m_propertyChanged.add(handler);
    }

    void BookSku::PropertyChanged(winrt::event_token const& token)
    {
        m_propertyChanged.remove(token);
    }
}
```

<span data-ttu-id="dde11-151">In der **Titel** Mutator-Funktion überprüfen wir, ob ein Wert festgelegt wird, die sich vom aktuellen Wert unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="dde11-151">In the **Title** mutator function, we check whether a value is being set that's different from the current value.</span></span> <span data-ttu-id="dde11-152">Und wenn Ja, wir aktualisieren den Titel und ebenfalls mit einem Argument gleich auf den Namen der Eigenschaft, die geändert wurde das [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) -Ereignis auslösen.</span><span class="sxs-lookup"><span data-stu-id="dde11-152">And, if so, we update the title and also raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event with an argument equal to the name of the property that has changed.</span></span> <span data-ttu-id="dde11-153">Dies dient dazu, dass die Benutzeroberfläche (UI) erkennt, welcher Eigenschaftswert erneut abgefragt werden muss.</span><span class="sxs-lookup"><span data-stu-id="dde11-153">This is so that the user-interface (UI) will know which property's value to re-query.</span></span>

## <a name="declare-and-implement-bookstoreviewmodel"></a><span data-ttu-id="dde11-154">**BookstoreViewModel** deklarieren und implementieren</span><span class="sxs-lookup"><span data-stu-id="dde11-154">Declare and implement **BookstoreViewModel**</span></span>
<span data-ttu-id="dde11-155">Unsere XAML-Hauptseite wird sich an ein Hauptansichtsmodell gebunden.</span><span class="sxs-lookup"><span data-stu-id="dde11-155">Our main XAML page is going to bind to a main view model.</span></span> <span data-ttu-id="dde11-156">Dieses Ansichtsmodell wird mehrere Eigenschaften haben, darunter eine vom Typ **BookSku**.</span><span class="sxs-lookup"><span data-stu-id="dde11-156">And that view model is going to have several properties, including one of type **BookSku**.</span></span> <span data-ttu-id="dde11-157">In diesem Schritt deklarieren und implementieren wir unsere Hauptansichtsmodell-Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="dde11-157">In this step, we'll declare and implement our main view model runtime class.</span></span>

<span data-ttu-id="dde11-158">Fügen Sie eine neue **Midl-Datei (.idl)** mit dem Namen `BookstoreViewModel.idl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="dde11-158">Add a new **Midl File (.idl)** item named `BookstoreViewModel.idl`.</span></span>

```idl
// BookstoreViewModel.idl
import "BookSku.idl";

namespace Bookstore
{
    runtimeclass BookstoreViewModel
    {
        BookSku BookSku{ get; };
    }
}
```

<span data-ttu-id="dde11-159">Speichern und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="dde11-159">Save and build.</span></span> <span data-ttu-id="dde11-160">Kopieren Sie `BookstoreViewModel.h` und `BookstoreViewModel.cpp` aus dem `Generated Files`-Ordner in den Projektordner und nehmen Sie sie in das Projekt auf.</span><span class="sxs-lookup"><span data-stu-id="dde11-160">Copy `BookstoreViewModel.h` and `BookstoreViewModel.cpp` from the `Generated Files` folder into the project folder, and include them in the project.</span></span> <span data-ttu-id="dde11-161">Öffnen Sie die Dateien und implementieren Sie die Common Language Runtime-Klasse, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="dde11-161">Open those files and implement the runtime class as shown below.</span></span> <span data-ttu-id="dde11-162">Hinweis wie in `BookstoreViewModel.h`, wir sind einschließlich `BookSku.h`, die den Implementierungstyp (**Winrt::Bookstore::implementation::BookSku**) deklariert.</span><span class="sxs-lookup"><span data-stu-id="dde11-162">Note how, in `BookstoreViewModel.h`, we're including `BookSku.h`, which declares the implementation type (**winrt::Bookstore::implementation::BookSku**).</span></span> <span data-ttu-id="dde11-163">Und wir sind mit dem Standardkonstruktor Wiederherstellen von durch Entfernen von `= delete`.</span><span class="sxs-lookup"><span data-stu-id="dde11-163">And we're restoring the default constructor by removing `= delete`.</span></span>

```cppwinrt
// BookstoreViewModel.h
#pragma once

#include "BookstoreViewModel.g.h"
#include "BookSku.h"

namespace winrt::Bookstore::implementation
{
    struct BookstoreViewModel final : BookstoreViewModelT<BookstoreViewModel>
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
> <span data-ttu-id="dde11-164">Der Typ von `m_bookSku` ist der projizierte Typ (**winrt::Bookstore::BookSku**), und der Template-Parameter, den Sie mit **make** verwenden, ist der Implementierungstyp (**winrt::Bookstore::implementation::BookSku**).</span><span class="sxs-lookup"><span data-stu-id="dde11-164">The type of `m_bookSku` is the projected type (**winrt::Bookstore::BookSku**), and the template parameter that you use with **make** is the implementation type (**winrt::Bookstore::implementation::BookSku**).</span></span> <span data-ttu-id="dde11-165">Dennoch gibt **make** eine Instanz des projizierten Typs zurück.</span><span class="sxs-lookup"><span data-stu-id="dde11-165">Even so, **make** returns an instance of the projected type.</span></span>

## <a name="add-a-property-of-type-bookstoreviewmodel-to-mainpage"></a><span data-ttu-id="dde11-166">Hinzufügen einer Eigenschaft vom Typ **BookstoreViewModel** zu **MainPage**</span><span class="sxs-lookup"><span data-stu-id="dde11-166">Add a property of type **BookstoreViewModel** to **MainPage**</span></span>
<span data-ttu-id="dde11-167">Öffnen Sie `MainPage.idl` (unsere Haupt-UI-Seite) mit der Deklaration der Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="dde11-167">Open `MainPage.idl`, which declares the runtime class that represents our main UI page.</span></span> <span data-ttu-id="dde11-168">Fügen Sie eine Import-Anweisung zum Import von `BookstoreViewModel.idl` hinzu und fügen Sie eine schreibgeschützte Eigenschaft namens MainViewModel vom Typ **BookstoreViewModel** hinzu.</span><span class="sxs-lookup"><span data-stu-id="dde11-168">Add an import statement to import `BookstoreViewModel.idl`, and add a read-only property named MainViewModel of type **BookstoreViewModel**.</span></span> <span data-ttu-id="dde11-169">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-169">Also remove the **MyProperty** property.</span></span> <span data-ttu-id="dde11-170">Beachten Sie außerdem die `import` Richtlinie in der Liste unten.</span><span class="sxs-lookup"><span data-stu-id="dde11-170">Also note the `import` directive in the listing below.</span></span>

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

<span data-ttu-id="dde11-171">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="dde11-171">Save the file.</span></span> <span data-ttu-id="dde11-172">Erstellen Sie das Projekt wird nicht erfolgreich abgeschlossen, in dem Moment, aber jetzt erstellen, ist ein sinnvoll, da es die Quellcodedateien generiert in der **MainPage** -Runtime-Klasse implementiert wird (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` und `MainPage.cpp`).</span><span class="sxs-lookup"><span data-stu-id="dde11-172">The project won't build to completion at the moment, but building now is a useful thing to do because it regenerates the source code files in which the **MainPage** runtime class is implemented (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` and `MainPage.cpp`).</span></span> <span data-ttu-id="dde11-173">Also nun und jetzt erstellen.</span><span class="sxs-lookup"><span data-stu-id="dde11-173">So go ahead and build now.</span></span> <span data-ttu-id="dde11-174">Ist der Fehler beim Erstellen Sie erwarten können, in dieser Phase finden Sie unter **'MainViewModel': ist kein Mitglied von 'Winrt::Bookstore::implementation::MainPage'**.</span><span class="sxs-lookup"><span data-stu-id="dde11-174">The build error you can expect to see at this stage is **'MainViewModel': is not a member of 'winrt::Bookstore::implementation::MainPage'**.</span></span>

<span data-ttu-id="dde11-175">Wenn Sie die einschließen von weglassen `BookstoreViewModel.idl` (finden Sie in der Liste der `MainPage.idl` oben), und klicken Sie dann die Fehlermeldung angezeigt wird **erwartet \ < near "MainViewModel"**.</span><span class="sxs-lookup"><span data-stu-id="dde11-175">If you omit the include of `BookstoreViewModel.idl` (see the listing of `MainPage.idl` above), then you'll see the error **expecting \< near "MainViewModel"**.</span></span> <span data-ttu-id="dde11-176">Ein weiterer Tipp ist, um sicherzustellen, dass Sie alle Typen im gleichen Namespace lassen: der Namespace, der in der Codebeispiele angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dde11-176">Another tip is to make sure that you leave all types in the same namespace: the namespace that's shown in the code listings.</span></span>

<span data-ttu-id="dde11-177">Zum Beheben des Fehlers, die wir finden Sie unter erwarten Sie jetzt müssen die Accessor Stubs für die **MainViewModel** -Eigenschaft aus der die generierten Dateien kopieren (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` und `MainPage.cpp`) und in `\Bookstore\Bookstore\MainPage.h` und `MainPage.cpp`.</span><span class="sxs-lookup"><span data-stu-id="dde11-177">To resolve the error that we expect to see, you'll now need to copy the accessor stubs for the **MainViewModel** property out of the generated files (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` and `MainPage.cpp`) and into `\Bookstore\Bookstore\MainPage.h` and `MainPage.cpp`.</span></span>

<span data-ttu-id="dde11-178">In `\Bookstore\Bookstore\MainPage.h`, umfassen `BookstoreViewModel.h`, die den Implementierungstyp (**Winrt::Bookstore::implementation::BookstoreViewModel**) deklariert.</span><span class="sxs-lookup"><span data-stu-id="dde11-178">In `\Bookstore\Bookstore\MainPage.h`, include `BookstoreViewModel.h`, which declares the implementation type (**winrt::Bookstore::implementation::BookstoreViewModel**).</span></span> <span data-ttu-id="dde11-179">Fügen Sie einen privaten Member, um das Ansichtsmodell zu speichern.</span><span class="sxs-lookup"><span data-stu-id="dde11-179">Add a private member to store the view model.</span></span> <span data-ttu-id="dde11-180">Beachten Sie, dass die Zugriffsfunktion für die Eigenschaft (und das Mitglied m_mainViewModel) als **Bookstore::BookstoreViewModel** (dem projizierten Typ) implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="dde11-180">Note that the property accessor function (and the member m_mainViewModel) is implemented in terms of **Bookstore::BookstoreViewModel**, which is the projected type.</span></span> <span data-ttu-id="dde11-181">Der Implementierungstyp in einem Projekt (Kompilierung Unit) wie die Anwendung ist, sodass wir M_mainViewModel über den Konstruktorüberladung erstellen, die akzeptiert `nullptr_t`.</span><span class="sxs-lookup"><span data-stu-id="dde11-181">The implementation type is in the same project (compilation unit) as the application, so we construct m_mainViewModel via the constructor overload that takes `nullptr_t`.</span></span> <span data-ttu-id="dde11-182">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-182">Also remove the **MyProperty** property.</span></span>

```cppwinrt
// MainPage.h
...
#include "BookstoreViewModel.h"
...
namespace winrt::Bookstore::implementation
{
    struct MainPage : MainPageT<MainPage>
    {
        MainPage();

        Bookstore::BookstoreViewModel MainViewModel();

        void ClickHandler(Windows::Foundation::IInspectable const&, Windows::UI::Xaml::RoutedEventArgs const&);

    private:
        Bookstore::BookstoreViewModel m_mainViewModel{ nullptr };
    };
}
...
```

<span data-ttu-id="dde11-183">In `\Bookstore\Bookstore\MainPage.cpp`, [**winrt::make**](/uwp/cpp-ref-for-winrt/make) (mit der Implementierungstyp) aufrufen, um eine neue Instanz des Typs voraussichtliche M_mainViewModel zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="dde11-183">In `\Bookstore\Bookstore\MainPage.cpp`, call [**winrt::make**](/uwp/cpp-ref-for-winrt/make) (with the implementation type) to assign a new instance of the projected type to m_mainViewModel.</span></span> <span data-ttu-id="dde11-184">Weisen Sie einen Initialwert für den Titel des Buches zu.</span><span class="sxs-lookup"><span data-stu-id="dde11-184">Assign an initial value for the book's title.</span></span> <span data-ttu-id="dde11-185">Implementieren Sie die Zugriffsfunktion für die MainViewModel-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-185">Implement the accessor for the MainViewModel property.</span></span> <span data-ttu-id="dde11-186">Aktualisieren Sie zum Schluss den Titel des Buches im Event-Handler der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="dde11-186">And finally, update the book's title in the button's event handler.</span></span> <span data-ttu-id="dde11-187">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-187">Also remove the **MyProperty** property.</span></span>

```cppwinrt
// MainPage.cpp
#include "pch.h"
#include "MainPage.h"

using namespace winrt;
using namespace Windows::UI::Xaml;

namespace winrt::Bookstore::implementation
{
    MainPage::MainPage()
    {
        m_mainViewModel = make<Bookstore::implementation::BookstoreViewModel>();
        InitializeComponent();
    }

    void MainPage::ClickHandler(Windows::Foundation::IInspectable const& /* sender */, Windows::UI::Xaml::RoutedEventArgs const& /* args */)
    {
        MainViewModel().BookSku().Title(L"To Kill a Mockingbird");
    }

    Bookstore::BookstoreViewModel MainPage::MainViewModel()
    {
        return m_mainViewModel;
    }
}
```

## <a name="bind-the-button-to-the-title-property"></a><span data-ttu-id="dde11-188">Binden Sie die Schaltfläche an die **Title**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="dde11-188">Bind the button to the **Title** property</span></span>
<span data-ttu-id="dde11-189">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="dde11-189">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="dde11-190">Wie in der folgenden Auflistung dargestellt, entfernen Sie den Namen der Schaltfläche aus, und ändern Sie dessen Wert der **Content** -Eigenschaft von Literal in eine Bindungsausdruck.</span><span class="sxs-lookup"><span data-stu-id="dde11-190">As shown in the listing below, remove the name from the button, and change its **Content** property value from a literal to a binding expression.</span></span> <span data-ttu-id="dde11-191">Beachten Sie die Eigenschaft `Mode=OneWay` des Bindungsausdrucks (einseitig vom Ansichtsmodell zum UI).</span><span class="sxs-lookup"><span data-stu-id="dde11-191">Note the `Mode=OneWay` property on the binding expression (one-way from the view model to the UI).</span></span> <span data-ttu-id="dde11-192">Ohne diese Eigenschaft reagiert die Benutzeroberfläche nicht auf Ereignisse zu Eigenschaftsänderungen.</span><span class="sxs-lookup"><span data-stu-id="dde11-192">Without that property, the UI will not respond to property changed events.</span></span>

```xaml
<Button Click="ClickHandler" Content="{x:Bind MainViewModel.BookSku.Title, Mode=OneWay}"/>
```

<span data-ttu-id="dde11-193">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="dde11-193">Now build and run the project.</span></span> <span data-ttu-id="dde11-194">Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen.</span><span class="sxs-lookup"><span data-stu-id="dde11-194">Click the button to execute the **Click** event handler.</span></span> <span data-ttu-id="dde11-195">Dieser Handler ruft die Zugriffsfunktion des Buches auf; diese Zugriffsfunktion löst ein Ereignis aus, um die Benutzeroberfläche wissen zu lassen, dass sich die **Title**-Eigenschaft geändert hat; die Schaltfläche fragt den Wert dieser Eigenschaft erneut ab, um ihren eigenen **Content**-Wert zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dde11-195">That handler calls the book's title mutator function; that mutator raises an event to let the UI know that the **Title** property has changed; and the button re-queries that property's value to update its own **Content** value.</span></span>

## <a name="using-the-binding-markup-extension-with-cwinrt"></a><span data-ttu-id="dde11-196">Verwenden die Erweiterung {Binding} Markup mit C + / WinRT</span><span class="sxs-lookup"><span data-stu-id="dde11-196">Using the {Binding} markup extension with C++/WinRT</span></span>
<span data-ttu-id="dde11-197">Für die derzeit endgültige Produktversion von C + / WinRT, damit werden die {Binding} Markup-Erweiterung verwenden, Sie die [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) und [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) Schnittstellen implementieren müssen, können.</span><span class="sxs-lookup"><span data-stu-id="dde11-197">For the currently released version of C++/WinRT, in order to be able to use the {Binding} markup extension you'll need to implement the [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) and [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) interfaces.</span></span>

## <a name="important-apis"></a><span data-ttu-id="dde11-198">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="dde11-198">Important APIs</span></span>
* [<span data-ttu-id="dde11-199">INotifyPropertyChanged::PropertyChanged</span><span class="sxs-lookup"><span data-stu-id="dde11-199">INotifyPropertyChanged::PropertyChanged</span></span>](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged)
* [<span data-ttu-id="dde11-200">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="dde11-200">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a><span data-ttu-id="dde11-201">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="dde11-201">Related topics</span></span>
* [<span data-ttu-id="dde11-202">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="dde11-202">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="dde11-203">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="dde11-203">Author APIs with C++/WinRT</span></span>](author-apis.md)
