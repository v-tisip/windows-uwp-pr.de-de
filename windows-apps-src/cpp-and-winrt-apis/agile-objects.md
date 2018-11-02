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
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5977304"
---
# <a name="agile-objects-in-cwinrt"></a>Agile Objekte in C++/WinRT

In den meisten Fällen kann eine Instanz einer Windows-Runtime-Klasse zugegriffen werden, von einem anderen Thread (genau wie die meisten standard C++-Objekte können). Eine solche Windows-Runtime-Klasse ist *agil*. Nur eine geringe Anzahl von Windows-Runtime-Klassen, die im Lieferumfang von Windows nicht agil sind, aber wenn Sie sie nutzen, Sie ihre threading-Modell und Ihr marshaling-Verhalten berücksichtigen müssen (marshaling ist die Weitergabe von Daten über eine Apartmentgrenze). Es ist ein guter Standard für jedes Windows-Runtime-Objekt, agil zu sein, Ihre eigenen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Typen sind standardmäßig agil.

Sie können jedoch auch von dieser Regel abweichen. Möglicherweise haben Sie einen zwingenden Grund, ein Objekt Ihres Typs zu beschränken (zum Beispiel in einer Anwendung mit einem einzelnen Thread). Dies hat typischerweise mit Wiedereinsprungsvoraussetzungen zu tun. Aber auch die UI-APIs (User Interface, Benutzerschnittstelle) bieten zunehmend agile Objekte. Im Allgemeinen ist Agilität die einfachste und leistungsfähigste Option. Auch wenn Sie eine Aktivierungs-Factory implementieren, muss diese agil sein (auch, wenn Ihre entsprechende Laufzeitklasse es nicht ist).

> [!NOTE]
> Windows-Runtime basiert auf COM. Im Sinne von COM ist eine agile Klasse mit `ThreadingModel` = *Both* registriert. Weitere Informationen zu COM-threading-Modellen und Apartments finden Sie [verstehen und Verwenden von COM-Threading-Modellen](https://msdn.microsoft.com/library/ms809971).

## <a name="code-examples"></a>Codebeispiele

Lassen Sie uns eine Beispiel einer Implementierung einer Laufzeitklasse verwenden, um zu veranschaulichen wie C++ / WinRT Agilität unterstützt.

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

struct MyType : winrt::implements<MyType, IStringable>
{
    winrt::hstring ToString(){ ... }
};
```

Da wir dies nicht explizit ausschließen, ist diese Implementierung agil. Die [**winrt::implementiert**](/uwp/cpp-ref-for-winrt/implements) Basisstruktur implementiert [**IAgileObject**](https://msdn.microsoft.com/library/windows/desktop/hh802476) und [**IMarshal**](/windows/desktop/api/objidl/nn-objidl-imarshal). Die **IMarshal**-Implementierung verwendet **CoCreateFreeThreadedMarshaler**, um das Legacy-Code zu unterstützen, der nichts über **IAgileObject** weiß.

Dieser Code prüft ein Objekt auf Agilität. Der Aufruf von [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) löst eine Ausnahme aus, wenn `myimpl` nicht agil ist.

```cppwinrt
winrt::com_ptr<MyType> myimpl{ winrt::make_self<MyType>() };
winrt::com_ptr<IAgileObject> iagileobject{ myimpl.as<IAgileObject>() };
```

Anstatt eine Ausnahme zu verarbeiten, können Sie [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) aufrufen.

```cppwinrt
winrt::com_ptr<IAgileObject> iagileobject{ myimpl.try_as<IAgileObject>() };
if (iagileobject) { /* myimpl is agile. */ }
```

**IAgileObject** hat keine eigenen Methoden, sodass man damit nicht viel anfangen kann. Diese nächste Variante ist eher typisch.

```cppwinrt
if (myimpl.try_as<IAgileObject>()) { /* myimpl is agile. */ }
```

**IAgileObject** ist eine *Marker-Schnittstelle*. Der Nutzen der Abfrage von **IAgileObject** besteht aus der Informationen zum Erfolg oder Misserfolg.

## <a name="opting-out-of-agile-object-support"></a>Vermeiden der Unterstützung von agilen Objekten

Sie können die Unterstützung für agile Objekte explizit deaktivieren, indem Sie die [**winrt::non_agile**](/uwp/cpp-ref-for-winrt/non_agile)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.

Wenn Sie direkt von **winrt::implements** ableiten.

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, winrt::non_agile>
{
    ...
}
```

Wenn Sie eine Laufzeitklasse schreiben.

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, winrt::non_agile>
{
    ...
}
```

Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint.

Unabhängig davon, ob Sie die Agilität, können Sie **IMarshal** selbst implementieren. Z. B. Sie den Marker **WinRT:: non_agile** verwenden, um die Standard-agilitäts-Implementierung zu vermeiden und **IMarshal** selbst implementieren können&mdash;um die Marshal-by-Value-Semantik zu unterstützen.

## <a name="agile-references-winrtagileref"></a>Agile Referenzen (winrt::agile_ref)

Wenn Sie ein Objekt verwenden, das nicht agil ist, aber Sie es in einem potentiell agilen Kontext weitergeben müssen, dann ist eine Option die Verwendung der [**winrt::agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref)-Strukturvorlage. So erhalten Sie eine agile Referenz auf eine Instanz eines nicht agilen Typs oder auf eine Schnittstelle eines nicht agilen Objekts.

```cppwinrt
NonAgileType nonagile_obj;
winrt::agile_ref<NonAgileType> agile{ nonagile_obj };
```

Oder Sie können die Hilfsfunktion [**winrt::make_agile**](/uwp/cpp-ref-for-winrt/make-agile) verwenden.

```cppwinrt
NonAgileType nonagile_obj;
auto agile{ winrt::make_agile(nonagile_obj) };
```

In beiden Fällen kann `agile` nun frei an einen Thread in einem anderen Apartment übergeben und dort verwendet werden.

```cppwinrt
co_await resume_background();
NonAgileType nonagile_obj_again{ agile.get() };
winrt::hstring message{ nonagile_obj_again.Message() };
```

Der Aufruf [**agile_ref::get**](/uwp/cpp-ref-for-winrt/agile-ref#agilerefget-function) gibt einen Proxy zurück, der in dem Thread-Kontext, in dem **get** aufgerufen wird, sicher verwendet werden kann.

## <a name="important-apis"></a>Wichtige APIs

* [IAgileObject Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/hh802476)
* [IMarshal Schnittstelle](https://docs.microsoft.com/previous-versions/windows/embedded/ms887993)
* [winrt::agile_ref Strukturvorlage](/uwp/cpp-ref-for-winrt/agile-ref)
* [winrt::implements Strukturvorlage](/uwp/cpp-ref-for-winrt/implements)
* [winrt::make_agile Funktionsvorlage](/uwp/cpp-ref-for-winrt/make-agile)
* [winrt::non_agile Markerstruktur](/uwp/cpp-ref-for-winrt/non_agile)
* [winrt::Windows::Foundation::IUnknown::as Funktion](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)
* [winrt::Windows::Foundation::IUnknown::try_as Funktion](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function)

## <a name="related-topics"></a>Verwandte Themen

* [Verstehen und Verwenden von COM-Threadingmodellen](https://msdn.microsoft.com/library/ms809971)
