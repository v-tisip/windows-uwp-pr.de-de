---
description: Dieses Thema führt Sie durch die Schritte zum Erstellen eines einfachen benutzerdefinierten Steuerelements mit C++ / WinRT. Sie können auf den Informationen zum Erstellen Ihrer eigenen Features und anpassbare UI-Steuerelemente erstellen.
title: Benutzerdefinierte (vorlagenbasierte) XAML-Steuerelemente mit C++ / WinRT
ms.date: 10/03/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projizierung, XAML, benutzerdefinierte Steuerelement mit Vorlagen,
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: e929f217c71a90540803b180e6e79b98802f9c7a
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8943655"
---
# <a name="xaml-custom-templated-controls-with-cwinrt"></a><span data-ttu-id="9ab3d-105">Benutzerdefinierte (vorlagenbasierte) XAML-Steuerelemente mit C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="9ab3d-105">XAML custom (templated) controls with C++/WinRT</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ab3d-106">Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit unterstützen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), finden Sie unter [Nutzen von APIs mit C++ / WinRT](consume-apis.md) und [Erstellen von APIs mit C++ / WinRT](author-apis.md).</span><span class="sxs-lookup"><span data-stu-id="9ab3d-106">For essential concepts and terms that support your understanding of how to consume and author runtime classes with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), see [Consume APIs with C++/WinRT](consume-apis.md) and [Author APIs with C++/WinRT](author-apis.md).</span></span>

<span data-ttu-id="9ab3d-107">Eines der leistungsstärksten Features von der universellen Windows-Plattform (UWP) ist die Flexibilität, die die Benutzeroberfläche (UI)-Stapel bereitstellt, um benutzerdefinierte Steuerelemente, die basierend auf dem Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-107">One of the most powerful features of the Universal Windows Platform (UWP) is the flexibility that the user-interface (UI) stack provides to create custom controls based on the XAML [**Control**](/uwp/api/windows.ui.xaml.controls.control) type.</span></span> <span data-ttu-id="9ab3d-108">Das XAML-UI-Framework bietet Features, z. B. [benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties) und angefügte Eigenschaften und [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates), die Erstellen von Steuerelementen mit zahlreichen Funktionen und anpassbare erleichtern.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-108">The XAML UI framework provides features such as [custom dependency properties](/windows/uwp/xaml-platform/custom-dependency-properties) and attached properties, and [control templates](/windows/uwp/design/controls-and-patterns/control-templates), which make it easy to create feature-rich and customizable controls.</span></span> <span data-ttu-id="9ab3d-109">Dieses Thema führt Sie durch die Schritte zum Erstellen einer benutzerdefinierten (Steuerelementvorlage) mit C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-109">This topic walks you through the steps of creating a custom (templated) control with C++/WinRT.</span></span>

## <a name="create-a-blank-app-bglabelcontrolapp"></a><span data-ttu-id="9ab3d-110">Erstellen Sie eine leere App (BgLabelControlApp)</span><span class="sxs-lookup"><span data-stu-id="9ab3d-110">Create a Blank App (BgLabelControlApp)</span></span>
<span data-ttu-id="9ab3d-111">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-111">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="9ab3d-112">Erstellen Sie ein **Visual C++** > **Universelle Windows-** > **leere App (C++ / WinRT)** Projekt und nennen Sie es *BgLabelControlApp*.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-112">Create a **Visual C++** > **Windows Universal** > **Blank App (C++/WinRT)** project, and name it *BgLabelControlApp*.</span></span>

<span data-ttu-id="9ab3d-113">Wir werden eine neue Klasse zum Darstellen eines benutzerdefinierte (vorlagenbasierte) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-113">We're going to author a new class to represent a custom (templated) control.</span></span> <span data-ttu-id="9ab3d-114">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-114">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="9ab3d-115">Aber wir wollen in der Lage, instanziieren Sie diese Klasse im XAML-Markup und für die, die Grund, warum, dass es eine Laufzeitklasse sein soll.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-115">But we want to be able to instantiate this class from XAML markup, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="9ab3d-116">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-116">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="9ab3d-117">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-117">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="9ab3d-118">Nennen Sie es `BgLabelControl.idl`.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-118">Name it `BgLabelControl.idl`.</span></span> <span data-ttu-id="9ab3d-119">Löschen Sie den Standardinhalt von `BgLabelControl.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-119">Delete the default contents of `BgLabelControl.idl`, and paste in this runtime class declaration.</span></span>

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

<span data-ttu-id="9ab3d-120">Der Eintrag oben zeigt das Muster, das Sie befolgen, wenn Sie eine Abhängigkeitseigenschaft (DP) zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-120">The listing above shows the pattern that you follow when declaring a dependency property (DP).</span></span> <span data-ttu-id="9ab3d-121">Es gibt zwei Teile für jede DP.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-121">There are two pieces to each DP.</span></span> <span data-ttu-id="9ab3d-122">Zunächst deklarieren Sie eine schreibgeschützte statische Eigenschaft vom Typ [**"DependencyProperty"**](/uwp/api/windows.ui.xaml.dependencyproperty).</span><span class="sxs-lookup"><span data-stu-id="9ab3d-122">First, you declare a read-only static property of type [**DependencyProperty**](/uwp/api/windows.ui.xaml.dependencyproperty).</span></span> <span data-ttu-id="9ab3d-123">Es verfügt über den Namen des DP plus *Eigenschaft*.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-123">It has the name of your DP plus *Property*.</span></span> <span data-ttu-id="9ab3d-124">Verwenden Sie diese statische Eigenschaft in Ihrer Implementierung.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-124">You'll use this static property in your implementation.</span></span> <span data-ttu-id="9ab3d-125">Zweitens können Sie eine Instanz der Lese-/ Schreibzugriff-Eigenschaft mit den Typ und den Namen von Ihrer DP deklarieren.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-125">Second, you declare a read-write instance property with the type and name of your DP.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab3d-126">Wenn Sie eine DP mit einem Gleitkommazahlen Typ möchten, machen sie `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span><span class="sxs-lookup"><span data-stu-id="9ab3d-126">If you want a DP with a floating-point type, then make it `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span></span> <span data-ttu-id="9ab3d-127">Deklarieren und implementieren eine DP vom Typ `float` (`Single` in MIDL), und klicken Sie dann einen Wert für diese DP im XAML-Markup festlegen, tritt der Fehler *Fehler beim Erstellen einer "Windows.Foundation.Single" aus dem Text "<NUMBER>"*.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-127">Declaring and implementing a DP of type `float` (`Single` in MIDL), and then setting a value for that DP in XAML markup, results in the error *Failed to create a 'Windows.Foundation.Single' from the text '<NUMBER>'*.</span></span>

<span data-ttu-id="9ab3d-128">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-128">Save the file and build the project.</span></span> <span data-ttu-id="9ab3d-129">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-129">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) describing the runtime class.</span></span> <span data-ttu-id="9ab3d-130">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-130">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="9ab3d-131">Diese Dateien enthalten Stubs, um die erste Schritte zum Implementieren der **BgLabelControl** -Runtime-Klasse, die Sie in Ihrer IDL deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-131">These files include stubs to get you started implementing the **BgLabelControl** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="9ab3d-132">Diese Stubs sind `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` und `BgLabelControl.cpp`.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-132">Those stubs are `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` and `BgLabelControl.cpp`.</span></span>

<span data-ttu-id="9ab3d-133">Kopieren Sie die Stub-Dateien `BgLabelControl.h` und `BgLabelControl.cpp` von `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` in den Projektordner `\BgLabelControlApp\BgLabelControlApp\`.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-133">Copy the stub files `BgLabelControl.h` and `BgLabelControl.cpp` from `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` into the project folder, which is `\BgLabelControlApp\BgLabelControlApp\`.</span></span> <span data-ttu-id="9ab3d-134">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-134">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="9ab3d-135">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-135">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-the-bglabelcontrol-custom-control-class"></a><span data-ttu-id="9ab3d-136">Implementieren Sie die **BgLabelControl** benutzerdefiniertes Steuerelement-Klasse</span><span class="sxs-lookup"><span data-stu-id="9ab3d-136">Implement the **BgLabelControl** custom control class</span></span>
<span data-ttu-id="9ab3d-137">Nun öffnen wir `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` und `BgLabelControl.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-137">Now, let's open `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` and `BgLabelControl.cpp` and implement our runtime class.</span></span> <span data-ttu-id="9ab3d-138">In `BgLabelControl.h`, ändern Sie den Konstruktor den Standard-Stilschlüssel festlegen, **Bezeichnung** und **LabelProperty**implementieren, fügen Sie einen statische Ereignishandler mit dem Namen **OnLabelChanged** Änderungen an den Wert der Abhängigkeitseigenschaft verarbeiten und fügen Sie ein privates Mitglied hinzu um die Sicherungsfeld für **LabelProperty**zu speichern.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-138">In `BgLabelControl.h`, change the constructor to set the default style key, implement **Label** and **LabelProperty**, add a static event handler named **OnLabelChanged** to process changes to the value of the dependency property, and add a private member to store the backing field for **LabelProperty**.</span></span>

<span data-ttu-id="9ab3d-139">Nach dem Hinzufügen, die `BgLabelControl.h` sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-139">After adding those, your `BgLabelControl.h` looks like this.</span></span>

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

<span data-ttu-id="9ab3d-140">In `BgLabelControl.cpp`, definieren Sie die statische Elemente wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-140">In `BgLabelControl.cpp`, define the static members like this.</span></span>

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

<span data-ttu-id="9ab3d-141">In dieser exemplarischen Vorgehensweise wird nicht **OnLabelChanged**verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-141">In this walkthrough, we won't be using **OnLabelChanged**.</span></span> <span data-ttu-id="9ab3d-142">Aber es gibt es, damit Sie sehen, wie Sie eine Abhängigkeitseigenschaft mit einem Rückruf mit geänderter Eigenschaft zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-142">But it's there so that you can see how to register a dependency property with a property-changed callback.</span></span> <span data-ttu-id="9ab3d-143">Die Implementierung des **OnLabelChanged** wird gezeigt, wie einen abgeleiteten projizierten Typ aus einer Basisklasse projizierten abrufen (Basis projizierten Typs **DependencyObject**, in diesem Fall ist).</span><span class="sxs-lookup"><span data-stu-id="9ab3d-143">The implementation of **OnLabelChanged** also shows how to obtain a derived projected type from a base projected type (the base projected type is **DependencyObject**, in this case).</span></span> <span data-ttu-id="9ab3d-144">Und es zeigt, wie Sie dann einen Zeiger auf den Typ zu erhalten, die den projizierten Typ implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-144">And it shows how to then obtain a pointer to the type that implements the projected type.</span></span> <span data-ttu-id="9ab3d-145">Die zweite Operation natürlich nur im Projekt, die den projizierten Typ (d. h., das Projekt, das die Laufzeitklasse implementiert) implementiert möglich ist.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-145">That second operation will naturally only be possible in the project that implements the projected type (that is, the project that implements the runtime class).</span></span>

> [!NOTE]
> <span data-ttu-id="9ab3d-146">Wenn Sie noch nicht installiert, das Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809 haben) oder höher, dann Sie [**WinRT:: from_abi**](/uwp/cpp-ref-for-winrt/from-abi) in Abhängigkeit Eigenschaft geänderte-Ereignishandler oben anstelle von [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self)aufrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-146">If you haven't installed the Windows SDK version 10.0.17763.0 (Windows 10, version 1809), or later, then you need to call [**winrt::from_abi**](/uwp/cpp-ref-for-winrt/from-abi) in the dependency property changed event handler above, instead of [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self).</span></span>

## <a name="design-the-default-style-for-bglabelcontrol"></a><span data-ttu-id="9ab3d-147">Entwerfen des Standardstils für **BgLabelControl**</span><span class="sxs-lookup"><span data-stu-id="9ab3d-147">Design the default style for **BgLabelControl**</span></span>

<span data-ttu-id="9ab3d-148">In den Konstruktor legt **BgLabelControl** einen Standard-Stilschlüssel für sich selbst.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-148">In its constructor, **BgLabelControl** sets a default style key for itself.</span></span> <span data-ttu-id="9ab3d-149">Was *ist* jedoch ein Standardstil?</span><span class="sxs-lookup"><span data-stu-id="9ab3d-149">But what *is* a default style?</span></span> <span data-ttu-id="9ab3d-150">Eine benutzerdefinierte (vorlagenbasierte)-Steuerelement benötigt einen Standardstil&mdash;, enthält eine standardmäßige Steuerelementvorlage&mdash;die sie verwenden können, selbst mit für den Fall, dass der Consumer des Steuerelements einen Stil bzw. die Vorlage festlegen nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-150">A custom (templated) control needs to have a default style&mdash;containing a default control template&mdash;which it can use to render itself with in case the consumer of the control doesn't set a style and/or template.</span></span> <span data-ttu-id="9ab3d-151">In diesem Abschnitt fügen wir eine Markupdatei dem Projekt, enthält unsere Standardstil.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-151">In this section we'll add a markup file to the project containing our default style.</span></span>

<span data-ttu-id="9ab3d-152">Klicken Sie unter Ihrem Projektknoten erstellen Sie einen neuen Ordner, und nennen Sie es "Themes".</span><span class="sxs-lookup"><span data-stu-id="9ab3d-152">Under your project node, create a new folder and name it "Themes".</span></span> <span data-ttu-id="9ab3d-153">Unter `Themes`, fügen Sie ein neues Element vom Typ **Visual C++** > **XAML** > **XAML-Ansicht**, und nennen Sie es "Generic.xaml".</span><span class="sxs-lookup"><span data-stu-id="9ab3d-153">Under `Themes`, add a new item of type **Visual C++** > **XAML** > **XAML View**, and name it "Generic.xaml".</span></span> <span data-ttu-id="9ab3d-154">Die Ordner- und müssen wie folgt in der Reihenfolge für die XAML-Framework den Standardstil für ein benutzerdefiniertes Steuerelement zu finden sein.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-154">The folder and file names have to be like this in order for the XAML framework to find the default style for a custom control.</span></span> <span data-ttu-id="9ab3d-155">Löschen Sie den Standardinhalt von `Generic.xaml`, und fügen Sie im Markup unten.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-155">Delete the default contents of `Generic.xaml`, and paste in the markup below.</span></span>

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

<span data-ttu-id="9ab3d-156">In diesem Fall ist die einzige Eigenschaft, die der Standardstil legt die Steuerelementvorlage.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-156">In this case, the only property that the default style sets is the control template.</span></span> <span data-ttu-id="9ab3d-157">Die Vorlage besteht aus einem Quadrat (dessen Hintergrund auf die **Hintergrund** -Eigenschaft, die alle Instanzen von den Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) gebunden ist) und ein Textelement (deren Text auf die Abhängigkeitseigenschaft **BgLabelControl::Label** gebunden ist).</span><span class="sxs-lookup"><span data-stu-id="9ab3d-157">The template consists of a square (whose background is bound to the **Background** property that all instances of the XAML [**Control**](/uwp/api/windows.ui.xaml.controls.control) type have), and a text element (whose text is bound to the **BgLabelControl::Label** dependency property).</span></span>

## <a name="add-an-instance-of-bglabelcontrol-to-the-main-ui-page"></a><span data-ttu-id="9ab3d-158">Fügen Sie eine Instanz des **BgLabelControl** auf die UI-Hauptseite</span><span class="sxs-lookup"><span data-stu-id="9ab3d-158">Add an instance of **BgLabelControl** to the main UI page</span></span>

<span data-ttu-id="9ab3d-159">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-159">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="9ab3d-160">Unmittelbar nach dem **Button** -Element (innerhalb der **StackPanel**) fügen Sie das folgende Markup hinzu.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-160">Immediately after the **Button** element (inside the **StackPanel**), add the following markup.</span></span>

```xaml
<local:BgLabelControl Background="Red" Label="Hello, World!"/>
```

<span data-ttu-id="9ab3d-161">Fügen Sie außerdem die folgenden #include `MainPage.h` , damit der **MainPage** -Typ (einer Kombination von XAML-Markup und imperativen Code Kompilieren) im Hinblick auf den Typ der benutzerdefinierten Steuerelements **BgLabelControl** ist.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-161">Also, add the following include directive to `MainPage.h` so that the **MainPage** type (a combination of compiling XAML markup and imperative code) is aware of the **BgLabelControl** custom control type.</span></span>

```cppwinrt
// MainPage.h
...
#include "BgLabelControl.h"
...
```

<span data-ttu-id="9ab3d-162">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-162">Now build and run the project.</span></span> <span data-ttu-id="9ab3d-163">Sie sehen, dass die standardmäßige Steuerelementvorlage für den Pinsel für den Hintergrund, und klicken Sie mit der Bezeichnung, die Instanz **BgLabelControl** im Markup gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-163">You'll see that the default control template is binding to the background brush, and to the label, of the **BgLabelControl** instance in the markup.</span></span>

<span data-ttu-id="9ab3d-164">In dieser exemplarischen Vorgehensweise gezeigt ein einfaches Beispiel für eine benutzerdefinierte (vorlagenbasierte)-Steuerelement in C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-164">This walkthrough showed a simple example of a custom (templated) control in C++/WinRT.</span></span> <span data-ttu-id="9ab3d-165">Sie können Ihre eigenen benutzerdefinierten Steuerelemente willkürlich reichhaltige und umfassende festlegen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-165">You can make your own custom controls arbitrarily rich and full-featured.</span></span> <span data-ttu-id="9ab3d-166">Beispielsweise kann ein benutzerdefiniertes Steuerelement etwas so kompliziert ist wie ein Datenraster bearbeitet werden oder ein video-Player, eine Schnellansicht der 3D-Geometrie Form dauern.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-166">For example, a custom control can take the form of something as complicated as an editable data grid, a video player, or a visualizer of 3D geometry.</span></span>

## <a name="implementing-overridable-functions-such-as-measureoverride-and-onapplytemplate"></a><span data-ttu-id="9ab3d-167">Implementieren von *überschreibbaren* Funktionen, z. B. **MeasureOverride** und **OnApplyTemplate**</span><span class="sxs-lookup"><span data-stu-id="9ab3d-167">Implementing *overridable* functions, such as **MeasureOverride** and **OnApplyTemplate**</span></span>

<span data-ttu-id="9ab3d-168">Sie leiten ein benutzerdefiniertes Steuerelement von der [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) -Runtime-Klasse, die selbst weiter Basis-Runtime-Klassen abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-168">You derive a custom control from the [**Control**](/uwp/api/windows.ui.xaml.controls.control) runtime class, which itself further derives from base runtime classes.</span></span> <span data-ttu-id="9ab3d-169">Und es gibt überschreibbare Methoden eines **Steuerelements**, [**FrameworkElement**](/uwp/api/windows.ui.xaml.frameworkelement)und [**UIElement**](/uwp/api/windows.ui.xaml.uielement) , die Sie in Ihre abgeleitete Klasse überschreiben können.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-169">And there are overridable methods of **Control**, [**FrameworkElement**](/uwp/api/windows.ui.xaml.frameworkelement), and [**UIElement**](/uwp/api/windows.ui.xaml.uielement) that you can override in your derived class.</span></span> <span data-ttu-id="9ab3d-170">Hier ist ein Codebeispiel zeigt, wie das geht.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-170">Here's a code example showing you how to do that.</span></span>

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

<span data-ttu-id="9ab3d-171">*Overridable* Funktionen vorhanden selbst unterschiedlich in verschiedenen sprachprojektionen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-171">*Overridable* functions present themselves differently in different language projections.</span></span> <span data-ttu-id="9ab3d-172">In c# werden beispielsweise überschreibbare Funktionen in der Regel als geschützte virtuelle Funktionen.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-172">In C#, for example, overridable functions typically appear as protected virtual functions.</span></span> <span data-ttu-id="9ab3d-173">In C++ / WinRT können sie weder virtuellen noch geschützten sind, Sie können jedoch außer Kraft setzen, und eine eigene Implementierung, bereitstellen, wie oben gezeigt.</span><span class="sxs-lookup"><span data-stu-id="9ab3d-173">In C++/WinRT, they're neither virtual nor protected, but you can still override them and provide your own implementation, as shown above.</span></span>

## <a name="important-apis"></a><span data-ttu-id="9ab3d-174">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9ab3d-174">Important APIs</span></span>
* [<span data-ttu-id="9ab3d-175">Control-Klasse</span><span class="sxs-lookup"><span data-stu-id="9ab3d-175">Control class</span></span>](/uwp/api/windows.ui.xaml.controls.control)
* [<span data-ttu-id="9ab3d-176">DependencyProperty-Klasse</span><span class="sxs-lookup"><span data-stu-id="9ab3d-176">DependencyProperty class</span></span>](/uwp/api/windows.ui.xaml.dependencyproperty)
* [<span data-ttu-id="9ab3d-177">FrameworkElement-Klasse</span><span class="sxs-lookup"><span data-stu-id="9ab3d-177">FrameworkElement class</span></span>](/uwp/api/windows.ui.xaml.frameworkelement)
* [<span data-ttu-id="9ab3d-178">UIElement-Klasse</span><span class="sxs-lookup"><span data-stu-id="9ab3d-178">UIElement class</span></span>](/uwp/api/windows.ui.xaml.uielement)

## <a name="related-topics"></a><span data-ttu-id="9ab3d-179">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9ab3d-179">Related topics</span></span>
* [<span data-ttu-id="9ab3d-180">Steuerelementvorlagen</span><span class="sxs-lookup"><span data-stu-id="9ab3d-180">Control templates</span></span>](/windows/uwp/design/controls-and-patterns/control-templates)
* [<span data-ttu-id="9ab3d-181">Benutzerdefinierte Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="9ab3d-181">Custom dependency properties</span></span>](/windows/uwp/xaml-platform/custom-dependency-properties)
