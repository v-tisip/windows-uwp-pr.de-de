---
author: stevewhims
description: Dieses Thema zeigt, wie man C++/WinRT-APIs mit Hilfe der **winrt::implements**-Basisstruktur direkt oder indirekt erstellt.
title: Erstellen von APIs mit C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, uwp, Standard, c++, cpp, winrt, projiziert, Projektion, Implementierung, implementieren, Laufzeitklasse, Aktivierung
ms.localizationpriority: medium
ms.openlocfilehash: d613cb87297cdc810e4d8e16dfeb36d4804678d1
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4111542"
---
# <a name="author-apis-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="a32cc-104">Erstellen von APIs mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="a32cc-104">Author APIs with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

> [!NOTE]
> **<span data-ttu-id="a32cc-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="a32cc-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="a32cc-107">Dieses Thema zeigt, wie man C++/WinRT-APIs mit Hilfe der [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements)-Basisstruktur direkt oder indirekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-107">This topic shows how to author C++/WinRT APIs by using the [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) base struct, either directly or indirectly.</span></span> <span data-ttu-id="a32cc-108">In diesem Zusammenhang werden die Synonyme *Produzieren* oder *Implementieren* für den Begriff *Erstellen* verwendet.</span><span class="sxs-lookup"><span data-stu-id="a32cc-108">Synonyms for *author* in this context are *produce*, or *implement*.</span></span> <span data-ttu-id="a32cc-109">Dieses Thema behandelt die folgenden Szenarien für die Implementierung von APIs für einen C++/WinRT-Typ in dieser Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="a32cc-109">This topic covers the following scenarios for implementing APIs on a C++/WinRT type, in this order.</span></span>

- <span data-ttu-id="a32cc-110">Sie erstellen *keine* Windows-Runtime-Klasse (Runtime-Klasse); Sie möchten lediglich eine oder mehrere Windows-Runtime-Schnittstellen für den lokalen Gebrauch in Ihrer App implementieren.</span><span class="sxs-lookup"><span data-stu-id="a32cc-110">You're *not* authoring a Windows Runtime class (runtime class); you just want to implement one or more Windows Runtime interfaces for local consumption within your app.</span></span> <span data-ttu-id="a32cc-111">Sie leiten sich in diesem Fall direkt von **winrt::implements** ab und implementieren Funktionen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-111">You derive directly from **winrt::implements** in this case, and implement functions.</span></span>
- <span data-ttu-id="a32cc-112">Sie schreiben eine *Laufzeitklasse*.</span><span class="sxs-lookup"><span data-stu-id="a32cc-112">You *are* authoring a runtime class.</span></span> <span data-ttu-id="a32cc-113">Möglicherweise erstellen Sie eine Komponente, die von einer App genutzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a32cc-113">You might be authoring a component to be consumed from an app.</span></span> <span data-ttu-id="a32cc-114">Oder Sie erstellen einen Typ, der von der XAML-Benutzeroberfläche (UI) genutzt werden soll, und in diesem Fall implementieren und nutzen Sie sowohl eine Laufzeitklasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="a32cc-114">Or you might be authoring a type to be consumed from XAML user interface (UI), and in that case you're both implementing and consuming a runtime class within the same compilation unit.</span></span> <span data-ttu-id="a32cc-115">In diesen Fällen lassen Sie sich von den Tools Klassen generieren, die von **winrt::implements** abgeleitet sind.</span><span class="sxs-lookup"><span data-stu-id="a32cc-115">In these cases, you let the tools generate classes for you that derive from **winrt::implements**.</span></span>

<span data-ttu-id="a32cc-116">In beiden Fällen wird der Typ, der Ihre C++/WinRT-APIs implementiert, als *Implementierungstyp* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a32cc-116">In both cases, the type that implements your C++/WinRT APIs is called the *implementation type*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a32cc-117">Es ist wichtig, das Konzept eines Implementierungstyps von dem eines projektierten Typs zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="a32cc-117">It's important to distinguish the concept of an implementation type from that of a projected type.</span></span> <span data-ttu-id="a32cc-118">Der projektierte Typ ist in [Verwenden von APIs mit C++/WinRT](consume-apis.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-118">The projected type is described in [Consume APIs with C++/WinRT](consume-apis.md).</span></span>

## <a name="if-youre-not-authoring-a-runtime-class"></a><span data-ttu-id="a32cc-119">Wenn Sie *keine* Laufzeitklasse erstellen</span><span class="sxs-lookup"><span data-stu-id="a32cc-119">If you're *not* authoring a runtime class</span></span>
<span data-ttu-id="a32cc-120">Das einfachste Szenario ist die Implementierung einer Windows-Runtime-Schnittstelle für die lokale Nutzung.</span><span class="sxs-lookup"><span data-stu-id="a32cc-120">The simplest scenario is where you're implementing a Windows Runtime interface for local consumption.</span></span> <span data-ttu-id="a32cc-121">Sie benötigen keine Laufzeitklasse, sondern nur eine normale C++ Klasse.</span><span class="sxs-lookup"><span data-stu-id="a32cc-121">You don't need a runtime class; just an ordinary C++ class.</span></span> <span data-ttu-id="a32cc-122">Beispielsweise können Sie eine App rund um [**CoreApplication**](/uwp/api/windows.applicationmodel.core.coreapplication) schreiben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-122">For example, you might be writing an app based around [**CoreApplication**](/uwp/api/windows.applicationmodel.core.coreapplication).</span></span>

> [!NOTE]
> <span data-ttu-id="a32cc-123">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="a32cc-123">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

<span data-ttu-id="a32cc-124">In Visual Studio, die **Visual C++** > **Universelle Windows-** > **Core App (C++ / WinRT)** Projektvorlage veranschaulicht das **CoreApplication** -Muster.</span><span class="sxs-lookup"><span data-stu-id="a32cc-124">In Visual Studio, the **Visual C++** > **Windows Universal** > **Core App (C++/WinRT)** project template illustrates the **CoreApplication** pattern.</span></span> <span data-ttu-id="a32cc-125">Das Muster beginnt mit der Übergabe einer Implementierung von [**Windows::ApplicationModel::Core::IFrameworkViewSource**](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) an [**CoreApplication::Run**](/uwp/api/windows.applicationmodel.core.coreapplication.run).</span><span class="sxs-lookup"><span data-stu-id="a32cc-125">The pattern begins with passing an implementation of [**Windows::ApplicationModel::Core::IFrameworkViewSource**](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) to [**CoreApplication::Run**](/uwp/api/windows.applicationmodel.core.coreapplication.run).</span></span>

```cppwinrt
using namespace Windows::ApplicationModel::Core;
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    IFrameworkViewSource source = ...
    CoreApplication::Run(source);
}
```

<span data-ttu-id="a32cc-126">**CoreApplication** verwendet die Schnittstelle, um die erste Ansicht der App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-126">**CoreApplication** uses the interface to create the app's first view.</span></span> <span data-ttu-id="a32cc-127">Konzeptionell sieht **IFrameworkViewSource** so aus.</span><span class="sxs-lookup"><span data-stu-id="a32cc-127">Conceptually, **IFrameworkViewSource** looks like this.</span></span>

```cppwinrt
struct IFrameworkViewSource : IInspectable
{
    IFrameworkView CreateView();
};
```

<span data-ttu-id="a32cc-128">Auch hier ist die Implementierung von **CoreApplication::Run** konzeptionell sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="a32cc-128">Again conceptually, the implementation of **CoreApplication::Run** does this.</span></span>

```cppwinrt
void Run(IFrameworkViewSource viewSource) const
{
    IFrameworkView view = viewSource.CreateView();
    ...
}
```

<span data-ttu-id="a32cc-129">Sie als Entwickler implementieren also die Schnittstelle **IFrameworkViewSource**.</span><span class="sxs-lookup"><span data-stu-id="a32cc-129">So you, as the developer, implement the **IFrameworkViewSource** interface.</span></span> <span data-ttu-id="a32cc-130">C++/WinRT beinhaltet das Basisstruktur-Template [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements), um es einfach zu machen, eine Schnittstelle (oder mehrere) zu implementieren, ohne auf eine Programmierung im COM-Stil zurückgreifen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-130">C++/WinRT has the base struct template [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) to make it easy to implement an interface (or several) without resorting to COM-style programming.</span></span> <span data-ttu-id="a32cc-131">Sie leiten Ihren Typ einfach aus **Implementierungen** ab und implementieren dann die Funktionen der Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="a32cc-131">You just derive your type from **implements**, and then implement the interface's functions.</span></span> <span data-ttu-id="a32cc-132">Dies funktioniert so.</span><span class="sxs-lookup"><span data-stu-id="a32cc-132">Here's how.</span></span>

```cppwinrt
// App.cpp
...
struct App : implements<App, IFrameworkViewSource>
{
    IFrameworkView CreateView()
    {
        return ...
    }
}
...
```

<span data-ttu-id="a32cc-133">Das hat sich um **IFrameworkViewSource** gekümmert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-133">That's taken care of **IFrameworkViewSource**.</span></span> <span data-ttu-id="a32cc-134">Im nächsten Schritt wird ein Objekt zurückgegeben, das die Schnittstelle **IFrameworkView** implementiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-134">The next step is to return an object that implements the **IFrameworkView** interface.</span></span> <span data-ttu-id="a32cc-135">Sie können diese Schnittstelle auch für **App** implementieren.</span><span class="sxs-lookup"><span data-stu-id="a32cc-135">You can choose to implement that interface on **App**, too.</span></span> <span data-ttu-id="a32cc-136">Dieses nächste Codebeispiel stellt eine minimale App dar, die zumindest ein Fenster auf dem Desktop öffnet.</span><span class="sxs-lookup"><span data-stu-id="a32cc-136">This next code example represents a minimal app that will at least get a window up and running on the desktop.</span></span>

```cppwinrt
// App.cpp
...
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    IFrameworkView CreateView()
    {
        return *this;
    }

    void Initialize(CoreApplicationView const &) {}

    void Load(hstring const&) {}

    void Run()
    {
        CoreWindow window = CoreWindow::GetForCurrentThread();
        window.Activate();

        CoreDispatcher dispatcher = window.Dispatcher();
        dispatcher.ProcessEvents(CoreProcessEventsOption::ProcessUntilQuit);
    }

    void SetWindow(CoreWindow const & window)
    {
        // Prepare app visuals here
    }

    void Uninitialize() {}
};
...
```

<span data-ttu-id="a32cc-137">Da Ihr **App**-Typ eine **IFrameworkViewSource** *ist*, können Sie einfach eine an **Run** übergeben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-137">Since your **App** type *is an* **IFrameworkViewSource**, you can just pass one to **Run**.</span></span>

```cppwinrt
using namespace Windows::ApplicationModel::Core;
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    CoreApplication::Run(App{});
}
```

## <a name="if-youre-authoring-a-runtime-class-in-a-windows-runtime-component"></a><span data-ttu-id="a32cc-138">Wenn Sie eine Laufzeitklasse in einer Komponente für Windows-Runtime erstellen, gehen Sie wie folgt vor</span><span class="sxs-lookup"><span data-stu-id="a32cc-138">If you're authoring a runtime class in a Windows Runtime Component</span></span>
<span data-ttu-id="a32cc-139">Wenn Ihr Typ in einer Komponente für Windows-Runtime für den Einsatz in einer Anwendung verpackt ist, dann muss es sich um eine Laufzeitklasse handeln.</span><span class="sxs-lookup"><span data-stu-id="a32cc-139">If your type is packaged in a Windows Runtime Component for consumption from an application, then it needs to be a runtime class.</span></span>

> [!TIP]
> <span data-ttu-id="a32cc-140">Wir empfehlen, jede Laufzeitklasse in einer eigenen Interface Definition Language (IDL)-Datei zu deklarieren, um die Buildleistung beim Bearbeiten einer IDL-Datei zu optimieren und um die logische Übereinstimmung einer IDL-Datei mit den generierten Quellcodedateien sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-140">We recommend that you declare each runtime class in its own Interface Definition Language (IDL) (.idl) file, in order to optimize build performance when you edit an IDL file, and for logical correspondence of an IDL file to its generated source code files.</span></span> <span data-ttu-id="a32cc-141">Visual Studio führt alle resultierenden `.winmd`-Dateien in einer einzigen Datei zusammen, die denselben Namen erhält wie der Stammnamespace.</span><span class="sxs-lookup"><span data-stu-id="a32cc-141">Visual Studio merges all of the resulting `.winmd` files into a single file with the same name as the root namespace.</span></span> <span data-ttu-id="a32cc-142">Die endgültige `.winmd`-Datei wird die sein, die von den Nutzern Ihrer Komponente referenziert wird.</span><span class="sxs-lookup"><span data-stu-id="a32cc-142">That final `.winmd` file will be the one that the consumers of your component will reference.</span></span>

<span data-ttu-id="a32cc-143">Hier ein Beispiel dazu.</span><span class="sxs-lookup"><span data-stu-id="a32cc-143">Here's an example.</span></span>

```idl
// MyRuntimeClass.idl
namespace MyProject
{
    runtimeclass MyRuntimeClass
    {
        // Declaring a constructor (or constructors) in the IDL causes the runtime class to be
        // activatable from outside the compilation unit.
        MyRuntimeClass();
        String Name;
    }
}
```

<span data-ttu-id="a32cc-144">Diese IDL deklariert eine Windows-Runtime-Klasse (Runtime).</span><span class="sxs-lookup"><span data-stu-id="a32cc-144">This IDL declares a Windows Runtime (runtime) class.</span></span> <span data-ttu-id="a32cc-145">Eine Laufzeitklasse ist ein Typ, der über moderne COM-Schnittstellen aktiviert und genutzt werden kann, typischerweise über Ausführungsgrenzen hinweg.</span><span class="sxs-lookup"><span data-stu-id="a32cc-145">A runtime class is a type that can be activated and consumed via modern COM interfaces, typically across executable boundaries.</span></span> <span data-ttu-id="a32cc-146">Wenn Sie eine IDL-Datei zu Ihrem Projekt hinzufügen und erstellen, generiert die C++/WinRT-Toolchain (`midl.exe` und `cppwinrt.exe`) einen Implementierungstyp für Sie.</span><span class="sxs-lookup"><span data-stu-id="a32cc-146">When you add an IDL file to your project, and build, the C++/WinRT toolchain (`midl.exe` and `cppwinrt.exe`) generate an implementation type for you.</span></span> <span data-ttu-id="a32cc-147">Unter Verwendung der obigen Beispiel-IDL ist der Implementierungstyp ein C++ Struktur-Stub namens **winrt::MyProject::implementation::MyRuntimeClass** in Quellcodedateien namens `\MyProject\MyProject\Generated Files\sources\MyRuntimeClass.h` und `MyRuntimeClass.cpp`.</span><span class="sxs-lookup"><span data-stu-id="a32cc-147">Using the example IDL above, the implementation type is a C++ struct stub named **winrt::MyProject::implementation::MyRuntimeClass** in source code files named `\MyProject\MyProject\Generated Files\sources\MyRuntimeClass.h` and `MyRuntimeClass.cpp`.</span></span>

<span data-ttu-id="a32cc-148">Der Implementierungstyp sieht so aus.</span><span class="sxs-lookup"><span data-stu-id="a32cc-148">The implementation type looks like this.</span></span>

```cppwinrt
// MyRuntimeClass.h
...
namespace winrt::MyProject::implementation
{
    struct MyRuntimeClass : MyRuntimeClassT<MyRuntimeClass>
    {
        MyRuntimeClass() = default;

        hstring Name();
        void Name(hstring const& value);
    };
}

// winrt::MyProject::factory_implementation::MyRuntimeClass is here, too.
```

<span data-ttu-id="a32cc-149">Beachten Sie das verwendete F-gebundene Polymorphismusmuster (**MyRuntimeClass** verwendet sich selbst als Vorlage für seine Basis, **MyRuntimeClassT**).</span><span class="sxs-lookup"><span data-stu-id="a32cc-149">Note the F-bound polymorphism pattern being used (**MyRuntimeClass** uses itself as a template argument to its base, **MyRuntimeClassT**).</span></span> <span data-ttu-id="a32cc-150">Dies wird auch als „curiously recurring template pattern” (CRTP) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a32cc-150">This is also called the curiously recurring template pattern (CRTP).</span></span> <span data-ttu-id="a32cc-151">Wenn Sie der Vererbungskette nach oben folgen, stoßen Sie auf **MyRuntimeClass_base**.</span><span class="sxs-lookup"><span data-stu-id="a32cc-151">If you follow the inheritance chain upwards, you'll come across **MyRuntimeClass_base**.</span></span>

```cppwinrt
template <typename D, typename... I>
struct MyRuntimeClass_base : implements<D, MyProject::IMyRuntimeClass, I...>
```

<span data-ttu-id="a32cc-152">In diesem Szenario steht also wieder die Basisstrukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) an der Wurzel der Vererbungshierarchie.</span><span class="sxs-lookup"><span data-stu-id="a32cc-152">So, in this scenario, at the root of the inheritance hierarchy is the [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) base struct template once again.</span></span>

<span data-ttu-id="a32cc-153">Weitere Details, Code und eine exemplarische Vorgehensweise bei der Erstellung von APIs in einer Komponente für Windows-Runtime finden Sie unter [Erstellen von Ereignissen in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span><span class="sxs-lookup"><span data-stu-id="a32cc-153">For more details, code, and a walkthrough of authoring APIs in a Windows Runtime component, see [Author events in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span></span>

## <a name="if-youre-authoring-a-runtime-class-to-be-referenced-in-your-xaml-ui"></a><span data-ttu-id="a32cc-154">Wenn Sie eine Laufzeitklasse erstellen, die in Ihrer XAML-Benutzeroberfläche referenziert werden soll, gehen Sie wie folgt vor</span><span class="sxs-lookup"><span data-stu-id="a32cc-154">If you're authoring a runtime class to be referenced in your XAML UI</span></span>
<span data-ttu-id="a32cc-155">Wenn Ihr Typ von Ihrer XAML-Benutzeroberfläche referenziert wird, dann muss er eine Laufzeitklasse sein (auch, wenn er sich im selben Projekt wie das XAML befindet).</span><span class="sxs-lookup"><span data-stu-id="a32cc-155">If your type is referenced by your XAML UI, then it needs to be a runtime class, even though it's in the same project as the XAML.</span></span> <span data-ttu-id="a32cc-156">Obwohl diese typischerweise über Ausführungsgrenzen hinweg aktiviert werden, kann eine Laufzeitklasse stattdessen innerhalb der Kompilierungseinheit verwendet werden, die sie implementiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-156">Although they are typically activated across executable boundaries, a runtime class can instead be used within the compilation unit that implements it.</span></span>

<span data-ttu-id="a32cc-157">In diesem Szenario erstellen *und* nutzen Sie die APIs.</span><span class="sxs-lookup"><span data-stu-id="a32cc-157">In this scenario, you're both authoring *and* consuming the APIs.</span></span> <span data-ttu-id="a32cc-158">Die Vorgehensweise bei der Implementierung Ihrer Laufzeitklasse ist im Wesentlichen die gleiche wie bei einer Komponente für Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="a32cc-158">The procedure for implementing your runtime class is essentially the same as that for a Windows Runtime Component.</span></span> <span data-ttu-id="a32cc-159">Weitere Informationen finden Sie im vorherigen Abschnitt &mdash;[Wenn Sie eine Laufzeitklasse in einer Komponente für Windows-Runtime erstellen, gehen Sie wie folgt vor](#if-youre-authoring-a-runtime-class-in-a-windows-runtime-component)</span><span class="sxs-lookup"><span data-stu-id="a32cc-159">So, see the previous section&mdash;[If you're authoring a runtime class in a Windows Runtime Component](#if-youre-authoring-a-runtime-class-in-a-windows-runtime-component).</span></span> <span data-ttu-id="a32cc-160">Das einzige Detail, das sich von der IDL unterscheidet, ist, dass die C++/WinRT-Toolchain nicht nur einen Implementierungstyp, sondern auch einen Projizierungsyp generiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-160">The only detail that differs is that, from the IDL, the C++/WinRT toolchain generates not only an implementation type but also a projected type.</span></span> <span data-ttu-id="a32cc-161">Es ist wichtig zu verstehen, dass in diesem Szenario die Angabe „**MyRuntimeClass**” mehrdeutig sein kann. Es gibt mehrere Entitäten von unterschiedlicher Art mit diesem Namen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-161">It's important to appreciate that saying only "**MyRuntimeClass**" in this scenario may be ambiguous; there are several entities with that name, of different kinds.</span></span>

- <span data-ttu-id="a32cc-162">**MyRuntimeClass** ist der Name einer Runtime-Klasse.</span><span class="sxs-lookup"><span data-stu-id="a32cc-162">**MyRuntimeClass** is the name of a runtime class.</span></span> <span data-ttu-id="a32cc-163">Tatsächlich handelt es sich aber um eine Abstraktion – in IDL deklariert und in einer Programmiersprache implementiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-163">But this is really an abstraction: declared in IDL, and implemented in some programming language.</span></span>
- <span data-ttu-id="a32cc-164">**MyRuntimeClass** ist der Name der C++ Struktur **winrt::MyProject::implementation::MyRuntimeClass**, die die C++/WinRT-Implementierung der Laufzeitklasse ist.</span><span class="sxs-lookup"><span data-stu-id="a32cc-164">**MyRuntimeClass** is the name of the C++ struct **winrt::MyProject::implementation::MyRuntimeClass**, which is the C++/WinRT implementation of the runtime class.</span></span> <span data-ttu-id="a32cc-165">Wenn es getrennte Implementierungs- und Nutzungsprojekte gibt, dann existiert diese Struktur nur im Implementierungsprojekt (wie gesehen).</span><span class="sxs-lookup"><span data-stu-id="a32cc-165">As we've seen, if there are separate implementing and consuming projects, then this struct exists only in the implementing project.</span></span> <span data-ttu-id="a32cc-166">Dies ist der *Implementierungstyp* oder *die Implementierung*.</span><span class="sxs-lookup"><span data-stu-id="a32cc-166">This is *the implementation type*, or *the implementation*.</span></span> <span data-ttu-id="a32cc-167">Dieser Typ wird (durch das `cppwinrt.exe` Tool) in den Dateien `\MyProject\MyProject\Generated Files\sources\MyRuntimeClass.h` und `MyRuntimeClass.cpp` erzeugt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-167">This type is generated (by the `cppwinrt.exe` tool) in the files `\MyProject\MyProject\Generated Files\sources\MyRuntimeClass.h` and `MyRuntimeClass.cpp`.</span></span>
- <span data-ttu-id="a32cc-168">**MyRuntimeClass** ist der Name des projizierten Typs in Form der C++ Struktur **winrt::MyProject::MyRuntimeClass**.</span><span class="sxs-lookup"><span data-stu-id="a32cc-168">**MyRuntimeClass** is the name of the projected type in the form of the C++ struct **winrt::MyProject::MyRuntimeClass**.</span></span> <span data-ttu-id="a32cc-169">Wenn es getrennte Implementierungs- und Nutzungsprojekte gibt, dann existiert diese Struktur nur im Nutzungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-169">If there are separate implementing and consuming projects, then this struct exists only in the consuming project.</span></span> <span data-ttu-id="a32cc-170">Dies ist der *projizierte Typ* oder die *Projizierung*.</span><span class="sxs-lookup"><span data-stu-id="a32cc-170">This is *the projected type*, or *the projection*.</span></span> <span data-ttu-id="a32cc-171">Dieser Typ wird (von `cppwinrt.exe`) in der Datei `\MyProject\MyProject\Generated Files\winrt\impl\MyProject.2.h` generiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-171">This type is generated (by `cppwinrt.exe`) in the file `\MyProject\MyProject\Generated Files\winrt\impl\MyProject.2.h`.</span></span>

![Projizierten Typ und Implementierungstyp](images/myruntimeclass.png)

<span data-ttu-id="a32cc-173">Hier sind die Teile des projizierten Typs, die für dieses Thema relevant sind.</span><span class="sxs-lookup"><span data-stu-id="a32cc-173">Here are the parts of the projected type that are relevant to this topic.</span></span>

```cppwinrt
// MyProject.2.h
...
namespace winrt::MyProject
{
    struct MyRuntimeClass : MyProject::IMyRuntimeClass
    {
        MyRuntimeClass(std::nullptr_t) noexcept {}
        MyRuntimeClass();
    };
}
```

<span data-ttu-id="a32cc-174">Ein Beispiel für die Implementierung der **INotifyPropertyChanged**-Schnittstelle in einer Laufzeitklasse finden Sie unter [XAML-Steuerelelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md).</span><span class="sxs-lookup"><span data-stu-id="a32cc-174">For an example walkthrough of implementing the **INotifyPropertyChanged** interface on a runtime class, see [XAML controls; bind to a C++/WinRT property](binding-property.md).</span></span>

<span data-ttu-id="a32cc-175">Die Vorgehensweise für die Verwendung Ihrer Laufzeitklasse in diesem Szenario ist unter [APIs mit C++/WinRT konsumieren](consume-apis.md#if-the-api-is-implemented-in-the-consuming-project) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-175">The procedure for consuming your runtime class in this scenario is described in [Consume APIs with C++/WinRT](consume-apis.md#if-the-api-is-implemented-in-the-consuming-project).</span></span>

## <a name="runtime-class-constructors"></a><span data-ttu-id="a32cc-176">Laufzeitklassenkonstruktoren</span><span class="sxs-lookup"><span data-stu-id="a32cc-176">Runtime class constructors</span></span>
<span data-ttu-id="a32cc-177">Hier sind einige Punkte, die wir aus den obigen Listings entfernen können.</span><span class="sxs-lookup"><span data-stu-id="a32cc-177">Here are some points to take away from the listings we've seen above.</span></span>

- <span data-ttu-id="a32cc-178">Jeder Konstruktor, den Sie in Ihrer IDL deklarieren, bewirkt, dass ein Konstruktor sowohl für Ihren Implementierungstyp als auch für Ihren projizierten Typ generiert wird.</span><span class="sxs-lookup"><span data-stu-id="a32cc-178">Each constructor you declare in your IDL causes a constructor to be generated on both your implementation type and on your projected type.</span></span> <span data-ttu-id="a32cc-179">IDL-deklarierte Konstruktoren werden verwendet, um die Laufzeitklasse aus einer *anderen Kompiliereinheit* zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-179">IDL-declared constructors are used to consume the runtime class from *a different* compilation unit.</span></span>
- <span data-ttu-id="a32cc-180">Unabhängig davon, ob Sie IDL-deklarierte Konstruktoren haben oder nicht, wird eine Konstruktorüberladung von `nullptr_t` für Ihren projizierten Typ erzeugt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-180">Whether you have IDL-declared constructor(s) or not, a constructor overload that takes `nullptr_t` is generated on your projected type.</span></span> <span data-ttu-id="a32cc-181">Der Aufruf des `nullptr_t`-Konstruktors ist *der erste von zwei Schritten*, um die Laufzeitklasse aus *derselben* Kompiliereinheit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a32cc-181">Calling the `nullptr_t` constructor is *the first of two steps* in consuming the runtime class from *the same* compilation unit.</span></span> <span data-ttu-id="a32cc-182">Weitere Details und ein Codebeispiel finden Sie unter [APIs mit C++/WinRT nutzen](consume-apis.md#if-the-api-is-implemented-in-the-consuming-project).</span><span class="sxs-lookup"><span data-stu-id="a32cc-182">For more details, and a code example, see [Consume APIs with C++/WinRT](consume-apis.md#if-the-api-is-implemented-in-the-consuming-project).</span></span>
- <span data-ttu-id="a32cc-183">Wenn Sie die Laufzeitklasse in *derselben* Kompilierungseinheit nutzen, können Sie auch Nicht-Default-Konstruktoren direkt für den Implementierungstyp implementieren (die sich in `MyRuntimeClass.h` befindet).</span><span class="sxs-lookup"><span data-stu-id="a32cc-183">If you're consuming the runtime class from *the same* compilation unit, then you can also implement non-default constructors directly on the implementation type (which, remember, is in `MyRuntimeClass.h`).</span></span>

> [!NOTE]
> <span data-ttu-id="a32cc-184">Wenn Sie erwarten, dass Ihre Laufzeitklasse von einer anderen Kompilierungseinheit genutzt wird (was üblich ist), nehmen Sie Konstruktor(en) in Ihre IDL auf (mindestens einen Standardkonstruktor).</span><span class="sxs-lookup"><span data-stu-id="a32cc-184">If you expect your runtime class to be consumed from a different compilation unit (which is common), then include constructor(s) in your IDL (at least a default constructor).</span></span> <span data-ttu-id="a32cc-185">Dadurch erhalten Sie neben Ihrem Implementierungstyp auch eine Factory-Implementierung.</span><span class="sxs-lookup"><span data-stu-id="a32cc-185">By doing that, you'll also get a factory implementation alongside your implementation type.</span></span>
> 
> <span data-ttu-id="a32cc-186">Wenn Sie Ihre Laufzeitklasse nur innerhalb derselben Kompilierungseinheit erstellen und nutzen wollen, dann deklarieren Sie keine Konstruktoren in Ihrer IDL.</span><span class="sxs-lookup"><span data-stu-id="a32cc-186">If you want to author and consume your runtime class only within the same compilation unit, then don't declare any constructor(s) in your IDL.</span></span> <span data-ttu-id="a32cc-187">Sie benötigen keine Factory-Implementierung, und es wird auch keine generiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-187">You don't need a factory implementation, and one won't be generated.</span></span> <span data-ttu-id="a32cc-188">Der Standardkonstruktor Ihres Implementierungstyps wird gelöscht, aber Sie können ihn einfach bearbeiten und den Standard verwenden.</span><span class="sxs-lookup"><span data-stu-id="a32cc-188">Your implementation type's default constructor will be deleted, but you can easily edit it and default it instead.</span></span>
> 
> <span data-ttu-id="a32cc-189">Wenn Sie Ihre Laufzeitklasse nur innerhalb derselben Kompilierungseinheit erstellen und nutzen wollen und Sie Konstruktorparameter benötigen, erstellen Sie den/die Konstruktor(en), die Sie direkt in Ihrem Implementierungstyp benötigen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-189">If you want to author and consume your runtime class only within the same compilation unit, and you need constructor parameters, then author the constructor(s) that you need directly on your implementation type.</span></span>

## <a name="instantiating-and-returning-implementation-types-and-interfaces"></a><span data-ttu-id="a32cc-190">Instanziierung und Rückgabe von Implementierungstypen und Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="a32cc-190">Instantiating and returning implementation types and interfaces</span></span>
<span data-ttu-id="a32cc-191">In diesem Abschnitt nehmen wir als Beispiel einen Implementierungstyp namens **MyType**, der die Schnittstellen [**IStringable**](/uwp/api/windows.foundation.istringable) und [**IClosable**](/uwp/api/windows.foundation.iclosable) implementiert.</span><span class="sxs-lookup"><span data-stu-id="a32cc-191">For this section, let's take as an example an implementation type named **MyType**, which implements the [**IStringable**](/uwp/api/windows.foundation.istringable) and [**IClosable**](/uwp/api/windows.foundation.iclosable) interfaces.</span></span>

<span data-ttu-id="a32cc-192">Sie können \*\*MyType \*\*direkt von [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) ableiten (es ist keine Laufzeitklasse).</span><span class="sxs-lookup"><span data-stu-id="a32cc-192">You can derive **MyType** directly from [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) (it's not a runtime class).</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

struct MyType : implements<MyType, IStringable, IClosable>
{
    winrt::hstring ToString(){ ... }
    void Close(){}
};
```

<span data-ttu-id="a32cc-193">Oder Sie können sie aus der IDL generieren (es ist eine Laufzeitklasse).</span><span class="sxs-lookup"><span data-stu-id="a32cc-193">Or you can generate it from IDL (it's a runtime class).</span></span>

```idl
// MyType.idl
namespace MyProject
{
    runtimeclass MyType: Windows.Foundation.IStringable, Windows.Foundation.IClosable
    {
        MyType();
    }    
}
```

<span data-ttu-id="a32cc-194">Um von **MyType** zu einem **IStringable**- oder **IClosable**-Objekt zu gelangen, das Sie als Teil Ihrer Projizierung verwenden oder zurückgeben können, können Sie die Funktionsvorlage [**winrt::make**](/uwp/cpp-ref-for-winrt/make) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-194">To go from **MyType** to an **IStringable** or **IClosable** object that you can use or return as part of your projection, you can call the [**winrt::make**](/uwp/cpp-ref-for-winrt/make) function template.</span></span> <span data-ttu-id="a32cc-195">**Stellen Sie** gibt die Standard-Schnittstelle des Implementierungstyps zurück.</span><span class="sxs-lookup"><span data-stu-id="a32cc-195">**make** returns the implementation type's default interface.</span></span>

```cppwinrt
IStringable istringable = winrt::make<MyType>();
```

> [!NOTE]
> <span data-ttu-id="a32cc-196">Wenn Sie Ihren Typ jedoch in Ihrer XAML-Benutzeroberfläche referenzieren, gibt es sowohl einen Implementierungstyp als auch einen projizierten Typ im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-196">However, if you're referencing your type from your XAML UI, then there will be both an implementation type and a projected type in the same project.</span></span> <span data-ttu-id="a32cc-197">**Stellen Sie** in diesem Fall gibt die eine Instanz des projizierten Typs zurück.</span><span class="sxs-lookup"><span data-stu-id="a32cc-197">In that case, **make** returns an instance of the projected type.</span></span> <span data-ttu-id="a32cc-198">Ein Codebeispiel für dieses Szenario finden Sie unter [XAML-Steuererlemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span><span class="sxs-lookup"><span data-stu-id="a32cc-198">For a code example of that scenario, see [XAML controls; bind to a C++/WinRT property](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span></span>

<span data-ttu-id="a32cc-199">Wir können nur `istringable` (im obigen Codebeispiel) verwenden, um die Mitglieder der **IStringable**-Schnittstelle aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-199">We can only use `istringable` (in the code example above) to call the members of the **IStringable** interface.</span></span> <span data-ttu-id="a32cc-200">Aber eine C++/WinRT-Schnittstelle (die eine projizierte Schnittstelle ist) ist von [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown) abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="a32cc-200">But a C++/WinRT interface (which is a projected interface) derives from [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown).</span></span> <span data-ttu-id="a32cc-201">Daher können Sie aufrufen [**IUnknown:: As**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) (oder [**IUnknown:: Try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)) für dieses auf, um die Abfrage für andere projizierte Typen und Schnittstellen, die Sie ebenfalls verwenden oder zurückgeben können.</span><span class="sxs-lookup"><span data-stu-id="a32cc-201">So, you can call [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) (or [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)) on it to query for other projected types or interfaces, which you can also either use or return.</span></span>

```cppwinrt
istringable.ToString();
IClosable iclosable = istringable.as<IClosable>();
iclosable.Close();
```

<span data-ttu-id="a32cc-202">Wenn Sie auf alle Mitglieder der Implementierung zugreifen und später eine Schnittstelle an einen Aufrufer zurückgeben müssen, verwenden Sie die Funktionsvorlage [**winrt::make_self**](/uwp/cpp-ref-for-winrt/make-self).</span><span class="sxs-lookup"><span data-stu-id="a32cc-202">If you need to access all of the implementation's members, and then later return an interface to a caller, then use the [**winrt::make_self**](/uwp/cpp-ref-for-winrt/make-self) function template.</span></span> <span data-ttu-id="a32cc-203">**make_self** gibt einen [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr)-Wrapper mit dem Implementierungstyp zurück.</span><span class="sxs-lookup"><span data-stu-id="a32cc-203">**make_self** returns a [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) wrapping the implementation type.</span></span> <span data-ttu-id="a32cc-204">Sie können auf die Mitglieder aller Schnittstellen zugreifen (mit dem Pfeiloperator), sie **unverändert** an einen Aufrufer zurückgeben oder das resultierende Interface-Objekt an einen Aufrufer zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-204">You can access the members of all of its interfaces (using the arrow operator), you can return it to a caller as-is, or you can call **as** on it and return the resulting interface object to a caller.</span></span>

```cppwinrt
winrt::com_ptr<MyType> myimpl = winrt::make_self<MyType>();
myimpl->ToString();
myimpl->Close();
IClosable iclosable = myimpl.as<IClosable>();
iclosable.Close();
```

<span data-ttu-id="a32cc-205">Die **MyType**-Klasse ist nicht Teil der Projizierung, sondern die Implementierung.</span><span class="sxs-lookup"><span data-stu-id="a32cc-205">The **MyType** class is not part of the projection; it's the implementation.</span></span> <span data-ttu-id="a32cc-206">Aber auf diese Weise können Sie die Implementierungsmethoden direkt aufrufen, ohne den Aufwand für einen virtuellen Funktionsaufruf.</span><span class="sxs-lookup"><span data-stu-id="a32cc-206">But this way you can call its implementation methods directly, without the overhead of a virtual function call.</span></span> <span data-ttu-id="a32cc-207">Obwohl im obigen Beispiel **MyType::ToString** die gleiche Signatur wie die projizierte Methode von **IStringable** verwendet, rufen wir die nicht-virtuelle Methode direkt auf, ohne die binäre Schnittstelle der Anwendung (ABI) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a32cc-207">In the example above, even though **MyType::ToString** uses the same signature as the projected method on **IStringable**, we're calling the non-virtual method directly, without crossing the application binary interface (ABI).</span></span> <span data-ttu-id="a32cc-208">Der **com_ptr** enthält einfach einen Zeiger auf die **MyType**-Struktur, sodass Sie auch auf alle anderen internen Details von **MyType** über die Variable `myimpl` und den Pfeiloperator zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="a32cc-208">The **com_ptr** simply holds a pointer to the **MyType** struct, so you can also access any other internal details of **MyType** via the `myimpl` variable and the arrow operator.</span></span>

<span data-ttu-id="a32cc-209">Falls Sie ein Interface-Objekt haben und Sie wissen, dass es sich um eine Schnittstelle für Ihre Implementierung handelt, können Sie mit der Funktionsvorlage [**from_abi**](/uwp/cpp-ref-for-winrt/from-abi) zur Implementierung zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a32cc-209">In the case where you have an interface object, and you happen to know that it's an interface on your implementation, then you can get back to the implementation using the [**from_abi**](/uwp/cpp-ref-for-winrt/from-abi) function template.</span></span> <span data-ttu-id="a32cc-210">Auch hier handelt es sich um eine Technik, die virtuelle Funktionsaufrufe vermeidet und Sie direkt die Implementierung nutzen lässt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-210">Again, it's a technique that avoids virtual function calls, and lets you get directly at the implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="a32cc-211">Wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher ist, dann Sie [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self) anstelle von [**WinRT:: from_abi rufen**](/uwp/cpp-ref-for-winrt/from-abi).</span><span class="sxs-lookup"><span data-stu-id="a32cc-211">If you've installed the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later, then you can call [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self) instead of [**winrt::from_abi**](/uwp/cpp-ref-for-winrt/from-abi).</span></span>

<span data-ttu-id="a32cc-212">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="a32cc-212">Here's an example.</span></span> <span data-ttu-id="a32cc-213">[Implementieren der benutzerdefinierten Steuerelementklasse **BgLabelControl** ](xaml-cust-ctrl.md#implement-the-bglabelcontrol-custom-control-class)ist ein weiteres Beispiel.</span><span class="sxs-lookup"><span data-stu-id="a32cc-213">There's another example in [Implement the **BgLabelControl** custom control class](xaml-cust-ctrl.md#implement-the-bglabelcontrol-custom-control-class).</span></span>

```cppwinrt
void ImplFromIClosable(IClosable const& from)
{
    MyType* myimpl = winrt::from_abi<MyType>(from);
    myimpl->ToString();
    myimpl->Close();
}
```

<span data-ttu-id="a32cc-214">Aber nur das ursprüngliche Interface-Objekt behält eine Referenz.</span><span class="sxs-lookup"><span data-stu-id="a32cc-214">But only the original interface object holds on to a reference.</span></span> <span data-ttu-id="a32cc-215">Wenn *Sie* es behalten wollen, können Sie [**com_ptr::copy_from**](/uwp/cpp-ref-for-winrt/com-ptr#comptrcopyfrom-function) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-215">If *you* want to hold on to it, then you can call [**com_ptr::copy_from**](/uwp/cpp-ref-for-winrt/com-ptr#comptrcopyfrom-function).</span></span>

```cppwinrt
winrt::com_ptr<MyType> impl;
impl.copy_from(winrt::from_abi<MyType>(from));
// com_ptr::copy_from ensures that AddRef is called.
```

<span data-ttu-id="a32cc-216">Der Implementierungstyp selbst ist nicht von **winrt::Windows::Foundation::IUnknown** abgeleitet. Daher hat er keine **as**-Funktion.</span><span class="sxs-lookup"><span data-stu-id="a32cc-216">The implementation type itself doesn't derive from **winrt::Windows::Foundation::IUnknown**, so it has no **as** function.</span></span> <span data-ttu-id="a32cc-217">Trotzdem können Sie eine instanziieren und auf die Mitglieder aller Schnittstellen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-217">Even so, you can instantiate one, and access the members of all of its interfaces.</span></span> <span data-ttu-id="a32cc-218">Wenn Sie dies tun, geben Sie die Instanz des Raw-Implementierungstyps jedoch nicht an den Aufrufer zurück.</span><span class="sxs-lookup"><span data-stu-id="a32cc-218">But if you do this, then don't return the raw implementation type instance to the caller.</span></span> <span data-ttu-id="a32cc-219">Verwenden Sie stattdessen eine der oben gezeigten Techniken und geben Sie eine projizierte Schnittstelle oder einen **com_ptr** zurück.</span><span class="sxs-lookup"><span data-stu-id="a32cc-219">Instead, use one of the techniques shown above and return a projected interface, or a **com_ptr**.</span></span>

```cppwinrt
MyType myimpl;
myimpl.ToString();
myimpl.Close();
IClosable ic1 = myimpl.as<IClosable>(); // error
```

<span data-ttu-id="a32cc-220">Wenn Sie eine Instanz Ihres Implementierungstyps haben und diese an eine Funktion übergeben müssen, die den entsprechenden projizierten Typ erwartet, dann können Sie dies tun.</span><span class="sxs-lookup"><span data-stu-id="a32cc-220">If you have an instance of your implementation type, and you need to pass it to a function that expects the corresponding projected type, then you can do so.</span></span> <span data-ttu-id="a32cc-221">Eine für Ihren Implementierungstyp existiert (vorausgesetzt, dass der Implementierungstyp vom generiert wurde der `cppwinrt.exe` Tool), die Dies ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a32cc-221">A conversion operator exists on your implementation type (provided that the implementation type was generated by the `cppwinrt.exe` tool) that makes this possible.</span></span>

## <a name="deriving-from-a-type-that-has-a-non-default-constructor"></a><span data-ttu-id="a32cc-222">Abgeleitet von einem Typ, der über einen Standardkonstruktor verfügt</span><span class="sxs-lookup"><span data-stu-id="a32cc-222">Deriving from a type that has a non-default constructor</span></span>
<span data-ttu-id="a32cc-223">[**ToggleButtonAutomationPeer::ToggleButtonAutomationPeer(ToggleButton)**](/uwp/api/windows.ui.xaml.automation.peers.togglebuttonautomationpeer.-ctor#Windows_UI_Xaml_Automation_Peers_ToggleButtonAutomationPeer__ctor_Windows_UI_Xaml_Controls_Primitives_ToggleButton_) ist ein Beispiel für einen Standardkonstruktor.</span><span class="sxs-lookup"><span data-stu-id="a32cc-223">[**ToggleButtonAutomationPeer::ToggleButtonAutomationPeer(ToggleButton)**](/uwp/api/windows.ui.xaml.automation.peers.togglebuttonautomationpeer.-ctor#Windows_UI_Xaml_Automation_Peers_ToggleButtonAutomationPeer__ctor_Windows_UI_Xaml_Controls_Primitives_ToggleButton_) is an example of a non-default constructor.</span></span> <span data-ttu-id="a32cc-224">Es gibt keinen Standardkonstruktor. Um ein **ToggleButtonAutomationPeer** zu erstellen, müssen Sie also einen *Owner*übergeben.</span><span class="sxs-lookup"><span data-stu-id="a32cc-224">There's no default constructor so, to construct a **ToggleButtonAutomationPeer**, you need to pass an *owner*.</span></span> <span data-ttu-id="a32cc-225">Wenn Sie von **ToggleButtonAutomationPeer** ableiten, dann müssen Sie also einen Konstruktor zur Verfügung stellen, der einen *Owner* entgegen nimmt und ihn an die Basisklasse übergibt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-225">Consequently, if you derive from **ToggleButtonAutomationPeer**, then you need to provide a constructor that takes an *owner* and passes it to the base.</span></span> <span data-ttu-id="a32cc-226">Mal sehen, wie das in der Praxis aussieht.</span><span class="sxs-lookup"><span data-stu-id="a32cc-226">Let's see what that looks like in practice.</span></span>

```idl
// MySpecializedToggleButton.idl
namespace MyNamespace
{
    runtimeclass MySpecializedToggleButton :
        Windows.UI.Xaml.Controls.Primitives.ToggleButton
    {
        ...
    };
}
```

```idl
// MySpecializedToggleButtonAutomationPeer.idl
namespace MyNamespace
{
    runtimeclass MySpecializedToggleButtonAutomationPeer :
        Windows.UI.Xaml.Automation.Peers.ToggleButtonAutomationPeer
    {
        MySpecializedToggleButtonAutomationPeer(MySpecializedToggleButton owner);
    };
}
```

<span data-ttu-id="a32cc-227">Der generierte Konstruktor für Ihren Implementierungstyp sieht so aus.</span><span class="sxs-lookup"><span data-stu-id="a32cc-227">The generated constructor for your implementation type looks like this.</span></span>

```cppwinrt
// MySpecializedToggleButtonAutomationPeer.cpp
...
MySpecializedToggleButtonAutomationPeer::MySpecializedToggleButtonAutomationPeer
    (MyNamespace::MySpecializedToggleButton const& owner)
{
    ...
}
...
```

<span data-ttu-id="a32cc-228">Der einzige noch fehlende Teil ist, dass Sie diesen Konstruktorparameter an die Basisklasse übergeben müssen.</span><span class="sxs-lookup"><span data-stu-id="a32cc-228">The only piece missing is that you need to pass that constructor parameter on to the base class.</span></span> <span data-ttu-id="a32cc-229">Erinnern Sie sich an das oben erwähnte, F-gebundene Polymorphisierungsmuster?</span><span class="sxs-lookup"><span data-stu-id="a32cc-229">Remember the F-bound polymorphism pattern that we mentioned above?</span></span> <span data-ttu-id="a32cc-230">Sobald Sie die Details dieses von C++/WinRT verwendeten Musters kennen, können Sie feststellen, wie Ihre Basisklasse heißt (oder Sie können einfach in der Header-Datei Ihrer Implementierungsklasse nachsehen).</span><span class="sxs-lookup"><span data-stu-id="a32cc-230">Once you're familiar with the details of that pattern as used by C++/WinRT, you can figure out what your base class is called (or you can just look in your implementation class's header file).</span></span> <span data-ttu-id="a32cc-231">So rufen Sie in diesem Fall den Konstruktor der Basisklasse auf.</span><span class="sxs-lookup"><span data-stu-id="a32cc-231">This is how to call the base class constructor in this case.</span></span>

```cppwinrt
// MySpecializedToggleButtonAutomationPeer.cpp
...
MySpecializedToggleButtonAutomationPeer::MySpecializedToggleButtonAutomationPeer
    (MyNamespace::MySpecializedToggleButton const& owner) : 
    MySpecializedToggleButtonAutomationPeerT<MySpecializedToggleButtonAutomationPeer>(owner)
{
    ...
}
...
```

<span data-ttu-id="a32cc-232">Der Konstruktor der Basisklasse erwartet ein **ToggleButton**.</span><span class="sxs-lookup"><span data-stu-id="a32cc-232">The base class constructor expects a **ToggleButton**.</span></span> <span data-ttu-id="a32cc-233">Und **MySpecializedToggleButton** *ist ein* **ToggleButton**.</span><span class="sxs-lookup"><span data-stu-id="a32cc-233">And **MySpecializedToggleButton** *is a* **ToggleButton**.</span></span>

<span data-ttu-id="a32cc-234">Bis Sie die oben beschriebene Änderung vornehmen (um den Konstruktorparameter an die Basisklasse weiterzugeben), wird der Compiler Ihren Konstruktor markieren und darauf hinweisen, dass es (in diesem Fall) keinen geeigneten Standardkonstruktor für einen Typ namens **MySpecializedToggleButtonAutomationPeer_base&lt;MySpecializedToggleButtonAutomationPeer&gt;** gibt.</span><span class="sxs-lookup"><span data-stu-id="a32cc-234">Until you make the edit described above (to pass that constructor parameter on to the base class), the compiler will flag your constructor and point out that there's no appropriate default constructor available on a type called (in this case) **MySpecializedToggleButtonAutomationPeer_base&lt;MySpecializedToggleButtonAutomationPeer&gt;**.</span></span> <span data-ttu-id="a32cc-235">Das ist die Basisklasse der Basisklasse Ihres Implementierungstyps.</span><span class="sxs-lookup"><span data-stu-id="a32cc-235">That's actually the base class of the bass class of your implementation type.</span></span>

## <a name="important-apis"></a><span data-ttu-id="a32cc-236">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="a32cc-236">Important APIs</span></span>
* [<span data-ttu-id="a32cc-237">winrt::com_ptr Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-237">winrt::com_ptr struct template</span></span>](/uwp/cpp-ref-for-winrt/com-ptr)
* [<span data-ttu-id="a32cc-238">WinRT::com_ptr::copy_from-Funktion</span><span class="sxs-lookup"><span data-stu-id="a32cc-238">winrt::com_ptr::copy_from function</span></span>](/uwp/cpp-ref-for-winrt/com-ptr#comptrcopyfrom-function)
* [<span data-ttu-id="a32cc-239">winrt::from_abi Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-239">winrt::from_abi function template</span></span>](/uwp/cpp-ref-for-winrt/from-abi)
* [<span data-ttu-id="a32cc-240">WinRT::get_self-Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-240">winrt::get_self function template</span></span>](/uwp/cpp-ref-for-winrt/get-self)
* [<span data-ttu-id="a32cc-241">winrt::implements Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-241">winrt::implements struct template</span></span>](/uwp/cpp-ref-for-winrt/implements)
* [<span data-ttu-id="a32cc-242">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-242">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)
* [<span data-ttu-id="a32cc-243">winrt::make_self Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="a32cc-243">winrt::make_self function template</span></span>](/uwp/cpp-ref-for-winrt/make-self)
* [<span data-ttu-id="a32cc-244">winrt::Windows::Foundation::IUnknown::as Funktion</span><span class="sxs-lookup"><span data-stu-id="a32cc-244">winrt::Windows::Foundation::IUnknown::as function</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)

## <a name="related-topics"></a><span data-ttu-id="a32cc-245">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a32cc-245">Related topics</span></span>
* [<span data-ttu-id="a32cc-246">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="a32cc-246">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="a32cc-247">XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a32cc-247">XAML controls; bind to a C++/WinRT property</span></span>](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage)
