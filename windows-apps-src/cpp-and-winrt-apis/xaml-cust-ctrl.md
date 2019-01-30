---
description: Dieses Thema führt Sie durch die Schritte zum Erstellen eines einfachen benutzerdefinierten Steuerelements mit C++ / WinRT. Sie können auf den Informationen zum Erstellen Ihrer eigenen funktionsreiche und anpassbare UI-Steuerelemente erstellen.
title: Benutzerdefinierte (vorlagenbasierte) XAML-Steuerelemente mit C++ / WinRT
ms.date: 10/03/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projizierung, XAML, benutzerdefinierten, auf Vorlagen basierenden-Steuerelement
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 24739e79b3999309aef9c1c6b35afd9ef2bbc9ab
ms.sourcegitcommit: a60ab85e9f2f9690e0141050ec3aa51f18ec61ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "9036992"
---
# <a name="xaml-custom-templated-controls-with-cwinrt"></a><span data-ttu-id="ffd6c-105">Benutzerdefinierte (vorlagenbasierte) XAML-Steuerelemente mit C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="ffd6c-105">XAML custom (templated) controls with C++/WinRT</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffd6c-106">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit unterstützen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), finden Sie unter [Nutzen von APIs mit C++ / WinRT](consume-apis.md) und [Erstellen von APIs mit C++ / WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-106">For essential concepts and terms that support your understanding of how to consume and author runtime classes with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

<span data-ttu-id="ffd6c-107">Eines der leistungsstärksten Features von der universellen Windows-Plattform (UWP) ist die Flexibilität, die der Benutzeroberfläche (UI)-Stapel bereitgestellt wird, um benutzerdefinierte Steuerelemente, die basierend auf dem Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) erstellen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-107">One of the most powerful features of the Universal Windows Platform (UWP) is the flexibility that the user-interface (UI) stack provides to create custom controls based on the XAML [**Control**](/uwp/api/windows.ui.xaml.controls.control) type.</span></span> <span data-ttu-id="ffd6c-108">Das XAML-UI-Framework bietet Features, z. B. [benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties) angefügte Eigenschaften und [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates), die Erstellen von Steuerelementen funktionsreiche und anpassbare erleichtern.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-108">The XAML UI framework provides features such as [custom dependency properties](/windows/uwp/xaml-platform/custom-dependency-properties) and attached properties, and [control templates](/windows/uwp/design/controls-and-patterns/control-templates), which make it easy to create feature-rich and customizable controls.</span></span> <span data-ttu-id="ffd6c-109">Dieses Thema führt Sie durch die Schritte zum Erstellen einer benutzerdefinierten (Steuerelementvorlage) mit C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-109">This topic walks you through the steps of creating a custom (templated) control with C++/WinRT.</span></span>

## <a name="create-a-blank-app-bglabelcontrolapp"></a><span data-ttu-id="ffd6c-110">Erstellen einer leeren App (BgLabelControlApp)</span><span class="sxs-lookup"><span data-stu-id="ffd6c-110">Create a Blank App (BgLabelControlApp)</span></span>
<span data-ttu-id="ffd6c-111">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-111">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="ffd6c-112">Erstellen Sie eine **Visual C++** > **Windows Universal** > **leere App (C++ / WinRT)** Projekt und nennen Sie es *BgLabelControlApp*.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-112">Create a **Visual C++** > **Windows Universal** > **Blank App (C++/WinRT)** project, and name it *BgLabelControlApp*.</span></span> <span data-ttu-id="ffd6c-113">In einem späteren Abschnitt dieses Themas, werden Sie zum Erstellen des Projekts weitergeleitet werden (nicht erst dann build).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-113">In a later section of this topic, you'll be directed to build your project (don't build until then).</span></span>

<span data-ttu-id="ffd6c-114">Wir werden eine neue Klasse zum Darstellen eines benutzerdefinierte (vorlagenbasierte) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-114">We're going to author a new class to represent a custom (templated) control.</span></span> <span data-ttu-id="ffd6c-115">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-115">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="ffd6c-116">Aber wir wollen in der Lage zu instanziieren diese Klasse im XAML-Markup für, die Grund, warum, dass es eine Laufzeitklasse sein soll.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-116">But we want to be able to instantiate this class from XAML markup, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="ffd6c-117">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-117">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="ffd6c-118">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-118">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="ffd6c-119">Nennen Sie es `BgLabelControl.idl`.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-119">Name it `BgLabelControl.idl`.</span></span> <span data-ttu-id="ffd6c-120">Löschen Sie den Standardinhalt von `BgLabelControl.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-120">Delete the default contents of `BgLabelControl.idl`, and paste in this runtime class declaration.</span></span>

```idl
// BgLabelControl.idl
namespace BgLabelControlApp
{
    runtimeclass BgLabelControl : Windows.UI.Xaml.Controls.Control
    {
        BgLabelControl();
        static Windows.UI.Xaml.DependencyProperty LabelProperty{ get; };
        String Label;
    }
}
```

<span data-ttu-id="ffd6c-121">Der Eintrag oben zeigt das Muster, das Sie befolgen, wenn Sie eine Abhängigkeitseigenschaft (DP) deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-121">The listing above shows the pattern that you follow when declaring a dependency property (DP).</span></span> <span data-ttu-id="ffd6c-122">Es gibt zwei Teile jedes DP.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-122">There are two pieces to each DP.</span></span> <span data-ttu-id="ffd6c-123">Zunächst deklarieren Sie eine schreibgeschützte statische Eigenschaft vom Typ [**"DependencyProperty"**](/uwp/api/windows.ui.xaml.dependencyproperty).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-123">First, you declare a read-only static property of type [**DependencyProperty**](/uwp/api/windows.ui.xaml.dependencyproperty).</span></span> <span data-ttu-id="ffd6c-124">Es verfügt über den Namen des DP plus *Eigenschaft*.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-124">It has the name of your DP plus *Property*.</span></span> <span data-ttu-id="ffd6c-125">Sie verwenden diese statische Eigenschaft in Ihrer Implementierung.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-125">You'll use this static property in your implementation.</span></span> <span data-ttu-id="ffd6c-126">Zweitens können Sie eine Instanz der Lese-/ Schreibzugriff-Eigenschaft mit den Typ und den Namen von Ihrem DP deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-126">Second, you declare a read-write instance property with the type and name of your DP.</span></span>

> [!NOTE]
> <span data-ttu-id="ffd6c-127">Wenn Sie eine DP mit einem Gleitkommazahlen Typ möchten, machen sie `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-127">If you want a DP with a floating-point type, then make it `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span></span> <span data-ttu-id="ffd6c-128">Deklarieren und implementieren eine DP vom Typ `float` (`Single` in MIDL), und klicken Sie dann für diese DP im XAML-Markup Festlegen eines Werts führt dazu, den Fehler *Fehler beim Erstellen einer "Windows.Foundation.Single" aus dem Text "<NUMBER>"*.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-128">Declaring and implementing a DP of type `float` (`Single` in MIDL), and then setting a value for that DP in XAML markup, results in the error *Failed to create a 'Windows.Foundation.Single' from the text '<NUMBER>'*.</span></span>

<span data-ttu-id="ffd6c-129">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-129">Save the file and build the project.</span></span> <span data-ttu-id="ffd6c-130">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-130">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) describing the runtime class.</span></span> <span data-ttu-id="ffd6c-131">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-131">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="ffd6c-132">Diese Dateien enthalten Stubs, um die erste Schritte zum Implementieren der **BgLabelControl** -Runtime-Klasse, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-132">These files include stubs to get you started implementing the **BgLabelControl** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="ffd6c-133">Diese Stubs sind `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` und `BgLabelControl.cpp`.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-133">Those stubs are `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` and `BgLabelControl.cpp`.</span></span>

<span data-ttu-id="ffd6c-134">Kopieren Sie die Stub-Dateien `BgLabelControl.h` und `BgLabelControl.cpp` von `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` in den Projektordner `\BgLabelControlApp\BgLabelControlApp\`.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-134">Copy the stub files `BgLabelControl.h` and `BgLabelControl.cpp` from `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` into the project folder, which is `\BgLabelControlApp\BgLabelControlApp\`.</span></span> <span data-ttu-id="ffd6c-135">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-135">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="ffd6c-136">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-136">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-the-bglabelcontrol-custom-control-class"></a><span data-ttu-id="ffd6c-137">Implementieren Sie die **BgLabelControl** benutzerdefiniertes Steuerelement-Klasse</span><span class="sxs-lookup"><span data-stu-id="ffd6c-137">Implement the **BgLabelControl** custom control class</span></span>
<span data-ttu-id="ffd6c-138">Nun öffnen wir `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` und `BgLabelControl.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-138">Now, let's open `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` and `BgLabelControl.cpp` and implement our runtime class.</span></span> <span data-ttu-id="ffd6c-139">In `BgLabelControl.h`, ändern Sie den Konstruktor zum Festlegen des Standard-Stilschlüssel, **Bezeichnung** und **LabelProperty**implementieren, fügen Sie einen statische Ereignishandler mit dem Namen **OnLabelChanged** Änderungen an den Wert der Abhängigkeitseigenschaft verarbeiten, und fügen Sie ein privates Mitglied hinzu um das Sicherungsfeld für **LabelProperty**zu speichern.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-139">In `BgLabelControl.h`, change the constructor to set the default style key, implement **Label** and **LabelProperty**, add a static event handler named **OnLabelChanged** to process changes to the value of the dependency property, and add a private member to store the backing field for **LabelProperty**.</span></span>

<span data-ttu-id="ffd6c-140">Nach dem Hinzufügen, Ihre `BgLabelControl.h` sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-140">After adding those, your `BgLabelControl.h` looks like this.</span></span>

```cppwinrt
// BgLabelControl.h
...
struct BgLabelControl : BgLabelControlT<BgLabelControl>
{
    BgLabelControl() { DefaultStyleKey(winrt::box_value(L"BgLabelControlApp.BgLabelControl")); }

    winrt::hstring Label()
    {
        return winrt::unbox_value<winrt::hstring>(GetValue(m_labelProperty));
    }

    void Label(winrt::hstring const& value)
    {
        SetValue(m_labelProperty, winrt::box_value(value));
    }

    static Windows::UI::Xaml::DependencyProperty LabelProperty() { return m_labelProperty; }

    static void OnLabelChanged(Windows::UI::Xaml::DependencyObject const&, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const&);

private:
    static Windows::UI::Xaml::DependencyProperty m_labelProperty;
};
...
```

<span data-ttu-id="ffd6c-141">In `BgLabelControl.cpp`, definieren Sie die statischen Member wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-141">In `BgLabelControl.cpp`, define the static members like this.</span></span>

```cppwinrt
// BgLabelControl.cpp
...
Windows::UI::Xaml::DependencyProperty BgLabelControl::m_labelProperty =
    Windows::UI::Xaml::DependencyProperty::Register(
        L"Label",
        winrt::xaml_typename<winrt::hstring>(),
        winrt::xaml_typename<BgLabelControlApp::BgLabelControl>(),
        Windows::UI::Xaml::PropertyMetadata{ winrt::box_value(L"default label"), Windows::UI::Xaml::PropertyChangedCallback{ &BgLabelControl::OnLabelChanged } }
);

void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject const& d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const& /* e */)
{
    if (BgLabelControlApp::BgLabelControl theControl{ d.try_as<BgLabelControlApp::BgLabelControl>() })
    {
        // Call members of the projected type via theControl.

        BgLabelControlApp::implementation::BgLabelControl* ptr{ winrt::get_self<BgLabelControlApp::implementation::BgLabelControl>(theControl) };
        // Call members of the implementation type via ptr.
    }
}
...
```

<span data-ttu-id="ffd6c-142">In dieser exemplarischen Vorgehensweise wird nicht wir **OnLabelChanged**verwenden.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-142">In this walkthrough, we won't be using **OnLabelChanged**.</span></span> <span data-ttu-id="ffd6c-143">Es ist jedoch vorhanden, damit Sie sehen können, wie Sie eine Abhängigkeitseigenschaft mit einem "PropertyChanged"-Rückruf registrieren.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-143">But it's there so that you can see how to register a dependency property with a property-changed callback.</span></span> <span data-ttu-id="ffd6c-144">Die Implementierung des **OnLabelChanged** veranschaulicht einen abgeleiteten projizierten Typ von projizierten Basistyp erhalten (des Basistyps projizierten **DependencyObject**, in diesem Fall ist).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-144">The implementation of **OnLabelChanged** also shows how to obtain a derived projected type from a base projected type (the base projected type is **DependencyObject**, in this case).</span></span> <span data-ttu-id="ffd6c-145">Und es zeigt, wie Sie dann einen Zeiger auf den Typ abrufen, die den projizierten Typ implementiert.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-145">And it shows how to then obtain a pointer to the type that implements the projected type.</span></span> <span data-ttu-id="ffd6c-146">Diese zweite Vorgang ist natürlich nur im Projekt möglich, die den projizierten Typ (d. h. das Projekt, das die Laufzeitklasse implementiert) implementiert.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-146">That second operation will naturally only be possible in the project that implements the projected type (that is, the project that implements the runtime class).</span></span>

> [!NOTE]
> <span data-ttu-id="ffd6c-147">Wenn Sie noch nicht installiert, das Windows SDK Version 10.0.17763.0 (Windows 10, Version 1809 haben) oder höher, dann Sie [**WinRT:: from_abi**](/uwp/cpp-ref-for-winrt/from-abi) im Abhängigkeit Eigenschaft geänderte Ereignishandler oben anstelle von [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self)aufrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-147">If you haven't installed the Windows SDK version 10.0.17763.0 (Windows 10, version 1809), or later, then you need to call [**winrt::from_abi**](/uwp/cpp-ref-for-winrt/from-abi) in the dependency property changed event handler above, instead of [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self).</span></span>

## <a name="design-the-default-style-for-bglabelcontrol"></a><span data-ttu-id="ffd6c-148">Entwerfen des Standardstils für **BgLabelControl**</span><span class="sxs-lookup"><span data-stu-id="ffd6c-148">Design the default style for **BgLabelControl**</span></span>

<span data-ttu-id="ffd6c-149">Im Konstruktor legt **BgLabelControl** einen Standard-Stilschlüssel für sich selbst.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-149">In its constructor, **BgLabelControl** sets a default style key for itself.</span></span> <span data-ttu-id="ffd6c-150">Was *ist* jedoch ein Standardstil?</span><span class="sxs-lookup"><span data-stu-id="ffd6c-150">But what *is* a default style?</span></span> <span data-ttu-id="ffd6c-151">Ein benutzerdefiniertes Steuerelement (vorlagenbasiertes) benötigt einen Standardstil&mdash;mit einer Standard-Steuerelementvorlage&mdash;die sie verwenden können, selbst mit für den Fall, dass der Consumer des Steuerelements einen Stil bzw. die Vorlage festlegen nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-151">A custom (templated) control needs to have a default style&mdash;containing a default control template&mdash;which it can use to render itself with in case the consumer of the control doesn't set a style and/or template.</span></span> <span data-ttu-id="ffd6c-152">In diesem Abschnitt fügen wir eine Markupdatei dem Projekt mit unseren Standardstil.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-152">In this section we'll add a markup file to the project containing our default style.</span></span>

<span data-ttu-id="ffd6c-153">Klicken Sie unter Ihrem Projektknoten erstellen Sie einen neuen Ordner, und nennen Sie es "Themes".</span><span class="sxs-lookup"><span data-stu-id="ffd6c-153">Under your project node, create a new folder and name it "Themes".</span></span> <span data-ttu-id="ffd6c-154">Unter `Themes`, fügen Sie ein neues Element vom Typ **Visual C++** > **XAML** > **XAML-Ansicht**, und nennen Sie es "Generic.xaml".</span><span class="sxs-lookup"><span data-stu-id="ffd6c-154">Under `Themes`, add a new item of type **Visual C++** > **XAML** > **XAML View**, and name it "Generic.xaml".</span></span> <span data-ttu-id="ffd6c-155">Die Ordner- und müssen wie folgt in der Reihenfolge für das XAML-Framework, um den Standardstil für ein benutzerdefiniertes Steuerelement zu finden sein.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-155">The folder and file names have to be like this in order for the XAML framework to find the default style for a custom control.</span></span> <span data-ttu-id="ffd6c-156">Löschen Sie den Standardinhalt von `Generic.xaml`, und fügen Sie im Markup unten.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-156">Delete the default contents of `Generic.xaml`, and paste in the markup below.</span></span>

```xaml
<!-- \Themes\Generic.xaml -->
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:BgLabelControlApp">

    <Style TargetType="local:BgLabelControl" >
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="local:BgLabelControl">
                    <Grid Width="100" Height="100" Background="{TemplateBinding Background}">
                        <TextBlock HorizontalAlignment="Center" VerticalAlignment="Center" Text="{TemplateBinding Label}"/>
                    </Grid>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
</ResourceDictionary>
```

<span data-ttu-id="ffd6c-157">In diesem Fall ist die einzige Eigenschaft, die der Standardstil legt die Steuerelementvorlage.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-157">In this case, the only property that the default style sets is the control template.</span></span> <span data-ttu-id="ffd6c-158">Die Vorlage besteht aus ein Quadrat (dessen Hintergrund auf die **Hintergrund** -Eigenschaft, die alle Instanzen von den Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) gebunden ist), und ein Textelement (, dessen Text auf die Abhängigkeitseigenschaft **BgLabelControl::Label** gebunden ist).</span><span class="sxs-lookup"><span data-stu-id="ffd6c-158">The template consists of a square (whose background is bound to the **Background** property that all instances of the XAML [**Control**](/uwp/api/windows.ui.xaml.controls.control) type have), and a text element (whose text is bound to the **BgLabelControl::Label** dependency property).</span></span>

## <a name="add-an-instance-of-bglabelcontrol-to-the-main-ui-page"></a><span data-ttu-id="ffd6c-159">Fügen Sie eine Instanz des **BgLabelControl** auf die UI-Hauptseite</span><span class="sxs-lookup"><span data-stu-id="ffd6c-159">Add an instance of **BgLabelControl** to the main UI page</span></span>

<span data-ttu-id="ffd6c-160">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-160">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="ffd6c-161">Unmittelbar nach dem **Button** -Element (innerhalb der **StackPanel**) fügen Sie das folgende Markup hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-161">Immediately after the **Button** element (inside the **StackPanel**), add the following markup.</span></span>

```xaml
<local:BgLabelControl Background="Red" Label="Hello, World!"/>
```

<span data-ttu-id="ffd6c-162">Fügen Sie außerdem hinzu, die folgenden #include `MainPage.h` , damit der **MainPage** -Typ (eine Kombination aus XAML-Markup und imperativen Code Kompilieren) im Hinblick auf den Typ der benutzerdefinierten Steuerelements **BgLabelControl** ist.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-162">Also, add the following include directive to `MainPage.h` so that the **MainPage** type (a combination of compiling XAML markup and imperative code) is aware of the **BgLabelControl** custom control type.</span></span> <span data-ttu-id="ffd6c-163">Wenn Sie möchten, **BgLabelControl** von einer anderen XAML-Seite, dann fügen Sie einzubeziehen identisch Richtlinie in der Headerdatei für diese Seite.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-163">If you want to use **BgLabelControl** from another XAML page, then add this same include directive to the header file for that page, too.</span></span> <span data-ttu-id="ffd6c-164">Oder, Alternativ stellen einfach eine einzelne Richtlinie in der vorkompilierten Header-Datei.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-164">Or, alternatively, just put a single include directive in your precompiled header file.</span></span>

```cppwinrt
// MainPage.h
...
#include "BgLabelControl.h"
...
```

<span data-ttu-id="ffd6c-165">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-165">Now build and run the project.</span></span> <span data-ttu-id="ffd6c-166">Sie sehen, dass die standardmäßige Steuerelementvorlage des Hintergrundpinsels und mit der Bezeichnung, die Instanz **BgLabelControl** im Markup gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-166">You'll see that the default control template is binding to the background brush, and to the label, of the **BgLabelControl** instance in the markup.</span></span>

<span data-ttu-id="ffd6c-167">In dieser exemplarischen Vorgehensweise wurde ein einfaches Beispiel für ein benutzerdefiniertes Steuerelement (vorlagenbasierte) gezeigt, in C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-167">This walkthrough showed a simple example of a custom (templated) control in C++/WinRT.</span></span> <span data-ttu-id="ffd6c-168">Sie können Ihre eigenen benutzerdefinierten Steuerelemente willkürlich reichhaltige und mit vollem Funktionsumfang machen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-168">You can make your own custom controls arbitrarily rich and full-featured.</span></span> <span data-ttu-id="ffd6c-169">Beispielsweise kann ein benutzerdefiniertes Steuerelement etwas so kompliziert ist wie ein Raster bearbeitbare Daten, einen video-Player oder eine Schnellansicht der 3D-Geometrie Form dauern.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-169">For example, a custom control can take the form of something as complicated as an editable data grid, a video player, or a visualizer of 3D geometry.</span></span>

## <a name="implementing-overridable-functions-such-as-measureoverride-and-onapplytemplate"></a><span data-ttu-id="ffd6c-170">Implementieren von *überschreibbaren* Funktionen, z. B. **MeasureOverride** und **OnApplyTemplate**</span><span class="sxs-lookup"><span data-stu-id="ffd6c-170">Implementing *overridable* functions, such as **MeasureOverride** and **OnApplyTemplate**</span></span>

<span data-ttu-id="ffd6c-171">Sie leiten ein benutzerdefiniertes Steuerelement von der [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) -Runtime-Klasse, die selbst weiter Basis-Runtime-Klassen abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-171">You derive a custom control from the [**Control**](/uwp/api/windows.ui.xaml.controls.control) runtime class, which itself further derives from base runtime classes.</span></span> <span data-ttu-id="ffd6c-172">Und es gibt überschreibbare Methoden eines **Steuerelements**, [**FrameworkElement**](/uwp/api/windows.ui.xaml.frameworkelement)und [**UIElement**](/uwp/api/windows.ui.xaml.uielement) , die Sie in Ihre abgeleitete Klasse überschreiben können.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-172">And there are overridable methods of **Control**, [**FrameworkElement**](/uwp/api/windows.ui.xaml.frameworkelement), and [**UIElement**](/uwp/api/windows.ui.xaml.uielement) that you can override in your derived class.</span></span> <span data-ttu-id="ffd6c-173">Hier ist ein Codebeispiel Sie wie das geht.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-173">Here's a code example showing you how to do that.</span></span>

```cppwinrt
struct BgLabelControl : BgLabelControlT<BgLabelControl>
{
...
    // Control overrides.
    void OnPointerPressed(Windows::UI::Xaml::Input::PointerRoutedEventArgs const& /* e */) const { ... };

    // FrameworkElement overrides.
    Windows::Foundation::Size MeasureOverride(Windows::Foundation::Size const& /* availableSize */) const { ... };
    void OnApplyTemplate() const { ... };

    // UIElement overrides.
    Windows::UI::Xaml::Automation::Peers::AutomationPeer OnCreateAutomationPeer() const { ... };
...
};
```

<span data-ttu-id="ffd6c-174">*Overridable* Funktionen darstellen selbst unterschiedlich in verschiedenen sprachprojektionen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-174">*Overridable* functions present themselves differently in different language projections.</span></span> <span data-ttu-id="ffd6c-175">In c# werden z. B. überschreibbare Funktionen in der Regel als geschützte virtuelle Funktionen.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-175">In C#, for example, overridable functions typically appear as protected virtual functions.</span></span> <span data-ttu-id="ffd6c-176">In C++ / WinRT können sie virtuelle weder geschützt sind, Sie können jedoch außer Kraft setzen, und eine eigene Implementierung, bereitstellen, wie oben gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ffd6c-176">In C++/WinRT, they're neither virtual nor protected, but you can still override them and provide your own implementation, as shown above.</span></span>

## <a name="important-apis"></a><span data-ttu-id="ffd6c-177">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="ffd6c-177">Important APIs</span></span>
* [<span data-ttu-id="ffd6c-178">Steuerelementklasse</span><span class="sxs-lookup"><span data-stu-id="ffd6c-178">Control class</span></span>](/uwp/api/windows.ui.xaml.controls.control)
* [<span data-ttu-id="ffd6c-179">DependencyProperty-Klasse</span><span class="sxs-lookup"><span data-stu-id="ffd6c-179">DependencyProperty class</span></span>](/uwp/api/windows.ui.xaml.dependencyproperty)
* [<span data-ttu-id="ffd6c-180">FrameworkElement-Klasse</span><span class="sxs-lookup"><span data-stu-id="ffd6c-180">FrameworkElement class</span></span>](/uwp/api/windows.ui.xaml.frameworkelement)
* [<span data-ttu-id="ffd6c-181">UIElement-Klasse</span><span class="sxs-lookup"><span data-stu-id="ffd6c-181">UIElement class</span></span>](/uwp/api/windows.ui.xaml.uielement)

## <a name="related-topics"></a><span data-ttu-id="ffd6c-182">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ffd6c-182">Related topics</span></span>
* [<span data-ttu-id="ffd6c-183">Steuerelementvorlagen</span><span class="sxs-lookup"><span data-stu-id="ffd6c-183">Control templates</span></span>](/windows/uwp/design/controls-and-patterns/control-templates)
* [<span data-ttu-id="ffd6c-184">Benutzerdefinierte Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="ffd6c-184">Custom dependency properties</span></span>](/windows/uwp/xaml-platform/custom-dependency-properties)
