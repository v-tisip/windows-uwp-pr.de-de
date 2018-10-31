---
author: stevewhims
description: Damit Sie C++/WinRT schneller verwenden können, werden Ihnen in diesem Thema einige einfache Codebeispiele vorgestellt.
title: Erste Schritte mit C++/WinRT
ms.author: stwhi
ms.date: 10/19/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, erste schritte
ms.localizationpriority: medium
ms.openlocfilehash: 6cb8e18904f61976103689c8d83475ec248eb38b
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5819721"
---
# <a name="get-started-with-cwinrt"></a><span data-ttu-id="37cdc-104">Erste Schritte mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="37cdc-104">Get started with C++/WinRT</span></span>

<span data-ttu-id="37cdc-105">Um Sie bei der Verwendung von Beschleunigung erhalten [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), dieses Thema führt durch ein einfaches Codebeispiel basierend auf einer neuen **Windows Console Application (C++ / WinRT)** Projekt.</span><span class="sxs-lookup"><span data-stu-id="37cdc-105">To get you up to speed with using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), this topic walks through a simple code example based on a new **Windows Console Application (C++/WinRT)** project.</span></span> <span data-ttu-id="37cdc-106">In diesem Thema wird auch so [Hinzufügen C++ / WinRT-Unterstützung zu einem Windows-Desktop-Anwendung-Projekt](#modify-a-windows-desktop-application-project-to-add-cwinrt-support).</span><span class="sxs-lookup"><span data-stu-id="37cdc-106">This topic also shows how to [add C++/WinRT support to a Windows Desktop application project](#modify-a-windows-desktop-application-project-to-add-cwinrt-support).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37cdc-107">Wenn Sie Visual Studio 2017 verwenden (Version 15.8.0 oder höher), und für das Windows SDK-Version 10.0.17134.0 (Windows 10, Version 1803), klicken Sie dann eine neu erstellte C++ / WinRT-Projekt wird möglicherweise mit dem Fehler kompilieren "*Fehler C3861: 'From_abi': Bezeichner nicht gefunden*", und mit anderen Fehlern mit Ursprung in *base.h*.</span><span class="sxs-lookup"><span data-stu-id="37cdc-107">If you're using Visual Studio 2017 (version 15.8.0 or higher), and targeting the Windows SDK version 10.0.17134.0 (Windows 10, version 1803), then a newly created C++/WinRT project may fail to compile with the error "*error C3861: 'from_abi': identifier not found*", and with other errors originating in *base.h*.</span></span> <span data-ttu-id="37cdc-108">Die Lösung besteht darin, entweder Ziel höher (Weitere konform) Version des Windows SDK oder der Set-Projekteigenschaft **C/C++-** > **Sprache** > **Konformitätsmodus: Nein** (auch, wenn **/ PERMISSIVE--** erscheint in Projekteigenschaft \*\* C/C++\*\* > **Sprache** > **Befehlszeile** unter **Zusätzliche Optionen**, löschen Sie ihn).</span><span class="sxs-lookup"><span data-stu-id="37cdc-108">The solution is to either target a later (more conformant) version of the Windows SDK, or set project property **C/C++** > **Language** > **Conformance mode: No** (also, if **/permissive-** appears in project property **C/C++** > **Language** > **Command Line** under **Additional Options**, then delete it).</span></span>

## <a name="a-cwinrt-quick-start"></a><span data-ttu-id="37cdc-109">Schnelleinstieg zu C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="37cdc-109">A C++/WinRT quick-start</span></span>

> [!NOTE]
> <span data-ttu-id="37cdc-110">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="37cdc-110">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

<span data-ttu-id="37cdc-111">Erstellen Sie ein neues **Windows Console Application (C++/WinRT)**-Projekt.</span><span class="sxs-lookup"><span data-stu-id="37cdc-111">Create a new **Windows Console Application (C++/WinRT)** project.</span></span>

<span data-ttu-id="37cdc-112">Bearbeiten Sie `pch.h` und `main.cpp` folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="37cdc-112">Edit `pch.h` and `main.cpp` to look like this.</span></span>

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

<span data-ttu-id="37cdc-113">Wir nehmen uns das kurze Codebeispiel oben Stück für Stück vor und erläutern, was in jedem Teil passiert.</span><span class="sxs-lookup"><span data-stu-id="37cdc-113">Let's take the short code example above piece by piece, and explain what's going on in each part.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
```

<span data-ttu-id="37cdc-114">Die enthaltenen Header sind Teil des SDKs und befinden sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-114">The headers that we include are part of the SDK, inside the folder `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt`.</span></span> <span data-ttu-id="37cdc-115">Visual Studio bezieht diesen Pfad in sein *IncludePath*-Makro ein.</span><span class="sxs-lookup"><span data-stu-id="37cdc-115">Visual Studio includes that path in its *IncludePath* macro.</span></span> <span data-ttu-id="37cdc-116">Die Header enthalten Windows-APIs, die in C++/WinRT projiziert werden.</span><span class="sxs-lookup"><span data-stu-id="37cdc-116">The headers contain Windows APIs projected into C++/WinRT.</span></span> <span data-ttu-id="37cdc-117">Anders ausgedrückt: Für jeden einzelnen Windows-Typ definiert C++/WinRT ein C++-freundliches Äquivalent (wird als *projizierter Typ* bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="37cdc-117">In other words, for each Windows type, C++/WinRT defines a C++-friendly equivalent (called the *projected type*).</span></span> <span data-ttu-id="37cdc-118">Ein projizierter Typ verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="37cdc-118">A projected type has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace.</span></span> <span data-ttu-id="37cdc-119">Wenn Sie diese in Ihrem vorkompilierten Header platzieren, werden die inkrementellen Buildzeiten reduziert.</span><span class="sxs-lookup"><span data-stu-id="37cdc-119">Putting these includes in your precompiled header reduces incremental build times.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37cdc-120">Wann immer Sie einen Typ aus einem Windows-Namespace verwenden möchten, schließen Sie die entsprechende C++/WinRT-Windows-Namespace-Headerdatei wie gezeigt ein.</span><span class="sxs-lookup"><span data-stu-id="37cdc-120">Whenever you want to use a type from a Windows namespaces, include the corresponding C++/WinRT Windows namespace header file, as shown.</span></span> <span data-ttu-id="37cdc-121">Der *zugehörige* Header ist derjenige mit dem gleichen Namen wie der Namespace des Typs.</span><span class="sxs-lookup"><span data-stu-id="37cdc-121">The *corresponding* header is the one with the same name as the type's namespace.</span></span> <span data-ttu-id="37cdc-122">Um z.B. die C++/WinRT-Projektion für die Laufzeitklasse [**Windows::Foundation::Collections::PropertySet**](/uwp/api/windows.foundation.collections.propertyset) zu verwenden, fügen Sie Folgendes ein: `#include <winrt/Windows.Foundation.Collections.h>`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-122">For example, to use the C++/WinRT projection for the [**Windows::Foundation::Collections::PropertySet**](/uwp/api/windows.foundation.collections.propertyset) runtime class, `#include <winrt/Windows.Foundation.Collections.h>`.</span></span>

```cppwinrt
using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;
```

<span data-ttu-id="37cdc-123">Die `using namespace`-Direktiven sind optional, aber praktisch.</span><span class="sxs-lookup"><span data-stu-id="37cdc-123">The `using namespace` directives are optional, but convenient.</span></span> <span data-ttu-id="37cdc-124">Das oben gezeigte Muster für diese Richtlinien (was die Suche nach unqualifizierten Namen für alles im**Winrt**-Namespace ermöglicht) eignet sich, wenn Sie ein neues Projekt beginnen und C++/WinRT die einzige Sprachprojektion ist, die Sie innerhalb dieses Projekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="37cdc-124">The pattern shown above for such directives (allowing unqualified name lookup for anything in the **winrt** namespace) is suitable for when you're beginning a new project and C++/WinRT is the only language projection you're using inside of that project.</span></span> <span data-ttu-id="37cdc-125">Wenn Sie andererseits C++/WinRT-Code mit [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) und/oder SDK-ABI-Code (Application Binary Interface) kombinieren (Sie davon entweder portieren oder interagieren, eines oder beide dieser Modelle), dann lesen Sie die Themen [Interoperabilität zwischen C++/WinRT und C++/CX](interop-winrt-cx.md), [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md) und [Interoperabilität zwischen C++/WinRT und der ABI](interop-winrt-abi.md).</span><span class="sxs-lookup"><span data-stu-id="37cdc-125">If, on the other hand, you're mixing C++/WinRT code with [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) and/or SDK application binary interface (ABI) code (you're either porting from, or interoperating with, one or both of those models), then see the topics [Interop between C++/WinRT and C++/CX](interop-winrt-cx.md), [Move to C++/WinRT from C++/CX](move-to-winrt-from-cx.md), and [Interop between C++/WinRT and the ABI](interop-winrt-abi.md).</span></span>

```cppwinrt
winrt::init_apartment();
```

<span data-ttu-id="37cdc-126">Der Aufruf von **winrt::init_apartment** initialisiert COM; standardmäßig in einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="37cdc-126">The call to **winrt::init_apartment** initializes COM; by default, in a multithreaded apartment.</span></span>

```cppwinrt
Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
SyndicationClient syndicationClient;
```

<span data-ttu-id="37cdc-127">Weisen Sie zwei Objekte mit Stapelzuordnung zu: Sie stellen den URI des Windows-Blogs dar, und einen Syndication-Client.</span><span class="sxs-lookup"><span data-stu-id="37cdc-127">Stack-allocate two objects: they represent the uri of the Windows blog, and a syndication client.</span></span> <span data-ttu-id="37cdc-128">Wir erstellen den URI mit einem einfachen Wide-String-Literal (unter [String-Verarbeitung in C++/WinRT](strings.md) finden Sie weitere Möglichkeiten zum Arbeiten mit Zeichenfolgen).</span><span class="sxs-lookup"><span data-stu-id="37cdc-128">We construct the uri with a simple wide string literal (see [String handling in C++/WinRT](strings.md) for more ways you can work with strings).</span></span>

```cppwinrt
SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
```

<span data-ttu-id="37cdc-129">[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) ist ein Beispiel für eine asynchrone Windows-Runtime-Funktion.</span><span class="sxs-lookup"><span data-stu-id="37cdc-129">[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) is an example of an asynchronous Windows Runtime function.</span></span> <span data-ttu-id="37cdc-130">Das Codebeispiel erhält von **RetrieveFeedAsync** ein Objekt für einen asynchronen Vorgang. Es ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren und auf das Ergebnis zu warten (in diesem Fall einen Syndication-Feed).</span><span class="sxs-lookup"><span data-stu-id="37cdc-130">The code example receives an asynchronous operation object from **RetrieveFeedAsync**, and it calls **get** on that object to block the calling thread and wait for the result (which is a syndication feed, in this case).</span></span> <span data-ttu-id="37cdc-131">Weitere Informationen über Parallelität und Non-Blocking-Techniken finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="37cdc-131">For more about concurrency, and for non-blocking techniques, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md).</span></span>

```cppwinrt
for (const SyndicationItem syndicationItem : syndicationFeed.Items()) { ... }
```

<span data-ttu-id="37cdc-132">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) ist ein Bereich, der durch die Iteratoren definiert wird, die von den **begin**- und **end**-Funktionen (oder deren constant-, reverse- und constant-reverse-Varianten) zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="37cdc-132">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) is a range, defined by the iterators returned from **begin** and **end** functions (or their constant, reverse, and constant-reverse variants).</span></span> <span data-ttu-id="37cdc-133">Aus diesem Grund können Sie **Items** entweder mit einer bereichsbasierten `for`-Anweisung oder mit der Template-Funktion **std::for_each** auflisten.</span><span class="sxs-lookup"><span data-stu-id="37cdc-133">Because of this, you can enumerate **Items** with either a range-based `for` statement, or with the **std::for_each** template function.</span></span>

```cppwinrt
winrt::hstring titleAsHstring = syndicationItem.Title().Text();
std::wcout << titleAsHstring.c_str() << std::endl;
```

<span data-ttu-id="37cdc-134">Der Code erhält dann den Titeltext des Feeds als [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Objekt (siehe [String-Verarbeitung in C++/WinRT](strings.md)).</span><span class="sxs-lookup"><span data-stu-id="37cdc-134">Gets the feed's title text, as a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) object (more details in [String handling in C++/WinRT](strings.md)).</span></span> <span data-ttu-id="37cdc-135">**hstring** ist dann die Ausgabe, über die **c_str**-Funktion, die das Muster wiedergibt, das mit C++-Standardbibliothekzeichenfolgen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="37cdc-135">The **hstring** is then output, via the **c_str** function, which reflects the pattern used with C++ Standard Library strings.</span></span>

<span data-ttu-id="37cdc-136">Wie Sie sehen können, unterstützt C++/WinRT moderne, klassenähnliche C++ Ausdrücke wie `syndicationItem.Title().Text()`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-136">As you can see, C++/WinRT encourages modern, and class-like, C++ expressions such as `syndicationItem.Title().Text()`.</span></span> <span data-ttu-id="37cdc-137">Dies ist ein anderer und saubererer Programmierstil als die traditionelle COM-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="37cdc-137">This is a different, and cleaner, programming style from traditional COM programming.</span></span> <span data-ttu-id="37cdc-138">Sie müssen COM nicht direkt initialisieren, arbeiten Sie mit COM-Zeigern.</span><span class="sxs-lookup"><span data-stu-id="37cdc-138">You don't need to directly initialize COM, work with COM pointers.</span></span>

<span data-ttu-id="37cdc-139">Sie müssen auch keine HRESULT-Rückgabecodes verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="37cdc-139">Nor do you need to handle HRESULT return codes.</span></span> <span data-ttu-id="37cdc-140">Für einen natürlichen und modernen Programmierstil konvertiert C++/WinRT Fehler-HRESULTs in Ausnahmen, wie z.B. [**winrt::hresult-error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span><span class="sxs-lookup"><span data-stu-id="37cdc-140">C++/WinRT converts error HRESULTs to exceptions such as [**winrt::hresult-error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) for a natural and modern programming style.</span></span> <span data-ttu-id="37cdc-141">Weitere Informationen zur Fehlerbehandlung sowie Codebeispiele finden Sie unter [Fehlerbehandlung bei C++/WinRT](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="37cdc-141">For more info about error-handling, and code examples, see [Error handling with C++/WinRT](error-handling.md).</span></span>

## <a name="modify-a-windows-desktop-application-project-to-add-cwinrt-support"></a><span data-ttu-id="37cdc-142">Ändern Sie ein Projekt Windows-Desktop-Anwendung zum Hinzufügen von C++ / WinRT-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="37cdc-142">Modify a Windows Desktop application project to add C++/WinRT support</span></span>

<span data-ttu-id="37cdc-143">In diesem Abschnitt erfahren Sie, wie Sie C++ hinzufügen können / WinRT-Unterstützung für ein Projekt der Windows-Desktop-Anwendung, die Sie möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="37cdc-143">This section shows you how you can add C++/WinRT support to a Windows Desktop application project that you might have.</span></span> <span data-ttu-id="37cdc-144">Wenn Sie ein vorhandenes Projekt der Windows-Desktop-Anwendung besitzen, können Sie zusammen mit diesen Schritten durch Erstellen von ersten folgen.</span><span class="sxs-lookup"><span data-stu-id="37cdc-144">If you don't have an existing Windows Desktop application project, then you can follow along with these steps by first creating one.</span></span> <span data-ttu-id="37cdc-145">Angenommen, öffnen Sie Visual Studio und erstellen Sie eine **Visual C++** \> **Windows-Desktop** \> Projekt**Windows Desktop-Anwendung** .</span><span class="sxs-lookup"><span data-stu-id="37cdc-145">For example, open Visual Studio and create a **Visual C++** \> **Windows Desktop** \> **Windows Desktop Application** project.</span></span>

### <a name="set-project-properties"></a><span data-ttu-id="37cdc-146">Set-Projekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="37cdc-146">Set project properties</span></span>

<span data-ttu-id="37cdc-147">Navigieren Sie zum Projekt-Eigenschaft, die **Allgemeine** \> **Windows SDK-Version**, und wählen Sie **Alle Konfigurationen** und **Alle Plattformen**.</span><span class="sxs-lookup"><span data-stu-id="37cdc-147">Go to project property **General** \> **Windows SDK Version**, and select **All Configurations** and **All Platforms**.</span></span> <span data-ttu-id="37cdc-148">Stellen Sie sicher, dass **Windows SDK-Version** 10.0.17134.0 (Windows 10, Version 1803) festgelegt ist oder größer.</span><span class="sxs-lookup"><span data-stu-id="37cdc-148">Ensure that **Windows SDK Version** is set to 10.0.17134.0 (Windows 10, version 1803) or greater.</span></span>

<span data-ttu-id="37cdc-149">Stellen Sie sicher, dass Sie nicht betroffen sind [Warum nicht Mein neue Projekt kompiliert?](/windows/uwp/cpp-and-winrt-apis/faq).</span><span class="sxs-lookup"><span data-stu-id="37cdc-149">Confirm that you're not affected by [Why won't my new project compile?](/windows/uwp/cpp-and-winrt-apis/faq).</span></span>

<span data-ttu-id="37cdc-150">Da C++ / WinRT Features aus dem C ++ 17-Standard verwendet, legen Sie die Projekteigenschaft **C/C++-** > **Sprache** > **C++ Sprache Standard** in *ISO C ++ 17 Standard (/ Std: c ++ 17)*.</span><span class="sxs-lookup"><span data-stu-id="37cdc-150">Because C++/WinRT uses features from the C++17 standard, set project property **C/C++** > **Language** > **C++ Language Standard** to *ISO C++17 Standard (/std:c++17)*.</span></span>

### <a name="the-precompiled-header"></a><span data-ttu-id="37cdc-151">Die vorkompilierte Headerdatei</span><span class="sxs-lookup"><span data-stu-id="37cdc-151">The precompiled header</span></span>

<span data-ttu-id="37cdc-152">Benennen Sie Ihre `stdafx.h` und `stdafx.cpp` , `pch.h` und `pch.cpp`bzw..</span><span class="sxs-lookup"><span data-stu-id="37cdc-152">Rename your `stdafx.h` and `stdafx.cpp` to `pch.h` and `pch.cpp`, respectively.</span></span> <span data-ttu-id="37cdc-153">Setzen Sie die Projekteigenschaft **C/C++-** > **Vorkompilierte Header** > **Vorkompilierte Headerdatei** *pch.h*.</span><span class="sxs-lookup"><span data-stu-id="37cdc-153">Set project property **C/C++** > **Precompiled Headers** > **Precompiled Header File** to *pch.h*.</span></span>

<span data-ttu-id="37cdc-154">Suchen und Ersetzen Sie den gesamten `#include "stdafx.h"` mit `#include "pch.h"`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-154">Find and replace all `#include "stdafx.h"` with `#include "pch.h"`.</span></span>

<span data-ttu-id="37cdc-155">In `pch.h`, gehören `winrt/base.h`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-155">In `pch.h`, include `winrt/base.h`.</span></span>

```cppwinrt
// pch.h
...
#include <winrt/base.h>
```

### <a name="linking"></a><span data-ttu-id="37cdc-156">Verknüpfen</span><span class="sxs-lookup"><span data-stu-id="37cdc-156">Linking</span></span>

<span data-ttu-id="37cdc-157">C++ / WinRT-sprachprojektion hängt von bestimmten Windows-Runtime-freien (nicht-Mitglieds)-Funktionen und Einstiegspunkten ab, erfordern, die Verknüpfung mit der überbibliothek ["windowsapp.lib"](/uwp/win32-and-com/win32-apis) .</span><span class="sxs-lookup"><span data-stu-id="37cdc-157">The C++/WinRT language projection depends on certain Windows Runtime free (non-member) functions, and entry points, that require linking to the [WindowsApp.lib](/uwp/win32-and-com/win32-apis) umbrella library.</span></span> <span data-ttu-id="37cdc-158">Dieser Abschnitt beschreibt die drei Arten den Linker Anfall.</span><span class="sxs-lookup"><span data-stu-id="37cdc-158">This section describes three ways of satisfying the linker.</span></span>

<span data-ttu-id="37cdc-159">Die erste Option ist hinzufügen zu Ihrem Visual Studio Projekt alle C++ / WinRT MSBuild-Eigenschaften und-Ziele.</span><span class="sxs-lookup"><span data-stu-id="37cdc-159">The first option is to add to your Visual Studio project all of the C++/WinRT MSBuild properties and targets.</span></span> <span data-ttu-id="37cdc-160">Bearbeiten Sie Ihre `.vcxproj` Datei, suchen Sie `<PropertyGroup Label="Globals">` aus, und legen Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-160">Edit your `.vcxproj` file, find `<PropertyGroup Label="Globals">` and, inside that property group, set the property `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span></span>

<span data-ttu-id="37cdc-161">Alternativ können Sie projektlinkeinstellungen verwenden, um eine explizite Verknüpfung `WindowsApp.lib`.</span><span class="sxs-lookup"><span data-stu-id="37cdc-161">Alternatively, you can use project link settings to explicitly link `WindowsApp.lib`.</span></span>

<span data-ttu-id="37cdc-162">Alternativ können Sie dies im Quellcode erledigen (in `pch.h`, z. B.) wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="37cdc-162">Or, you can do it in source code (in `pch.h`, for example) like this.</span></span>

```cppwinrt
#pragma comment(lib, "windowsapp")
```

<span data-ttu-id="37cdc-163">Können Sie jetzt kompilieren und verknüpfen, und fügen C++ / WinRT-Code zu Ihrem Projekt (z. B. der Code in der [ein c++ / WinRT-Schnellstart-](#a-cwinrt-quick-start) Abschnitt oben beschrieben)</span><span class="sxs-lookup"><span data-stu-id="37cdc-163">You can now compile and link, and add C++/WinRT code to your project (for example, the code shown in the [A C++/WinRT quick-start](#a-cwinrt-quick-start) section, above)</span></span>

## <a name="important-apis"></a><span data-ttu-id="37cdc-164">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="37cdc-164">Important APIs</span></span>
* [<span data-ttu-id="37cdc-165">Syndicationclient:: Retrievefeedasync-Methode</span><span class="sxs-lookup"><span data-stu-id="37cdc-165">SyndicationClient::RetrieveFeedAsync method</span></span>](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [<span data-ttu-id="37cdc-166">SyndicationFeed.Items-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="37cdc-166">SyndicationFeed.Items property</span></span>](/uwp/api/windows.web.syndication.syndicationfeed.items)
* [<span data-ttu-id="37cdc-167">winrt::hstring struct</span><span class="sxs-lookup"><span data-stu-id="37cdc-167">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="37cdc-168">WinRT:: HRESULT-Error-Struktur</span><span class="sxs-lookup"><span data-stu-id="37cdc-168">winrt::hresult-error struct</span></span>](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)

## <a name="related-topics"></a><span data-ttu-id="37cdc-169">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="37cdc-169">Related topics</span></span>
* [<span data-ttu-id="37cdc-170">C++/CX</span><span class="sxs-lookup"><span data-stu-id="37cdc-170">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="37cdc-171">Fehlerbehandlung bei C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="37cdc-171">Error handling with C++/WinRT</span></span>](error-handling.md)
* [<span data-ttu-id="37cdc-172">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="37cdc-172">Interop between C++/WinRT and C++/CX</span></span>](interop-winrt-cx.md)
* [<span data-ttu-id="37cdc-173">Interoperabilität zwischen C++/WinRT und der ABI</span><span class="sxs-lookup"><span data-stu-id="37cdc-173">Interop between C++/WinRT and the ABI</span></span>](interop-winrt-abi.md)
* [<span data-ttu-id="37cdc-174">Wechsel zu C++/WinRT von C++/CX</span><span class="sxs-lookup"><span data-stu-id="37cdc-174">Move to C++/WinRT from C++/CX</span></span>](move-to-winrt-from-cx.md)
* [<span data-ttu-id="37cdc-175">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="37cdc-175">String handling in C++/WinRT</span></span>](strings.md)
