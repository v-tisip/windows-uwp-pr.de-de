---
author: stevewhims
description: Ein agiles Objekt ist ein Objekt, auf das von jedem Thread aus zugegriffen werden kann. Ihre C++/WinRT-Typen sind standardmäßig agil, aber Sie können diese Option deaktivieren.
title: Agile Objekte mit C++/WinRT
ms.author: stwhi
ms.date: 10/20/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, agil, objekt, agilität, IAgileObject
ms.localizationpriority: medium
ms.openlocfilehash: 2fa129a60c7dfcc170a9ddeec318a062fb8cbe56
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5683499"
---
# <a name="agile-objects-in-cwinrt"></a><span data-ttu-id="8126e-105">Agile Objekte in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="8126e-105">Agile objects in C++/WinRT</span></span>

<span data-ttu-id="8126e-106">In den meisten Fällen kann eine Instanz einer Windows-Runtime-Klasse zugegriffen werden, von einem anderen Thread (genau wie die meisten standard C++-Objekte können).</span><span class="sxs-lookup"><span data-stu-id="8126e-106">In the vast majority of cases, an instance of a Windows Runtime class can be accessed from any thread (just like most standard C++ objects can).</span></span> <span data-ttu-id="8126e-107">Eine solche Windows-Runtime-Klasse ist *agil*.</span><span class="sxs-lookup"><span data-stu-id="8126e-107">Such a Windows Runtime class is *agile*.</span></span> <span data-ttu-id="8126e-108">Nur eine geringe Anzahl von Windows-Runtime-Klassen, die im Lieferumfang von Windows nicht agil sind, aber wenn Sie sie nutzen, Sie ihre threading-Modell und Ihr marshaling-Verhalten berücksichtigen müssen (marshaling ist die Weitergabe von Daten über eine Apartmentgrenze).</span><span class="sxs-lookup"><span data-stu-id="8126e-108">Only a small number of Windows Runtime classes that ship with Windows are non-agile, but when you consume them you need to take into consideration their threading model and marshaling behavior (marshaling is passing data across an apartment boundary).</span></span> <span data-ttu-id="8126e-109">Es ist ein guter Standard für jedes Windows-Runtime-Objekt, agil zu sein, Ihre eigenen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Typen sind standardmäßig agil.</span><span class="sxs-lookup"><span data-stu-id="8126e-109">It's a good default for every Windows Runtime object to be agile, so your own [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) types are agile by default.</span></span>

<span data-ttu-id="8126e-110">Sie können jedoch auch von dieser Regel abweichen. Möglicherweise haben Sie einen zwingenden Grund, ein Objekt Ihres Typs zu beschränken (zum Beispiel in einer Anwendung mit einem einzelnen Thread).</span><span class="sxs-lookup"><span data-stu-id="8126e-110">But you can opt out. You might have a compelling reason to require an object of your type to reside, for example, in a given single-threaded apartment.</span></span> <span data-ttu-id="8126e-111">Dies hat typischerweise mit Wiedereinsprungsvoraussetzungen zu tun.</span><span class="sxs-lookup"><span data-stu-id="8126e-111">This typically has to do with reentrancy requirements.</span></span> <span data-ttu-id="8126e-112">Aber auch die UI-APIs (User Interface, Benutzerschnittstelle) bieten zunehmend agile Objekte.</span><span class="sxs-lookup"><span data-stu-id="8126e-112">But increasingly, even user interface (UI) APIs offer agile objects.</span></span> <span data-ttu-id="8126e-113">Im Allgemeinen ist Agilität die einfachste und leistungsfähigste Option.</span><span class="sxs-lookup"><span data-stu-id="8126e-113">In general, agility is the simplest and most performant option.</span></span> <span data-ttu-id="8126e-114">Auch wenn Sie eine Aktivierungs-Factory implementieren, muss diese agil sein (auch, wenn Ihre entsprechende Laufzeitklasse es nicht ist).</span><span class="sxs-lookup"><span data-stu-id="8126e-114">Also, when you implement an activation factory, it must be agile even if your corresponding runtime class isn't.</span></span>

> [!NOTE]
> <span data-ttu-id="8126e-115">Windows-Runtime basiert auf COM.</span><span class="sxs-lookup"><span data-stu-id="8126e-115">The Windows Runtime is based on COM.</span></span> <span data-ttu-id="8126e-116">Im Sinne von COM ist eine agile Klasse mit `ThreadingModel` = *Both* registriert.</span><span class="sxs-lookup"><span data-stu-id="8126e-116">In COM terms, an agile class is registered with `ThreadingModel` = *Both*.</span></span> <span data-ttu-id="8126e-117">Weitere Informationen zu COM-threading-Modellen und Apartments finden Sie [verstehen und Verwenden von COM-Threading-Modellen](https://msdn.microsoft.com/library/ms809971).</span><span class="sxs-lookup"><span data-stu-id="8126e-117">For more info about COM threading models, and apartments, see [Understanding and Using COM Threading Models](https://msdn.microsoft.com/library/ms809971).</span></span>

## <a name="code-examples"></a><span data-ttu-id="8126e-118">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="8126e-118">Code examples</span></span>

<span data-ttu-id="8126e-119">Lassen Sie uns eine Beispiel einer Implementierung einer Laufzeitklasse verwenden, um zu veranschaulichen wie C++ / WinRT Agilität unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8126e-119">Let's use an example implementation of a runtime class to illustrate how C++/WinRT supports agility.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

struct MyType : winrt::implements<MyType, IStringable>
{
    winrt::hstring ToString(){ ... }
};
```

<span data-ttu-id="8126e-120">Da wir dies nicht explizit ausschließen, ist diese Implementierung agil.</span><span class="sxs-lookup"><span data-stu-id="8126e-120">Because we haven't opted out, this implementation is agile.</span></span> <span data-ttu-id="8126e-121">Die [**winrt::implementiert**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur implementiert [**IAgileObject**](https://msdn.microsoft.com/library/windows/desktop/hh802476) und [**IMarshal**](/windows/desktop/api/objidl/nn-objidl-imarshal).</span><span class="sxs-lookup"><span data-stu-id="8126e-121">The [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) base struct implements [**IAgileObject**](https://msdn.microsoft.com/library/windows/desktop/hh802476) and [**IMarshal**](/windows/desktop/api/objidl/nn-objidl-imarshal).</span></span> <span data-ttu-id="8126e-122">Die **IMarshal**-Implementierung verwendet **CoCreateFreeThreadedMarshaler**, um das Legacy-Code zu unterstützen, der nichts über **IAgileObject** weiß.</span><span class="sxs-lookup"><span data-stu-id="8126e-122">The **IMarshal** implementation uses **CoCreateFreeThreadedMarshaler** to do the right thing for legacy code that doesn't know about **IAgileObject**.</span></span>

<span data-ttu-id="8126e-123">Dieser Code prüft ein Objekt auf Agilität.</span><span class="sxs-lookup"><span data-stu-id="8126e-123">This code checks an object for agility.</span></span> <span data-ttu-id="8126e-124">Der Aufruf von [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) löst eine Ausnahme aus, wenn `myimpl` nicht agil ist.</span><span class="sxs-lookup"><span data-stu-id="8126e-124">The call to [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) throws an exception if `myimpl` is not agile.</span></span>

```cppwinrt
winrt::com_ptr<MyType> myimpl{ winrt::make_self<MyType>() };
winrt::com_ptr<IAgileObject> iagileobject{ myimpl.as<IAgileObject>() };
```

<span data-ttu-id="8126e-125">Anstatt eine Ausnahme zu verarbeiten, können Sie [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="8126e-125">Rather than handle an exception, you can call [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) instead.</span></span>

```cppwinrt
winrt::com_ptr<IAgileObject> iagileobject{ myimpl.try_as<IAgileObject>() };
if (iagileobject) { /* myimpl is agile. */ }
```

<span data-ttu-id="8126e-126">**IAgileObject** hat keine eigenen Methoden, sodass man damit nicht viel anfangen kann.</span><span class="sxs-lookup"><span data-stu-id="8126e-126">**IAgileObject** has no methods of its own, so you can't do much with it.</span></span> <span data-ttu-id="8126e-127">Diese nächste Variante ist eher typisch.</span><span class="sxs-lookup"><span data-stu-id="8126e-127">This next variant, then, is more typical.</span></span>

```cppwinrt
if (myimpl.try_as<IAgileObject>()) { /* myimpl is agile. */ }
```

<span data-ttu-id="8126e-128">**IAgileObject** ist eine *Marker-Schnittstelle*.</span><span class="sxs-lookup"><span data-stu-id="8126e-128">**IAgileObject** is a *marker interface*.</span></span> <span data-ttu-id="8126e-129">Der Nutzen der Abfrage von **IAgileObject** besteht aus der Informationen zum Erfolg oder Misserfolg.</span><span class="sxs-lookup"><span data-stu-id="8126e-129">The mere success or failure of querying for **IAgileObject** is the extent of the information and utility you get from it.</span></span>

## <a name="opting-out-of-agile-object-support"></a><span data-ttu-id="8126e-130">Vermeiden der Unterstützung von agilen Objekten</span><span class="sxs-lookup"><span data-stu-id="8126e-130">Opting out of agile object support</span></span>

<span data-ttu-id="8126e-131">Sie können die Unterstützung für agile Objekte explizit deaktivieren, indem Sie die [**winrt::non_agile**](/uwp/cpp-ref-for-winrt/non_agile)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.</span><span class="sxs-lookup"><span data-stu-id="8126e-131">You can choose explicitly to opt out of agile object support by passing the [**winrt::non_agile**](/uwp/cpp-ref-for-winrt/non_agile) marker struct as a template argument to your base class.</span></span>

<span data-ttu-id="8126e-132">Wenn Sie direkt von **winrt::implements** ableiten.</span><span class="sxs-lookup"><span data-stu-id="8126e-132">If you derive directly from **winrt::implements**.</span></span>

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, winrt::non_agile>
{
    ...
}
```

<span data-ttu-id="8126e-133">Wenn Sie eine Laufzeitklasse schreiben.</span><span class="sxs-lookup"><span data-stu-id="8126e-133">If you're authoring a runtime class.</span></span>

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, winrt::non_agile>
{
    ...
}
```

<span data-ttu-id="8126e-134">Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint.</span><span class="sxs-lookup"><span data-stu-id="8126e-134">It doesn't matter where in the variadic parameter pack the marker struct appears.</span></span>

<span data-ttu-id="8126e-135">Unabhängig davon, ob Sie die Agilität, können Sie **IMarshal** selbst implementieren.</span><span class="sxs-lookup"><span data-stu-id="8126e-135">Whether or not you opt out of agility, you can implement **IMarshal** yourself.</span></span> <span data-ttu-id="8126e-136">Z. B. Sie den Marker **WinRT:: non_agile** verwenden, um die Standard-agilitäts-Implementierung zu vermeiden und **IMarshal** selbst implementieren können&mdash;um die Marshal-by-Value-Semantik zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8126e-136">For example, you can use the **winrt::non_agile** marker to avoid the default agility implementation, and implement **IMarshal** yourself&mdash;perhaps to support marshal-by-value semantics.</span></span>

## <a name="agile-references-winrtagileref"></a><span data-ttu-id="8126e-137">Agile Referenzen (winrt::agile_ref)</span><span class="sxs-lookup"><span data-stu-id="8126e-137">Agile references (winrt::agile_ref)</span></span>

<span data-ttu-id="8126e-138">Wenn Sie ein Objekt verwenden, das nicht agil ist, aber Sie es in einem potentiell agilen Kontext weitergeben müssen, dann ist eine Option die Verwendung der [**winrt::agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref)-Strukturvorlage. So erhalten Sie eine agile Referenz auf eine Instanz eines nicht agilen Typs oder auf eine Schnittstelle eines nicht agilen Objekts.</span><span class="sxs-lookup"><span data-stu-id="8126e-138">If you're consuming an object that isn't agile, but you need to pass it around in some potentially agile context, then one option is to use the [**winrt::agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref) struct template to get an agile reference to an instance of a non-agile type, or to an interface of a non-agile object.</span></span>

```cppwinrt
NonAgileType nonagile_obj;
winrt::agile_ref<NonAgileType> agile{ nonagile_obj };
```

<span data-ttu-id="8126e-139">Oder Sie können die Hilfsfunktion [**winrt::make_agile**](/uwp/cpp-ref-for-winrt/make-agile) verwenden.</span><span class="sxs-lookup"><span data-stu-id="8126e-139">Or, you can use the use the [**winrt::make_agile**](/uwp/cpp-ref-for-winrt/make-agile) helper function.</span></span>

```cppwinrt
NonAgileType nonagile_obj;
auto agile{ winrt::make_agile(nonagile_obj) };
```

<span data-ttu-id="8126e-140">In beiden Fällen kann `agile` nun frei an einen Thread in einem anderen Apartment übergeben und dort verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8126e-140">In either case, `agile` may now be freely passed to a thread in a different apartment, and used there.</span></span>

```cppwinrt
co_await resume_background();
NonAgileType nonagile_obj_again{ agile.get() };
winrt::hstring message{ nonagile_obj_again.Message() };
```

<span data-ttu-id="8126e-141">Der Aufruf [**agile_ref::get**](/uwp/cpp-ref-for-winrt/agile-ref#agilerefget-function) gibt einen Proxy zurück, der in dem Thread-Kontext, in dem **get** aufgerufen wird, sicher verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8126e-141">The [**agile_ref::get**](/uwp/cpp-ref-for-winrt/agile-ref#agilerefget-function) call returns a proxy that may safely be used within the thread context in which **get** is called.</span></span>

## <a name="important-apis"></a><span data-ttu-id="8126e-142">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="8126e-142">Important APIs</span></span>

* [<span data-ttu-id="8126e-143">IAgileObject Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8126e-143">IAgileObject interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh802476)
* [<span data-ttu-id="8126e-144">IMarshal Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8126e-144">IMarshal interface</span></span>](https://docs.microsoft.com/previous-versions/windows/embedded/ms887993)
* [<span data-ttu-id="8126e-145">winrt::agile_ref Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="8126e-145">winrt::agile_ref struct template</span></span>](/uwp/cpp-ref-for-winrt/agile-ref)
* [<span data-ttu-id="8126e-146">winrt::implements Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="8126e-146">winrt::implements struct template</span></span>](/uwp/cpp-ref-for-winrt/implements)
* [<span data-ttu-id="8126e-147">winrt::make_agile Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="8126e-147">winrt::make_agile function template</span></span>](/uwp/cpp-ref-for-winrt/make-agile)
* [<span data-ttu-id="8126e-148">winrt::non_agile Markerstruktur</span><span class="sxs-lookup"><span data-stu-id="8126e-148">winrt::non_agile marker struct</span></span>](/uwp/cpp-ref-for-winrt/non_agile)
* [<span data-ttu-id="8126e-149">winrt::Windows::Foundation::IUnknown::as Funktion</span><span class="sxs-lookup"><span data-stu-id="8126e-149">winrt::Windows::Foundation::IUnknown::as function</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)
* [<span data-ttu-id="8126e-150">winrt::Windows::Foundation::IUnknown::try_as Funktion</span><span class="sxs-lookup"><span data-stu-id="8126e-150">winrt::Windows::Foundation::IUnknown::try_as function</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)

## <a name="related-topics"></a><span data-ttu-id="8126e-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8126e-151">Related topics</span></span>

* [<span data-ttu-id="8126e-152">Verstehen und Verwenden von COM-Threadingmodellen</span><span class="sxs-lookup"><span data-stu-id="8126e-152">Understanding and Using COM Threading Models</span></span>](https://msdn.microsoft.com/library/ms809971)
