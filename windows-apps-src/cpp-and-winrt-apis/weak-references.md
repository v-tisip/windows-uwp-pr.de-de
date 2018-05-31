---
author: stevewhims
description: Die Unterstützung von schwachen Referenzen in C++/WinRT kostet Sie nichts. Es sei denn Ihr Objekt wird auf IWeakReferenceSource abgefragt.
title: Schwache Referenzen in C++/WinRT
ms.author: stwhi
ms.date: 04/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, schwache, referenz
ms.localizationpriority: medium
ms.openlocfilehash: 63ffad19c0ae8a52737ae13a54e5657df875d0b5
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832604"
---
# <a name="weak-references-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="acf90-104">Schwache Referenzen in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="acf90-104">Weak references in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
<span data-ttu-id="acf90-105">Sie sollten in der Lage sein, Ihre eigenen C++/WinRT-APIs so zu gestalten, dass zyklische Referenzen und schwache Referenzen vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="acf90-105">You should be able, more often than not, to design your own C++/WinRT APIs in such a way as to avoid the need for cyclic references and weak references.</span></span> <span data-ttu-id="acf90-106">Bei der nativen Implementierung des XAML-basierten UI-Frameworks ist der schwache Referenzmechanismus aufgrund des historischen Designs des Frameworks in C++/WinRT jedoch notwendig, um zyklische Referenzen zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="acf90-106">However, when it comes to the native implementation of the XAML-based UI frameworkL&mdash;because of the historic design of the framework&mdash;the weak reference mechanism in C++/WinRT is necessary to handle cyclic references.</span></span> <span data-ttu-id="acf90-107">Außerhalb von XAML ist es unwahrscheinlich, dass Sie schwache Referenzen verwenden müssen (obwohl es theoretisch nichts XAML-spezifisches an ihnen gibt).</span><span class="sxs-lookup"><span data-stu-id="acf90-107">Outside of XAML, it's unlikely you'll need to use weak references (although, there’s nothing XAML-specific about them in theory).</span></span>

<span data-ttu-id="acf90-108">Bei einem von Ihnen deklarierten Typ ist es für C++/WinRT nicht sofort ersichtlich, ob oder wann schwache Referenzen benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="acf90-108">For any given type that you declare, it's not immediately obvious to C++/WinRT whether or when weak references are needed.</span></span> <span data-ttu-id="acf90-109">Daher bietet C++/WinRT für die Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) automatisch eine Unterstützung von schwache Referenzen. Von dieser werden Ihre eigenen C++/WinRT-Typen direkt oder indirekt abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="acf90-109">So, C++/WinRT provides weak reference support automatically on the struct template [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements), from which your own C++/WinRT types directly or indirectly derive.</span></span> <span data-ttu-id="acf90-110">Dies kostet Sie nichts, es sei denn, Ihr Objekt wird tatsächlich auf [**IWeakReferenceSource**](https://msdn.microsoft.com/library/br224609) abgefragt.</span><span class="sxs-lookup"><span data-stu-id="acf90-110">It's pay-for-play, in that it doesn't cost you anything unless your object is actually queried for [**IWeakReferenceSource**](https://msdn.microsoft.com/library/br224609).</span></span> <span data-ttu-id="acf90-111">Und Sie können sich explizit [gegen diese Unterstützung](#opting-out-of-weak-reference-support) entscheiden.</span><span class="sxs-lookup"><span data-stu-id="acf90-111">And you can choose explicitly to [opt out of that support](#opting-out-of-weak-reference-support).</span></span>

## <a name="code-examples"></a><span data-ttu-id="acf90-112">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="acf90-112">Code examples</span></span>
<span data-ttu-id="acf90-113">Die Strukturvorlage [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) ist eine Option, um eine schwache Referenz auf eine Klasseninstanz zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="acf90-113">The [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) struct template is one option for getting a weak reference to a class instance.</span></span>

```cppwinrt
Class c;
winrt::weak_ref<Class> weak{ c };
```
<span data-ttu-id="acf90-114">Oder Sie können die Hilfsfunktion [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) verwenden.</span><span class="sxs-lookup"><span data-stu-id="acf90-114">Or, you can use the use the [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) helper function.</span></span>

```cppwinrt
Class c;
auto weak = winrt::make_weak(c);
```

<span data-ttu-id="acf90-115">Die Erstellung einer schwachen Referenz hat keinen Einfluss auf die Anzahl der Referenzen auf das Objekt selbst, sondern bewirkt lediglich die Zuweisung eines Kontrollblocks.</span><span class="sxs-lookup"><span data-stu-id="acf90-115">Creating a weak reference doesn't affect the reference count on the object itself; it just causes a control block to be allocated.</span></span> <span data-ttu-id="acf90-116">Dieser Kontrollblock kümmert sich um die Implementierung der schwachen Referenzsemantik.</span><span class="sxs-lookup"><span data-stu-id="acf90-116">That control block takes care of implementing the weak reference semantics.</span></span> <span data-ttu-id="acf90-117">Sie können dann versuchen, den schwachen Verweis auf einen starken Verweis hochzustufen (und, wenn dies erfolgreich ist, ihn zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="acf90-117">You can then try to promote the weak reference to a strong reference and, if successful, use it.</span></span>

```cppwinrt
if (Class strong = weak.get())
{
    // use strong, for example strong.DoWork();
}
```

<span data-ttu-id="acf90-118">Sofern noch eine andere starke Referenz existiert, erhöht der Aufruf von [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) die Referenzanzahl und gibt die starke Referenz an den Aufrufer zurück.</span><span class="sxs-lookup"><span data-stu-id="acf90-118">Provided that some other strong reference still exists, the [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) call increments the reference count and returns the strong reference to the caller.</span></span>

## <a name="a-weak-reference-to-the-this-pointer"></a><span data-ttu-id="acf90-119">Eine schwache Referenz auf den *this*-Zeiger</span><span class="sxs-lookup"><span data-stu-id="acf90-119">A weak reference to the *this* pointer</span></span>
<span data-ttu-id="acf90-120">Ein C++/WinRT-Objekt leitet sich direkt oder indirekt aus der Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) ab.</span><span class="sxs-lookup"><span data-stu-id="acf90-120">A C++/WinRT object directly or indirectly derives from the struct template [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements).</span></span> <span data-ttu-id="acf90-121">Die geschützte [**implements::get_weak protected**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) Mitgliedsfunktion gibt eine schwache Referenz auf den *this*-Zeiger eines C++/WinRT-Objekts zurück.</span><span class="sxs-lookup"><span data-stu-id="acf90-121">The [**implements::get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) protected member function returns a weak reference to a C++/WinRT object's *this* pointer.</span></span> <span data-ttu-id="acf90-122">[**implements.get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) erhält eine starke Referenz.</span><span class="sxs-lookup"><span data-stu-id="acf90-122">[**implements.get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) gets a strong reference.</span></span>

## <a name="opting-out-of-weak-reference-support"></a><span data-ttu-id="acf90-123">Opt-out der Unterstützung von schwachen Referenzen</span><span class="sxs-lookup"><span data-stu-id="acf90-123">Opting out of weak reference support</span></span>
<span data-ttu-id="acf90-124">Die Unterstützung schwacher Referenzen erfolgt automatisch.</span><span class="sxs-lookup"><span data-stu-id="acf90-124">Weak reference support is automatic.</span></span> <span data-ttu-id="acf90-125">Sie können diese Unterstützung jedoch explizit deaktivieren, indem Sie die [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.</span><span class="sxs-lookup"><span data-stu-id="acf90-125">But you can choose explicitly to opt out of that support by passing the [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref) marker struct as a template argument to your base class.</span></span>

<span data-ttu-id="acf90-126">Wenn Sie direkt von **winrt::implements** ableiten.</span><span class="sxs-lookup"><span data-stu-id="acf90-126">If you derive directly from **winrt::implements**.</span></span>

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, no_weak_ref>
{
    ...
}
```

<span data-ttu-id="acf90-127">Wenn Sie eine Laufzeitklasse schreiben.</span><span class="sxs-lookup"><span data-stu-id="acf90-127">If you're authoring a runtime class.</span></span>

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, no_weak_ref>
{
    ...
}
```

<span data-ttu-id="acf90-128">Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint.</span><span class="sxs-lookup"><span data-stu-id="acf90-128">It doesn't matter where in the variadic parameter pack the marker struct appears.</span></span> <span data-ttu-id="acf90-129">Wenn Sie eine schwache Referenz für einen Opted-Out-Typ anfordern, dann hilft Ihnen der Compiler mit der Meldung „*Dies ist nur für die Unterstützung schwacher Referenzen*”.</span><span class="sxs-lookup"><span data-stu-id="acf90-129">If you request a weak reference for an opted-out type, then the compiler will help you out with "*This is only for weak ref support*".</span></span>

## <a name="important-apis"></a><span data-ttu-id="acf90-130">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="acf90-130">Important APIs</span></span>
* [<span data-ttu-id="acf90-131">implements::get_weak Funktion</span><span class="sxs-lookup"><span data-stu-id="acf90-131">implements::get_weak function</span></span>](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [<span data-ttu-id="acf90-132">winrt::make_weak Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="acf90-132">winrt::make_weak function template</span></span>](/uwp/cpp-ref-for-winrt/make-weak)
* [<span data-ttu-id="acf90-133">winrt::no_weak_ref Markerstruktur</span><span class="sxs-lookup"><span data-stu-id="acf90-133">winrt::no_weak_ref marker struct</span></span>](/uwp/cpp-ref-for-winrt/no-weak-ref)
* [<span data-ttu-id="acf90-134">winrt::weak_ref Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="acf90-134">winrt::weak_ref struct template</span></span>](/uwp/cpp-ref-for-winrt/weak-ref)
