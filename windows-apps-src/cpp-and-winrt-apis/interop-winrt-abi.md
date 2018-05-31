---
author: stevewhims
description: Dieses Thema zeigt, wie man zwischen Application Binary Interface (ABI) und C++/WinRT-Objekten konvertiert.
title: Interoperabilität zwischen C++/WinRT und der ABI
ms.author: stwhi
ms.date: 05/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, interoperabilität, ABI
ms.localizationpriority: medium
ms.openlocfilehash: 84f9f557134e69c396ed63ace3474325856c6cd0
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832044"
---
# <a name="interop-between-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-and-the-abi"></a><span data-ttu-id="2bf1f-104">Interoperabilität zwischen [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) und der ABI</span><span class="sxs-lookup"><span data-stu-id="2bf1f-104">Interop between [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) and the ABI</span></span>
<span data-ttu-id="2bf1f-105">Dieses Thema zeigt, wie man zwischen Application Binary Interface (ABI) und C++/WinRT-Objekten konvertiert.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-105">This topic shows how to convert between application binary interface (ABI) and C++/WinRT objects.</span></span> <span data-ttu-id="2bf1f-106">Sie können diese Techniken verwenden, um zwischen Code, der diese beiden Möglichkeiten der Programmierung mit Windows-Runtime verwendet, zu interagieren. Sie können sie außerdem verwenden, wenn Sie Ihren Code schrittweise von der ABI nach C++/WinRT verschieben.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-106">You can use these techniques to interop between code that uses these two ways of programming with the Windows Runtime, or you can use them as you gradually move your code from the ABI to C++/WinRT.</span></span>

## <a name="what-are-windows-runtime-abi-types"></a><span data-ttu-id="2bf1f-107">Was sind Windows-Runtime-ABI-Typen?</span><span class="sxs-lookup"><span data-stu-id="2bf1f-107">What are Windows Runtime ABI types?</span></span>
<span data-ttu-id="2bf1f-108">Die Windows SDK-Header im Ordner „%WindowsSdkDir%Include\10.0.17134.0\winrt” (passen Sie ggf. die SDK-Versionsnummer an) sind die Windows-Runtime-ABI-Header-Dateien.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-108">The Windows SDK headers in the folder "%WindowsSdkDir%Include\10.0.17134.0\winrt" (adjust the SDK version number for your case, if necessary), are the Windows Runtime ABI header files.</span></span> <span data-ttu-id="2bf1f-109">Sie wurden vom MIDL-Compiler erstellt.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-109">They were produced by the MIDL compiler.</span></span> <span data-ttu-id="2bf1f-110">Hier ist ein Beispiel für die Verwendung eines dieser Header.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-110">Here's an example of including one of these headers.</span></span>

```
#include <windows.foundation.h>
```

<span data-ttu-id="2bf1f-111">Und hier ist ein vereinfachtes Beispiel für einen der ABI-Typen, die Sie in diesem speziellen Header finden.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-111">And here's a simplified example of one of the ABI types that you'll find in that particular header.</span></span>

```
namespace ABI::Windows::Foundation
{
    IUriRuntimeClass : public IInspectable
    {
    public:
        /* [propget] */ virtual HRESULT STDMETHODCALLTYPE get_AbsoluteUri(/* [retval, out] */__RPC__deref_out_opt HSTRING * value) = 0;
        ...
    }
}
```

<span data-ttu-id="2bf1f-112">**IUriRuntimeClass** ist eine COM-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-112">**IUriRuntimeClass** is a COM interface.</span></span> <span data-ttu-id="2bf1f-113">Da die Basis **IInspectable** ist, ist **IUriRuntimeClass** außerdem eine Windows-Runtime-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-113">But more than that&mdash;since its base is **IInspectable**&mdash;**IUriRuntimeClass** is a Windows Runtime interface.</span></span> <span data-ttu-id="2bf1f-114">Beachten Sie den Rückgabetyp **HRESULT** und nicht das Auslösen von Ausnahmen.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-114">Note the **HRESULT** return type, rather than the raising of exceptions.</span></span> <span data-ttu-id="2bf1f-115">Und die Verwendung von Artefakten wie dem **HSTRING**-Handle (es ist gute Praxis, dieses Handle wieder auf `nullptr` zu setzen, wenn Sie damit fertig sind).</span><span class="sxs-lookup"><span data-stu-id="2bf1f-115">And the use of artifacts such as the **HSTRING** handle (it's good practice to set that handle back to `nullptr` when you're finished with it).</span></span> <span data-ttu-id="2bf1f-116">Dies gibt einen Vorgeschmack darauf, wie die Windows-Runtime auf der binären Ebene der Anwendung, also auf der COM-Programmierebene, aussieht.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-116">This gives a taste of what the Windows Runtime looks like at the application binary level; in other words, at the COM programming level.</span></span>

<span data-ttu-id="2bf1f-117">Die Windows-Runtime basiert auf COM-APIs (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="2bf1f-117">The Windows Runtime is based on Component Object Model (COM) APIs.</span></span> <span data-ttu-id="2bf1f-118">Sie können auf diese Weise oder über *Sprachprojektionen* auf die Windows-Runtime zugreifen.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-118">You can access the Windows Runtime that way, or you can access it through *language projections*.</span></span> <span data-ttu-id="2bf1f-119">Eine Projektion verbirgt die COM-Details und bietet eine natürlichere Programmiererfahrung für eine bestimmte Sprache.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-119">A projection hides the COM details, and provides a more natural programming experience for a given language.</span></span>

<span data-ttu-id="2bf1f-120">Wenn Sie z. B. in den Ordner „%WindowsSdkDir%Include\10.0.17134.0\cppwinrt\winrt” (passen Sie ggf. die SDK-Versionsnummer an) sehen, dann finden Sie die C++/WinRT-Sprachprojektionsheader.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-120">For example, if you look in the folder "%WindowsSdkDir%Include\10.0.17134.0\cppwinrt\winrt" (again, adjust the SDK version number for your case, if necessary), then you'll find the C++/WinRT language projection headers.</span></span> <span data-ttu-id="2bf1f-121">Es gibt einen Header für jeden Windows-Namespace, so wie es einen ABI-Header pro Windows-Namespace gibt.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-121">There's a header for each Windows namespace, just like there's one ABI header per Windows namespace.</span></span> <span data-ttu-id="2bf1f-122">Hier ist ein Beispiel für die Einbindung eines der C++/WinRT-Header.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-122">Here's an example of including one of the C++/WinRT headers.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>
```

<span data-ttu-id="2bf1f-123">Und aus diesem Header sehen Sie hier (vereinfacht) das C++/WinRT-Äquivalent zu dem ABI-Typ, den wir gerade gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-123">And, from that header, here (simplified) is the C++/WinRT equivalent of that ABI type we just saw.</span></span>

```
namespace winrt::Windows::Foundation
{
    struct Uri : IUriRuntimeClass, ...
    {
        winrt::hstring AbsoluteUri() const { ... }
        ...
    };
}
```

<span data-ttu-id="2bf1f-124">Die Schnittstelle ist modernes Standard C++.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-124">The interface here is modern, standard C++.</span></span> <span data-ttu-id="2bf1f-125">Es beseitigt **HRESULT**-Elemente (C++/WinRT löst bei Bedarf Ausnahmen aus).</span><span class="sxs-lookup"><span data-stu-id="2bf1f-125">It does away with **HRESULT**s (C++/WinRT raises exceptions if necessary).</span></span> <span data-ttu-id="2bf1f-126">Und die Zugriffsfunktion gibt ein einfaches String-Objekt zurück, das am Ende seines Gültigkeitsbereichs bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-126">And the accessor function returns a simple string object, which is cleaned up at the end of its scope.</span></span>

## <a name="converting-to-and-from-abi-types-in-code"></a><span data-ttu-id="2bf1f-127">Konvertierung von und zu ABI-Typen im Code</span><span class="sxs-lookup"><span data-stu-id="2bf1f-127">Converting to and from ABI types in code</span></span>
<span data-ttu-id="2bf1f-128">Zur Sicherheit und Einfachheit können Sie für Konvertierungen in beide Richtungen einfach [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr), [**com_ptr::as**](/uwp/cpp-ref-for-winrt/com-ptr#comptras-function) und [**winrt::Windows::Foundation::IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-128">For safety and simplicity, for conversions in both directions you can simply use [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr), [**com_ptr::as**](/uwp/cpp-ref-for-winrt/com-ptr#comptras-function), and [**winrt::Windows::Foundation::IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function).</span></span> <span data-ttu-id="2bf1f-129">Hier ist ein Codebeispiel (basierend auf der Projektvorlage **Console App**), das auch zeigt, wie Sie mit Namespacekollisionen zwischen der Projektion und der ABI umgehen können.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-129">Here's a code example (based on the **Console App** project template), which also illustrates how you can deal with namespace collisions between the projection and the ABI.</span></span>

```cppwinrt
// main.cpp
#include "pch.h"

#include <windows.foundation.h>
#include <winrt/Windows.Foundation.h>

namespace winrt
{
    using namespace Windows::Foundation;
}

namespace abi
{
    using namespace ABI::Windows::Foundation;
};

int main()
{
    winrt::init_apartment();
    
    winrt::Uri uri(L"http://aka.ms/cppwinrt");

    // Convert to an ABI type.
    winrt::com_ptr<abi::IStringable> ptr = uri.as<abi::IStringable>();

    // Convert from an ABI type.
    uri = ptr.as<winrt::Uri>();
    winrt::IStringable uriAsIStringable = ptr.as<winrt::IStringable>();
}
```

<span data-ttu-id="2bf1f-130">Die Implementierungen der **as**-Funktionen rufen [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) auf.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-130">The implementations of the **as** functions call [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span> <span data-ttu-id="2bf1f-131">Wenn Sie Low-Level-Konvertierungen benötigen, die nur [**AddRef**](https://msdn.microsoft.com/library/windows/desktop/ms691379) aufrufen, können Sie die Hilfsfunktionen [**winrt::copy_to_abi**](/uwp/cpp-ref-for-winrt/copy-to-abi) und [**winrt::copy_from_abi**](/uwp/cpp-ref-for-winrt/copy-from-abi) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-131">If you want lower-level conversions that only call [**AddRef**](https://msdn.microsoft.com/library/windows/desktop/ms691379), then you can use the [**winrt::copy_to_abi**](/uwp/cpp-ref-for-winrt/copy-to-abi) and [**winrt::copy_from_abi**](/uwp/cpp-ref-for-winrt/copy-from-abi) helper functions.</span></span> <span data-ttu-id="2bf1f-132">Dieses nächste Codebeispiel fügt diese Low-Level-Konvertierungen dem obigen Codebeispiel hinzu.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-132">This next code example adds these lower-level conversions to the code example above.</span></span>

```cppwinrt
int main()
{
    ...

    // Lower-level conversions that only call AddRef.

    // Convert to an ABI type.
    ptr = nullptr;
    winrt::copy_to_abi(uri, *ptr.put_void());

    // Convert from an ABI type.
    uri = nullptr;
    winrt::copy_from_abi(uri, ptr.get());
    ptr = nullptr;
}
```

<span data-ttu-id="2bf1f-133">Hier sind andere ähnliche Low-Level-Konvertierungstechniken. Diese verwenden jedoch nur Zeiger auf ABI-Schnittstellentypen (die durch die Windows SDK-Header definiert sind).</span><span class="sxs-lookup"><span data-stu-id="2bf1f-133">Here are other similarly low-level conversions techniques but using raw pointers to ABI interface types (those defined by the Windows SDK headers) this time.</span></span>

```cppwinrt
    ...
    
    // Copy to an owning raw ABI pointer with copy_to_abi.
    abi::IStringable* owning = nullptr;
    winrt::copy_to_abi(uri, *reinterpret_cast<void**>(&owning));
    
    // Copy from a raw ABI pointer.
    uri = nullptr;
    winrt::copy_from_abi(uri, owning);
    owning->Release();
```

<span data-ttu-id="2bf1f-134">Für die größtmöglichen Low-Level-Konvertierungen, die nur Adressen kopieren, können Sie die Hilfsfunktionen [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi), [**winrt::detach_abi**](/uwp/cpp-ref-for-winrt/detach-abi) und [**winrt::attach_abi**](/uwp/cpp-ref-for-winrt/attach-abi) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-134">For the lowest-level conversions, which only copy addresses, you can use the [**winrt::get_abi**](/uwp/cpp-ref-for-winrt/get-abi), [**winrt::detach_abi**](/uwp/cpp-ref-for-winrt/detach-abi), and [**winrt::attach_abi**](/uwp/cpp-ref-for-winrt/attach-abi) helper functions.</span></span>

```cppwinrt
    ...
    
    // Lowest-level conversions that only copy addresses
    
    // Convert to a non-owning ABI object with get_abi.
    abi::IStringable* non_owning = static_cast<abi::IStringable*>(winrt::get_abi(uri));
    WINRT_ASSERT(non_owning);
    
    // Avoid interlocks this way.
    owning = static_cast<abi::IStringable*>(winrt::detach_abi(uri));
    WINRT_ASSERT(!uri);
    winrt::attach_abi(uri, owning);
    WINRT_ASSERT(uri);
```

## <a name="convertfromabi-function"></a><span data-ttu-id="2bf1f-135">convert_from_abi Funktion</span><span class="sxs-lookup"><span data-stu-id="2bf1f-135">convert_from_abi function</span></span>
<span data-ttu-id="2bf1f-136">Diese Helferfunktion konvertiert einen Raw-ABI-Interface-Zeiger in ein äquivalentes C++/WinRT-Objekt mit minimalem Overhead.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-136">This helper function converts a raw ABI interface pointer to an equivalent C++/WinRT object, with minimal overhead.</span></span>

```cppwinrt
template <typename T>
T convert_from_abi(::IUnknown* from)
{
    T to{ nullptr };

    winrt::check_hresult(from->QueryInterface(winrt::guid_of<T>(),
        reinterpret_cast<void**>(winrt::put_abi(to))));

    return to;
}
```

<span data-ttu-id="2bf1f-137">Die Funktion ruft einfach [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) auf, um die Standardschnittstelle des gewünschten C++/WinRT-Typs abzufragen.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-137">The function simply calls [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521) to query for the default interface of the requested C++/WinRT type.</span></span>

<span data-ttu-id="2bf1f-138">Wie wir gesehen haben, ist eine Hilfsfunktion nicht erforderlich, um von einem C++/WinRT-Objekt in den entsprechenden ABI-Interface-Zeiger zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-138">As we've seen, a helper function is not required to convert from a C++/WinRT object to the equivalent ABI interface pointer.</span></span> <span data-ttu-id="2bf1f-139">Verwenden Sie einfach die Funktion [**winrt::Windows::Foundation::IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)-Mitgliedsfunktion (oder [**try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)), um nach der gewünschten Schnittstelle zu suchen.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-139">Simply use the [**winrt::Windows::Foundation::IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) (or [**try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)) member function to query for the requested interface.</span></span> <span data-ttu-id="2bf1f-140">Die Funktionen **as** und **try_as** geben ein [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr)-Wrapper-Objekt für den gewünschten ABI-Typ zurück.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-140">The **as** and **try_as** functions return a [**winrt::com_ptr**](/uwp/cpp-ref-for-winrt/com-ptr) object wrapping the requested ABI type.</span></span>

## <a name="code-example-using-convertfromabi"></a><span data-ttu-id="2bf1f-141">Codebeispiel mit convert_from_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-141">Code example using convert_from_abi</span></span>
<span data-ttu-id="2bf1f-142">Hier ist ein Codebeispiel, das diese Helferfunktion in der Praxis zeigt.</span><span class="sxs-lookup"><span data-stu-id="2bf1f-142">Here's a code example showing this helper function in practice.</span></span>

```cppwinrt
// main.cpp
#include "pch.h"

#include <windows.foundation.h>
#include <winrt/Windows.Foundation.h>
#include <iostream>

using namespace winrt;
using namespace Windows::Foundation;

namespace winrt
{
    using namespace Windows::Foundation;
}

namespace abi
{
    using namespace ABI::Windows::Foundation;
};

template <typename T>
T convert_from_abi(::IUnknown* from)
{
    T to{ nullptr };

    winrt::check_hresult(from->QueryInterface(winrt::guid_of<T>(),
        reinterpret_cast<void**>(winrt::put_abi(to))));

    return to;
}

int main()
{
    winrt::init_apartment();

    winrt::Uri uri(L"http://aka.ms/cppwinrt");
    std::wcout << "C++/WinRT: " << uri.Domain().c_str() << std::endl;

    // Convert to an ABI type.
    winrt::com_ptr<abi::IUriRuntimeClass> ptr = uri.as<abi::IUriRuntimeClass>();
    winrt::hstring domain;
    winrt::check_hresult(ptr->get_Domain(put_abi(domain)));
    std::wcout << "ABI: " << domain.c_str() << std::endl;

    // Convert from an ABI type.
    winrt::Uri uri_from_abi = convert_from_abi<winrt::Uri>(ptr.get());

    WINRT_ASSERT(uri.Domain() == uri_from_abi.Domain());
    WINRT_ASSERT(uri == uri_from_abi);
}
```

## <a name="important-apis"></a><span data-ttu-id="2bf1f-143">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2bf1f-143">Important APIs</span></span>
* [<span data-ttu-id="2bf1f-144">AddRef</span><span class="sxs-lookup"><span data-stu-id="2bf1f-144">AddRef</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms691379)
* [<span data-ttu-id="2bf1f-145">QueryInterface</span><span class="sxs-lookup"><span data-stu-id="2bf1f-145">QueryInterface</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682521)
* [<span data-ttu-id="2bf1f-146">winrt::attach_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-146">winrt::attach_abi</span></span>](/uwp/cpp-ref-for-winrt/attach-abi)
* [<span data-ttu-id="2bf1f-147">winrt::com_ptr Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="2bf1f-147">winrt::com_ptr struct template</span></span>](/uwp/cpp-ref-for-winrt/com-ptr)
* [<span data-ttu-id="2bf1f-148">winrt::copy_from_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-148">winrt::copy_from_abi</span></span>](/uwp/cpp-ref-for-winrt/copy-from-abi)
* [<span data-ttu-id="2bf1f-149">winrt::copy_to_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-149">winrt::copy_to_abi</span></span>](/uwp/cpp-ref-for-winrt/copy-to-abi)
* [<span data-ttu-id="2bf1f-150">winrt::detach_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-150">winrt::detach_abi</span></span>](/uwp/cpp-ref-for-winrt/detach-abi)
* [<span data-ttu-id="2bf1f-151">winrt::get_abi</span><span class="sxs-lookup"><span data-stu-id="2bf1f-151">winrt::get_abi</span></span>](/uwp/cpp-ref-for-winrt/get-abi)
* [<span data-ttu-id="2bf1f-152">winrt::Windows::Foundation::IUnknown::as Mitgliedsfunktion</span><span class="sxs-lookup"><span data-stu-id="2bf1f-152">winrt::Windows::Foundation::IUnknown::as member function</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)
* [<span data-ttu-id="2bf1f-153">winrt::Windows::Foundation::IUnknown::try_as Mitgliedsfunktion</span><span class="sxs-lookup"><span data-stu-id="2bf1f-153">winrt::Windows::Foundation::IUnknown::try_as member function</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)
