---
author: stevewhims
description: Windows-Runtime ist ein System Verweis gezählt. und in einem solchen System es ist wichtig, dass Sie über die Bedeutung von und den Unterschied zwischen, wissen starke und schwache Referenzen.
title: Schwache Referenzen in C++/WinRT
ms.author: stwhi
ms.date: 10/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, standard, c++, Cpp, Winrt, Projektion, eine sichere, schwache, Referenz
ms.localizationpriority: medium
ms.openlocfilehash: 414a73c8df31e4547b8bd154945a8e9960529320
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5468783"
---
# <a name="strong-and-weak-references-in-cwinrt"></a><span data-ttu-id="5f75e-104">Starke und schwache Referenzen in C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="5f75e-104">Strong and weak references in C++/WinRT</span></span>

<span data-ttu-id="5f75e-105">Windows-Runtime ist ein System Verweis gezählt. und bei einem solchen System ist es wichtig für starke über die Bedeutung der und die Unterscheidung zwischen, wissen Sie, und schwache Referenzen (und Verweise, die keiner, z. B. den impliziten *diesem* Zeiger sind).</span><span class="sxs-lookup"><span data-stu-id="5f75e-105">The Windows Runtime is a reference-counted system; and in such a system it's important for you to know about the significance of, and distinction between, strong and weak references (and references that are neither, such as the implicit *this* pointer).</span></span> <span data-ttu-id="5f75e-106">Wie Sie in diesem Thema werden feststellen, kann zu wissen, wie Sie diese Verweise korrekt verwalten bedeuten den Unterschied zwischen ein zuverlässiges System, das problemlos ausgeführt werden kann und, die möglicherweise nicht ordnungsgemäß stürzt ab.</span><span class="sxs-lookup"><span data-stu-id="5f75e-106">As you'll see in this topic, knowing how to manage these references correctly can mean the difference between a reliable system that runs smoothly, and one that crashes unpredictably.</span></span> <span data-ttu-id="5f75e-107">Durch die Bereitstellung Hilfsfunktionen, die eine umfassende Unterstützung in der sprachprojektion verfügen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Sie in der Mitte bei Ihrer Arbeit der Erstellung komplexer Systeme einfach und korrekt erfüllt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-107">By providing helper functions that have deep support in the language projection, [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) meets you halfway in your work of building more complex systems simply and correctly.</span></span>

## <a name="safely-accessing-the-this-pointer-in-a-class-member-coroutine"></a><span data-ttu-id="5f75e-108">Problemlos den Zugriff auf die *dieser* Zeiger in einer Coroutine Klassenmember</span><span class="sxs-lookup"><span data-stu-id="5f75e-108">Safely accessing the *this* pointer in a class-member coroutine</span></span>

<span data-ttu-id="5f75e-109">Der untenstehenden codeauflistung zeigt ein typisches Beispiel für eine Coroutine, die eine Member-Funktion einer Klasse ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-109">The code listing below shows a typical example of a coroutine that's a member function of a class.</span></span>

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;
using namespace std::chrono_literals;

struct MyClass : winrt::implements<MyClass, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    IAsyncOperation<winrt::hstring> RetrieveValueAsync()
    {
        co_await 5s;
        co_return m_value;
    }
};

int main()
{
    winrt::init_apartment();

    auto myclass_instance{ winrt::make_self<MyClass>() };
    auto async{ myclass_instance->RetrieveValueAsync() };

    winrt::hstring result{ async.get() };
    std::wcout << result.c_str() << std::endl;
}
```

<span data-ttu-id="5f75e-110">**MyClass::RetrieveValueAsync** funktioniert eine Weile, und schließlich wird dann eine Kopie des zurückgegeben der `MyClass::m_value` Datenmember.</span><span class="sxs-lookup"><span data-stu-id="5f75e-110">**MyClass::RetrieveValueAsync** does work for a while, and then eventually it returns a copy of the `MyClass::m_value` data member.</span></span> <span data-ttu-id="5f75e-111">**RetrieveValueAsync** aufrufen bewirkt, dass eine asynchrone Objekt erstellt wird, und dieses Objekt verfügt über einen impliziten *diesem* Zeiger (über die schließlich `m_value` zugegriffen wird).</span><span class="sxs-lookup"><span data-stu-id="5f75e-111">Calling **RetrieveValueAsync** causes an asynchronous object to be created, and that object has an implicit *this* pointer (through which, eventually, `m_value` is accessed).</span></span>

<span data-ttu-id="5f75e-112">Hier ist die vollständige Abfolge von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-112">Here's the full sequence of events.</span></span>

1. <span data-ttu-id="5f75e-113">Im **Hauptmenü**, wird eine Instanz von **MyClass** erstellt (`myclass_instance`).</span><span class="sxs-lookup"><span data-stu-id="5f75e-113">In **main**, an instance of **MyClass** is created (`myclass_instance`).</span></span>
2. <span data-ttu-id="5f75e-114">Die `async` Objekt wird erstellt, zeigen (über seine *dieser*) `myclass_instance`.</span><span class="sxs-lookup"><span data-stu-id="5f75e-114">The `async` object is created, pointing (via its *this*) to `myclass_instance`.</span></span>
3. <span data-ttu-id="5f75e-115">Die Funktion **Winrt::Windows::Foundation::IAsyncAction::get** ein paar Sekunden lang blockiert und dann das Ergebnis der **RetrieveValueAsync**zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-115">The **winrt::Windows::Foundation::IAsyncAction::get** function blocks for a few seconds, and then returns the result of **RetrieveValueAsync**.</span></span>
4. <span data-ttu-id="5f75e-116">**RetrieveValueAsync** gibt den Wert der `this->m_value`.</span><span class="sxs-lookup"><span data-stu-id="5f75e-116">**RetrieveValueAsync** returns the value of `this->m_value`.</span></span>

<span data-ttu-id="5f75e-117">Schritt 4 ist sicher, solange *diese* gültig ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-117">Step 4 is safe as long as *this* is valid.</span></span>

<span data-ttu-id="5f75e-118">Aber was geschieht, wenn die Klasseninstanz zerstört wird, bevor der asynchrone Vorgang abgeschlossen ist?</span><span class="sxs-lookup"><span data-stu-id="5f75e-118">But, what if the class instance is destroyed before the async operation completes?</span></span> <span data-ttu-id="5f75e-119">Es gibt alle Arten von Möglichkeiten, die Instanz der umgebenden auftreten kann, bevor die asynchrone Methode abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="5f75e-119">There are all kinds of ways the class instance could go out of scope before the asynchronous method has completed.</span></span> <span data-ttu-id="5f75e-120">Aber wir können sie durch Festlegen der Klasseninstanz zu simulieren `nullptr`.</span><span class="sxs-lookup"><span data-stu-id="5f75e-120">But, we can simulate it by setting the class instance to `nullptr`.</span></span>

```cppwinrt
int main()
{
    winrt::init_apartment();

    auto myclass_instance{ winrt::make_self<MyClass>() };
    auto async{ myclass_instance->RetrieveValueAsync() };
    myclass_instance = nullptr; // Simulate the class instance going out of scope.

    winrt::hstring result{ async.get() }; // Behavior is now undefined; crashing is likely.
    std::wcout << result.c_str() << std::endl;
}
```

<span data-ttu-id="5f75e-121">Nach dem Punkt, in dem wir die Klasseninstanz zerstören, sieht es wie wir direkt darauf erneut verweisen nicht aus.</span><span class="sxs-lookup"><span data-stu-id="5f75e-121">After the point where we destroy the class instance, it looks like we don't directly refer to it again.</span></span> <span data-ttu-id="5f75e-122">Aber natürlich das asynchrone Objekt verfügt über einen *dieser* Zeiger darauf und versucht, die zum Kopieren von innerhalb der Klasseninstanz gespeicherten Wert zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-122">But of course the asynchronous object has a *this* pointer to it, and tries to use that to copy the value stored inside the class instance.</span></span> <span data-ttu-id="5f75e-123">Die Coroutine ist eine Member-Funktion, und es geht davon aus, dessen *diesen* Zeiger mit verhüten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5f75e-123">The coroutine is a member function, and it expects to be able to use its *this* pointer with impunity.</span></span>

<span data-ttu-id="5f75e-124">Aufgrund dieser Änderung an den Code ausgeführt werden wir auf ein Problem in Schritt 4, da die Klasseninstanz zerstört wurde und *diese* ist nicht mehr gültig.</span><span class="sxs-lookup"><span data-stu-id="5f75e-124">With this change to the code, we run into a problem in step 4, because the class instance has been destroyed, and *this* is no longer valid.</span></span> <span data-ttu-id="5f75e-125">Sobald das asynchrone Objekt versucht, auf die Variable innerhalb der Klasseninstanz zugreifen, wird es abstürzt, wenn (oder Aktionen nicht vollständig definiert).</span><span class="sxs-lookup"><span data-stu-id="5f75e-125">As soon as the asynchronous object attempts to access the variable inside the class instance, it will crash (or do something entirely undefined).</span></span>

<span data-ttu-id="5f75e-126">Die Lösung besteht darin, geben Sie den asynchronen Vorgang&mdash;die Coroutine&mdash;eigene starken Verweis auf die Klasseninstanz.</span><span class="sxs-lookup"><span data-stu-id="5f75e-126">The solution is to give the asynchronous operation&mdash;the coroutine&mdash;its own strong reference to the class instance.</span></span> <span data-ttu-id="5f75e-127">Im derzeitigen Zustand enthält die Coroutine effektiv einen unformatierten *diesem* Zeiger auf die Klasseninstanz; aber das ist nicht ausreicht, um eine Instanz der beibehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="5f75e-127">As currently written, the coroutine effectively holds a raw *this* pointer to the class instance; but that's not enough to keep the class instance alive.</span></span>

<span data-ttu-id="5f75e-128">Um die Klasseninstanz beizubehalten, ändern Sie die Implementierung von **RetrieveValueAsync** siehe unten.</span><span class="sxs-lookup"><span data-stu-id="5f75e-128">To keep the class instance alive, change the implementation of **RetrieveValueAsync** to that shown below.</span></span>

```cppwinrt
IAsyncOperation<winrt::hstring> RetrieveValueAsync()
{
    auto strong_this{ get_strong() }; // Keep *this* alive.
    co_await 5s;
    co_return m_value;
}
```

<span data-ttu-id="5f75e-129">Da eine C++ / WinRT-Objekt direkt oder indirekt abgeleitet aus der Vorlage [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) , C++ / WinRT-Objekt aufrufen seiner [**get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) geschützt-Memberfunktion auf, um einen starken Verweis auf seine *diesen* Zeiger abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-129">Because a C++/WinRT object directly or indirectly derives from the [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) template, the C++/WinRT object can call its [**implements.get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) protected member function to retrieve a strong reference to its *this* pointer.</span></span> <span data-ttu-id="5f75e-130">Beachten Sie, dass keine Notwendigkeit besteht für die eigentliche Verwendung der `strong_this` Variable; nur aufrufen **Get_strong** Ihrer Verweiszähler erhöht und führt die impliziten *diesem* Zeiger gültig.</span><span class="sxs-lookup"><span data-stu-id="5f75e-130">Note that there's no need to actually use the `strong_this` variable; just calling **get_strong** increments your reference count, and keeps your implicit *this* pointer valid.</span></span>

<span data-ttu-id="5f75e-131">Dies behebt das Problem, das wir hatten, wenn wir mit Schritt 4 erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-131">This resolves the problem that we previously had when we got to step 4.</span></span> <span data-ttu-id="5f75e-132">Selbst wenn alle anderen Verweise auf die Klasseninstanz ausgeblendet werden, hat die Coroutine übernommen, die Vorsichtsmaßnahme garantieren, dass dessen Abhängigkeiten stabil sind.</span><span class="sxs-lookup"><span data-stu-id="5f75e-132">Even if all other references to the class instance disappear, the coroutine has taken the precaution of guaranteeing that its dependencies are stable.</span></span>

<span data-ttu-id="5f75e-133">Wenn eine starke Referenz nicht geeignet ist, können Sie stattdessen [**Implements:: get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) rufen Sie einen schwachen Verweis auf *diese*aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-133">If a strong reference isn't appropriate, then you can instead call [**implements::get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) to retrieve a weak reference to *this*.</span></span> <span data-ttu-id="5f75e-134">Bestätigen Sie, dass Sie einen starken Verweis abrufen können, bevor Sie auf *diese*zugreifen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-134">Just confirm that you can retrieve a strong reference before accessing *this*.</span></span>

```cppwinrt
IAsyncOperation<winrt::hstring> RetrieveValueAsync()
{
    auto weak_this{ get_weak() }; // Maybe keep *this* alive.

    co_await 5s;

    if (auto strong_this{ weak_this.get() })
    {
        co_return m_value;
    }
    else
    {
        co_return L"";
    }
}
```

<span data-ttu-id="5f75e-135">Im obigen Beispiel halten nicht der schwache Verweis Sie die Klasseninstanz aus gelöscht wird, wenn keine starken Verweise verbleiben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-135">In the example above, the weak reference doesn't keep the class instance from being destroyed when no strong references remain.</span></span> <span data-ttu-id="5f75e-136">Aber es ist eine Möglichkeit zur Überprüfung, ob eine starke Referenz vor dem Zugriff auf die Membervariable erworben werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f75e-136">But it gives you a way of checking whether a strong reference can be acquired before accessing the member variable.</span></span>

## <a name="safely-accessing-the-this-pointer-with-an-event-handling-delegate"></a><span data-ttu-id="5f75e-137">Problemlos den Zugriff auf die *dieser* Zeiger mit einem Delegaten für die Ereignisbehandlung</span><span class="sxs-lookup"><span data-stu-id="5f75e-137">Safely accessing the *this* pointer with an event-handling delegate</span></span>

### <a name="the-scenario"></a><span data-ttu-id="5f75e-138">Das Szenario</span><span class="sxs-lookup"><span data-stu-id="5f75e-138">The scenario</span></span>

<span data-ttu-id="5f75e-139">Allgemeine Informationen zur Ereignisbehandlung finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++ / WinRT](handle-events.md).</span><span class="sxs-lookup"><span data-stu-id="5f75e-139">For general info about event-handling, see [Handle events by using delegates in C++/WinRT](handle-events.md).</span></span>

<span data-ttu-id="5f75e-140">Im vorherige Abschnitt hervorgehoben potenzielle Probleme mit der Objektlebensdauer in den Bereichen Coroutinen und Parallelität.</span><span class="sxs-lookup"><span data-stu-id="5f75e-140">The previous section highlighted potential lifetime issues in the areas of coroutines and concurrency.</span></span> <span data-ttu-id="5f75e-141">Wenn Sie ein Ereignis mit Mitgliedsfunktion eines Objekts oder innerhalb von behandeln müssen eine Lambda-Funktion innerhalb der Mitgliedsfunktion eines Objekts, dann können Sie über die relative Lebensdauer des Ereignisempfängers (das Objekt, das das Ereignis behandelt) und die Ereignisquelle (das Objekt vorstellen jedoch das Ereignis auslöst).</span><span class="sxs-lookup"><span data-stu-id="5f75e-141">But, if you handle an event with an object's member function, or from within a lambda function inside an object's member function, then you need to think about the relative lifetimes of the event recipient (the object handling the event) and the event source (the object raising the event).</span></span> <span data-ttu-id="5f75e-142">Betrachten wir einige Codebeispiele.</span><span class="sxs-lookup"><span data-stu-id="5f75e-142">Let's look at some code examples.</span></span>

<span data-ttu-id="5f75e-143">Im Codebeispiel unten definiert zuerst eine einfache **Ereignisquelle** -Klasse, die ein generisches Ereignis auslöst, das indem alle Delegaten behandelt wird, die sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-143">The code listing below first defines a simple **EventSource** class, which raises a generic event that's handled by any delegates that have been added to it.</span></span> <span data-ttu-id="5f75e-144">Dieses Beispiel-Ereignis tritt auf den Delegattyp [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) verwenden, aber die Probleme und Problembehandlungen hier gelten für alle Delegattypen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-144">This example event happens to use the [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) delegate type, but the issues and remedies here apply to any and all delegate types.</span></span>

<span data-ttu-id="5f75e-145">Anschließend stellt die **EventRecipient** -Klasse einen Handler für das Ereignis **EventSource::Event** in Form einer Lambda-Funktion.</span><span class="sxs-lookup"><span data-stu-id="5f75e-145">Then, the **EventRecipient** class provides a handler for the **EventSource::Event** event in the form of a lambda function.</span></span>

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;

struct EventSource
{
    winrt::event<EventHandler<int>> m_event;

    void Event(EventHandler<int> const& handler)
    {
        m_event.add(handler);
    }

    void RaiseEvent()
    {
        m_event(nullptr, 0);
    }
};

struct EventRecipient : winrt::implements<EventRecipient, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    void Register(EventSource& event_source)
    {
        event_source.Event([&](auto&& ...)
        {
            std::wcout << m_value.c_str() << std::endl;
        });
    }
};

int main()
{
    winrt::init_apartment();

    EventSource event_source;
    auto event_recipient{ winrt::make_self<EventRecipient>() };
    event_recipient->Register(event_source);
    event_source.RaiseEvent();
}
```

<span data-ttu-id="5f75e-146">Das Muster besteht darin, dass der Empfänger Ereignis einen Ereignishandler Lambda-Funktion mit Abhängigkeiten für seine *diesen* Zeiger.</span><span class="sxs-lookup"><span data-stu-id="5f75e-146">The pattern is that the event recipient has a lambda event handler with dependencies on its *this* pointer.</span></span> <span data-ttu-id="5f75e-147">Bei jedem Ereignisempfängers die Ereignisquelle überlebt, überlebt es diese Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="5f75e-147">Whenever the event recipient outlives the event source, it outlives those dependencies.</span></span> <span data-ttu-id="5f75e-148">Und in diesen Fällen, die häufig verwendet werden, wird das Muster gut funktioniert.</span><span class="sxs-lookup"><span data-stu-id="5f75e-148">And in those cases, which are common, the pattern works well.</span></span> <span data-ttu-id="5f75e-149">Einige dieser Fälle sind offensichtlich, z. B. wenn eine UI-Seite ein Ereignis verarbeitet, das von einem Steuerelement ausgelöst wird, das sich auf der Seite befindet.</span><span class="sxs-lookup"><span data-stu-id="5f75e-149">Some of these cases are obvious, such as when a UI page handles an event raised by a control that's on the page.</span></span> <span data-ttu-id="5f75e-150">Die Seite die Schaltfläche überlebt&mdash;also der Handler auch die Schaltfläche überlebt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-150">The page outlives the button&mdash;so, the handler also outlives the button.</span></span> <span data-ttu-id="5f75e-151">Dies gilt immer dann, wenn der Empfänger die Quelle besitzt (z. B. als Datenelement), oder wenn der Empfänger und die Quelle gleichgeordnet sind und sich direkt im Besitz eines anderen Objekts befinden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-151">This holds true any time the recipient owns the source (as a data member, for example), or any time the recipient and the source are siblings and directly owned by some other object.</span></span> <span data-ttu-id="5f75e-152">Wenn Sie sicher sind, dass Sie einen Fall haben, in dem der Handler das *this*-Objekt nicht überleben wird, können Sie *this*normal verwenden, ohne Rücksicht auf eine starke oder schwache Lebensdauer zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-152">If you're sure you have a case where the handler won't outlive the *this* that it depends on, then you can capture *this* normally, without consideration for strong or weak lifetime.</span></span>

<span data-ttu-id="5f75e-153">Aber es gibt immer noch Fälle, in denen *diese* nicht überlebt seine Verwendung in einem Handler (einschließlich Handlern für Completion- und Progress-Ereignisse, die durch asynchrone Aktionen und Vorgänge ausgelöst werden), und es ist wichtig zu wissen, wie diese behandelt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-153">But there are still cases where *this* doesn't outlive its use in a handler (including handlers for completion and progress events raised by asynchronous actions and operations), and it's important to know how to deal with them.</span></span>

- <span data-ttu-id="5f75e-154">Wenn Sie eine Coroutine erstellen, um eine asynchrone Methode zu implementieren, dann ist dies möglich.</span><span class="sxs-lookup"><span data-stu-id="5f75e-154">If you're authoring a coroutine to implement an asynchronous method, then it's possible.</span></span>
- <span data-ttu-id="5f75e-155">In seltenen Fällen mit bestimmten XAML-UI-Framework-Objekten (z. B. [**SwapChainPanel**](/uwp/api/windows.ui.xaml.controls.swapchainpanel)) ist dies möglich wenn der Empfänger finalisiert wird, ohne die Registrierung für die Ereignisquelle aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-155">In rare cases with certain XAML UI framework objects ([**SwapChainPanel**](/uwp/api/windows.ui.xaml.controls.swapchainpanel), for example), then it's possible, if the recipient is finalized without unregistering from the event source.</span></span>

### <a name="the-issue"></a><span data-ttu-id="5f75e-156">Das Problem</span><span class="sxs-lookup"><span data-stu-id="5f75e-156">The issue</span></span>

<span data-ttu-id="5f75e-157">Diese nächste Version der **main** -Funktion simuliert, was geschieht, wenn der Empfänger Ereignis zerstört wird (z. B. es den gültigen Bereich verlässt) während die Ereignisquelle noch Auslösen von Ereignissen ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-157">This next version of the **main** function simulates what happens when the event recipient is destroyed (perhaps it goes out of scope) while the event source is still raising events.</span></span>

```cppwinrt
int main()
{
    winrt::init_apartment();

    EventSource event_source;
    auto event_recipient{ winrt::make_self<EventRecipient>() };
    event_recipient->Register(event_source);
    event_recipient = nullptr; // Simulate the event recipient going out of scope.
    event_source.RaiseEvent(); // Behavior is now undefined within the lambda event handler; crashing is likely.
}
```

<span data-ttu-id="5f75e-158">Ereignisempfängers zerstört, aber der Lambda-Ereignishandler darin ist weiterhin für **das Ereignis** abonniert.</span><span class="sxs-lookup"><span data-stu-id="5f75e-158">The event recipient is destroyed, but the lambda event handler within it is still subscribed to the **Event** event.</span></span> <span data-ttu-id="5f75e-159">Wenn das Ereignis ausgelöst wird, versucht der Lambda-Ausdruck, den *diesem* Zeiger dereferenzieren, der an diesem Punkt ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-159">When that event is raised, the lambda attempts to dereference the *this* pointer, which is at that point invalid.</span></span> <span data-ttu-id="5f75e-160">Dies führt eine zugriffsverletzung durch Code im Ereignishandler (oder in der Fortsetzung einer Coroutine) versucht, es zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-160">So, an access violation results from code in the handler (or in a coroutine's continuation) attempting to use it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f75e-161">Wenn Sie eine solchen Situation auftreten, müssen Sie über die Lebensdauer des *dieses* Objekts vorstellen. und davon, ob das aufgenommenen *dieses* Objekt die Aufnahme überlebt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-161">If you encounter a situation like this, then you'll need to think about the lifetime of the *this* object; and whether or not the captured *this* object outlives the capture.</span></span> <span data-ttu-id="5f75e-162">Wenn dies nicht der Fall, dann verwenden Sie es mit einer starken oder einen schwachen Verweis wie weiter unten unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="5f75e-162">If it doesn't, then capture it with a strong or a weak reference, as we'll demonstrate below.</span></span>
>
> <span data-ttu-id="5f75e-163">Oder&mdash;Wenn es für Ihr Szenario sinnvoll ist, und wenn threading-Überlegungen ermöglichen es sogar&mdash;und dann eine andere Möglichkeit besteht darin, den Handler zu widerrufen, nachdem der Empfänger mit dem Ereignis oder im Destruktor des Empfängers fertig ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-163">Or&mdash;if it makes sense for your scenario, and if threading considerations make it even possible&mdash;then another option is to revoke the handler after the recipient is done with the event, or in the recipient's destructor.</span></span> <span data-ttu-id="5f75e-164">Finden Sie [einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).</span><span class="sxs-lookup"><span data-stu-id="5f75e-164">See [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate).</span></span>

<span data-ttu-id="5f75e-165">Dies ist wie wir den Ereignishandler registriert werden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-165">This is how we're registering the handler.</span></span>

```cppwinrt
event_source.Event([&](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

<span data-ttu-id="5f75e-166">Der Lambda-Ausdruck erfasst automatisch alle lokalen Variablen durch einen Verweis.</span><span class="sxs-lookup"><span data-stu-id="5f75e-166">The lambda automatically captures any local variables by reference.</span></span> <span data-ttu-id="5f75e-167">Daher in diesem Beispiel konnten wir vorigen dies geschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-167">So, for this example, we could equivalently have written this.</span></span>

```cppwinrt
event_source.Event([this](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

<span data-ttu-id="5f75e-168">In beiden Fällen sind wir gerade den unformatierten *dieser* -Zeiger aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-168">In both cases, we're just capturing the raw *this* pointer.</span></span> <span data-ttu-id="5f75e-169">Und die keine Auswirkung auf die Referenzzähler, sodass nichts verhindert das aktuelle Objekt zerstört wird.</span><span class="sxs-lookup"><span data-stu-id="5f75e-169">And that has no effect on reference-counting, so nothing is preventing the current object from being destroyed.</span></span>

### <a name="the-solution"></a><span data-ttu-id="5f75e-170">Die Lösung</span><span class="sxs-lookup"><span data-stu-id="5f75e-170">The solution</span></span>

<span data-ttu-id="5f75e-171">Die Lösung besteht darin, eine starke Referenz zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-171">The solution is to capture a strong reference.</span></span> <span data-ttu-id="5f75e-172">Eine starke Referenz *wird* erhöht die Referenzzähler, und es *ist* , lassen Sie das aktuelle Objekt aktiv.</span><span class="sxs-lookup"><span data-stu-id="5f75e-172">A strong reference *does* increment the reference count, and it *does* keep the current object alive.</span></span> <span data-ttu-id="5f75e-173">Sie deklarieren Sie eine Variable Aufnahme (aufgerufen `strong_this` in diesem Beispiel), und initialisieren Sie es mit einem Aufruf von [**get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function), die einen starken Verweis auf unser *diesen* Zeiger abruft.</span><span class="sxs-lookup"><span data-stu-id="5f75e-173">You just declare a capture variable (called `strong_this` in this example), and initialize it with a call to [**implements.get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function), which retrieves a strong reference to our *this* pointer.</span></span>

```cppwinrt
event_source.Event([this, strong_this { get_strong()}](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

<span data-ttu-id="5f75e-174">Sie können sogar auslassen die automatische Erfassung des aktuellen Objekts und greifen Sie auf das Datenelement über die Aufnahme Variable anstelle von über den impliziten *dieses*.</span><span class="sxs-lookup"><span data-stu-id="5f75e-174">You can even omit the automatic capture of the current object, and access the data member through the capture variable instead of via the implicit *this*.</span></span>

```cppwinrt
event_source.Event([strong_this { get_strong()}](auto&& ...)
{
    std::wcout << strong_this->m_value.c_str() << std::endl;
});
```

<span data-ttu-id="5f75e-175">Wenn eine starke Referenz nicht geeignet ist, können Sie stattdessen [**Implements:: get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) rufen Sie einen schwachen Verweis auf *diese*aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-175">If a strong reference isn't appropriate, then you can instead call [**implements::get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) to retrieve a weak reference to *this*.</span></span> <span data-ttu-id="5f75e-176">Bestätigen Sie, dass Sie einen starken Verweis weiterhin daraus abrufen können, bevor Sie den Zugriff auf Member.</span><span class="sxs-lookup"><span data-stu-id="5f75e-176">Just confirm that you can still retrieve a strong reference from it before accessing members.</span></span>

```cppwinrt
event_source.Event([weak_this{ get_weak() }](auto&& ...)
{
    if (auto strong_this{ weak_this.get() })
    {
        std::wcout << strong_this->m_value.c_str() << std::endl;
    }
});
```

### <a name="if-you-use-a-member-function-as-a-delegate"></a><span data-ttu-id="5f75e-177">Wenn Sie eine Member-Funktion als Delegaten verwenden</span><span class="sxs-lookup"><span data-stu-id="5f75e-177">If you use a member function as a delegate</span></span>

<span data-ttu-id="5f75e-178">Als auch Lambda-Funktionen, diese Grundsätze gelten auch für eine Member-Funktion als den Delegaten verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-178">As well as lambda functions, these principles also apply to using a member function as your delegate.</span></span> <span data-ttu-id="5f75e-179">Die Syntax unterscheidet, also sehen wir uns etwas Code.</span><span class="sxs-lookup"><span data-stu-id="5f75e-179">The syntax is different, so let's look at some code.</span></span> <span data-ttu-id="5f75e-180">Hier wird zunächst mithilfe eines unformatierten *dieses* Zeigers potenziell unsichere Member-Funktion-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="5f75e-180">First, here's the potentially unsafe member function event handler, using a raw *this* pointer.</span></span>

```cppwinrt
struct EventRecipient : winrt::implements<EventRecipient, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    void Register(EventSource& event_source)
    {
        event_source.Event({ this, &EventRecipient::OnEvent });
    }

    void OnEvent(IInspectable const& /* sender */, int /* args */)
    {
        std::wcout << m_value.c_str() << std::endl;
    }
};
```

<span data-ttu-id="5f75e-181">Dies ist der standard, herkömmlichen Möglichkeit zum Verweisen auf ein Objekt und dessen Member-Funktion.</span><span class="sxs-lookup"><span data-stu-id="5f75e-181">This is the standard, conventional way to refer to an object and its member function.</span></span> <span data-ttu-id="5f75e-182">Um dies zu sicherer machen, können Sie&mdash;ab Version 10.0.17763.0 (Windows 10, Version 1809) des Windows SDK&mdash;herstellen, eine starke oder schwache Referenz auf den Punkt, wo der Handler registriert ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-182">To make this safe, you can&mdash;as of version 10.0.17763.0 (Windows 10, version 1809) of the Windows SDK&mdash;establish a strong or a weak reference at the point where the handler is registered.</span></span> <span data-ttu-id="5f75e-183">An dieser Stelle wird bekanntermaßen Empfänger Event-Objekts ist immer noch verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-183">At that point, the event recipient object is known to be still alive.</span></span>

<span data-ttu-id="5f75e-184">Rufen Sie einfach für einen starken Verweis [**Get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) anstelle der unformatierten *diesem* Zeiger.</span><span class="sxs-lookup"><span data-stu-id="5f75e-184">For a strong reference, just call [**get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) in place of the raw *this* pointer.</span></span> <span data-ttu-id="5f75e-185">C++ / WinRT stellt sicher, dass der resultierende Delegat einen starken Verweis auf das aktuelle Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="5f75e-185">C++/WinRT ensures that the resulting delegate holds a strong reference to the current object.</span></span>

```cppwinrt
event_source.Event({ get_strong(), &EventRecipient::OnEvent });
```

<span data-ttu-id="5f75e-186">Rufen Sie für eine schwache Referenz [**Get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function).</span><span class="sxs-lookup"><span data-stu-id="5f75e-186">For a weak reference, call [**get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function).</span></span> <span data-ttu-id="5f75e-187">C++ / WinRT stellt sicher, dass der resultierende Delegat einen schwachen Verweis enthält.</span><span class="sxs-lookup"><span data-stu-id="5f75e-187">C++/WinRT ensures that the resulting delegate holds a weak reference.</span></span> <span data-ttu-id="5f75e-188">In letzter Minute, im Hintergrund der Delegat versucht, den schwachen Verweis auf eine starke aufzulösen und nur die Memberfunktion aufruft, wenn dies erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="5f75e-188">At the last minute, and behind the scenes, the delegate attempts to resolve the weak reference to a strong one, and only calls the member function if it's successful.</span></span>

```cppwinrt
event_source.Event({ get_weak(), &EventRecipient::OnEvent });
```

### <a name="a-weak-reference-example-using-swapchainpanelcompositionscalechanged"></a><span data-ttu-id="5f75e-189">Eine schwache Referenz Beispiel für die Verwendung von **SwapChainPanel::CompositionScaleChanged**</span><span class="sxs-lookup"><span data-stu-id="5f75e-189">A weak reference example using **SwapChainPanel::CompositionScaleChanged**</span></span>

<span data-ttu-id="5f75e-190">In diesem Beispiel verwenden wir das Ereignis [**SwapChainPanel::CompositionScaleChanged**](/uwp/api/windows.ui.xaml.controls.swapchainpanel.compositionscalechanged) über einem anderen Illustration schwache Referenzen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-190">In this code example, we use the [**SwapChainPanel::CompositionScaleChanged**](/uwp/api/windows.ui.xaml.controls.swapchainpanel.compositionscalechanged) event by way of another illustration of weak references.</span></span> <span data-ttu-id="5f75e-191">Der Code registriert einen Ereignishandler mit einer Lambda-Funktion, die einen schwachen Verweis auf den Empfänger erfasst.</span><span class="sxs-lookup"><span data-stu-id="5f75e-191">The code registers an event handler using a lambda that captures a weak reference to the recipient.</span></span>

```cppwinrt
winrt::Windows::UI::Xaml::Controls::SwapChainPanel m_swapChainPanel;
winrt::event_token m_compositionScaleChangedEventToken;

void RegisterEventHandler()
{
    m_compositionScaleChangedEventToken = m_swapChainPanel.CompositionScaleChanged([weak_this{ get_weak() }]
        (Windows::UI::Xaml::Controls::SwapChainPanel const& sender,
        Windows::Foundation::IInspectable const& object)
    {
        if (auto strong_this{ weak_this.get() })
        {
            strong_this->OnCompositionScaleChanged(sender, object);
        }
    });
}

void OnCompositionScaleChanged(Windows::UI::Xaml::Controls::SwapChainPanel const& sender,
    Windows::Foundation::IInspectable const& object)
{
    // Here, we know that the "this" object is valid.
}
```

<span data-ttu-id="5f75e-192">In der Lamba-Bedingung wird eine temporäre Variable erzeugt, die eine schwache Referenz auf *this* darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-192">In the lamba capture clause, a temporary variable is created, representing a weak reference to *this*.</span></span> <span data-ttu-id="5f75e-193">In der Lambda wird die Funktion **OnCompositionScaleChanged** aufgerufen, wenn eine starke Referenz auf *this* abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f75e-193">In the body of the lambda, if a strong reference to *this* can be obtained, then the **OnCompositionScaleChanged** function is called.</span></span> <span data-ttu-id="5f75e-194">Auf diese Weise kann *this* innerhalb von **OnCompositionScaleChanged** sicher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-194">That way, inside **OnCompositionScaleChanged**, *this* can safely be used.</span></span>

## <a name="weak-references-in-cwinrt"></a><span data-ttu-id="5f75e-195">Schwache Referenzen in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="5f75e-195">Weak references in C++/WinRT</span></span>

<span data-ttu-id="5f75e-196">Oben haben wir gesehen, schwache Verweise verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f75e-196">Above, we saw weak references being used.</span></span> <span data-ttu-id="5f75e-197">Im Allgemeinen sind, ist dies eignet sich gut für zyklische Referenzen zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="5f75e-197">In general, they're good for breaking cyclic references.</span></span> <span data-ttu-id="5f75e-198">Z. B. für die systemeigene Implementierung des XAML-basierte Benutzeroberflächen-Frameworks&mdash;aufgrund des historischen Designs des Frameworks&mdash;der schwache verweisen in C++ / WinRT ist erforderlich, um zyklische Referenzen zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="5f75e-198">For example, for the native implementation of the XAML-based UI framework&mdash;because of the historic design of the framework&mdash;the weak reference mechanism in C++/WinRT is necessary to handle cyclic references.</span></span> <span data-ttu-id="5f75e-199">Außerhalb von XAML jedoch wahrscheinlich müssen Sie nicht schwache Referenzen verwenden (nicht, dass es nichts gibt grundsätzlich XAML-spezifischen über diese).</span><span class="sxs-lookup"><span data-stu-id="5f75e-199">Outside of XAML, though, you likely won't need to use weak references (not that there's anything inherently XAML-specific about them).</span></span> <span data-ttu-id="5f75e-200">Anstatt Sie sollten mehr häufig als nicht in der Lage, Entwerfen Sie Ihre eigenen C++ / WinRT-APIs so, dass zyklische Referenzen und schwache Referenzen vermieden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-200">Rather you should, more often than not, be able to design your own C++/WinRT APIs in such a way as to avoid the need for cyclic references and weak references.</span></span> 

<span data-ttu-id="5f75e-201">Bei einem von Ihnen deklarierten Typ ist es für C++/WinRT nicht sofort ersichtlich, ob oder wann schwache Referenzen benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-201">For any given type that you declare, it's not immediately obvious to C++/WinRT whether or when weak references are needed.</span></span> <span data-ttu-id="5f75e-202">Daher bietet C++/WinRT für die Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) automatisch eine Unterstützung von schwache Referenzen. Von dieser werden Ihre eigenen C++/WinRT-Typen direkt oder indirekt abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="5f75e-202">So, C++/WinRT provides weak reference support automatically on the struct template [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements), from which your own C++/WinRT types directly or indirectly derive.</span></span> <span data-ttu-id="5f75e-203">Dies kostet Sie nichts, es sei denn, Ihr Objekt wird tatsächlich auf [**IWeakReferenceSource**](/windows/desktop/api/weakreference/nn-weakreference-iweakreferencesource) abgefragt.</span><span class="sxs-lookup"><span data-stu-id="5f75e-203">It's pay-for-play, in that it doesn't cost you anything unless your object is actually queried for [**IWeakReferenceSource**](/windows/desktop/api/weakreference/nn-weakreference-iweakreferencesource).</span></span> <span data-ttu-id="5f75e-204">Und Sie können sich explizit [gegen diese Unterstützung](#opting-out-of-weak-reference-support) entscheiden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-204">And you can choose explicitly to [opt out of that support](#opting-out-of-weak-reference-support).</span></span>

### <a name="code-examples"></a><span data-ttu-id="5f75e-205">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="5f75e-205">Code examples</span></span>
<span data-ttu-id="5f75e-206">Die Strukturvorlage [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) ist eine Option, um eine schwache Referenz auf eine Klasseninstanz zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5f75e-206">The [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) struct template is one option for getting a weak reference to a class instance.</span></span>

```cppwinrt
Class c;
winrt::weak_ref<Class> weak{ c };
```

<span data-ttu-id="5f75e-207">Oder Sie können die Hilfsfunktion [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f75e-207">Or, you can use the use the [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) helper function.</span></span>

```cppwinrt
Class c;
auto weak = winrt::make_weak(c);
```

<span data-ttu-id="5f75e-208">Die Erstellung einer schwachen Referenz hat keinen Einfluss auf die Anzahl der Referenzen auf das Objekt selbst, sondern bewirkt lediglich die Zuweisung eines Kontrollblocks.</span><span class="sxs-lookup"><span data-stu-id="5f75e-208">Creating a weak reference doesn't affect the reference count on the object itself; it just causes a control block to be allocated.</span></span> <span data-ttu-id="5f75e-209">Dieser Kontrollblock kümmert sich um die Implementierung der schwachen Referenzsemantik.</span><span class="sxs-lookup"><span data-stu-id="5f75e-209">That control block takes care of implementing the weak reference semantics.</span></span> <span data-ttu-id="5f75e-210">Sie können dann versuchen, den schwachen Verweis auf einen starken Verweis hochzustufen (und, wenn dies erfolgreich ist, ihn zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="5f75e-210">You can then try to promote the weak reference to a strong reference and, if successful, use it.</span></span>

```cppwinrt
if (Class strong = weak.get())
{
    // use strong, for example strong.DoWork();
}
```

<span data-ttu-id="5f75e-211">Sofern noch eine andere starke Referenz existiert, erhöht der Aufruf von [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) die Referenzanzahl und gibt die starke Referenz an den Aufrufer zurück.</span><span class="sxs-lookup"><span data-stu-id="5f75e-211">Provided that some other strong reference still exists, the [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) call increments the reference count and returns the strong reference to the caller.</span></span>

### <a name="opting-out-of-weak-reference-support"></a><span data-ttu-id="5f75e-212">Opt-out der Unterstützung von schwachen Referenzen</span><span class="sxs-lookup"><span data-stu-id="5f75e-212">Opting out of weak reference support</span></span>
<span data-ttu-id="5f75e-213">Die Unterstützung schwacher Referenzen erfolgt automatisch.</span><span class="sxs-lookup"><span data-stu-id="5f75e-213">Weak reference support is automatic.</span></span> <span data-ttu-id="5f75e-214">Sie können diese Unterstützung jedoch explizit deaktivieren, indem Sie die [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-214">But you can choose explicitly to opt out of that support by passing the [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref) marker struct as a template argument to your base class.</span></span>

<span data-ttu-id="5f75e-215">Wenn Sie direkt von **winrt::implements** ableiten.</span><span class="sxs-lookup"><span data-stu-id="5f75e-215">If you derive directly from **winrt::implements**.</span></span>

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, no_weak_ref>
{
    ...
}
```

<span data-ttu-id="5f75e-216">Wenn Sie eine Laufzeitklasse schreiben.</span><span class="sxs-lookup"><span data-stu-id="5f75e-216">If you're authoring a runtime class.</span></span>

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, no_weak_ref>
{
    ...
}
```

<span data-ttu-id="5f75e-217">Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint.</span><span class="sxs-lookup"><span data-stu-id="5f75e-217">It doesn't matter where in the variadic parameter pack the marker struct appears.</span></span> <span data-ttu-id="5f75e-218">Wenn Sie eine schwache Referenz für einen Opted-Out-Typ anfordern, dann hilft Ihnen der Compiler mit der Meldung „*Dies ist nur für die Unterstützung schwacher Referenzen*”.</span><span class="sxs-lookup"><span data-stu-id="5f75e-218">If you request a weak reference for an opted-out type, then the compiler will help you out with "*This is only for weak ref support*".</span></span>

## <a name="important-apis"></a><span data-ttu-id="5f75e-219">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5f75e-219">Important APIs</span></span>
* [<span data-ttu-id="5f75e-220">implements::get_weak Funktion</span><span class="sxs-lookup"><span data-stu-id="5f75e-220">implements::get_weak function</span></span>](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [<span data-ttu-id="5f75e-221">winrt::make_weak Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="5f75e-221">winrt::make_weak function template</span></span>](/uwp/cpp-ref-for-winrt/make-weak)
* [<span data-ttu-id="5f75e-222">winrt::no_weak_ref Markerstruktur</span><span class="sxs-lookup"><span data-stu-id="5f75e-222">winrt::no_weak_ref marker struct</span></span>](/uwp/cpp-ref-for-winrt/no-weak-ref)
* [<span data-ttu-id="5f75e-223">winrt::weak_ref Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="5f75e-223">winrt::weak_ref struct template</span></span>](/uwp/cpp-ref-for-winrt/weak-ref)
