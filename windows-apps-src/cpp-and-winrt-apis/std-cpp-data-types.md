---
author: stevewhims
description: Mit C++/WinRT können Sie Windows-Runtime-APIs über Standard-C++ Datentypen aufrufen.
title: Standard C++ Datentypen und C++/WinRT
ms.author: stwhi
ms.date: 04/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, datentypen
ms.localizationpriority: medium
ms.openlocfilehash: ccf79b1ec21688d9573e62777def8f15295c3fca
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832074"
---
# <a name="standard-c-data-types-and-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="cedf7-104">Standard C++ Datentypen und [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="cedf7-104">Standard C++ data types and [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
<span data-ttu-id="cedf7-105">Mit C++/WinRT können Sie Windows-Runtime-APIs über Standard-C++ Datentypen aufrufen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-105">With C++/WinRT, you can call Windows Runtime APIs using Standard C++ data types, including some C++ Standard Library data types.</span></span>

## <a name="standard-initializer-lists"></a><span data-ttu-id="cedf7-106">Standard-Initialisierungslisten</span><span class="sxs-lookup"><span data-stu-id="cedf7-106">Standard initializer lists</span></span>
<span data-ttu-id="cedf7-107">Eine Initialisierungsliste (**std::initializer_list**) ist ein Konstrukt aus der C++ Standard Library.</span><span class="sxs-lookup"><span data-stu-id="cedf7-107">An initializer list (**std::initializer_list**) is a C++ Standard Library construct.</span></span> <span data-ttu-id="cedf7-108">Sie können Initialisierungslisten verwenden, wenn Sie bestimmte Windows-Runtime-Konstruktoren und -Methoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-108">You can use initializer lists when you call certain Windows Runtime constructors and methods.</span></span> <span data-ttu-id="cedf7-109">Beispielsweise können Sie [**DataWriter::WriteBytes**](/uwp/api/windows.storage.streams.datawriter.writebytes) mit einer Initialisierungsliste aufrufen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-109">For example, you can call [**DataWriter::WriteBytes**](/uwp/api/windows.storage.streams.datawriter.writebytes) with one.</span></span>

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

<span data-ttu-id="cedf7-110">Es gibt zwei Elemente, die daran beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="cedf7-110">There are two pieces involved in making this work.</span></span> <span data-ttu-id="cedf7-111">Die **DataWriter::WriteBytes**-Methode nimmt zunächst einen Parameter vom Typ [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) entgegen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-111">First, the **DataWriter::WriteBytes** method takes a parameter of type [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view).</span></span>

```cppwinrt
void WriteBytes(array_view<uint8_t const> value) const
```

 <span data-ttu-id="cedf7-112">**array_view** ist ein benutzerdefinierter C++/WinRT-Typ, der eine zusammenhängende Reihe von Werten repräsentiert (er ist unter `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h` in der C++/WinRT-Basisbibliothek definiert).</span><span class="sxs-lookup"><span data-stu-id="cedf7-112">**array_view** is a custom C++/WinRT type that safely represents a contiguous series of values (it is defined in the C++/WinRT base library, which is `%WindowsSdkDir%Include\<WindowsTargetPlatformVersion>\cppwinrt\winrt\base.h`).</span></span>

<span data-ttu-id="cedf7-113">Zweitens hat **array_view** einen Initialisierungslisten-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="cedf7-113">Second, **array_view** has an initializer-list constructor.</span></span>

```cppwinrt
template <typename T> array_view(std::initializer_list<T> value) noexcept
```

<span data-ttu-id="cedf7-114">In vielen Fällen können Sie wählen, ob Sie **array_view** in Ihrer Programmierung berücksichtigen wollen oder nicht.</span><span class="sxs-lookup"><span data-stu-id="cedf7-114">In many cases, you can choose whether or not to be aware of **array_view** in your programming.</span></span> <span data-ttu-id="cedf7-115">Wenn Sie sich dafür entscheiden, dies *nicht* zu tun, müssen Sie keinen Code zu ändern, wenn ein entsprechender Typ in der C++ Standard Library auftaucht.</span><span class="sxs-lookup"><span data-stu-id="cedf7-115">If you choose *not* to be aware of it then you won't have any code to change if and when an equivalent type appears in the C++ Standard Library.</span></span>

<span data-ttu-id="cedf7-116">Sie können eine Initialisierungsliste an eine Windows-Runtime-API übergeben, die einen Collection-Parameter erwartet.</span><span class="sxs-lookup"><span data-stu-id="cedf7-116">You can pass an initializer list to a Windows Runtime API that expects a collection parameter.</span></span> <span data-ttu-id="cedf7-117">Nehmen wir zum Beispiel **StorageItemContentProperties::RetrievePropertiesAsync**.</span><span class="sxs-lookup"><span data-stu-id="cedf7-117">Take **StorageItemContentProperties::RetrievePropertiesAsync** for example.</span></span>

```cppwinrt
IAsyncOperation<IMap<winrt::hstring, IInspectable>> StorageItemContentProperties::RetrievePropertiesAsync(IIterable<winrt::hstring> propertiesToRetrieve) const;
```

<span data-ttu-id="cedf7-118">Sie können dieses API mit einer Initialisierungsliste wie dieser aufrufen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-118">You can call that API with an initializer list like this.</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const& storageFile)
{
    auto properties = co_await storageFile.Properties().RetrievePropertiesAsync({ L"System.ItemUrl" });
}
```

<span data-ttu-id="cedf7-119">Hier spielen zwei Faktoren eine Rolle.</span><span class="sxs-lookup"><span data-stu-id="cedf7-119">Two factors are at work here.</span></span> <span data-ttu-id="cedf7-120">Zuerst konstruiert der Callee ein **std::vector** aus der Initialisierungsliste (dieser Callee ist asynchron, also kann er das Objekt besitzen).</span><span class="sxs-lookup"><span data-stu-id="cedf7-120">First, the callee constructs a **std::vector** from the initializer list (this callee is async, so it's able to own that object, which it must).</span></span> <span data-ttu-id="cedf7-121">Zweitens bindet C++/WinRT **std::vector** transparent (und ohne Einführung von Kopien) als Windows-Runtime-Collection-Parameter.</span><span class="sxs-lookup"><span data-stu-id="cedf7-121">Second, C++/WinRT transparently (and without introducing copies) binds **std::vector** as a Windows Runtime collection parameter.</span></span>

## <a name="standard-arrays-and-vectors"></a><span data-ttu-id="cedf7-122">Standard-Arrays und -Vektoren</span><span class="sxs-lookup"><span data-stu-id="cedf7-122">Standard arrays and vectors</span></span>
<span data-ttu-id="cedf7-123">**array_view** hat ebenfalls **std::vector**- und **std::array**-Konvertierungskonstruktoren.</span><span class="sxs-lookup"><span data-stu-id="cedf7-123">**array_view** also has conversion constructors from **std::vector** and **std::array**.</span></span>

```cppwinrt
template <typename C, size_type N> array_view(std::array<C, N>& value) noexcept
template <typename C> array_view(std::vector<C>& vectorValue) noexcept
```

<span data-ttu-id="cedf7-124">Sie können also **DataWriter::WriteBytes** mit einem **std::vector** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-124">So, you could instead call **DataWriter::WriteBytes** with a **std::vector**.</span></span>

```cppwinrt
std::vector<byte> theVector{ 99, 98, 97 };
dataWriter.WriteBytes(theVector); // theVector is converted to an array_view before being passed to WriteBytes.
```

<span data-ttu-id="cedf7-125">Oder mit einem **std::array**.</span><span class="sxs-lookup"><span data-stu-id="cedf7-125">Or with a **std::array**.</span></span>

```cppwinrt
std::array<byte, 3> theArray{ 99, 98, 97 };
dataWriter.WriteBytes(theArray); // theArray is converted to an array_view before being passed to WriteBytes.
```

<span data-ttu-id="cedf7-126">C++/WinRT bindet **std::vector** als Windows-Runtime-Collection-Parameter.</span><span class="sxs-lookup"><span data-stu-id="cedf7-126">C++/WinRT binds **std::vector** as a Windows Runtime collection parameter.</span></span> <span data-ttu-id="cedf7-127">Sie können also ein **std::vector&lt;winrt::hstring&gt;** übergeben und es wird in die entsprechende Windows-Runtime-Collection **winrt::hstring** konvertiert.</span><span class="sxs-lookup"><span data-stu-id="cedf7-127">So, you can pass a **std::vector&lt;winrt::hstring&gt;**, and it will be converted to the appropriate Windows Runtime collection of **winrt::hstring**.</span></span> <span data-ttu-id="cedf7-128">Wenn der Callee asynchron ist, müssen Sie den Vektor entweder kopieren oder verschieben.</span><span class="sxs-lookup"><span data-stu-id="cedf7-128">If the callee is async then you must either copy or move the vector.</span></span> <span data-ttu-id="cedf7-129">Im folgenden Codebeispiel verschieben wir den Besitz des Vektors in den asynchronen Callee.</span><span class="sxs-lookup"><span data-stu-id="cedf7-129">In the code example below, we move ownership of the vector to the async callee.</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const& storageFile, std::vector<winrt::hstring> const& vecH)
{
    auto properties = co_await storageFile.Properties().RetrievePropertiesAsync(std::move(vecH));
}
```

<span data-ttu-id="cedf7-130">Sie können aber kein **std::vector&lt;std::wstring&gt;** übergeben, da eine Windows-Runtime-Collection erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="cedf7-130">But you can't pass a **std::vector&lt;std::wstring&gt;** where a Windows Runtime collection is expected.</span></span> <span data-ttu-id="cedf7-131">Dies liegt daran, dass die C++ die Typparameter dieser Collection nicht erzwingt, nachdem sie in die entsprechende Windows-Runtime-Collection **std::wstring** konvertiert wurde.</span><span class="sxs-lookup"><span data-stu-id="cedf7-131">This is because, having converted to the appropriate Windows Runtime collection of **std::wstring**, the C++ language won't then coerce that collection's type parameter(s).</span></span> <span data-ttu-id="cedf7-132">Folglich wird das folgende Codebeispiel nicht kompiliert.</span><span class="sxs-lookup"><span data-stu-id="cedf7-132">Consequently, the following code example won't compile.</span></span>

```cppwinrt
IAsyncAction retrieve_properties_async(StorageFile const& storageFile, std::vector<std::wstring> const& vecW)
{
    auto properties = co_await storageFile.Properties().RetrievePropertiesAsync(std::move(vecW)); // error! Can't convert from vector of wstring to async_iterable of hstring.
}
```

## <a name="raw-arrays-and-pointer-ranges"></a><span data-ttu-id="cedf7-133">Raw-Arrays und Zeigerbereiche</span><span class="sxs-lookup"><span data-stu-id="cedf7-133">Raw arrays, and pointer ranges</span></span>
<span data-ttu-id="cedf7-134">In Anbetracht dessen, dass in der C++ Standard Library in Zukunft ein äquivalenter Typ existieren könnte, können Sie auch direkt mit **array_view** arbeiten, wenn Sie dies wünschen oder benötigen.</span><span class="sxs-lookup"><span data-stu-id="cedf7-134">Bearing in mind the caveat that an equivalent type may exist in the future in the C++ Standard Library, you can also work directly with **array_view** if you choose to, or need to.</span></span>

<span data-ttu-id="cedf7-135">**array_view** hat Konvertierungskonstruktoren aus einem Raw-Array und aus einem Bereich von **T**\* (Zeiger auf den Elementtyp).</span><span class="sxs-lookup"><span data-stu-id="cedf7-135">**array_view** has conversion constructors from a raw array, and from a range of **T**\* (pointers to the element type).</span></span>

```cppwinrt
using namespace winrt;
...
byte theRawArray[]{ 99, 98, 97 };
array_view<byte const> fromRawArray{ theRawArray };
dataWriter.WriteBytes(fromRawArray); // the array_view is passed to WriteBytes.

array_view<byte const> fromRange{ theArray.data(), theArray.data() + 2 }; // just the first two elements.
dataWriter.WriteBytes(fromRange); // the array_view is passed to WriteBytes.
```

## <a name="winrtarrayview-functions-and-operators"></a><span data-ttu-id="cedf7-136">winrt::array_view Funktionen und Operatoren</span><span class="sxs-lookup"><span data-stu-id="cedf7-136">winrt::array_view functions and operators</span></span>
<span data-ttu-id="cedf7-137">Eine Vielzahl von Konstruktoren, Operatoren, Funktionen und Iteratoren sind für **array_view** implementiert.</span><span class="sxs-lookup"><span data-stu-id="cedf7-137">A host of constructors, operators, functions, and iterators are implemented for **array_view**.</span></span> <span data-ttu-id="cedf7-138">Ein **array_view** ist ein Bereich, also können Sie ihn gültigkeitsbereichbasiert mit `for` oder mit **std::for_each** verwenden.</span><span class="sxs-lookup"><span data-stu-id="cedf7-138">An **array_view** is a range, so you can use it with range-based `for`, or with **std::for_each**.</span></span>

<span data-ttu-id="cedf7-139">Weitere Beispiele und Informationen finden Sie im API-Referenzthema zu [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view).</span><span class="sxs-lookup"><span data-stu-id="cedf7-139">For more examples and info, see the [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) API reference topic.</span></span>

## <a name="important-apis"></a><span data-ttu-id="cedf7-140">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="cedf7-140">Important APIs</span></span>
* [<span data-ttu-id="cedf7-141">winrt::array_view Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="cedf7-141">winrt::array_view struct template</span></span>](/uwp/cpp-ref-for-winrt/array-view)
