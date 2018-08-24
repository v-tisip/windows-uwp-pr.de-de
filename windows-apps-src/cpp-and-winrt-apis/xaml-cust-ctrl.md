---
author: stevewhims
description: In diesem Thema führt Sie durch die Schritte zum Erstellen eines einfachen benutzerdefinierten Steuerelements mit C + / WinRT. Sie können auf die Informationen zum Erstellen eigener Features und anpassbare UI-Steuerelemente erstellt werden.
title: XAML-benutzerdefinierte (mit Vorlagen) Steuerelemente mit C + / WinRT
ms.author: stwhi
ms.date: 08/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c ++, Cpp, Winrt, Projektion, XAML, benutzerdefinierte Vorlagen, Steuerung
ms.localizationpriority: medium
ms.openlocfilehash: c108175c66d27b2cdbd910a0f7653ca1befb68e9
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2843692"
---
# <a name="xaml-custom-templated-controls-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="d1b72-105">XAML-benutzerdefinierte (mit Vorlagen) Steuerelemente mit [C + / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="d1b72-105">XAML custom (templated) controls with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>

<span data-ttu-id="d1b72-106">Eine der nützlichsten Merkmale von universellen Windows Plattform (UWP) ist die Flexibilität, die die Benutzeroberfläche (UI) Stack bereitgestellt werden, um benutzerdefinierte Steuerelemente basierend auf dem Typ XAML- [Steuerelement](/uwp/api/windows.ui.xaml.controls.control) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1b72-106">One of the most powerful features of the Universal Windows Platform (UWP) is the flexibility that the user-interface (UI) stack provides to create custom controls based on the XAML [Control](/uwp/api/windows.ui.xaml.controls.control) type.</span></span> <span data-ttu-id="d1b72-107">Framework der XAML-UI bietet Funktionen wie [benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties) und angefügte Eigenschaften und [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates), die zum Erstellen von Steuerelementen funktionsreiche und anpassbarer erleichtern.</span><span class="sxs-lookup"><span data-stu-id="d1b72-107">The XAML UI framework provides features such as [custom dependency properties](/windows/uwp/xaml-platform/custom-dependency-properties) and attached properties, and [control templates](/windows/uwp/design/controls-and-patterns/control-templates), which make it easy to create feature-rich and customizable controls.</span></span> <span data-ttu-id="d1b72-108">In diesem Thema führt Sie durch die Schritte zum Erstellen einer benutzerdefinierten (Steuerelementvorlage) mit C + / WinRT.</span><span class="sxs-lookup"><span data-stu-id="d1b72-108">This topic walks you through the steps of creating a custom (templated) control with C++/WinRT.</span></span>

## <a name="create-a-blank-app-bglabelcontrolapp"></a><span data-ttu-id="d1b72-109">Erstellen Sie eine leere App (BgLabelControlApp)</span><span class="sxs-lookup"><span data-stu-id="d1b72-109">Create a Blank App (BgLabelControlApp)</span></span>
<span data-ttu-id="d1b72-110">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1b72-110">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="d1b72-111">Erstellen einer **Visual C++ leere App (C + / WinRT)** project, und nennen Sie es *BgLabelControlApp*.</span><span class="sxs-lookup"><span data-stu-id="d1b72-111">Create a **Visual C++ Blank App (C++/WinRT)** project, and name it *BgLabelControlApp*.</span></span>

<span data-ttu-id="d1b72-112">Wir werden das Erstellen einer neuen Klasse zur Darstellung einer benutzerdefinierten (Steuerelementvorlage).</span><span class="sxs-lookup"><span data-stu-id="d1b72-112">We're going to author a new class to represent a custom (templated) control.</span></span> <span data-ttu-id="d1b72-113">Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit.</span><span class="sxs-lookup"><span data-stu-id="d1b72-113">We're authoring and consuming the class within the same compilation unit.</span></span> <span data-ttu-id="d1b72-114">Aber wir möchten möglicherweise instanziieren Sie diese Klasse von XAML-Markup und für, die Ursache, dass es eine Runtime-Klasse werden soll.</span><span class="sxs-lookup"><span data-stu-id="d1b72-114">But we want to be able to instantiate this class from XAML markup, and for that reason it's going to be a runtime class.</span></span> <span data-ttu-id="d1b72-115">Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="d1b72-115">And we're going to use C++/WinRT to both author and consume it.</span></span>

<span data-ttu-id="d1b72-116">Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d1b72-116">The first step in authoring a new runtime class is to add a new **Midl File (.idl)** item to the project.</span></span> <span data-ttu-id="d1b72-117">Nennen Sie es `BgLabelControl.idl`.</span><span class="sxs-lookup"><span data-stu-id="d1b72-117">Name it `BgLabelControl.idl`.</span></span> <span data-ttu-id="d1b72-118">Löschen Sie den Standardinhalt von `BgLabelControl.idl` und fügen Sie diese Laufzeitklassendeklaration ein.</span><span class="sxs-lookup"><span data-stu-id="d1b72-118">Delete the default contents of `BgLabelControl.idl`, and paste in this runtime class declaration.</span></span>

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

<span data-ttu-id="d1b72-119">Die oben stehenden Codebeispiel zeigt das Muster, das Sie befolgen, wenn Sie eine Abhängigkeitseigenschaft (DP) zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="d1b72-119">The listing above shows the pattern that you follow when declaring a dependency property (DP).</span></span> <span data-ttu-id="d1b72-120">Es gibt zwei Datenelemente auf jedem DP.</span><span class="sxs-lookup"><span data-stu-id="d1b72-120">There are two pieces to each DP.</span></span> <span data-ttu-id="d1b72-121">Deklarieren Sie Sie zunächst eine schreibgeschützte statische Eigenschaft vom Typ ["DependencyProperty"](/uwp/api/windows.ui.xaml.dependencyproperty).</span><span class="sxs-lookup"><span data-stu-id="d1b72-121">First, you declare a read-only static property of type [DependencyProperty](/uwp/api/windows.ui.xaml.dependencyproperty).</span></span> <span data-ttu-id="d1b72-122">Der Name der Ihre DP plus *Eigenschaft*besitzt.</span><span class="sxs-lookup"><span data-stu-id="d1b72-122">It has the name of your DP plus *Property*.</span></span> <span data-ttu-id="d1b72-123">Verwenden Sie diese statische Eigenschaft in der Implementierung.</span><span class="sxs-lookup"><span data-stu-id="d1b72-123">You'll use this static property in your implementation.</span></span> <span data-ttu-id="d1b72-124">Zweitens deklarieren Sie eine Instanz der Lese-/ Schreibzugriff-Eigenschaft mit dem Typ und Namen von Ihrer DP.</span><span class="sxs-lookup"><span data-stu-id="d1b72-124">Second, you declare a read-write instance property with the type and name of your DP.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b72-125">Wenn Sie eine DP mit einem Gleitkomma-Typ möchten, legen Sie es `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span><span class="sxs-lookup"><span data-stu-id="d1b72-125">If you want a DP with a floating-point type, then make it `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)).</span></span> <span data-ttu-id="d1b72-126">Deklarieren und Implementieren einer DP vom Typ `float` (`Single` in MIDL), und klicken Sie dann Festlegen eines Werts für diese DP in XAML-Markup führt zu folgender Fehlermeldung *konnte nicht aus dem Text einer 'Windows.Foundation.Single' erstellen '<NUMBER>'*.</span><span class="sxs-lookup"><span data-stu-id="d1b72-126">Declaring and implementing a DP of type `float` (`Single` in MIDL), and then setting a value for that DP in XAML markup, results in the error *Failed to create a 'Windows.Foundation.Single' from the text '<NUMBER>'*.</span></span>

<span data-ttu-id="d1b72-127">Speichern Sie die Datei, und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="d1b72-127">Save the file and build the project.</span></span> <span data-ttu-id="d1b72-128">Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) zu erstellen, die die Laufzeitklasse beschreibt.</span><span class="sxs-lookup"><span data-stu-id="d1b72-128">During the build process, the `midl.exe` tool is run to create a Windows Runtime metadata file (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) describing the runtime class.</span></span> <span data-ttu-id="d1b72-129">Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d1b72-129">Then, the `cppwinrt.exe` tool is run to generate source code files to support you in authoring and consuming your runtime class.</span></span> <span data-ttu-id="d1b72-130">Diese Dateien enthalten Stubs, um Ihnen den Einstieg Implementieren der **BgLabelControl** Runtime-Klasse, die Sie in Ihre IDL deklariert zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d1b72-130">These files include stubs to get you started implementing the **BgLabelControl** runtime class that you declared in your IDL.</span></span> <span data-ttu-id="d1b72-131">Diese Stubs sind `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` und `BgLabelControl.cpp`.</span><span class="sxs-lookup"><span data-stu-id="d1b72-131">Those stubs are `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` and `BgLabelControl.cpp`.</span></span>

<span data-ttu-id="d1b72-132">Kopieren Sie die Stub-Dateien `BgLabelControl.h` und `BgLabelControl.cpp` von `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` in den Projektordner `\BgLabelControlApp\BgLabelControlApp\`.</span><span class="sxs-lookup"><span data-stu-id="d1b72-132">Copy the stub files `BgLabelControl.h` and `BgLabelControl.cpp` from `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` into the project folder, which is `\BgLabelControlApp\BgLabelControlApp\`.</span></span> <span data-ttu-id="d1b72-133">Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="d1b72-133">In **Solution Explorer**, make sure **Show All Files** is toggled on.</span></span> <span data-ttu-id="d1b72-134">Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.</span><span class="sxs-lookup"><span data-stu-id="d1b72-134">Right-click the stub files that you copied, and click **Include In Project**.</span></span>

## <a name="implement-the-bglabelcontrol-custom-control-class"></a><span data-ttu-id="d1b72-135">Implementieren der benutzerdefinierten Steuerelementklasse **BgLabelControl**</span><span class="sxs-lookup"><span data-stu-id="d1b72-135">Implement the **BgLabelControl** custom control class</span></span>
<span data-ttu-id="d1b72-136">Nun öffnen wir `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` und `BgLabelControl.cpp` und implementieren unsere Laufzeitklasse.</span><span class="sxs-lookup"><span data-stu-id="d1b72-136">Now, let's open `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` and `BgLabelControl.cpp` and implement our runtime class.</span></span> <span data-ttu-id="d1b72-137">In `BgLabelControl.h`, ändern Sie den Konstruktor zum Festlegen des standardmäßigen Style-Schlüssels, **Beschriftung** und **LabelProperty**implementieren, fügen Sie einen statische Ereignishandler mit dem Namen **OnLabelChanged** zum Verarbeiten von Änderungen an den Wert der Abhängigkeitseigenschaft, und fügen Sie einen privaten Member das zugrunde liegende Feld für **LabelProperty**gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d1b72-137">In `BgLabelControl.h`, change the constructor to set the default style key, implement **Label** and **LabelProperty**, add a static event handler named **OnLabelChanged** to process changes to the value of the dependency property, and add a private member to store the backing field for **LabelProperty**.</span></span>

<span data-ttu-id="d1b72-138">In dieser exemplarischen Vorgehensweise wird nicht **OnLabelChanged**verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1b72-138">In this walkthrough, we won't be using **OnLabelChanged**.</span></span> <span data-ttu-id="d1b72-139">Es ist jedoch vorhanden, sodass Sie sehen können, wie Sie zum Registrieren einer Abhängigkeitseigenschaft mit einem Rückruf-Eigenschaft geändert.</span><span class="sxs-lookup"><span data-stu-id="d1b72-139">But it's there so that you can see how to register a dependency property with a property-changed callback.</span></span>

<span data-ttu-id="d1b72-140">Nach dem Hinzufügen, Ihre `BgLabelControl.h` wie folgt.</span><span class="sxs-lookup"><span data-stu-id="d1b72-140">After adding those, your `BgLabelControl.h` looks like this.</span></span>

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

    static void OnLabelChanged(Windows::UI::Xaml::DependencyObject const& d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const& e);

private:
    static Windows::UI::Xaml::DependencyProperty m_labelProperty;
};
...
```

<span data-ttu-id="d1b72-141">In `BgLabelControl.cpp`, die statische Member wie folgt definieren.</span><span class="sxs-lookup"><span data-stu-id="d1b72-141">In `BgLabelControl.cpp`, define the static members like this.</span></span>

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

void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject const& d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const& e) {}
...
```

## <a name="design-the-default-style-for-bglabelcontrol"></a><span data-ttu-id="d1b72-142">Entwerfen der Standardformatvorlage für **BgLabelControl**</span><span class="sxs-lookup"><span data-stu-id="d1b72-142">Design the default style for **BgLabelControl**</span></span>

<span data-ttu-id="d1b72-143">In seinem Konstruktor wird **BgLabelControl** einen standardmäßigen Style-Schlüssel für sich selbst.</span><span class="sxs-lookup"><span data-stu-id="d1b72-143">In its constructor, **BgLabelControl** sets a default style key for itself.</span></span> <span data-ttu-id="d1b72-144">Aber was *ist* ein Standardformat?</span><span class="sxs-lookup"><span data-stu-id="d1b72-144">But what *is* a default style?</span></span> <span data-ttu-id="d1b72-145">Eine benutzerdefinierte (Steuerelementvorlage) muss ein Standardformat haben&mdash;mit einer standardmäßigen Steuerelementvorlage&mdash;es selbst mit Rendern für den Fall, dass der Consumer des Steuerelements eine Formatvorlage und/oder der Vorlage festlegen nicht verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d1b72-145">A custom (templated) control needs to have a default style&mdash;containing a default control template&mdash;which it can use to render itself with in case the consumer of the control doesn't set a style and/or template.</span></span> <span data-ttu-id="d1b72-146">In diesem Abschnitt fügen wir eine Markupdatei um dem Projekt mit unserem Standardformat.</span><span class="sxs-lookup"><span data-stu-id="d1b72-146">In this section we'll add a markup file to the project containing our default style.</span></span>

<span data-ttu-id="d1b72-147">Erstellen Sie unter den Projektknoten einen neuen Ordner, und nennen Sie sie "Designs".</span><span class="sxs-lookup"><span data-stu-id="d1b72-147">Under your project node, create a new folder and name it "Themes".</span></span> <span data-ttu-id="d1b72-148">Klicken Sie unter `Themes`, fügen Sie ein neues Element vom Typ **Visual C++** > **XAML** > **XAML-Ansicht**, und nennen Sie sie "Generic.xaml".</span><span class="sxs-lookup"><span data-stu-id="d1b72-148">Under `Themes`, add a new item of type **Visual C++** > **XAML** > **XAML View**, and name it "Generic.xaml".</span></span> <span data-ttu-id="d1b72-149">Die Ordner und die Dateinamen müssen wie folgt in der Reihenfolge für die XAML-Framework Standardformatvorlage für ein benutzerdefiniertes Steuerelement gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d1b72-149">The folder and file names have to be like this in order for the XAML framework to find the default style for a custom control.</span></span> <span data-ttu-id="d1b72-150">Löschen der Standardinhalt des `Generic.xaml`, und fügen Sie im Markup unten.</span><span class="sxs-lookup"><span data-stu-id="d1b72-150">Delete the default contents of `Generic.xaml`, and paste in the markup below.</span></span>

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

<span data-ttu-id="d1b72-151">In diesem Fall ist die einzige Eigenschaft, die die Standardformatvorlage festlegt, die Steuerelementvorlage.</span><span class="sxs-lookup"><span data-stu-id="d1b72-151">In this case, the only property that the default style sets is the control template.</span></span> <span data-ttu-id="d1b72-152">Die Vorlage besteht aus einem Quadrat (, deren Hintergrund an die **Background** -Eigenschaft, die alle Instanzen des Typs XAML- [Steuerelement](/uwp/api/windows.ui.xaml.controls.control) gebunden ist) und ein Textelement (, dessen Text auf die Abhängigkeitseigenschaft **BgLabelControl::Label** gebunden ist).</span><span class="sxs-lookup"><span data-stu-id="d1b72-152">The template consists of a square (whose background is bound to the **Background** property that all instances of the XAML [Control](/uwp/api/windows.ui.xaml.controls.control) type have), and a text element (whose text is bound to the **BgLabelControl::Label** dependency property).</span></span>

## <a name="add-an-instance-of-bglabelcontrol-to-the-main-ui-page"></a><span data-ttu-id="d1b72-153">Fügen Sie eine Instanz des **BgLabelControl** zur Hauptseite der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d1b72-153">Add an instance of **BgLabelControl** to the main UI page</span></span>

<span data-ttu-id="d1b72-154">Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite.</span><span class="sxs-lookup"><span data-stu-id="d1b72-154">Open `MainPage.xaml`, which contains the XAML markup for our main UI page.</span></span> <span data-ttu-id="d1b72-155">Fügen Sie unmittelbar nach der (inside **StackPanel**) **Button** -Element das folgende Markup hinzu.</span><span class="sxs-lookup"><span data-stu-id="d1b72-155">Immediately after the **Button** element (inside the **StackPanel**), add the following markup.</span></span>

```xaml
<local:BgLabelControl Background="Red" Label="Hello, World!"/>
```

<span data-ttu-id="d1b72-156">Darüber hinaus hinzufügen die folgenden #include `MainPage.h` , damit der **MainPage** -Typ (eine Kombination der Kompilierung von XAML-Markup und imperative Code) des Typs benutzerdefiniertes Steuerelement **BgLabelControl** kennt.</span><span class="sxs-lookup"><span data-stu-id="d1b72-156">Also, add the following include directive to `MainPage.h` so that the **MainPage** type (a combination of compiling XAML markup and imperative code) is aware of the **BgLabelControl** custom control type.</span></span>

```cppwinrt
// MainPage.h
...
#include "BgLabelControl.h"
...
```

<span data-ttu-id="d1b72-157">Erstellen Sie nun das Projekt und führen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="d1b72-157">Now build and run the project.</span></span> <span data-ttu-id="d1b72-158">Sie sehen, dass die standardmäßige Steuerelementvorlage auf den Hintergrundpinsel, und klicken Sie auf die Beschriftung der **BgLabelControl** -Instanz im Markup gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="d1b72-158">You'll see that the default control template is binding to the background brush, and to the label, of the **BgLabelControl** instance in the markup.</span></span>

<span data-ttu-id="d1b72-159">In dieser exemplarischen Vorgehensweise bedeutete für ein einfaches Beispiel für einen benutzerdefinierten (Steuerelementvorlage) in C + / WinRT.</span><span class="sxs-lookup"><span data-stu-id="d1b72-159">This walkthrough showed a simple example of a custom (templated) control in C++/WinRT.</span></span> <span data-ttu-id="d1b72-160">Sie können Ihre eigenen benutzerdefinierten Steuerelemente willkürlich umfassende und vollem Funktionsumfang tätigen.</span><span class="sxs-lookup"><span data-stu-id="d1b72-160">You can make your own custom controls arbitrarily rich and full-featured.</span></span> <span data-ttu-id="d1b72-161">Beispielsweise kann ein benutzerdefiniertes Steuerelement Form etwas so kompliziert ist wie ein bearbeitbaren Datenraster, einen Videoplayer oder eine Schnellansicht 3D Geometrie dauern.</span><span class="sxs-lookup"><span data-stu-id="d1b72-161">For example, a custom control can take the form of something as complicated as an editable data grid, a video player, or a visualizer of 3D geometry.</span></span>

## <a name="important-apis"></a><span data-ttu-id="d1b72-162">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d1b72-162">Important APIs</span></span>
* [<span data-ttu-id="d1b72-163">Steuerelement</span><span class="sxs-lookup"><span data-stu-id="d1b72-163">Control</span></span>](/uwp/api/windows.ui.xaml.controls.control)
* [<span data-ttu-id="d1b72-164">DependencyProperty</span><span class="sxs-lookup"><span data-stu-id="d1b72-164">DependencyProperty</span></span>](/uwp/api/windows.ui.xaml.dependencyproperty)

## <a name="related-topics"></a><span data-ttu-id="d1b72-165">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d1b72-165">Related topics</span></span>
* [<span data-ttu-id="d1b72-166">Steuerelementvorlagen</span><span class="sxs-lookup"><span data-stu-id="d1b72-166">Control templates</span></span>](/windows/uwp/design/controls-and-patterns/control-templates)
* [<span data-ttu-id="d1b72-167">Benutzerdefinierte Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="d1b72-167">Custom dependency properties</span></span>](/windows/uwp/xaml-platform/custom-dependency-properties)
