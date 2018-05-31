---
author: stevewhims
description: Mit C++/WinRT können Sie Windows-Runtime-APIs mit Standard-C++ String-Typen aufrufen, oder Sie können den Typ winrt::hstring verwenden.
title: String-Verarbeitung in C++/WinRT
ms.author: stwhi
ms.date: 04/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, string
ms.localizationpriority: medium
ms.openlocfilehash: 433b3423c27910f1c680bba4ae2ede5a1e13f8ea
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832054"
---
# <a name="string-handling-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="43e30-104">String-Verarbeitung in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="43e30-104">String handling in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
<span data-ttu-id="43e30-105">Mit C++/WinRT können Sie Windows-Runtime-APIs mit Standard-C++ Wide-String-Typen wie **std::wstring** aufrufen (Hinweis: Nicht mit Narrow-String-Typen wie **std::string**).</span><span class="sxs-lookup"><span data-stu-id="43e30-105">With C++/WinRT, you can call Windows Runtime APIs using C++ Standard Library wide string types such as **std::wstring** (note: not with narrow string types such as **std::string**).</span></span> <span data-ttu-id="43e30-106">C++/WinRT hat einen benutzerdefinierten String-Typ namens [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) (definiert in der C++/WinRT-Basisbibliothek `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h`).</span><span class="sxs-lookup"><span data-stu-id="43e30-106">C++/WinRT does have a custom string type called [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) (defined in the C++/WinRT base library, which is `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h`).</span></span> <span data-ttu-id="43e30-107">Und das ist der String-Typ, den Windows-Runtime-Konstruktoren, -Funktionen und -Eigenschaften tatsächlich entgegennehmen und zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="43e30-107">And that's the string type that Windows Runtime constructors, functions, and properties actually take and return.</span></span> <span data-ttu-id="43e30-108">Aber in vielen Fällen können Sie dank der Konvertierungskonstruktoren und Konvertierungsoperatoren von **hstring** wählen, ob Sie **hstring** in Ihrem Client-Code nutzen oder nicht.</span><span class="sxs-lookup"><span data-stu-id="43e30-108">But in many cases&mdash;thanks to **hstring**'s conversion constructors and conversion operators&mdash;you can choose whether or not to be aware of **hstring** in your client code.</span></span> <span data-ttu-id="43e30-109">Wenn Sie APIs *erstellen*, ist es wahrscheinlicher, dass Sie **hstring** kennen müssen.</span><span class="sxs-lookup"><span data-stu-id="43e30-109">If you're *authoring* APIs, then you're more likely to need to know about **hstring**.</span></span>

<span data-ttu-id="43e30-110">Es gibt viele String-Typen in C++.</span><span class="sxs-lookup"><span data-stu-id="43e30-110">There are many string types in C++.</span></span> <span data-ttu-id="43e30-111">Zusätzlich zu **std::basic_string** aus der C++ Standard Library existieren in vielen Bibliotheken Varianten.</span><span class="sxs-lookup"><span data-stu-id="43e30-111">Variants exist in many libraries in addition to **std::basic_string** from the C++ Standard Library.</span></span> <span data-ttu-id="43e30-112">C++17 hat String-Konvertierungstools und **std::basic_string_view**, um die Lücken zwischen den String-Typen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="43e30-112">C++17 has string conversion utilities, and **std::basic_string_view**, to bridge the gaps between all of the string types.</span></span> <span data-ttu-id="43e30-113">**hstring** bietet eine Konvertierbarkeit über **std::wstring_view**, um die Interoperabilität zu gewährleisten, für die **std::basic_string_view** entworfen wurde.</span><span class="sxs-lookup"><span data-stu-id="43e30-113">**hstring** provides convertibility with **std::wstring_view** to provide the interoperability that **std::basic_string_view** was designed for.</span></span>

## <a name="using-stdwstring-and-optionally-winrthstringuwpcpp-ref-for-winrthstring-with-uriuwpapiwindowsfoundationuri"></a><span data-ttu-id="43e30-114">Verwendung von **std::wstring** (und optional [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)) mit [**Uri**](/uwp/api/windows.foundation.uri)</span><span class="sxs-lookup"><span data-stu-id="43e30-114">Using **std::wstring** (and optionally [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)) with [**Uri**](/uwp/api/windows.foundation.uri)</span></span>

<span data-ttu-id="43e30-115">[**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri) ist aus einem [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="43e30-115">[**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri) is constructed from a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span></span>

```cppwinrt
public:
    Uri(winrt::hstring uri) const;
```

<span data-ttu-id="43e30-116">Aber **hstring** hat [Konvertierungskonstruktoren](/uwp/api/windows.foundation.uri#hstringhstring-constructor), mit denen Sie damit arbeiten können, ohne sich dessen bewusst sein zu müssen.</span><span class="sxs-lookup"><span data-stu-id="43e30-116">But **hstring** has [conversion constructors](/uwp/api/windows.foundation.uri#hstringhstring-constructor) that let you work with it without needing to be aware of it.</span></span> <span data-ttu-id="43e30-117">Hier ist ein Codebeispiel, das zeigt, wie man ein **Uri** aus einem Wide-String-Literal, aus einer Wide-String-Ansicht und aus einem **std::wstring** macht.</span><span class="sxs-lookup"><span data-stu-id="43e30-117">Here's a code example showing how to make a **Uri** from a wide string literal, from a wide string view, and from a **std::wstring**.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <string_view>

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    using namespace std::literals;

    winrt::init_apartment();

    // You can make a Uri from a wide string literal.
    Uri contosoUri{ L"http://www.contoso.com" };

    // Or from a wide string view.
    Uri contosoSVUri{ L"http://www.contoso.com"sv };

    // Or from a std::wstring.
    std::wstring wideString{ L"http://www.adventure-works.com" };
    Uri awUri{ wideString };
}
```

<span data-ttu-id="43e30-118">Die Eigenschaftszugriffsfunktion [**Uri::Domain**](https://docs.microsoft.com/uwp/api/windows.foundation.uri.Domain) ist vom Typ **hstring**.</span><span class="sxs-lookup"><span data-stu-id="43e30-118">The property accessor [**Uri::Domain**](https://docs.microsoft.com/uwp/api/windows.foundation.uri.Domain) is of type **hstring**.</span></span>

```cppwinrt
public:
    winrt::hstring Domain();
```

<span data-ttu-id="43e30-119">Aber auch dieses Detail ist optional (dank des [Konvertierungsoperators für **std::wstring_view**](/uwp/api/windows.foundation.uri#hstringoperator-stdwstringview) von **hstring**.</span><span class="sxs-lookup"><span data-stu-id="43e30-119">But, again, being aware of that detail is optional thanks to **hstring**'s [conversion operator to **std::wstring_view**](/uwp/api/windows.foundation.uri#hstringoperator-stdwstringview).</span></span>

```cppwinrt
// Access a property of type hstring, via a conversion operator to a standard type.
std::wstring domainWstring{ contosoUri.Domain() }; // L"contoso.com"
domainWstring = awUri.Domain(); // L"adventure-works.com"

// Or, you can choose to keep the hstring unconverted.
hstring domainHstring{ contosoUri.Domain() }; // L"contoso.com"
domainHstring = awUri.Domain(); // L"adventure-works.com"
```

<span data-ttu-id="43e30-120">Ebenso gibt [**IStringable::ToString**](https://msdn.microsoft.com/library/windows/desktop/dn302136) ein hstring zurück.</span><span class="sxs-lookup"><span data-stu-id="43e30-120">Similarly, [**IStringable::ToString**](https://msdn.microsoft.com/library/windows/desktop/dn302136) returns hstring.</span></span>

```cppwinrt
public:
    hstring ToString() const;
```

<span data-ttu-id="43e30-121">**Uri** implementiert die [**IStringable**](https://msdn.microsoft.com/library/windows/desktop/dn302135)-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="43e30-121">**Uri** implements the [**IStringable**](https://msdn.microsoft.com/library/windows/desktop/dn302135) interface.</span></span>

```cppwinrt
// Access hstring's IStringable::ToString, via a conversion operator to a standard type.
std::wstring tostringWstring{ contosoUri.ToString() }; // L"http://www.contoso.com/"
tostringWstring = awUri.ToString(); // L"http://www.adventure-works.com/"

// Or you can choose to keep the hstring unconverted.
hstring tostringHstring{ contosoUri.ToString() }; // L"http://www.contoso.com/"
tostringHstring = awUri.ToString(); // L"http://www.adventure-works.com/"
```

<span data-ttu-id="43e30-122">Sie können die [hstring::c_str Funktion](/uwp/api/windows.foundation.uri#hstringcstr-function) verwenden, um einen Standard Wide-String aus einem **hstring** zu erhalten (genau wie aus einem **std::wstring**).</span><span class="sxs-lookup"><span data-stu-id="43e30-122">You can use the [hstring::c_str function](/uwp/api/windows.foundation.uri#hstringcstr-function) to get a standard wide string from an **hstring** (just as you can from a **std::wstring**).</span></span>

```cppwinrt
#include <iostream>
std::wcout << tostringHstring.c_str() << std::endl;
```
<span data-ttu-id="43e30-123">Wenn Sie einen **hstring** haben, dann können Sie daraus einen **Uri** machen.</span><span class="sxs-lookup"><span data-stu-id="43e30-123">If you have an **hstring** then you can make a **Uri** from it.</span></span>

```cppwinrt
Uri awUriFromHstring{ tostringHstring };
```

<span data-ttu-id="43e30-124">Nehmen wir eine Methode, die einen **hstring** entgegennimmt.</span><span class="sxs-lookup"><span data-stu-id="43e30-124">Consider a method that takes an **hstring**.</span></span>

```cppwinrt
public:
    Uri CombineUri(winrt::hstring relativeUri) const;
```

<span data-ttu-id="43e30-125">Alle Optionen, die Sie gerade gesehen haben, gelten auch in solchen Fällen.</span><span class="sxs-lookup"><span data-stu-id="43e30-125">All of the options you've just seen also apply in such cases.</span></span>

```cppwinrt
std::wstring contact{ L"contact" };
contosoUri = contosoUri.CombineUri(contact);
    
std::wcout << contosoUri.ToString().c_str() << std::endl;
```

<span data-ttu-id="43e30-126">**hstring** hat einen MItgliedkonvertierungsoperator **std::wstring_view**, und die Konvertierung wird kostenlos durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="43e30-126">**hstring** has a member **std::wstring_view** conversion operator, and the conversion is achieved at no cost.</span></span>

```cppwinrt
void legacy_print(std::wstring_view view);

void Print(winrt::hstring const& hstring)
{
    legacy_print(hstring);
}
```

## <a name="winrthstring-functions-and-operators"></a><span data-ttu-id="43e30-127">**winrt::hstring** Funktionen und Operatoren</span><span class="sxs-lookup"><span data-stu-id="43e30-127">**winrt::hstring** functions and operators</span></span>
<span data-ttu-id="43e30-128">Eine Vielzahl von Konstruktoren, Operatoren, Funktionen und Iteratoren sind für **hstring** implementiert.</span><span class="sxs-lookup"><span data-stu-id="43e30-128">A host of constructors, operators, functions, and iterators are implemented for **hstring**.</span></span>

<span data-ttu-id="43e30-129">Ein **hstring** ist ein Gültigkeitsbereich, also können Sie ihn mit einem bereichsbasierten `for` oder mit `std::for_each` verwenden.</span><span class="sxs-lookup"><span data-stu-id="43e30-129">An **hstring** is a range, so you can use it with range-based `for`, or with `std::for_each`.</span></span> <span data-ttu-id="43e30-130">Es bietet auch Vergleichsoperatoren für den natürlichen und effizienten Vergleich mit seinen Pendants in der C++ Standard Library.</span><span class="sxs-lookup"><span data-stu-id="43e30-130">It also provides comparison operators for naturally and efficiently comparing against its counterparts in the C++ Standard Library.</span></span> <span data-ttu-id="43e30-131">Und es enthält alles, was Sie brauchen, um **hstring** als Schlüssel für assoziative Container zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="43e30-131">And it includes everything you need to use **hstring** as a key for associative containers.</span></span> <span data-ttu-id="43e30-132">Wir stellen fest, dass viele C++ Bibliotheken **std::basic_string** verwenden und ausschließlich mit UTF-8-Text arbeiten.</span><span class="sxs-lookup"><span data-stu-id="43e30-132">We recognize that many C++ libraries use **std::basic_string**, and work exclusively with UTF-8 text.</span></span> <span data-ttu-id="43e30-133">Zur Bequemlichkeit stellen wir daher Helfer für die Konvertierung in beide Richtungen bereit.</span><span class="sxs-lookup"><span data-stu-id="43e30-133">As a convenience, we provide helpers for converting back and forth.</span></span>

```cppwinrt
hstring w{ L"hello world" };
 
std::string c = to_string(w);
assert(c == "hello world");
 
w = to_hstring(c);
assert(w == L"hello world");
```

<span data-ttu-id="43e30-134">Weitere Beispiele und Informationen über **hstring**-Funktionen und -Operatoren finden Sie im Referenzthema der [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-API.</span><span class="sxs-lookup"><span data-stu-id="43e30-134">For more examples and info about **hstring** functions and operators, see the [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) API reference topic.</span></span>

## <a name="the-rationale-for-winrthstring-and-winrtparamhstring"></a><span data-ttu-id="43e30-135">Die Gründe für **winrt::hstring** und **winrt::param::hstring**</span><span class="sxs-lookup"><span data-stu-id="43e30-135">The rationale for **winrt::hstring** and **winrt::param::hstring**</span></span>
<span data-ttu-id="43e30-136">Die Windows-Runtime ist in Form von **wchar_t** Zeichen implementiert, aber das Application Binary Interface (ABI) von Windows-Runtime ist keine Teilmenge der Möglichkeiten von **std::wstring **oder **std::wstring_view**.</span><span class="sxs-lookup"><span data-stu-id="43e30-136">The Windows Runtime is implemented in terms of **wchar_t** characters, but the Windows Runtime's Application Binary Interface (ABI) is not a subset of what either **std::wstring** or **std::wstring_view** provide.</span></span> <span data-ttu-id="43e30-137">Diese zu nutzen, würde zu erheblicher Ineffizienz führen.</span><span class="sxs-lookup"><span data-stu-id="43e30-137">Using those would lead to significant inefficiency.</span></span> <span data-ttu-id="43e30-138">Stattdessen bietet C++/WinRT **winrt::hstring**, das einen unveränderlichen String darstellt, der mit dem zugrundeliegenden [HSTRING](https://msdn.microsoft.com/library/windows/desktop/br205775) übereinstimmt und hinter einer Schnittstelle ähnlich der von **std::wstring** implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="43e30-138">Instead, C++/WinRT provides **winrt::hstring**, which represents an immutable string consistent with the underlying [HSTRING](https://msdn.microsoft.com/library/windows/desktop/br205775), and implemented behind an interface similar to that of **std::wstring**.</span></span> 

<span data-ttu-id="43e30-139">Sie werden feststellen, dass C++/WinRT-Eingabeparameter, die logisch **winrt::hstring** akzeptieren, tatsächlich **winrt::param::hstring** erwarten.</span><span class="sxs-lookup"><span data-stu-id="43e30-139">You may notice that C++/WinRT input parameters that should logically accept **winrt::hstring** actually expect **winrt::param::hstring**.</span></span> <span data-ttu-id="43e30-140">Der **param**-Namespace enthält eine Reihe von Typen, die ausschließlich zur Optimierung von Eingabeparametern verwendet werden, um für eine natürliche Bindung an C++ Standard Library-Typen zu sorgen und Kopien und andere Ineffizienzen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="43e30-140">The **param** namespace contains a set of types used exclusively to optimize input parameters to naturally bind to C++ Standard Library types and avoid copies and other inefficiencies.</span></span> <span data-ttu-id="43e30-141">Sie sollten diese Typen nicht direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="43e30-141">You shouldn't use these types directly.</span></span> <span data-ttu-id="43e30-142">Wenn Sie eine Optimierung für Ihre eigenen Funktionen verwenden wollen, dann verwenden Sie **std::wstring_view**.</span><span class="sxs-lookup"><span data-stu-id="43e30-142">If you want to use an optimization for your own functions then use **std::wstring_view**.</span></span>

<span data-ttu-id="43e30-143">Das Ergebnis ist, dass Sie die Besonderheiten der Windows-Runtime-String-Verwaltung weitgehend ignorieren und mit dem, was Sie wissen, effizient arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="43e30-143">The upshot is that you can largely ignore the specifics of Windows Runtime string management, and just work with efficiency with what you know.</span></span> <span data-ttu-id="43e30-144">Wenn man bedenkt, wie stark Strings in der Windows-Runtime verwendet werden, ist dies sehr wichtig.</span><span class="sxs-lookup"><span data-stu-id="43e30-144">And that's important, given how heavily strings are used in the Windows Runtime.</span></span>

# <a name="formatting-strings"></a><span data-ttu-id="43e30-145">Strings formatieren</span><span class="sxs-lookup"><span data-stu-id="43e30-145">Formatting strings</span></span>
<span data-ttu-id="43e30-146">Eine Option für die Stringformatierung ist **std::wstringstream**.</span><span class="sxs-lookup"><span data-stu-id="43e30-146">One option for string-formatting is **std::wstringstream**.</span></span> <span data-ttu-id="43e30-147">Hier ist ein Beispiel, das eine einfache Debug-Trace-Meldung formatiert und anzeigt.</span><span class="sxs-lookup"><span data-stu-id="43e30-147">Here's an example that formats and displays a simple debug trace message.</span></span>

```cppwinrt
#include <sstream>
...
void OnPointerPressed(IInspectable const&, PointerEventArgs const& args)
{
    float2 const point = args.CurrentPoint().Position();
    std::wstringstream wstringstream;
    wstringstream << L"Pointer pressed at (" << point.x << L"," << point.y << L")" << std::endl;
    ::OutputDebugString(wstringstream.str().c_str());
}
```

## <a name="important-apis"></a><span data-ttu-id="43e30-148">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="43e30-148">Important APIs</span></span>
* [<span data-ttu-id="43e30-149">winrt::hstring Struktur</span><span class="sxs-lookup"><span data-stu-id="43e30-149">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
