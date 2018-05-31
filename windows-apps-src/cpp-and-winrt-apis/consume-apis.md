---
author: stevewhims
description: Dieses Thema zeigt, wie man selbst implementierte oder von Windows oder von Drittanbietern implementierte C++/WinRT-APIs verwendet.
title: Verwenden von APIs mit C++/WinRT
ms.author: stwhi
ms.date: 04/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projiziert, projektion, implementierung, laufzeitklasse, aktivierung
ms.localizationpriority: medium
ms.openlocfilehash: e777aca8f1d9f3892f67b10c785c056b14c8070c
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832244"
---
# <a name="consume-apis-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="ff3f4-104">Verwenden von APIs mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="ff3f4-104">Consume APIs with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
> [!NOTE]
> **<span data-ttu-id="ff3f4-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="ff3f4-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="ff3f4-107">Dieses Thema zeigt, wie man selbst implementierte oder von Windows oder von Drittanbietern implementierte C++/WinRT-APIs verwendet.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-107">This topic shows how to consume C++/WinRT APIs, whether they're part of Windows, implemented by a third-party component vendor, or implemented by yourself.</span></span>

## <a name="if-the-api-is-in-a-windows-namespace"></a><span data-ttu-id="ff3f4-108">Wenn sich die API in einem Windows-Namespace befindet</span><span class="sxs-lookup"><span data-stu-id="ff3f4-108">If the API is in a Windows namespace</span></span>
<span data-ttu-id="ff3f4-109">Dies ist der häufigste Fall, bei dem Sie eine Windows-Runtime-API verwenden.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-109">This is the most common case in which you'll consume a Windows Runtime API.</span></span> <span data-ttu-id="ff3f4-110">Dies ist ein einfaches Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-110">Here's a simple code example.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    winrt::init_apartment();
    Uri contosoUri{ L"http://www.contoso.com" };
}
```

<span data-ttu-id="ff3f4-111">Der enthaltene Header `winrt/Windows.Foundation.h` ist Teil des SDKs, und befindet sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-111">The included header `winrt/Windows.Foundation.h` is part of the SDK, found inside the folder `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`.</span></span> <span data-ttu-id="ff3f4-112">Die Header in diesem Ordner enthalten Windows-APIs, die in C++/WinRT projiziert werden.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-112">The headers in that folder contain Windows APIs projected into C++/WinRT.</span></span> <span data-ttu-id="ff3f4-113">Wenn Sie einen Typ aus einem Windows-Namespace verwenden möchten, fügen Sie den C++/WinRT-Projektions-Header ein, der diesem Namespace entspricht.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-113">Whenever you want to use a type from a Windows namespace, include the C++/WinRT projection header corresponding to that namespace.</span></span> <span data-ttu-id="ff3f4-114">Die `using namespace`-Direktiven sind optional, aber praktisch.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-114">The `using namespace` directives are optional, but convenient.</span></span>

<span data-ttu-id="ff3f4-115">In diesem Beispiel enthält `winrt/Windows.Foundation.h` den projizierten Typ für die Laufzeitklasse [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-115">In this example, `winrt/Windows.Foundation.h` contains the projected type for the runtime class [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri).</span></span>

> [!TIP]
> <span data-ttu-id="ff3f4-116">Ein *projizierter Typ* ist ein Wrapper für eine Laufzeitklasse, um deren APIs zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-116">A *projected type* is a wrapper over a runtime class for purposes of consuming its APIs.</span></span> <span data-ttu-id="ff3f4-117">Eine *projizierte Schnittstelle* ist ein Wrapper für eine Windows-Runtime-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-117">A *projected interface* is a wrapper over a Windows Runtime interface.</span></span>

<span data-ttu-id="ff3f4-118">Im obigen Codebeispiel wird nach der Initialisierung von C++/WinRT der projizierte Typ **Uri** über einen seiner öffentlich dokumentierten Konstruktoren (in diesem Beispiel [**Uri(String)**](/uwp/api/windows.foundation.uri#Windows_Foundation_Uri__ctor_System_String_)) konstruiert.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-118">In the code example above, after initializing C++/WinRT, we construct the **Uri** projected type via one of its publicly documented constructors ([**Uri(String)**](/uwp/api/windows.foundation.uri#Windows_Foundation_Uri__ctor_System_String_), in this example).</span></span> <span data-ttu-id="ff3f4-119">Für diesen häufigsten Anwendungsfall müssen Sie nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-119">For this, the most common use case, that's all you have to do.</span></span>

## <a name="if-the-api-is-implemented-in-a-windows-runtime-component"></a><span data-ttu-id="ff3f4-120">Wenn die API in einer Komponente für Windows-Runtime implementiert ist</span><span class="sxs-lookup"><span data-stu-id="ff3f4-120">If the API is implemented in a Windows Runtime component</span></span>
<span data-ttu-id="ff3f4-121">Dieser Abschnitt gilt unabhängig davon, ob Sie die Komponente selbst erstellt haben oder ob sie von einem Anbieter stammt.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-121">This section applies whether you authored the component yourself, or it came from a vendor.</span></span>

> [!NOTE]
> <span data-ttu-id="ff3f4-122">Informationen über die aktuelle Verfügbarkeit der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-122">For info about the current availability of the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

<span data-ttu-id="ff3f4-123">Verweisen Sie in Ihrem Anwendungsprojekt auf die Windows-Runtime-Metadaten-Datei (`.winmd`) der Komponente für Windows-Runtime und erstellen Sie diese.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-123">In your application project, reference the Windows Runtime component's Windows Runtime metadata (`.winmd`) file, and build.</span></span> <span data-ttu-id="ff3f4-124">Während des Builds erzeugt das `cppwinrt.exe`-Tool eine Standard-C++ Bibliothek, die die API-Oberfläche der Komponente vollständig beschreibt (bzw. *projiziert*).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-124">During the build, the `cppwinrt.exe` tool generates a standard C++ library that fully describes&mdash;or *projects*&mdash;the API surface for the component.</span></span> <span data-ttu-id="ff3f4-125">Mit anderen Worten, die generierte Bibliothek enthält die projizierten Typen für die Komponente.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-125">In other words, the generated library contains the projected types for the component.</span></span>

<span data-ttu-id="ff3f4-126">Dann fügen Sie wie bei einem Windows-Namespace-Typ einen Header ein und konstruieren den projizierten Typ über einen seiner Konstruktoren.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-126">Then, just as for a Windows namespace type, you include a header and construct the projected type via one of its constructors.</span></span> <span data-ttu-id="ff3f4-127">Der Startcode Ihres Anwendungsprojekts registriert die Laufzeitklasse, und der Konstruktor des projizierten Typs ruft [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) auf, um die Laufzeitklasse der referenzierten Komponente zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-127">Your application project's startup code registers the runtime class, and the projected type's constructor calls [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to activate the runtime class from the referenced component.</span></span>

```cppwinrt
#include <winrt/BankAccountWRC.h>

struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount bankAccount;
    ...
};
```

<span data-ttu-id="ff3f4-128">Weitere Details, Code und eine exemplarische Vorgehensweise bei der Verwendung von APIs, die in einer Komponente für Windows-Runtime implementiert sind, finden Sie unter [Erstellen von Ereignissen in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-128">For more details, code, and a walkthrough of consuming APIs implemented in a Windows Runtime component, see [Author events in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span></span>

## <a name="if-the-api-is-implemented-in-the-consuming-project"></a><span data-ttu-id="ff3f4-129">Wenn die API im verwendenden Projekt implementiert ist</span><span class="sxs-lookup"><span data-stu-id="ff3f4-129">If the API is implemented in the consuming project</span></span>
<span data-ttu-id="ff3f4-130">Ein Typ, der vom XAML-UI verwendet wird, muss eine Laufzeitklasse sein (auch, wenn er sich im selben Projekt wie das XAML-UI befindet).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-130">A type that's consumed from XAML UI must be a runtime class, even if it's in the same project as the XAML.</span></span>

<span data-ttu-id="ff3f4-131">Für dieses Szenario generieren Sie einen projizierten Typ aus den Windows-Runtime-Metadaten der Laufzeitklasse (`.winmd`).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-131">For this scenario, you generate a projected type from the runtime class's Windows Runtime metadata (`.winmd`).</span></span> <span data-ttu-id="ff3f4-132">Auch hier fügen Sie einen Header ein. Aber diesmal konstruieren Sie den projizierten Typ über seinen `nullptr`-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-132">Again, you include a header, but this time you construct the projected type via its `nullptr` constructor.</span></span> <span data-ttu-id="ff3f4-133">Dieser Konstruktor führt keine Initialisierung durch. Daher müssen Sie der Instanz über die [**winrt::make**](/uwp/cpp-ref-for-winrt/make)-Helper-Funktion einen Wert zuweisen und alle notwendigen Konstruktorargumente übergeben.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-133">That constructor doesn't perform any initialization, so you must next assign a value to the instance via the [**winrt::make**](/uwp/cpp-ref-for-winrt/make) helper function, passing any necessary constructor arguments.</span></span> <span data-ttu-id="ff3f4-134">Eine Laufzeitklasse, die im selben Projekt wie der verwendende Code implementiert ist, muss weder registriert noch über die Windows-Runtime/COM-Aktivierung instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-134">A runtime class implemented in the same project as the consuming code doesn't need to be registered, nor instantiated via Windows Runtime/COM activation.</span></span>

```cppwinrt
// MainPage.h
...
struct MainPage : MainPageT<MainPage>
{
    ...
    private:
        Bookstore::BookstoreViewModel m_mainViewModel{ nullptr };
        ...
    };
}
...
// MainPage.cpp
...
#include "BookstoreViewModel.h"

MainPage::MainPage()
{
    m_mainViewModel = make<Bookstore::implementation::BookstoreViewModel>();
    ...
}
```

<span data-ttu-id="ff3f4-135">Weitere Details, Code und eine exemplarische Vorgehensweise für die Nutzung einer im verwendenden Projekt implementierten Laufzeitklasse finden Sie unter [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-135">For more details, code, and a walkthrough of consuming a runtime class implemented in the consuming project, see [XAML controls; bind to a C++/WinRT property](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span></span>

## <a name="instantiating-and-returning-projected-types-and-interfaces"></a><span data-ttu-id="ff3f4-136">Instanziierung und Rückgabe von projizierten Typen und Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="ff3f4-136">Instantiating and returning projected types and interfaces</span></span>
<span data-ttu-id="ff3f4-137">Hier ist ein Beispiel dafür, wie projizierte Typen und Schnittstellen in Ihrem Projekt aussehen könnten.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-137">Here's an example of what projected types and interfaces might look like in your consuming project.</span></span>

```cppwinrt
struct MyRuntimeClass : MyProject::IMyRuntimeClass, impl::require<MyRuntimeClass,
    Windows::Foundation::IStringable, Windows::Foundation::IClosable>
```

<span data-ttu-id="ff3f4-138">**MyRuntimeClass** ist ein projizierter Typ. Projizierte Schnittstellen sind **IMyRuntimeClass**, **IStringable** und **IClosable**.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-138">**MyRuntimeClass** is a projected type; projected interfaces include **IMyRuntimeClass**, **IStringable**, and **IClosable**.</span></span> <span data-ttu-id="ff3f4-139">Dieses Thema hat die verschiedenen Möglichkeiten gezeigt, über die Sie einen projizierten Typ instanziieren können.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-139">This topic has shown the different ways in which you can instantiate a projected type.</span></span> <span data-ttu-id="ff3f4-140">Hier ist eine Zusammenfassung, die **MyRuntimeClass** als Beispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-140">Here's a reminder and summary, using **MyRuntimeClass** as an example.</span></span>

```cppwinrt
// The runtime class is implemented in another compilation unit (it's either a Windows API,
// or it's implemented in a second- or third-party component).
MyProject::MyRuntimeClass myrc1;

// The runtime class is implemented in the same compilation unit.
MyProject::MyRuntimeClass myrc2{ nullptr };
myrc2 = winrt::make<MyProject::implementation::MyRuntimeClass>();
```

- <span data-ttu-id="ff3f4-141">Sie können auf die Mitglieder aller Schnittstellen eines projizierten Typs zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-141">You can access the members of all of the interfaces of a projected type.</span></span>
- <span data-ttu-id="ff3f4-142">Sie können einen projizierten Typ an einen Aufrufer zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-142">You can return a projected type to a caller.</span></span>
- <span data-ttu-id="ff3f4-143">Projizierte Typen und Schnittstellen sind von [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown) abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-143">Projected types and interfaces derive from [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown).</span></span> <span data-ttu-id="ff3f4-144">Sie können [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) für einen projizierten Typ oder eine Interface aufrufen, um nach anderen projizierten Schnittstellen zu suchen, die Sie ebenfalls verwenden oder an einen Aufrufer zurückgeben können.</span><span class="sxs-lookup"><span data-stu-id="ff3f4-144">So, you can call [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) on a projected type or interface to query for other projected interfaces, which you can also either use or return to a caller.</span></span> <span data-ttu-id="ff3f4-145">Die **as**Mitgliedsfunktion arbeitet wie [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span><span class="sxs-lookup"><span data-stu-id="ff3f4-145">The **as** member function works like [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span>

```cppwinrt
void f(MyProject::MyRuntimeClass const& myrc)
{
    myrc.ToString();
    myrc.Close();
    IClosable iclosable = myrc.as<IClosable>();
    iclosable.Close();
}
```

## <a name="important-apis"></a><span data-ttu-id="ff3f4-146">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="ff3f4-146">Important APIs</span></span>
* [<span data-ttu-id="ff3f4-147">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="ff3f4-147">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)
* [<span data-ttu-id="ff3f4-148">winrt::Windows::Foundation::IUnknown::as</span><span class="sxs-lookup"><span data-stu-id="ff3f4-148">winrt::Windows::Foundation::IUnknown::as</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)

## <a name="related-topics"></a><span data-ttu-id="ff3f4-149">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ff3f4-149">Related topics</span></span>
* [<span data-ttu-id="ff3f4-150">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="ff3f4-150">Author events in C++/WinRT</span></span>](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component)
* [<span data-ttu-id="ff3f4-151">XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ff3f4-151">XAML controls; bind to a C++/WinRT property</span></span>](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage)
