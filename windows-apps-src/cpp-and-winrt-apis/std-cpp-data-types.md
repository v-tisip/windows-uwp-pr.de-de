---
author: stevewhims
description: Mit C++/WinRT können Sie Windows-Runtime-APIs über Standard-C++ Datentypen aufrufen.
title: Standard C++ Datentypen und C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, datentypen
ms.localizationpriority: medium
ms.openlocfilehash: 5aa6e17fcd95813b6abe05e9e42ad7c86657159f
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5745150"
---
# <a name="standard-c-data-types-and-cwinrt"></a><span data-ttu-id="6318e-104">C++-Standarddatentypen und C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="6318e-104">Standard C++ data types and C++/WinRT</span></span>

<span data-ttu-id="6318e-105">Mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), Sie können Windows-Runtime-APIs mit Standard-c++-Datentypen, z. B. einige Standard-c++ Datentypen aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-105">With [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), you can call Windows Runtime APIs using Standard C++ data types, including some C++ Standard Library data types.</span></span> <span data-ttu-id="6318e-106">Sie können standard Zeichenfolgen an APIs übergeben (finden Sie unter [String-Verarbeitung in C++ / WinRT](strings.md)), und Sie können Initialisierer Listen und standard-Containern übergeben, auf APIs, die davon ausgehen, eine semantisch Auflistung dass.</span><span class="sxs-lookup"><span data-stu-id="6318e-106">You can pass standard strings to APIs (see [String handling in C++/WinRT](strings.md)), and you can pass initializer lists and standard containers to APIs that expect a semantically equivalent collection.</span></span>

## <a name="standard-initializer-lists"></a><span data-ttu-id="6318e-107">Standard-Initialisierungslisten</span><span class="sxs-lookup"><span data-stu-id="6318e-107">Standard initializer lists</span></span>
<span data-ttu-id="6318e-108">Eine Initialisierungsliste (**std::initializer_list**) ist ein Konstrukt aus der C++ Standard Library.</span><span class="sxs-lookup"><span data-stu-id="6318e-108">An initializer list (**std::initializer_list**) is a C++ Standard Library construct.</span></span> <span data-ttu-id="6318e-109">Sie können Initialisierungslisten verwenden, wenn Sie bestimmte Windows-Runtime-Konstruktoren und -Methoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-109">You can use initializer lists when you call certain Windows Runtime constructors and methods.</span></span> <span data-ttu-id="6318e-110">Beispielsweise können Sie [**DataWriter::WriteBytes**](/uwp/api/windows.storage.streams.datawriter.writebytes) mit einer Initialisierungsliste aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-110">For example, you can call [**DataWriter::WriteBytes**](/uwp/api/windows.storage.streams.datawriter.writebytes) with one.</span></span>

```cppwinrt
#include <winrt/Windows.Storage.Streams.h>

using namespace winrt::Windows::Storage::Streams;

int main()
{
    winrt::init_apartment();

    InMemoryRandomAccessStream stream;
    DataWriter dataWriter{stream};
    dataWriter.WriteBytes({ 99, 98, 97 }); // the initializer list is converted to an array_view before being passed to WriteBytes.
}
```

<span data-ttu-id="6318e-111">Es gibt zwei Elemente, die daran beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="6318e-111">There are two pieces involved in making this work.</span></span> <span data-ttu-id="6318e-112">Die **DataWriter::WriteBytes**-Methode nimmt zunächst einen Parameter vom Typ [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) entgegen.</span><span class="sxs-lookup"><span data-stu-id="6318e-112">First, the **DataWriter::WriteBytes** method takes a parameter of type [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view).</span></span>

```cppwinrt
void WriteBytes(array_view<uint8_t const> value) const
```

 <span data-ttu-id="6318e-113">**array_view** ist ein benutzerdefinierter C++/WinRT-Typ, der eine zusammenhängende Reihe von Werten repräsentiert (er ist unter `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h` in der C++/WinRT-Basisbibliothek definiert).</span><span class="sxs-lookup"><span data-stu-id="6318e-113">**array_view** is a custom C++/WinRT type that safely represents a contiguous series of values (it is defined in the C++/WinRT base library, which is `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h`).</span></span>

<span data-ttu-id="6318e-114">Zweitens hat **array_view** einen Initialisierungslisten-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6318e-114">Second, **array_view** has an initializer-list constructor.</span></span>

```cppwinrt
template <typename T> array_view(std::initializer_list<T> value) noexcept
```

<span data-ttu-id="6318e-115">In vielen Fällen können Sie wählen, ob Sie **array_view** in Ihrer Programmierung berücksichtigen wollen oder nicht.</span><span class="sxs-lookup"><span data-stu-id="6318e-115">In many cases, you can choose whether or not to be aware of **array_view** in your programming.</span></span> <span data-ttu-id="6318e-116">Wenn Sie sich dafür entscheiden, dies *nicht* zu tun, müssen Sie keinen Code zu ändern, wenn ein entsprechender Typ in der C++ Standard Library auftaucht.</span><span class="sxs-lookup"><span data-stu-id="6318e-116">If you choose *not* to be aware of it then you won't have any code to change if and when an equivalent type appears in the C++ Standard Library.</span></span>

<span data-ttu-id="6318e-117">Sie können eine Initialisierungsliste an eine Windows-Runtime-API übergeben, die einen Collection-Parameter erwartet.</span><span class="sxs-lookup"><span data-stu-id="6318e-117">You can pass an initializer list to a Windows Runtime API that expects a collection parameter.</span></span> <span data-ttu-id="6318e-118">Nehmen wir zum Beispiel **StorageItemContentProperties::RetrievePropertiesAsync**.</span><span class="sxs-lookup"><span data-stu-id="6318e-118">Take **StorageItemContentProperties::RetrievePropertiesAsync** for example.</span></span>

```cppwinrt
IAsyncOperation<IMap<winrt::hstring, IInspectable>> StorageItemContentProperties::RetrievePropertiesAsync(IIterable<winrt::hstring> propertiesToRetrieve) const;
```

<span data-ttu-id="6318e-119">Sie können dieses API mit einer Initialisierungsliste wie dieser aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-119">You can call that API with an initializer list like this.</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const& storageFile)
{
    auto properties{ co_await storageFile.Properties().RetrievePropertiesAsync({ L"System.ItemUrl" }) };
}
```

<span data-ttu-id="6318e-120">Hier spielen zwei Faktoren eine Rolle.</span><span class="sxs-lookup"><span data-stu-id="6318e-120">Two factors are at work here.</span></span> <span data-ttu-id="6318e-121">Zuerst konstruiert der Callee ein **std::vector** aus der Initialisierungsliste (dieser Callee ist asynchron, also kann er das Objekt besitzen).</span><span class="sxs-lookup"><span data-stu-id="6318e-121">First, the callee constructs a **std::vector** from the initializer list (this callee is async, so it's able to own that object, which it must).</span></span> <span data-ttu-id="6318e-122">Zweitens bindet C++/WinRT **std::vector** transparent (und ohne Einführung von Kopien) als Windows-Runtime-Collection-Parameter.</span><span class="sxs-lookup"><span data-stu-id="6318e-122">Second, C++/WinRT transparently (and without introducing copies) binds **std::vector** as a Windows Runtime collection parameter.</span></span>

## <a name="standard-arrays-and-vectors"></a><span data-ttu-id="6318e-123">Standard-Arrays und -Vektoren</span><span class="sxs-lookup"><span data-stu-id="6318e-123">Standard arrays and vectors</span></span>
<span data-ttu-id="6318e-124">**array_view** hat ebenfalls **std::vector**- und **std::array**-Konvertierungskonstruktoren.</span><span class="sxs-lookup"><span data-stu-id="6318e-124">**array_view** also has conversion constructors from **std::vector** and **std::array**.</span></span>

```cppwinrt
template <typename C, size_type N> array_view(std::array<C, N>& value) noexcept
template <typename C> array_view(std::vector<C>& vectorValue) noexcept
```

<span data-ttu-id="6318e-125">Sie können also **DataWriter::WriteBytes** mit einem **std::vector** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-125">So, you could instead call **DataWriter::WriteBytes** with a **std::vector**.</span></span>

```cppwinrt
std::vector<byte> theVector{ 99, 98, 97 };
dataWriter.WriteBytes(theVector); // theVector is converted to an array_view before being passed to WriteBytes.
```

<span data-ttu-id="6318e-126">Oder mit einem **std::array**.</span><span class="sxs-lookup"><span data-stu-id="6318e-126">Or with a **std::array**.</span></span>

```cppwinrt
std::array<byte, 3> theArray{ 99, 98, 97 };
dataWriter.WriteBytes(theArray); // theArray is converted to an array_view before being passed to WriteBytes.
```

<span data-ttu-id="6318e-127">C++/WinRT bindet **std::vector** als Windows-Runtime-Collection-Parameter.</span><span class="sxs-lookup"><span data-stu-id="6318e-127">C++/WinRT binds **std::vector** as a Windows Runtime collection parameter.</span></span> <span data-ttu-id="6318e-128">Sie können also ein **std::vector&lt;winrt::hstring&gt;** übergeben und es wird in die entsprechende Windows-Runtime-Collection **winrt::hstring** konvertiert.</span><span class="sxs-lookup"><span data-stu-id="6318e-128">So, you can pass a **std::vector&lt;winrt::hstring&gt;**, and it will be converted to the appropriate Windows Runtime collection of **winrt::hstring**.</span></span> <span data-ttu-id="6318e-129">Es gibt eine zusätzliche Details zu beachten, wenn der Callee asynchron ist.</span><span class="sxs-lookup"><span data-stu-id="6318e-129">There's an extra detail to bear in mind if the callee is asynchronous.</span></span> <span data-ttu-id="6318e-130">Aufgrund der Implementierungsdetails von diesen Fall müssen Sie ein r-Wert bereitstellen, damit Sie eine Kopie bzw. das Verschieben des Vektors angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="6318e-130">Due to the implementation details of that case, you'll need to provide an rvalue, so you must provide a copy or a move of the vector.</span></span> <span data-ttu-id="6318e-131">Im folgenden Codebeispiel verschieben wir den Besitz des Vektors auf das Objekt des Typs Parameter akzeptiert, indem Sie den asynchronen Callee (und wir sind dann nicht für den Zugriff auf vorsichtig `vecH` erneut nach dem Verschieben).</span><span class="sxs-lookup"><span data-stu-id="6318e-131">In the code example below, we move ownership of the vector to the object of the parameter type accepted by the async callee (and then we're careful not to access `vecH` again after moving it).</span></span> <span data-ttu-id="6318e-132">Wenn Sie mehr über Rvalues erfahren möchten, finden Sie unter [Wertekategorien, und Verweise auf diese](cpp-value-categories.md).</span><span class="sxs-lookup"><span data-stu-id="6318e-132">If you want to know more about rvalues, see [Value categories, and references to them](cpp-value-categories.md).</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const storageFile, std::vector<winrt::hstring> vecH)
{
    auto properties{ co_await storageFile.Properties().RetrievePropertiesAsync(std::move(vecH)) };
}
```

<span data-ttu-id="6318e-133">Sie können aber kein **std::vector&lt;std::wstring&gt;** übergeben, da eine Windows-Runtime-Collection erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="6318e-133">But you can't pass a **std::vector&lt;std::wstring&gt;** where a Windows Runtime collection is expected.</span></span> <span data-ttu-id="6318e-134">Dies liegt daran, dass die C++ die Typparameter dieser Collection nicht erzwingt, nachdem sie in die entsprechende Windows-Runtime-Collection **std::wstring** konvertiert wurde.</span><span class="sxs-lookup"><span data-stu-id="6318e-134">This is because, having converted to the appropriate Windows Runtime collection of **std::wstring**, the C++ language won't then coerce that collection's type parameter(s).</span></span> <span data-ttu-id="6318e-135">Folglich das folgende Codebeispiel nicht kompiliert (und die Lösung besteht darin, übergeben Sie eine \*\*Std:: vector&lt;hstring&gt; \*\* stattdessen, wie oben gezeigt).</span><span class="sxs-lookup"><span data-stu-id="6318e-135">Consequently, the following code example won't compile (and the solution is to pass a **std::vector&lt;winrt::hstring&gt;** instead, as shown above).</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const& storageFile, std::vector<std::wstring> const& vecW)
{
    auto properties{ co_await storageFile.Properties().RetrievePropertiesAsync(std::move(vecW)) }; // error! Can't convert from vector of wstring to async_iterable of hstring.
}
```

## <a name="raw-arrays-and-pointer-ranges"></a><span data-ttu-id="6318e-136">Raw-Arrays und Zeigerbereiche</span><span class="sxs-lookup"><span data-stu-id="6318e-136">Raw arrays, and pointer ranges</span></span>
<span data-ttu-id="6318e-137">In Anbetracht dessen, dass in der C++ Standard Library in Zukunft ein äquivalenter Typ existieren könnte, können Sie auch direkt mit **array_view** arbeiten, wenn Sie dies wünschen oder benötigen.</span><span class="sxs-lookup"><span data-stu-id="6318e-137">Bearing in mind the caveat that an equivalent type may exist in the future in the C++ Standard Library, you can also work directly with **array_view** if you choose to, or need to.</span></span>

<span data-ttu-id="6318e-138">**Array_view** hat konvertierungskonstruktoren aus einem raw-Array und aus einer Reihe von \*\*T&ast; \*\* (Zeiger auf den Elementtyp).</span><span class="sxs-lookup"><span data-stu-id="6318e-138">**array_view** has conversion constructors from a raw array, and from a range of **T&ast;** (pointers to the element type).</span></span>

```cppwinrt
using namespace winrt;
...
byte theRawArray[]{ 99, 98, 97 };
array_view<byte const> fromRawArray{ theRawArray };
dataWriter.WriteBytes(fromRawArray); // the array_view is passed to WriteBytes.

array_view<byte const> fromRange{ theArray.data(), theArray.data() + 2 }; // just the first two elements.
dataWriter.WriteBytes(fromRange); // the array_view is passed to WriteBytes.
```

## <a name="winrtarrayview-functions-and-operators"></a><span data-ttu-id="6318e-139">winrt::array_view Funktionen und Operatoren</span><span class="sxs-lookup"><span data-stu-id="6318e-139">winrt::array_view functions and operators</span></span>
<span data-ttu-id="6318e-140">Eine Vielzahl von Konstruktoren, Operatoren, Funktionen und Iteratoren sind für **array_view** implementiert.</span><span class="sxs-lookup"><span data-stu-id="6318e-140">A host of constructors, operators, functions, and iterators are implemented for **array_view**.</span></span> <span data-ttu-id="6318e-141">Ein **array_view** ist ein Bereich, also können Sie ihn gültigkeitsbereichbasiert mit `for` oder mit **std::for_each** verwenden.</span><span class="sxs-lookup"><span data-stu-id="6318e-141">An **array_view** is a range, so you can use it with range-based `for`, or with **std::for_each**.</span></span>

<span data-ttu-id="6318e-142">Weitere Beispiele und Informationen finden Sie im API-Referenzthema zu [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view).</span><span class="sxs-lookup"><span data-stu-id="6318e-142">For more examples and info, see the [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) API reference topic.</span></span>

## <a name="ivectorlttgt-and-standard-iteration-constructs"></a><span data-ttu-id="6318e-143">\*\*IVector&lt;T&gt; \*\* und standard Iteration Konstrukte</span><span class="sxs-lookup"><span data-stu-id="6318e-143">**IVector&lt;T&gt;** and standard iteration constructs</span></span>
<span data-ttu-id="6318e-144">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) ist ein Beispiel für eine Windows-Runtime-API, die eine Sammlung von Typ zurückgibt [\*\*IVector&lt;T&gt; \*\*](/uwp/api/windows.foundation.collections.ivector_t_) (projiziert in C++ / WinRT als \*\*Winrt::Windows::Foundation::Collections::IVector&lt;T&gt; \*\* ).</span><span class="sxs-lookup"><span data-stu-id="6318e-144">[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) is an example of a Windows Runtime API that returns a collection of type [**IVector&lt;T&gt;**](/uwp/api/windows.foundation.collections.ivector_t_) (projected into C++/WinRT as **winrt::Windows::Foundation::Collections::IVector&lt;T&gt;**).</span></span> <span data-ttu-id="6318e-145">Sie können dieses Typs wie z. B. mit standardmäßigen Iteration Konstrukte verwenden bereichsbasierten `for`.</span><span class="sxs-lookup"><span data-stu-id="6318e-145">You can use this type with standard iteration constructs, such as range-based `for`.</span></span>

```cppwinrt
// main.cpp
#include "pch.h"
#include <winrt/Windows.Web.Syndication.h>
#include <iostream>

using namespace winrt;
using namespace Windows::Web::Syndication;

void PrintFeed(SyndicationFeed const& syndicationFeed)
{
    for (SyndicationItem const& syndicationItem : syndicationFeed.Items())
    {
        std::wcout << syndicationItem.Title().Text().c_str() << std::endl;
    }
}
```

## <a name="c-coroutines-with-asynchronous-windows-runtime-apis"></a><span data-ttu-id="6318e-146">C++-Coroutinen mit asynchronen Windows-Runtime-APIs</span><span class="sxs-lookup"><span data-stu-id="6318e-146">C++ coroutines with asynchronous Windows Runtime APIs</span></span>
<span data-ttu-id="6318e-147">Sie können weiterhin der [Parallel Patterns Library (PPL)](/cpp/parallel/concrt/parallel-patterns-library-ppl) verwenden, wenn Sie asynchrone Windows-Runtime APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6318e-147">You can continue to use the [Parallel Patterns Library (PPL)](/cpp/parallel/concrt/parallel-patterns-library-ppl) when calling asynchronous Windows Runtime APIs.</span></span> <span data-ttu-id="6318e-148">In vielen Fällen bieten C++ Coroutinen jedoch eine effiziente und mehr einfach codierten Ausdrucksweise für die Interaktion mit asynchronen Objekte.</span><span class="sxs-lookup"><span data-stu-id="6318e-148">However, in many cases, C++ coroutines provide an efficient and more easily-coded idiom for interacting with asynchronous objects.</span></span> <span data-ttu-id="6318e-149">Weitere Informationen und Codebeispiele finden Sie unter [Parallelität und asynchrone Vorgänge mit C++ / WinRT](concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="6318e-149">For more info, and code examples, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md).</span></span>

## <a name="important-apis"></a><span data-ttu-id="6318e-150">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="6318e-150">Important APIs</span></span>
* [<span data-ttu-id="6318e-151">IVector&lt;T&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="6318e-151">IVector&lt;T&gt; interface</span></span>](/uwp/api/windows.foundation.collections.ivector_t_)
* [<span data-ttu-id="6318e-152">winrt::array_view Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="6318e-152">winrt::array_view struct template</span></span>](/uwp/cpp-ref-for-winrt/array-view)

## <a name="related-topics"></a><span data-ttu-id="6318e-153">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6318e-153">Related topics</span></span>
* [<span data-ttu-id="6318e-154">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="6318e-154">String handling in C++/WinRT</span></span>](strings.md)
