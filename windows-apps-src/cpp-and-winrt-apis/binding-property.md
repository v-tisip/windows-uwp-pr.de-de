---
author: stevewhims
description: Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *Observable*-Eigenschaft bezeichnet. Dieses Thema zeigt, wie man eine Observable-Eigenschaft implementiert und nutzt und wie man ein XAML-Steuerelement daran bindet.
title: XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft
ms.author: stwhi
ms.date: 08/21/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, binden, eigenschaft
ms.localizationpriority: medium
ms.openlocfilehash: 6b7c20e0e6cf56afa7e2193739401bf49e0403a2
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6996257"
---
# <a name="xaml-controls-bind-to-a-cwinrt-property"></a><span data-ttu-id="b563f-105">XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b563f-105">XAML controls; bind to a C++/WinRT property</span></span>
<span data-ttu-id="b563f-106">Eine Eigenschaft, die effektiv an ein XAML-Steuerelement gebunden werden kann, wird als *observable*-Eigenschaft bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b563f-106">A property that can be effectively bound to a XAML control is known as an *observable* property.</span></span> <span data-ttu-id="b563f-107">Dieses Konzept basiert auf dem Software-Design-Muster, das als *Observer-Pattern* bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="b563f-107">This idea is based on the software design pattern known as the *observer pattern*.</span></span> <span data-ttu-id="b563f-108">Dieses Thema zeigt, wie Sie Observable-Eigenschaften in implementieren [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), und wie man XAML-Steuerelemente an diese bindet.</span><span class="sxs-lookup"><span data-stu-id="b563f-108">This topic shows how to implement observable properties in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), and how to bind XAML controls to them.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b563f-109">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="b563f-109">For essential concepts and terms that support your understanding of how to consume and author runtime classes with C++/WinRT, see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

## <a name="what-does-observable-mean-for-a-property"></a><span data-ttu-id="b563f-110">Was bedeutet *observable* für eine Eigenschaft?</span><span class="sxs-lookup"><span data-stu-id="b563f-110">What does *observable* mean for a property?</span></span>
<span data-ttu-id="b563f-111">Angenommen, eine Laufzeitklasse namens **BookSku** hat eine Eigenschaft namens **Title**.</span><span class="sxs-lookup"><span data-stu-id="b563f-111">Let's say that a runtime class named **BookSku** has a property named **Title**.</span></span> <span data-ttu-id="b563f-112">Wenn **BookSku** das Ereignis [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) auslöst, wenn sich der Wert von **Title** ändert, dann ist **Title** eine Observable-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-112">If **BookSku** chooses to raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event whenever the value of **Title** changes, then **Title** is an observable property.</span></span> <span data-ttu-id="b563f-113">Es ist das Verhalten von **BookSku** (Auslösen oder nicht Auslösen des Ereignisses), das bestimmt, welche seiner Eigenschaften Observable-Eigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="b563f-113">It's the behavior of **BookSku** (raising or not raising the event) that determines which, if any, of its properties are observable.</span></span>

<span data-ttu-id="b563f-114">Ein XAML-Textelement oder -Steuerelement kann sich an diese Ereignisse binden und sie verarbeiten, indem es den/die aktualisierten Wert(e) abruft und dann eine Aktualisierung durchführt, um den neuen Wert anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b563f-114">A XAML text element, or control, can bind to, and handle, these events by retrieving the updated value(s) and then updating itself to show the new value.</span></span>

> [!NOTE]
> <span data-ttu-id="b563f-115">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="b563f-115">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="create-a-blank-app-bookstore"></a><span data-ttu-id="b563f-116">Erstellen einer leeren App (Bookstore)</span><span class="sxs-lookup"><span data-stu-id="b563f-116">Create a Blank App (Bookstore)</span></span>
<span data-ttu-id="b563f-117">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b563f-117">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="b563f-118">Erstellen Sie ein **Visual C++** > **Universelle Windows-** > **leere App (C++ / WinRT)** Projekt und nennen Sie es *Bookstore*.</span><span class="sxs-lookup"><span data-stu-id="b563f-118">Create a **Visual C++** > **Windows Universal** > **Blank App (C++/WinRT)** project, and name it *Bookstore*.</span></span>

<span data-ttu-id="b563f-119">Wir werden eine neue Klasse schreiben, um ein Buch mit einer Observable-Eigenschaft namens „Titel” darzustellen.</span><span class="sxs-lookup"><span data-stu-id="b563f-119">We're going to author a new class to represent a book that has an observable title property.</span></span> <span data-ttu-id="b563f-120">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="b563f-120">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="b563f-121">Aber wir wollen in der Lage sein, aus XAML eine Bindung an diese Klasse zu nutzen. Daher wird es eine Laufzeitklasse sein.</span><span class="sxs-lookup"><span data-stu-id="b563f-121">But we want to be able to bind to this class from XAML, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="b563f-122">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="b563f-122">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="b563f-123">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b563f-123">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="b563f-124">Nennen Sie es `BookSku.idl`.</span><span class="sxs-lookup"><span data-stu-id="b563f-124">Name it `BookSku.idl`.</span></span> <span data-ttu-id="b563f-125">Löschen Sie den Standardinhalt von `BookSku.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="b563f-125">Delete the default contents of `BookSku.idl`, and paste in this runtime class declaration.</span></span>

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
> <span data-ttu-id="b563f-126">Ihre Ansichtsmodell-Klassen&mdash;in der Tat, jede Laufzeitklasse, die Sie in Ihrer Anwendung deklarieren&mdash;müssen nicht von einer Basisklasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="b563f-126">Your view model classes&mdash;in fact, any runtime class that you declare in your application&mdash;need not derive from a base class.</span></span> <span data-ttu-id="b563f-127">Die oben deklarierte **BookSku** -Klasse ist ein Beispiel für die.</span><span class="sxs-lookup"><span data-stu-id="b563f-127">The **BookSku** class declared above is an example of that.</span></span> <span data-ttu-id="b563f-128">Es eine Schnittstelle implementiert, aber sie nicht von einer Basisklasse abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="b563f-128">It implements an interface, but it doesn't derive from any base class.</span></span>
>
> <span data-ttu-id="b563f-129">Laufzeitklasse, die Sie in der Anwendung deklarieren, *wird* von Basis abgeleitet Klasse genannt wird eine *zusammensetzbaren* Klasse.</span><span class="sxs-lookup"><span data-stu-id="b563f-129">Any runtime class that you declare in the application that *does* derive from a base class is known as a *composable* class.</span></span> <span data-ttu-id="b563f-130">Und es gibt Einschränkungen um zusammensetzbaren Klassen.</span><span class="sxs-lookup"><span data-stu-id="b563f-130">And there are constraints around composable classes.</span></span> <span data-ttu-id="b563f-131">Damit eine Anwendung die [Zertifizierungskit für Windows-App](../debug-test-perf/windows-app-certification-kit.md) -Tests von Visual Studio und vom Microsoft Store verwendet, um Übermittlungen zu überprüfen (und daher für die Anwendung erfolgreich in den Microsoft Store aufgenommen werden), müssen Sie eine zusammensetzbare-Klasse letztlich von einem Windows-Basisklasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="b563f-131">For an application to pass the [Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md) tests used by Visual Studio and by the Microsoft Store to validate submissions (and therefore for the application to be successfully ingested into the Microsoft Store), a composable class must ultimately derive from a Windows base class.</span></span> <span data-ttu-id="b563f-132">Dies bedeutet, dass die Klasse im sehr Stammverzeichnis der Vererbungshierarchie ein Typ sein, in einem Windows-Namespace sein muss.</span><span class="sxs-lookup"><span data-stu-id="b563f-132">Meaning that the class at the very root of the inheritance hierarchy must be a type originating in a Windows.\* namespace.</span></span> <span data-ttu-id="b563f-133">Wenn Sie eine Laufzeitklasse von einer Basisklasse abgeleitet benötigen&mdash;z. B. implementieren eine Klasse **BindableBase** für alle Ihre Ansichtsmodelle Ableiten von&mdash;dann [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject)abgeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="b563f-133">If you do need to derive a runtime class from a base class&mdash;for example, to implement a **BindableBase** class for all of your view models to derive from&mdash;then you can derive from [**Windows.UI.Xaml.DependencyObject**](/uwp/api/windows.ui.xaml.dependencyobject).</span></span>
>
> <span data-ttu-id="b563f-134">Ein Ansichtsmodell ist eine Abstraktion einer Ansicht und ist daher direkt an die Ansicht (das XAML-Markup) gebunden.</span><span class="sxs-lookup"><span data-stu-id="b563f-134">A view model is an abstraction of a view, and so it's bound directly to the view (the XAML markup).</span></span> <span data-ttu-id="b563f-135">Ein Datenmodell ist eine Abstraktion von Daten, und er nur in Ihren Ansichtsmodellen genutzt, und nicht direkt mit XAML gebunden.</span><span class="sxs-lookup"><span data-stu-id="b563f-135">A data model is an abstraction of data, and it's consumed only from your view models, and not bound directly to XAML.</span></span> <span data-ttu-id="b563f-136">Daher können Sie Ihre Datenmodelle nicht als-Runtime-Klassen, sondern als C++ Strukturen oder Klassen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="b563f-136">So, you can declare your data models not as runtime classes, but as C++ structs or classes.</span></span> <span data-ttu-id="b563f-137">Sie müssen nicht in MIDL deklariert werden, und Sie können den Vererbungshierarchie verwenden Sie, wie.</span><span class="sxs-lookup"><span data-stu-id="b563f-137">They don't need to be declared in MIDL, and you're free to use whatever inheritance hierarchy you like.</span></span>

<span data-ttu-id="b563f-138">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="b563f-138">Save the file and build the project.</span></span> <span data-ttu-id="b563f-139">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="b563f-139">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\Bookstore\Debug\Bookstore\Unmerged\BookSku.winmd`) describing the runtime class.</span></span> <span data-ttu-id="b563f-140">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b563f-140">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="b563f-141">Diese Dateien enthalten Stubs, um mit der Implementierung der **BookSku**-Laufzeitklasse zu beginnen, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="b563f-141">These files include stubs to get you started implementing the **BookSku** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="b563f-142">Diese Stubs sind `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` und `BookSku.cpp`.</span><span class="sxs-lookup"><span data-stu-id="b563f-142">Those stubs are `\Bookstore\Bookstore\Generated Files\sources\BookSku.h` and `BookSku.cpp`.</span></span>

<span data-ttu-id="b563f-143">Kopieren Sie die Stub-Dateien `BookSku.h` und `BookSku.cpp` von `\Bookstore\Bookstore\Generated Files\sources\` in den Projektordner `\Bookstore\Bookstore\`.</span><span class="sxs-lookup"><span data-stu-id="b563f-143">Copy the stub files `BookSku.h` and `BookSku.cpp` from `\Bookstore\Bookstore\Generated Files\sources\` into the project folder, which is `\Bookstore\Bookstore\`.</span></span> <span data-ttu-id="b563f-144">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b563f-144">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="b563f-145">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="b563f-145">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-booksku"></a><span data-ttu-id="b563f-146">Implementieren von **BookSku**</span><span class="sxs-lookup"><span data-stu-id="b563f-146">Implement **BookSku**</span></span>
<span data-ttu-id="b563f-147">Nun öffnen wir `\Bookstore\Bookstore\BookSku.h` und `BookSku.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="b563f-147">Now, let's open `\Bookstore\Bookstore\BookSku.h` and `BookSku.cpp` and implement our runtime class.</span></span> <span data-ttu-id="b563f-148">Fügen Sie in `BookSku.h` einen Konstruktor hinzu, der ein [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Argument (ein privates Mitglied zum Speichern des Titels) und eine weiteres für das bei einer Titeländerung ausgelöste Ereignis entgegen nimmt.</span><span class="sxs-lookup"><span data-stu-id="b563f-148">In `BookSku.h`, add a constructor that takes a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring), a private member to store the title string, and another for the event that we'll raise when the title changes.</span></span> <span data-ttu-id="b563f-149">Nachdem Sie diese geändert, Ihre `BookSku.h` sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="b563f-149">After making these changes, your `BookSku.h` will look like this.</span></span>

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

<span data-ttu-id="b563f-150">Implementieren Sie in `BookSku.cpp` die Funktionen wie folgt.</span><span class="sxs-lookup"><span data-stu-id="b563f-150">In `BookSku.cpp`, implement the functions like this.</span></span>

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

<span data-ttu-id="b563f-151">In der **Titelleiste** Zugriffsfunktion überprüfen wir, ob ein Wert festgelegt wird, die von den aktuellen Wert unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="b563f-151">In the **Title** mutator function, we check whether a value is being set that's different from the current value.</span></span> <span data-ttu-id="b563f-152">Und wenn dies der Fall ist, wir aktualisieren die Titel und ebenfalls Auslösen des Ereignisses [**INotifyPropertyChanged:: PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) mit einem Argument gleich dem Namen der Eigenschaft, die geändert hat.</span><span class="sxs-lookup"><span data-stu-id="b563f-152">And, if so, we update the title and also raise the [**INotifyPropertyChanged::PropertyChanged**](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged) event with an argument equal to the name of the property that has changed.</span></span> <span data-ttu-id="b563f-153">Dies dient dazu, dass die Benutzeroberfläche (UI) erkennt, welcher Eigenschaftswert erneut abgefragt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b563f-153">This is so that the user-interface (UI) will know which property's value to re-query.</span></span>

## <a name="declare-and-implement-bookstoreviewmodel"></a><span data-ttu-id="b563f-154">**BookstoreViewModel** deklarieren und implementieren</span><span class="sxs-lookup"><span data-stu-id="b563f-154">Declare and implement **BookstoreViewModel**</span></span>
<span data-ttu-id="b563f-155">Unsere XAML-Hauptseite wird sich an ein Hauptansichtsmodell gebunden.</span><span class="sxs-lookup"><span data-stu-id="b563f-155">Our main XAML page is going to bind to a main view model.</span></span> <span data-ttu-id="b563f-156">Dieses Ansichtsmodell wird mehrere Eigenschaften haben, darunter eine vom Typ **BookSku**.</span><span class="sxs-lookup"><span data-stu-id="b563f-156">And that view model is going to have several properties, including one of type **BookSku**.</span></span> <span data-ttu-id="b563f-157">In diesem Schritt deklarieren und implementieren wir unsere Hauptansichtsmodell-Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="b563f-157">In this step, we'll declare and implement our main view model runtime class.</span></span>

<span data-ttu-id="b563f-158">Fügen Sie eine neue **Midl-Datei (.idl)** mit dem Namen `BookstoreViewModel.idl` hinzu.</span><span class="sxs-lookup"><span data-stu-id="b563f-158">Add a new **Midl File (.idl)** item named `BookstoreViewModel.idl`.</span></span>

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

<span data-ttu-id="b563f-159">Speichern und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="b563f-159">Save and build.</span></span> <span data-ttu-id="b563f-160">Kopieren Sie `BookstoreViewModel.h` und `BookstoreViewModel.cpp` aus dem `Generated Files`-Ordner in den Projektordner und nehmen Sie sie in das Projekt auf.</span><span class="sxs-lookup"><span data-stu-id="b563f-160">Copy `BookstoreViewModel.h` and `BookstoreViewModel.cpp` from the `Generated Files` folder into the project folder, and include them in the project.</span></span> <span data-ttu-id="b563f-161">Öffnen Sie diese Dateien und implementieren Sie die Laufzeitklasse aus, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b563f-161">Open those files and implement the runtime class as shown below.</span></span> <span data-ttu-id="b563f-162">Hinweis: wie im `BookstoreViewModel.h`, wir sind einschließlich `BookSku.h`, der Deklaration des Implementierungstyps (**Winrt::Bookstore::implementation::BookSku**).</span><span class="sxs-lookup"><span data-stu-id="b563f-162">Note how, in `BookstoreViewModel.h`, we're including `BookSku.h`, which declares the implementation type (**winrt::Bookstore::implementation::BookSku**).</span></span> <span data-ttu-id="b563f-163">Und wir sind Wiederherstellen der Standardkonstruktor durch das Entfernen von `= delete`.</span><span class="sxs-lookup"><span data-stu-id="b563f-163">And we're restoring the default constructor by removing `= delete`.</span></span>

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
        m_bookSku = winrt::make<Bookstore::implementation::BookSku>(L"Atticus");
    }

    Bookstore::BookSku BookstoreViewModel::BookSku()
    {
        return m_bookSku;
    }
}
```

> [!NOTE]
> <span data-ttu-id="b563f-164">Die Art der `m_bookSku` ist der projizierte Typ (**Winrt::Bookstore::BookSku**) und der Template-Parameter, die Sie mit [**WinRT:: Make**](/uwp/cpp-ref-for-winrt/make) verwenden, ist der Implementierungstyp (**Winrt::Bookstore::implementation::BookSku**).</span><span class="sxs-lookup"><span data-stu-id="b563f-164">The type of `m_bookSku` is the projected type (**winrt::Bookstore::BookSku**), and the template parameter that you use with [**winrt::make**](/uwp/cpp-ref-for-winrt/make) is the implementation type (**winrt::Bookstore::implementation::BookSku**).</span></span> <span data-ttu-id="b563f-165">Dennoch gibt **make** eine Instanz des projizierten Typs zurück.</span><span class="sxs-lookup"><span data-stu-id="b563f-165">Even so, **make** returns an instance of the projected type.</span></span>

## <a name="add-a-property-of-type-bookstoreviewmodel-to-mainpage"></a><span data-ttu-id="b563f-166">Hinzufügen einer Eigenschaft vom Typ **BookstoreViewModel** zu **MainPage**</span><span class="sxs-lookup"><span data-stu-id="b563f-166">Add a property of type **BookstoreViewModel** to **MainPage**</span></span>
<span data-ttu-id="b563f-167">Öffnen Sie `MainPage.idl` (unsere Haupt-UI-Seite) mit der Deklaration der Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="b563f-167">Open `MainPage.idl`, which declares the runtime class that represents our main UI page.</span></span> <span data-ttu-id="b563f-168">Fügen Sie eine Import-Anweisung zum Import von `BookstoreViewModel.idl` hinzu und fügen Sie eine schreibgeschützte Eigenschaft namens MainViewModel vom Typ **BookstoreViewModel** hinzu.</span><span class="sxs-lookup"><span data-stu-id="b563f-168">Add an import statement to import `BookstoreViewModel.idl`, and add a read-only property named MainViewModel of type **BookstoreViewModel**.</span></span> <span data-ttu-id="b563f-169">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-169">Also remove the **MyProperty** property.</span></span> <span data-ttu-id="b563f-170">Beachten Sie außerdem die `import` -Direktive in den folgenden Eintrag.</span><span class="sxs-lookup"><span data-stu-id="b563f-170">Also note the `import` directive in the listing below.</span></span>

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

<span data-ttu-id="b563f-171">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="b563f-171">Save the file.</span></span> <span data-ttu-id="b563f-172">Erstellen des Projekts wird nicht bis zum Abschluss im Moment, aber nun erstellen ist hilfreich, etwas zu tun, da es die Quellcodedateien generiert in der **MainPage** -Runtime-Klasse implementiert wird (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` und `MainPage.cpp`).</span><span class="sxs-lookup"><span data-stu-id="b563f-172">The project won't build to completion at the moment, but building now is a useful thing to do because it regenerates the source code files in which the **MainPage** runtime class is implemented (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` and `MainPage.cpp`).</span></span> <span data-ttu-id="b563f-173">So einfach, und erstellen Sie jetzt.</span><span class="sxs-lookup"><span data-stu-id="b563f-173">So go ahead and build now.</span></span> <span data-ttu-id="b563f-174">Der Buildfehler kann angezeigt werden in dieser Phase ist **'MainViewModel': ist kein Mitglied von 'Winrt::Bookstore::implementation::MainPage'**.</span><span class="sxs-lookup"><span data-stu-id="b563f-174">The build error you can expect to see at this stage is **'MainViewModel': is not a member of 'winrt::Bookstore::implementation::MainPage'**.</span></span>

<span data-ttu-id="b563f-175">Wenn Sie das Hinzufügen von weglassen `BookstoreViewModel.idl` (finden Sie unter den Eintrag der `MainPage.idl` oben), und klicken Sie dann den Fehler **erwartet \< in der Nähe "MainViewModel"** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b563f-175">If you omit the include of `BookstoreViewModel.idl` (see the listing of `MainPage.idl` above), then you'll see the error **expecting \< near "MainViewModel"**.</span></span> <span data-ttu-id="b563f-176">Ein weiterer Tipp ist, um sicherzustellen, dass Sie alle Typen im gleichen Namespace lassen: der Namespace, der in der Code-Einträgen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b563f-176">Another tip is to make sure that you leave all types in the same namespace: the namespace that's shown in the code listings.</span></span>

<span data-ttu-id="b563f-177">Um den Fehler zu beheben, die wir angezeigt werden, jetzt müssen Sie die Zugriffs-Stubs für die **MainViewModel** -Eigenschaft aus der generierten Dateien kopieren (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` und `MainPage.cpp`) und in `\Bookstore\Bookstore\MainPage.h` und `MainPage.cpp`.</span><span class="sxs-lookup"><span data-stu-id="b563f-177">To resolve the error that we expect to see, you'll now need to copy the accessor stubs for the **MainViewModel** property out of the generated files (`\Bookstore\Bookstore\Generated Files\sources\MainPage.h` and `MainPage.cpp`) and into `\Bookstore\Bookstore\MainPage.h` and `MainPage.cpp`.</span></span>

<span data-ttu-id="b563f-178">In `\Bookstore\Bookstore\MainPage.h`, gehören `BookstoreViewModel.h`, der Deklaration des Implementierungstyps (**Winrt::Bookstore::implementation::BookstoreViewModel**).</span><span class="sxs-lookup"><span data-stu-id="b563f-178">In `\Bookstore\Bookstore\MainPage.h`, include `BookstoreViewModel.h`, which declares the implementation type (**winrt::Bookstore::implementation::BookstoreViewModel**).</span></span> <span data-ttu-id="b563f-179">Fügen Sie ein privates Mitglied zum Ansichtsmodell zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b563f-179">Add a private member to store the view model.</span></span> <span data-ttu-id="b563f-180">Beachten Sie, dass die Zugriffsfunktion für die Eigenschaft (und das Mitglied m_mainViewModel) als **Bookstore::BookstoreViewModel** (dem projizierten Typ) implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="b563f-180">Note that the property accessor function (and the member m_mainViewModel) is implemented in terms of **Bookstore::BookstoreViewModel**, which is the projected type.</span></span> <span data-ttu-id="b563f-181">Der Implementierungstyp im selben Projekt (Kompilierungseinheit) wie die Anwendung, damit wir M_mainViewModel über der Konstruktorüberladung erstellt, die benötigt wird `nullptr_t`.</span><span class="sxs-lookup"><span data-stu-id="b563f-181">The implementation type is in the same project (compilation unit) as the application, so we construct m_mainViewModel via the constructor overload that takes `nullptr_t`.</span></span> <span data-ttu-id="b563f-182">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-182">Also remove the **MyProperty** property.</span></span>

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

<span data-ttu-id="b563f-183">In `\Bookstore\Bookstore\MainPage.cpp`, rufen Sie [**WinRT:: Make**](/uwp/cpp-ref-for-winrt/make) (mit dem Implementierungstyp), um M_mainViewModel eine neue Instanz des projizierten Typs zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="b563f-183">In `\Bookstore\Bookstore\MainPage.cpp`, call [**winrt::make**](/uwp/cpp-ref-for-winrt/make) (with the implementation type) to assign a new instance of the projected type to m_mainViewModel.</span></span> <span data-ttu-id="b563f-184">Weisen Sie einen Initialwert für den Titel des Buches zu.</span><span class="sxs-lookup"><span data-stu-id="b563f-184">Assign an initial value for the book's title.</span></span> <span data-ttu-id="b563f-185">Implementieren Sie die Zugriffsfunktion für die MainViewModel-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-185">Implement the accessor for the MainViewModel property.</span></span> <span data-ttu-id="b563f-186">Aktualisieren Sie zum Schluss den Titel des Buches im Event-Handler der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="b563f-186">And finally, update the book's title in the button's event handler.</span></span> <span data-ttu-id="b563f-187">Entfernen Sie auch die **MyProperty** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-187">Also remove the **MyProperty** property.</span></span>

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
        m_mainViewModel = winrt::make<Bookstore::implementation::BookstoreViewModel>();
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

## <a name="bind-the-button-to-the-title-property"></a><span data-ttu-id="b563f-188">Binden Sie die Schaltfläche an die **Title**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b563f-188">Bind the button to the **Title** property</span></span>
<span data-ttu-id="b563f-189">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="b563f-189">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="b563f-190">Wie in den Eintrag unten gezeigt, entfernen Sie den Namen von der Schaltfläche, und ändern Sie den **Content** -Eigenschaft-Wert von einem Literal in einen Bindungsausdruck.</span><span class="sxs-lookup"><span data-stu-id="b563f-190">As shown in the listing below, remove the name from the button, and change its **Content** property value from a literal to a binding expression.</span></span> <span data-ttu-id="b563f-191">Beachten Sie die Eigenschaft `Mode=OneWay` des Bindungsausdrucks (einseitig vom Ansichtsmodell zum UI).</span><span class="sxs-lookup"><span data-stu-id="b563f-191">Note the `Mode=OneWay` property on the binding expression (one-way from the view model to the UI).</span></span> <span data-ttu-id="b563f-192">Ohne diese Eigenschaft reagiert die Benutzeroberfläche nicht auf Ereignisse zu Eigenschaftsänderungen.</span><span class="sxs-lookup"><span data-stu-id="b563f-192">Without that property, the UI will not respond to property changed events.</span></span>

```xaml
<Button Click="ClickHandler" Content="{x:Bind MainViewModel.BookSku.Title, Mode=OneWay}"/>
```

<span data-ttu-id="b563f-193">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="b563f-193">Now build and run the project.</span></span> <span data-ttu-id="b563f-194">Klicken Sie auf die Schaltfläche, um den **Click**-Ereignis-Handler auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b563f-194">Click the button to execute the **Click** event handler.</span></span> <span data-ttu-id="b563f-195">Dieser Handler ruft die Zugriffsfunktion des Buches auf; diese Zugriffsfunktion löst ein Ereignis aus, um die Benutzeroberfläche wissen zu lassen, dass sich die **Title**-Eigenschaft geändert hat; die Schaltfläche fragt den Wert dieser Eigenschaft erneut ab, um ihren eigenen **Content**-Wert zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b563f-195">That handler calls the book's title mutator function; that mutator raises an event to let the UI know that the **Title** property has changed; and the button re-queries that property's value to update its own **Content** value.</span></span>

## <a name="using-the-binding-markup-extension-with-cwinrt"></a><span data-ttu-id="b563f-196">Die Markuperweiterung {Binding} mit C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="b563f-196">Using the {Binding} markup extension with C++/WinRT</span></span>
<span data-ttu-id="b563f-197">Für die derzeit veröffentlichte Version von C++ / WinRT, damit eventuell die Markuperweiterung {Binding} verwenden, Sie die [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) und [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) -Schnittstellen implementieren müssen.</span><span class="sxs-lookup"><span data-stu-id="b563f-197">For the currently released version of C++/WinRT, in order to be able to use the {Binding} markup extension you'll need to implement the [ICustomPropertyProvider](/uwp/api/windows.ui.xaml.data.icustompropertyprovider) and [ICustomProperty](/uwp/api/windows.ui.xaml.data.icustomproperty) interfaces.</span></span>

## <a name="important-apis"></a><span data-ttu-id="b563f-198">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="b563f-198">Important APIs</span></span>
* [<span data-ttu-id="b563f-199">INotifyPropertyChanged::PropertyChanged</span><span class="sxs-lookup"><span data-stu-id="b563f-199">INotifyPropertyChanged::PropertyChanged</span></span>](/uwp/api/windows.ui.xaml.data.inotifypropertychanged.PropertyChanged)
* [<span data-ttu-id="b563f-200">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="b563f-200">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)

## <a name="related-topics"></a><span data-ttu-id="b563f-201">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b563f-201">Related topics</span></span>
* [<span data-ttu-id="b563f-202">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="b563f-202">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="b563f-203">Erstellen von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="b563f-203">Author APIs with C++/WinRT</span></span>](author-apis.md)
