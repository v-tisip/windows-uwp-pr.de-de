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
# <a name="weak-references-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Schwache Referenzen in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)
Sie sollten in der Lage sein, Ihre eigenen C++/WinRT-APIs so zu gestalten, dass zyklische Referenzen und schwache Referenzen vermieden werden. Bei der nativen Implementierung des XAML-basierten UI-Frameworks ist der schwache Referenzmechanismus aufgrund des historischen Designs des Frameworks in C++/WinRT jedoch notwendig, um zyklische Referenzen zu verarbeiten. Außerhalb von XAML ist es unwahrscheinlich, dass Sie schwache Referenzen verwenden müssen (obwohl es theoretisch nichts XAML-spezifisches an ihnen gibt).

Bei einem von Ihnen deklarierten Typ ist es für C++/WinRT nicht sofort ersichtlich, ob oder wann schwache Referenzen benötigt werden. Daher bietet C++/WinRT für die Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) automatisch eine Unterstützung von schwache Referenzen. Von dieser werden Ihre eigenen C++/WinRT-Typen direkt oder indirekt abgeleitet. Dies kostet Sie nichts, es sei denn, Ihr Objekt wird tatsächlich auf [**IWeakReferenceSource**](https://msdn.microsoft.com/library/br224609) abgefragt. Und Sie können sich explizit [gegen diese Unterstützung](#opting-out-of-weak-reference-support) entscheiden.

## <a name="code-examples"></a>Codebeispiele
Die Strukturvorlage [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) ist eine Option, um eine schwache Referenz auf eine Klasseninstanz zu erhalten.

```cppwinrt
Class c;
winrt::weak_ref<Class> weak{ c };
```
Oder Sie können die Hilfsfunktion [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) verwenden.

```cppwinrt
Class c;
auto weak = winrt::make_weak(c);
```

Die Erstellung einer schwachen Referenz hat keinen Einfluss auf die Anzahl der Referenzen auf das Objekt selbst, sondern bewirkt lediglich die Zuweisung eines Kontrollblocks. Dieser Kontrollblock kümmert sich um die Implementierung der schwachen Referenzsemantik. Sie können dann versuchen, den schwachen Verweis auf einen starken Verweis hochzustufen (und, wenn dies erfolgreich ist, ihn zu verwenden).

```cppwinrt
if (Class strong = weak.get())
{
    // use strong, for example strong.DoWork();
}
```

Sofern noch eine andere starke Referenz existiert, erhöht der Aufruf von [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) die Referenzanzahl und gibt die starke Referenz an den Aufrufer zurück.

## <a name="a-weak-reference-to-the-this-pointer"></a>Eine schwache Referenz auf den *this*-Zeiger
Ein C++/WinRT-Objekt leitet sich direkt oder indirekt aus der Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) ab. Die geschützte [**implements::get_weak protected**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) Mitgliedsfunktion gibt eine schwache Referenz auf den *this*-Zeiger eines C++/WinRT-Objekts zurück. [**implements.get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) erhält eine starke Referenz.

## <a name="opting-out-of-weak-reference-support"></a>Opt-out der Unterstützung von schwachen Referenzen
Die Unterstützung schwacher Referenzen erfolgt automatisch. Sie können diese Unterstützung jedoch explizit deaktivieren, indem Sie die [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.

Wenn Sie direkt von **winrt::implements** ableiten.

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, no_weak_ref>
{
    ...
}
```

Wenn Sie eine Laufzeitklasse schreiben.

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, no_weak_ref>
{
    ...
}
```

Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint. Wenn Sie eine schwache Referenz für einen Opted-Out-Typ anfordern, dann hilft Ihnen der Compiler mit der Meldung „*Dies ist nur für die Unterstützung schwacher Referenzen*”.

## <a name="important-apis"></a>Wichtige APIs
* [implements::get_weak Funktion](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [winrt::make_weak Funktionsvorlage](/uwp/cpp-ref-for-winrt/make-weak)
* [winrt::no_weak_ref Markerstruktur](/uwp/cpp-ref-for-winrt/no-weak-ref)
* [winrt::weak_ref Strukturvorlage](/uwp/cpp-ref-for-winrt/weak-ref)
