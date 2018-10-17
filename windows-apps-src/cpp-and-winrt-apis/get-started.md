---
author: stevewhims
description: Damit Sie C++/WinRT schneller verwenden können, werden Ihnen in diesem Thema einige einfache Codebeispiele vorgestellt.
title: Erste Schritte mit C++/WinRT
ms.author: stwhi
ms.date: 09/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, erste schritte
ms.localizationpriority: medium
ms.openlocfilehash: b5954aa8236a9abeee6e5c74a200f77fcccf97e3
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4750139"
---
# <a name="get-started-with-cwinrt"></a><span data-ttu-id="9f875-104">Erste Schritte mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9f875-104">Get started with C++/WinRT</span></span>
<span data-ttu-id="9f875-105">Um Sie bei der Verwendung von Beschleunigung erhalten [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), in diesem Thema eine einfache Codebeispiele vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="9f875-105">To get you up to speed with using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), this topic walks through a simple code example.</span></span>

## <a name="a-cwinrt-quick-start"></a><span data-ttu-id="9f875-106">Schnelleinstieg zu C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9f875-106">A C++/WinRT quick-start</span></span>
> [!NOTE]
> <span data-ttu-id="9f875-107">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="9f875-107">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

<span data-ttu-id="9f875-108">Erstellen Sie ein neues **Windows Console Application (C++/WinRT)**-Projekt.</span><span class="sxs-lookup"><span data-stu-id="9f875-108">Create a new **Windows Console Application (C++/WinRT)** project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f875-109">Wenn Sie Visual Studio 2017 verwenden (Version 15.8.0 oder höher), und für das Windows SDK Version 10.0.17134.0 (Windows 10, Version 1803), klicken Sie dann eine neu erstellte C++ / WinRT-Projekt wird möglicherweise mit dem Fehler kompilieren "*Fehler C3861: 'From_abi': Bezeichner nicht gefunden*", und mit anderen Fehlern mit Ursprung in *base.h*.</span><span class="sxs-lookup"><span data-stu-id="9f875-109">If you're using Visual Studio 2017 (version 15.8.0 or higher), and targeting the Windows SDK version 10.0.17134.0 (Windows 10, version 1803), then a newly created C++/WinRT project may fail to compile with the error "*error C3861: 'from_abi': identifier not found*", and with other errors originating in *base.h*.</span></span> <span data-ttu-id="9f875-110">Die Lösung besteht darin, entweder Ziel höher (Weitere konform) Version des Windows SDK oder der Set-Projekteigenschaft **C/C++-** > **Sprache** > **Konformitätsmodus: Nein** (auch, wenn **/ PERMISSIVE--** erscheint in Projekteigenschaft \*\* C/C++\*\* > **Sprache** > **Befehlszeile** unter **Zusätzliche Optionen**, löschen Sie ihn).</span><span class="sxs-lookup"><span data-stu-id="9f875-110">The solution is to either target a later (more conformant) version of the Windows SDK, or set project property **C/C++** > **Language** > **Conformance mode: No** (also, if **/permissive-** appears in project property **C/C++** > **Language** > **Command Line** under **Additional Options**, then delete it).</span></span>

<span data-ttu-id="9f875-111">Bearbeiten Sie `pch.h` und `main.cpp` folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="9f875-111">Edit `pch.h` and `main.cpp` to look like this.</span></span>

```cppwinrt
// pch.h
...
#include <iostream>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
...
```

```cppwinrt
// main.cpp
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

int main()
{
    winrt::init_apartment();

    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
    for (const SyndicationItem syndicationItem : syndicationFeed.Items())
    {
        winrt::hstring titleAsHstring = syndicationItem.Title().Text();
        std::wcout << titleAsHstring.c_str() << std::endl;
    }
}
```

<span data-ttu-id="9f875-112">Wir nehmen uns das kurze Codebeispiel oben Stück für Stück vor und erläutern, was in jedem Teil passiert.</span><span class="sxs-lookup"><span data-stu-id="9f875-112">Let's take the short code example above piece by piece, and explain what's going on in each part.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
```

<span data-ttu-id="9f875-113">Die enthaltenen Header sind Teil des SDKs und befinden sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt`.</span><span class="sxs-lookup"><span data-stu-id="9f875-113">The headers that we include are part of the SDK, inside the folder `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt`.</span></span> <span data-ttu-id="9f875-114">Visual Studio bezieht diesen Pfad in sein *IncludePath*-Makro ein.</span><span class="sxs-lookup"><span data-stu-id="9f875-114">Visual Studio includes that path in its *IncludePath* macro.</span></span> <span data-ttu-id="9f875-115">Die Header enthalten Windows-APIs, die in C++/WinRT projiziert werden.</span><span class="sxs-lookup"><span data-stu-id="9f875-115">The headers contain Windows APIs projected into C++/WinRT.</span></span> <span data-ttu-id="9f875-116">Anders ausgedrückt: Für jeden einzelnen Windows-Typ definiert C++/WinRT ein C++-freundliches Äquivalent (wird als *projizierter Typ* bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="9f875-116">In other words, for each Windows type, C++/WinRT defines a C++-friendly equivalent (called the *projected type*).</span></span> <span data-ttu-id="9f875-117">Ein projizierter Typ verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="9f875-117">A projected type has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace.</span></span> <span data-ttu-id="9f875-118">Wenn Sie diese in Ihrem vorkompilierten Header platzieren, werden die inkrementellen Buildzeiten reduziert.</span><span class="sxs-lookup"><span data-stu-id="9f875-118">Putting these includes in your precompiled header reduces incremental build times.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f875-119">Wann immer Sie einen Typ aus einem Windows-Namespace verwenden möchten, schließen Sie die entsprechende C++/WinRT-Windows-Namespace-Headerdatei wie gezeigt ein.</span><span class="sxs-lookup"><span data-stu-id="9f875-119">Whenever you want to use a type from a Windows namespaces, include the corresponding C++/WinRT Windows namespace header file, as shown.</span></span> <span data-ttu-id="9f875-120">Der *zugehörige* Header ist derjenige mit dem gleichen Namen wie der Namespace des Typs.</span><span class="sxs-lookup"><span data-stu-id="9f875-120">The *corresponding* header is the one with the same name as the type's namespace.</span></span> <span data-ttu-id="9f875-121">Um z.B. die C++/WinRT-Projektion für die Laufzeitklasse [**Windows::Foundation::Collections::PropertySet**](/uwp/api/windows.foundation.collections.propertyset) zu verwenden, fügen Sie Folgendes ein: `#include <winrt/Windows.Foundation.Collections.h>`.</span><span class="sxs-lookup"><span data-stu-id="9f875-121">For example, to use the C++/WinRT projection for the [**Windows::Foundation::Collections::PropertySet**](/uwp/api/windows.foundation.collections.propertyset) runtime class, `#include <winrt/Windows.Foundation.Collections.h>`.</span></span>

```cppwinrt
using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;
```

<span data-ttu-id="9f875-122">Die `using namespace`-Direktiven sind optional, aber praktisch.</span><span class="sxs-lookup"><span data-stu-id="9f875-122">The `using namespace` directives are optional, but convenient.</span></span> <span data-ttu-id="9f875-123">Das oben gezeigte Muster für diese Richtlinien (was die Suche nach unqualifizierten Namen für alles im**Winrt**-Namespace ermöglicht) eignet sich, wenn Sie ein neues Projekt beginnen und C++/WinRT die einzige Sprachprojektion ist, die Sie innerhalb dieses Projekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f875-123">The pattern shown above for such directives (allowing unqualified name lookup for anything in the **winrt** namespace) is suitable for when you're beginning a new project and C++/WinRT is the only language projection you're using inside of that project.</span></span> <span data-ttu-id="9f875-124">Wenn Sie andererseits C++/WinRT-Code mit [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) und/oder SDK-ABI-Code (Application Binary Interface) kombinieren (Sie davon entweder portieren oder interagieren, eines oder beide dieser Modelle), dann lesen Sie die Themen [Interoperabilität zwischen C++/WinRT und C++/CX](interop-winrt-cx.md), [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md) und [Interoperabilität zwischen C++/WinRT und der ABI](interop-winrt-abi.md).</span><span class="sxs-lookup"><span data-stu-id="9f875-124">If, on the other hand, you're mixing C++/WinRT code with [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) and/or SDK application binary interface (ABI) code (you're either porting from, or interoperating with, one or both of those models), then see the topics [Interop between C++/WinRT and C++/CX](interop-winrt-cx.md), [Move to C++/WinRT from C++/CX](move-to-winrt-from-cx.md), and [Interop between C++/WinRT and the ABI](interop-winrt-abi.md).</span></span>

```cppwinrt
winrt::init_apartment();
```

<span data-ttu-id="9f875-125">Der Aufruf von **winrt::init_apartment** initialisiert COM; standardmäßig in einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="9f875-125">The call to **winrt::init_apartment** initializes COM; by default, in a multithreaded apartment.</span></span>

```cppwinrt
Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
SyndicationClient syndicationClient;
```

<span data-ttu-id="9f875-126">Weisen Sie zwei Objekte mit Stapelzuordnung zu: Sie stellen den URI des Windows-Blogs dar, und einen Syndication-Client.</span><span class="sxs-lookup"><span data-stu-id="9f875-126">Stack-allocate two objects: they represent the uri of the Windows blog, and a syndication client.</span></span> <span data-ttu-id="9f875-127">Wir erstellen den URI mit einem einfachen Wide-String-Literal (unter [String-Verarbeitung in C++/WinRT](strings.md) finden Sie weitere Möglichkeiten zum Arbeiten mit Zeichenfolgen).</span><span class="sxs-lookup"><span data-stu-id="9f875-127">We construct the uri with a simple wide string literal (see [String handling in C++/WinRT](strings.md) for more ways you can work with strings).</span></span>

```cppwinrt
SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
```

<span data-ttu-id="9f875-128">[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) ist ein Beispiel für eine asynchrone Windows-Runtime-Funktion.</span><span class="sxs-lookup"><span data-stu-id="9f875-128">[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) is an example of an asynchronous Windows Runtime function.</span></span> <span data-ttu-id="9f875-129">Das Codebeispiel erhält von **RetrieveFeedAsync** ein Objekt für einen asynchronen Vorgang. Es ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren und auf das Ergebnis zu warten (in diesem Fall einen Syndication-Feed).</span><span class="sxs-lookup"><span data-stu-id="9f875-129">The code example receives an asynchronous operation object from **RetrieveFeedAsync**, and it calls **get** on that object to block the calling thread and wait for the result (which is a syndication feed, in this case).</span></span> <span data-ttu-id="9f875-130">Weitere Informationen über Parallelität und Non-Blocking-Techniken finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="9f875-130">For more about concurrency, and for non-blocking techniques, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md).</span></span>

```cppwinrt
for (const SyndicationItem syndicationItem : syndicationFeed.Items()) { ... }
```

<span data-ttu-id="9f875-131">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) ist ein Bereich, der durch die Iteratoren definiert wird, die von den **begin**- und **end**-Funktionen (oder deren constant-, reverse- und constant-reverse-Varianten) zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9f875-131">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) is a range, defined by the iterators returned from **begin** and **end** functions (or their constant, reverse, and constant-reverse variants).</span></span> <span data-ttu-id="9f875-132">Aus diesem Grund können Sie **Items** entweder mit einer bereichsbasierten `for`-Anweisung oder mit der Template-Funktion **std::for_each** auflisten.</span><span class="sxs-lookup"><span data-stu-id="9f875-132">Because of this, you can enumerate **Items** with either a range-based `for` statement, or with the **std::for_each** template function.</span></span>

```cppwinrt
winrt::hstring titleAsHstring = syndicationItem.Title().Text();
std::wcout << titleAsHstring.c_str() << std::endl;
```

<span data-ttu-id="9f875-133">Der Code erhält dann den Titeltext des Feeds als [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Objekt (siehe [String-Verarbeitung in C++/WinRT](strings.md)).</span><span class="sxs-lookup"><span data-stu-id="9f875-133">Gets the feed's title text, as a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) object (more details in [String handling in C++/WinRT](strings.md)).</span></span> <span data-ttu-id="9f875-134">**hstring** ist dann die Ausgabe, über die **c_str**-Funktion, die das Muster wiedergibt, das mit C++-Standardbibliothekzeichenfolgen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9f875-134">The **hstring** is then output, via the **c_str** function, which reflects the pattern used with C++ Standard Library strings.</span></span>

<span data-ttu-id="9f875-135">Wie Sie sehen können, unterstützt C++/WinRT moderne, klassenähnliche C++ Ausdrücke wie `syndicationItem.Title().Text()`.</span><span class="sxs-lookup"><span data-stu-id="9f875-135">As you can see, C++/WinRT encourages modern, and class-like, C++ expressions such as `syndicationItem.Title().Text()`.</span></span> <span data-ttu-id="9f875-136">Dies ist ein anderer und saubererer Programmierstil als die traditionelle COM-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="9f875-136">This is a different, and cleaner, programming style from traditional COM programming.</span></span> <span data-ttu-id="9f875-137">Sie müssen COM nicht direkt initialisieren, arbeiten Sie mit COM-Zeigern.</span><span class="sxs-lookup"><span data-stu-id="9f875-137">You don't need to directly initialize COM, work with COM pointers.</span></span>

<span data-ttu-id="9f875-138">Sie müssen auch keine HRESULT-Rückgabecodes verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9f875-138">Nor do you need to handle HRESULT return codes.</span></span> <span data-ttu-id="9f875-139">Für einen natürlichen und modernen Programmierstil konvertiert C++/WinRT Fehler-HRESULTs in Ausnahmen, wie z.B. [**winrt::hresult-error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span><span class="sxs-lookup"><span data-stu-id="9f875-139">C++/WinRT converts error HRESULTs to exceptions such as [**winrt::hresult-error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) for a natural and modern programming style.</span></span> <span data-ttu-id="9f875-140">Weitere Informationen zur Fehlerbehandlung sowie Codebeispiele finden Sie unter [Fehlerbehandlung bei C++/WinRT](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="9f875-140">For more info about error-handling, and code examples, see [Error handling with C++/WinRT](error-handling.md).</span></span>

## <a name="important-apis"></a><span data-ttu-id="9f875-141">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9f875-141">Important APIs</span></span>
* [<span data-ttu-id="9f875-142">Syndicationclient:: Retrievefeedasync-Methode</span><span class="sxs-lookup"><span data-stu-id="9f875-142">SyndicationClient::RetrieveFeedAsync method</span></span>](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [<span data-ttu-id="9f875-143">SyndicationFeed.Items-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9f875-143">SyndicationFeed.Items property</span></span>](/uwp/api/windows.web.syndication.syndicationfeed.items)
* [<span data-ttu-id="9f875-144">winrt::hstring struct</span><span class="sxs-lookup"><span data-stu-id="9f875-144">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="9f875-145">WinRT:: HRESULT-Error-Struktur</span><span class="sxs-lookup"><span data-stu-id="9f875-145">winrt::hresult-error struct</span></span>](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)

## <a name="related-topics"></a><span data-ttu-id="9f875-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9f875-146">Related topics</span></span>
* [<span data-ttu-id="9f875-147">C++/CX</span><span class="sxs-lookup"><span data-stu-id="9f875-147">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="9f875-148">Fehlerbehandlung bei C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9f875-148">Error handling with C++/WinRT</span></span>](error-handling.md)
* [<span data-ttu-id="9f875-149">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="9f875-149">Interop between C++/WinRT and C++/CX</span></span>](interop-winrt-cx.md)
* [<span data-ttu-id="9f875-150">Interoperabilität zwischen C++/WinRT und der ABI</span><span class="sxs-lookup"><span data-stu-id="9f875-150">Interop between C++/WinRT and the ABI</span></span>](interop-winrt-abi.md)
* [<span data-ttu-id="9f875-151">Wechsel zu C++/WinRT von C++/CX</span><span class="sxs-lookup"><span data-stu-id="9f875-151">Move to C++/WinRT from C++/CX</span></span>](move-to-winrt-from-cx.md)
* [<span data-ttu-id="9f875-152">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="9f875-152">String handling in C++/WinRT</span></span>](strings.md)
