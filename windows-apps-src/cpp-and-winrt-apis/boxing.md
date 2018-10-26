---
author: stevewhims
description: Ein Einzelwert muss in ein Referenzklassenobjekt gepackt werden, bevor er an eine Funktion übergeben wird, die **IInspectable** erwartet. Dieser Wrapping-Prozess wird als *Boxing* des Wertes bezeichnet.
title: Boxing und Unboxing von Einzelwerten für IInspectable mit C++/WinRT
ms.author: stwhi
ms.date: 04/10/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, XAML, steuerelement, boxing, einzelwert
ms.localizationpriority: medium
ms.openlocfilehash: f4b99f587fbd517b677d85b50abb26fdf072b359
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5595095"
---
# <a name="boxing-and-unboxing-scalar-values-to-iinspectable-with-cwinrt"></a><span data-ttu-id="42707-105">Boxing und Unboxing von Einzelwerten für IInspectable mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="42707-105">Boxing and unboxing scalar values to IInspectable with C++/WinRT</span></span>
 
<span data-ttu-id="42707-106">Die [**IInspectable**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)-Schnittstellen ist die Root-Schnittstelle jeder Laufzeitklasse in Windows-Runtime (WinRT).</span><span class="sxs-lookup"><span data-stu-id="42707-106">The [**IInspectable interface**](/windows/desktop/api/inspectable/nn-inspectable-iinspectable) is the root interface of every runtime class in the Windows Runtime (WinRT).</span></span> <span data-ttu-id="42707-107">Dies ist eine Idee, die analoge zu [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) am Stammknoten jeder COM-Schnittstelle und Klasse ist. **System.Object** ist der Stammknoten jeder [Common Type System](https://docs.microsoft.com/dotnet/standard/base-types/common-type-system)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="42707-107">This is an analogous idea to [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) being at the root of every COM interface and class; and **System.Object** being at the root of every [Common Type System](https://docs.microsoft.com/dotnet/standard/base-types/common-type-system) class.</span></span>

<span data-ttu-id="42707-108">Mit anderen Worten, eine Funktion, die **IInspectable** erwartet, kann eine Instanz einer beliebigen Laufzeitklasse übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="42707-108">In other words, a function that expects **IInspectable** can be passed an instance of any runtime class.</span></span> <span data-ttu-id="42707-109">Sie können aber nicht direkt einen Einzelwert, wie z. B. einen Zahlen- oder Textwert, an eine solche Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="42707-109">But you can't directly pass a scalar value, such as a numeric or text value, to such a function.</span></span> <span data-ttu-id="42707-110">Stattdessen muss ein Einzelwert in ein Objekt der Referenzklasse gepackt werden.</span><span class="sxs-lookup"><span data-stu-id="42707-110">Instead, a scalar value needs to be wrapped inside a reference class object.</span></span> <span data-ttu-id="42707-111">Dieser Wrapping-Prozess wird als *Boxing* des Wertes bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="42707-111">That wrapping process is known as *boxing* the value.</span></span>

<span data-ttu-id="42707-112">[C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) bietet die [**WinRT:: box_value**](/uwp/cpp-ref-for-winrt/box-value) -Funktion, die einen Einzelwert entgegennimmt und den boxed-Wert in einer **IInspectable**zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="42707-112">[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)  provides the [**winrt::box_value**](/uwp/cpp-ref-for-winrt/box-value) function, which takes a scalar value and returns the value boxed into an **IInspectable**.</span></span> <span data-ttu-id="42707-113">Um ein **IInspectable** wieder in einen Einzelwert zu entpacken, gibt es die Funktionen [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) und [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or).</span><span class="sxs-lookup"><span data-stu-id="42707-113">For unboxing an **IInspectable** back into a scalar value, there are the [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) and  [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) functions.</span></span>

## <a name="examples-of-boxing-a-value"></a><span data-ttu-id="42707-114">Beispiele für das Boxen eines Wertes</span><span class="sxs-lookup"><span data-stu-id="42707-114">Examples of boxing a value</span></span>
<span data-ttu-id="42707-115">Die Zugriffsfunktion [**LaunchActivatedEventArgs::Arguments**](/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.Arguments) gibt einen [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) zurück, der ein Einzelwert ist.</span><span class="sxs-lookup"><span data-stu-id="42707-115">The [**LaunchActivatedEventArgs::Arguments**](/uwp/api/windows.applicationmodel.activation.launchactivatedeventargs.Arguments) accessor function returns a [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring), which is a scalar value.</span></span> <span data-ttu-id="42707-116">Wir können diesen **hstring**-Wert einpacken und an eine Funktion übergeben, die so ein **IInspectable** erwartet.</span><span class="sxs-lookup"><span data-stu-id="42707-116">We can box that **hstring** value and pass it to a function that expects **IInspectable** like this.</span></span>

```cppwinrt
void App::OnLaunched(LaunchActivatedEventArgs const& e)
{
    ...
    rootFrame.Navigate(winrt::xaml_typename<BlankApp1::MainPage>(), winrt::box_value(e.Arguments()));
    ...
}
```

<span data-ttu-id="42707-117">Um die Content-Eigenschaft eines XAML-[**Button**](/uwp/api/windows.ui.xaml.controls.button) festzulegen, rufen Sie die Zugriffsfunktion [**Button::Content**](/uwp/api/windows.ui.xaml.controls.contentcontrol.content?) auf.</span><span class="sxs-lookup"><span data-stu-id="42707-117">To set the content property of a XAML [**Button**](/uwp/api/windows.ui.xaml.controls.button), you call the [**Button::Content**](/uwp/api/windows.ui.xaml.controls.contentcontrol.content?) mutator function.</span></span> <span data-ttu-id="42707-118">Um die Content-Eigenschaft auf einen String-Wert zu setzen, können Sie diesen Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="42707-118">To set the content property to a string value, you can use this code.</span></span>

```cppwinrt
Button().Content(winrt::box_value(L"Clicked"));
```

<span data-ttu-id="42707-119">Zuerst wandelt der [**hstring**](/uwp/cpp-ref-for-winrt/hstring)-Konvertierungskonstruktor das String-Literal in einen **hstring** um.</span><span class="sxs-lookup"><span data-stu-id="42707-119">First, the [**hstring**](/uwp/cpp-ref-for-winrt/hstring) conversion constructor converts the string literal into an **hstring**.</span></span> <span data-ttu-id="42707-120">Dann wird die Überladung von **winrt::box_value**, die einen **hstring** benötigt, aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="42707-120">Then the overload of **winrt::box_value** that takes an **hstring** is invoked.</span></span>

## <a name="examples-of-unboxing-an-iinspectable"></a><span data-ttu-id="42707-121">Beispiele für das Unboxing eines IInspectable</span><span class="sxs-lookup"><span data-stu-id="42707-121">Examples of unboxing an IInspectable</span></span>
<span data-ttu-id="42707-122">In Ihren eigenen Funktionen (die ein **IInspectable** erwarten) können Sie [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) zum Unboxing verwenden. Sie können [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) zum Unboxing mit einem Standardwert verwenden.</span><span class="sxs-lookup"><span data-stu-id="42707-122">In your own functions that expect **IInspectable**, you can use [**winrt::unbox_value**](/uwp/cpp-ref-for-winrt/unbox-value) to unbox, and you can use [**winrt::unbox_value_or**](/uwp/cpp-ref-for-winrt/unbox-value-or) to unbox with a default value.</span></span>

```cppwinrt
void Unbox(winrt::Windows::Foundation::IInspectable const& object)
{
    hstring hstringValue = unbox_value<hstring>(object); // Throws if object is not a boxed string.
    hstringValue = unbox_value_or<hstring>(object, L"Default"); // Returns L"Default" if object is not a boxed string.
    float floatValue = unbox_value_or<float>(object, 0.f); // Returns 0.0 if object is not a boxed float.
}
```

## <a name="determine-the-type-of-a-boxed-value"></a><span data-ttu-id="42707-123">Ermitteln des Typs eines eingepackten Werts</span><span class="sxs-lookup"><span data-stu-id="42707-123">Determine the type of a boxed value</span></span>
<span data-ttu-id="42707-124">Wenn Sie einen eingepackten Wert erhalten und nicht sicher sind, welchen Typ er enthält (Sie müssen den Typ wissen, um ihn zu entpacken), können Sie den eingepackten Wert nach seiner [**IPropertyValue**](/uwp/api/windows.foundation.ipropertyvalue)-Schnittstelle abfragen und dann **Type** dafür aufrufen.</span><span class="sxs-lookup"><span data-stu-id="42707-124">If you receive a boxed value and you're unsure what type it contains (you need to know its type in order to unbox it), then you can query the boxed value for its [**IPropertyValue**](/uwp/api/windows.foundation.ipropertyvalue) interface, and then call **Type** on that.</span></span> <span data-ttu-id="42707-125">Dies ist ein Codebeispiel:</span><span class="sxs-lookup"><span data-stu-id="42707-125">Here's a code example.</span></span>

```cppwinrt
float pi = 3.14f;
auto piInspectable = winrt::box_value(pi);
auto piPropertyValue = piInspectable.as<winrt::Windows::Foundation::IPropertyValue>();
WINRT_ASSERT(piPropertyValue.Type() == winrt::Windows::Foundation::PropertyType::Single);
```

## <a name="important-apis"></a><span data-ttu-id="42707-126">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="42707-126">Important APIs</span></span>
* [<span data-ttu-id="42707-127">IInspectable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="42707-127">IInspectable interface</span></span>](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)
* [<span data-ttu-id="42707-128">winrt::box_value Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="42707-128">winrt::box_value function template</span></span>](/uwp/cpp-ref-for-winrt/box-value)
* [<span data-ttu-id="42707-129">winrt::hstring Struktur</span><span class="sxs-lookup"><span data-stu-id="42707-129">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="42707-130">winrt::unbox_value Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="42707-130">winrt::unbox_value function template</span></span>](/uwp/cpp-ref-for-winrt/unbox-value)
* [<span data-ttu-id="42707-131">winrt::unbox_value_or Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="42707-131">winrt::unbox_value_or function template</span></span>](/uwp/cpp-ref-for-winrt/unbox-value-or)
