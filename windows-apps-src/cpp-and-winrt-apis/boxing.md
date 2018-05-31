---
author: stevewhims
description: Ein Einzelwert muss in ein Referenzklassenobjekt gepackt werden, bevor er an eine Funktion übergeben wird, die **IInspectable** erwartet. Dieser Wrapping-Prozess wird als *Boxing* des Wertes bezeichnet.
title: Boxing und Unboxing von Einzelwerten für IInspectable mit C++/WinRT
ms.author: stwhi
ms.date: 04/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, boxing, einzelwert
ms.localizationpriority: medium
ms.openlocfilehash: 61d5c7a35fb7a6ff9952f3fe768f4faa3f6c6347
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832004"
---
# <a name="boxing-and-unboxing-scalar-values-to-iinspectable-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="0a6b2-105">Boxing und Unboxing von Einzelwerten für IInspectable mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="0a6b2-105">Boxing and unboxing scalar values to IInspectable with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span> 
<span data-ttu-id="0a6b2-106">Die [**IInspectable**](https://msdn.microsoft.com/library/windows/desktop/br205821)-Schnittstellen ist die Root-Schnittstelle jeder Laufzeitklasse in Windows-Runtime (WinRT).</span><span class="sxs-lookup"><span data-stu-id="0a6b2-106">The [**IInspectable interface**](https://msdn.microsoft.com/library/windows/desktop/br205821) is the root interface of every runtime class in the Windows Runtime (WinRT).</span></span> <span data-ttu-id="0a6b2-107">Dies ist eine Idee, die analoge zu [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) am Stammknoten jeder COM-Schnittstelle und Klasse ist. **System.Object** ist der Stammknoten jeder [Common Type System](https://docs.microsoft.com/dotnet/standard/base-types/common-type-system)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-107">This is an analogous idea to [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) being at the root of every COM interface and class; and **System.Object** being at the root of every [Common Type System](https://docs.microsoft.com/dotnet/standard/base-types/common-type-system) class.</span></span>

<span data-ttu-id="0a6b2-108">Mit anderen Worten, eine Funktion, die **IInspectable** erwartet, kann eine Instanz einer beliebigen Laufzeitklasse übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-108">In other words, a function that expects **IInspectable** can be passed an instance of any runtime class.</span></span> <span data-ttu-id="0a6b2-109">Sie können aber nicht direkt einen Einzelwert, wie z. B. einen Zahlen- oder Textwert, an eine solche Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-109">But you can't directly pass a scalar value, such as a numeric or text value, to such a function.</span></span> <span data-ttu-id="0a6b2-110">Stattdessen muss ein Einzelwert in ein Objekt der Referenzklasse gepackt werden.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-110">Instead, a scalar value needs to be wrapped inside a reference class object.</span></span> <span data-ttu-id="0a6b2-111">Dieser Wrapping-Prozess wird als *Boxing* des Wertes bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-111">That wrapping process is known as *boxing* the value.</span></span>

<span data-ttu-id="0a6b2-112">C++/WinRT stellt die Funktion [**winrt::box_value**](/uwp/cpp-ref-for-winrt/box-value) zur Verfügung, die einen Einzelwert entgegennimmt und den Boxed-Wert als **IInspectable** zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-112">C++/WinRT provides the [**winrt::box_value**](/uwp/cpp-ref-for-winrt/box-value) function, which takes a scalar value and returns the value boxed into an **IInspectable**.</span></span> <span data-ttu-id="0a6b2-113">Um ein **IInspectable** wieder in einen Einzelwert zu entpacken, gibt es die Funktionen [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) und [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or).</span><span class="sxs-lookup"><span data-stu-id="0a6b2-113">For unboxing an **IInspectable** back into a scalar value, there are the [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) and  [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) functions.</span></span>

## <a name="examples-of-boxing-a-value"></a><span data-ttu-id="0a6b2-114">Beispiele für das Boxen eines Wertes</span><span class="sxs-lookup"><span data-stu-id="0a6b2-114">Examples of boxing a value</span></span>
<span data-ttu-id="0a6b2-115">Die Zugriffsfunktion [**LaunchActivatedEventArgs::Arguments**](/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.Arguments) gibt einen [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) zurück, der ein Einzelwert ist.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-115">The [**LaunchActivatedEventArgs::Arguments**](/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.Arguments) accessor function returns a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring), which is a scalar value.</span></span> <span data-ttu-id="0a6b2-116">Wir können diesen **hstring**-Wert einpacken und an eine Funktion übergeben, die so ein **IInspectable** erwartet.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-116">We can box that **hstring** value and pass it to a function that expects **IInspectable** like this.</span></span>

```cppwinrt
void App::OnLaunched(LaunchActivatedEventArgs const& e)
{
    ...
    rootFrame.Navigate(xaml_typename<BlankApp1::MainPage>(), winrt::box_value(e.Arguments()));
    ...
}
```

<span data-ttu-id="0a6b2-117">Um die Content-Eigenschaft eines XAML-[**Button**](/uwp/api/windows.ui.xaml.controls.button) festzulegen, rufen Sie die Zugriffsfunktion [**Button::Content**](/uwp/api/windows.ui.xaml.controls.contentcontrol.content?) auf.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-117">To set the content property of a XAML [**Button**](/uwp/api/windows.ui.xaml.controls.button), you call the [**Button::Content**](/uwp/api/windows.ui.xaml.controls.contentcontrol.content?) mutator function.</span></span> <span data-ttu-id="0a6b2-118">Um die Content-Eigenschaft auf einen String-Wert zu setzen, können Sie diesen Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-118">To set the content property to a string value, you can use this code.</span></span>

```cppwinrt
Button().Content(winrt::box_value(L"Clicked"));
```

<span data-ttu-id="0a6b2-119">Zuerst wandelt der **hstring**-Konvertierungskonstruktor das String-Literal in einen **hstring** um.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-119">First, the **hstring** conversion constructor converts the string literal into an **hstring**.</span></span> <span data-ttu-id="0a6b2-120">Dann wird die Überladung von **winrt::box_value**, die einen **hstring** benötigt, aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-120">Then the overload of **winrt::box_value** that takes an **hstring** is invoked.</span></span>

## <a name="examples-of-unboxing-an-iinspectable"></a><span data-ttu-id="0a6b2-121">Beispiele für das Unboxing eines IInspectable</span><span class="sxs-lookup"><span data-stu-id="0a6b2-121">Examples of unboxing an IInspectable</span></span>
<span data-ttu-id="0a6b2-122">In Ihren eigenen Funktionen (die ein **IInspectable** erwarten) können Sie [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) zum Unboxing verwenden. Sie können [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) zum Unboxing mit einem Standardwert verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a6b2-122">In your own functions that expect **IInspectable**, you can use [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) to unbox, and you can use [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) to unbox with a default value.</span></span>

```cppwinrt
void Unbox(Windows::Foundation::IInspectable const& object)
{
    hstring hstringValue = unbox_value<hstring>(object); // Throws if object is not a boxed string.
    hstringValue = unbox_value_or<hstring>(object, L"Default"); // Returns L"Default" if object is not a boxed string.
    float floatValue = unbox_value_or<float>(object, 0.f); // Returns 0.0 if object is not a boxed float.
}
```

## <a name="important-apis"></a><span data-ttu-id="0a6b2-123">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="0a6b2-123">Important APIs</span></span>
* [<span data-ttu-id="0a6b2-124">IInspectable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="0a6b2-124">IInspectable interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/br205821)
* [<span data-ttu-id="0a6b2-125">winrt::box_value Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="0a6b2-125">winrt::box_value function template</span></span>](/uwp/cpp-ref-for-winrt/box-value)
* [<span data-ttu-id="0a6b2-126">winrt::unbox_value Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="0a6b2-126">winrt::unbox_value function template</span></span>](/uwp/cpp-ref-for-winrt/unbox-value)
* [<span data-ttu-id="0a6b2-127">winrt::unbox_value_or Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="0a6b2-127">winrt::unbox_value_or function template</span></span>](/uwp/cpp-ref-for-winrt/unbox-value-or)
