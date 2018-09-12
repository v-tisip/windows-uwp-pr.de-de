---
author: stevewhims
description: Dieses Thema führt Sie durch die Schritte zum Erstellen eines einfachen benutzerdefinierten Steuerelements mit C++ / WinRT. Sie können auf den Informationen zum Erstellen Ihrer eigenen funktionsreiche und anpassbare UI-Steuerelemente erstellen.
title: XAML-benutzerdefinierte (vorlagenbasierten)-Steuerelemente mit C++ / WinRT
ms.author: stwhi
ms.date: 08/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projizierung, XAML, benutzerdefinierte Steuerelement der auf Vorlagen basierenden
ms.localizationpriority: medium
ms.openlocfilehash: fd1843afc58bc758db1c6e575f3733bdc4f47b4e
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3929496"
---
# <a name="xaml-custom-templated-controls-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>XAML-benutzerdefinierte (vorlagenbasierten)-Steuerelemente mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

Eines der leistungsstärksten Features von der universellen Windows-Plattform (UWP) bietet die Flexibilität, die die Benutzeroberfläche (UI)-Stapel bereitstellt, um benutzerdefinierte Steuerelemente, die basierend auf dem Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) zu erstellen. Das XAML-UI-Framework bietet Features, z. B. [benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties) und angefügte Eigenschaften und [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates), die Erstellen von Steuerelementen funktionsreiche und anpassbare erleichtern. Dieses Thema führt Sie durch die Schritte zum Erstellen einer benutzerdefinierten (Steuerelementvorlage) mit C++ / WinRT.

## <a name="create-a-blank-app-bglabelcontrolapp"></a>Erstellen einer leeren App (BgLabelControlApp)
Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie ein **Visual C++** > **Universelle Windows-** > **leere App (C++ / WinRT)** Projekt und nennen Sie es *BgLabelControlApp*.

Wir werden eine neue Klasse zum Darstellen von einer benutzerdefinierten (Steuerelementvorlage) erstellen. Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit. Aber wir wollen in der Lage zu instanziieren diese Klasse im XAML-Markup für, die Grund, warum, dass es eine Laufzeitklasse sein soll. Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.

Der erste Schritt beim Erstellen einer neuen Laufzeitklasse besteht darin, dem Projekt ein neues **Midl-Datei (.idl)**-Element hinzuzufügen. Nennen Sie es `BgLabelControl.idl`. Löschen Sie den Standardinhalt von `BgLabelControl.idl` und fügen Sie diese Laufzeitklassendeklaration ein.

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

Der Eintrag oben zeigt das Muster, das Sie befolgen Sie bei eine Abhängigkeitseigenschaft (DP) deklarieren. Es gibt zwei Teile für jede DP. Zunächst deklarieren Sie eine schreibgeschützte statische Eigenschaft vom Typ [**"DependencyProperty"**](/uwp/api/windows.ui.xaml.dependencyproperty). Es verfügt über den Namen des DP plus *Eigenschaft*. Sie verwenden diese statische Eigenschaft in Ihrer Implementierung. Zweitens können Sie eine Instanz von Lese-/ Schreibzugriff-Eigenschaft mit den Typ und den Namen von Ihrer DP deklarieren.

> [!NOTE]
> Wenn Sie eine DP mit einem Gleitkommazahlen Typ möchten, machen sie `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)). Deklarieren und implementieren eine DP vom Typ `float` (`Single` in MIDL), und dann für die DP im XAML-Markup Festlegen eines Werts führt zum Fehler *Fehler beim Erstellen einer "Windows.Foundation.Single" aus den Text "<NUMBER>"*.

Speichern Sie die Datei, und erstellen Sie das Projekt. Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) zu erstellen, die die Laufzeitklasse beschreibt. Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen. Diese Dateien enthalten Stubs, um die erste Schritte zum Implementieren der **BgLabelControl** -Runtime-Klasse, die Sie in Ihrer IDL deklariert haben. Diese Stubs sind `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` und `BgLabelControl.cpp`.

Kopieren Sie die Stub-Dateien `BgLabelControl.h` und `BgLabelControl.cpp` von `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` in den Projektordner `\BgLabelControlApp\BgLabelControlApp\`. Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist. Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.

## <a name="implement-the-bglabelcontrol-custom-control-class"></a>Implementieren Sie die **BgLabelControl** benutzerdefiniertes Steuerelement-Klasse
Nun öffnen wir `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` und `BgLabelControl.cpp` und implementieren unsere Laufzeitklasse. In `BgLabelControl.h`, ändern Sie den Konstruktor zum Festlegen des Standard-Stilschlüssel, **Bezeichnung** und **LabelProperty**implementieren, fügen Sie eine statische Ereignishandler mit dem Namen **OnLabelChanged** Änderungen an den Wert der Abhängigkeitseigenschaft verarbeiten hinzu und fügen Sie ein privates Mitglied hinzu um das Sicherungsfeld für **LabelProperty**zu speichern.

Nach dem Hinzufügen, Ihre `BgLabelControl.h` sieht wie folgt aus.

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

In `BgLabelControl.cpp`, definieren Sie die statischen Member wie folgt aus.

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

        BgLabelControlApp::implementation::BgLabelControl* ptr{ winrt::from_abi<BgLabelControlApp::implementation::BgLabelControl>(theControl) };
        // Call members of the implementation type via ptr.
    }
}
...
```

In dieser exemplarischen Vorgehensweise wird nicht **OnLabelChanged**verwenden. Es ist jedoch vorhanden, damit Sie sehen können, wie Sie eine Abhängigkeitseigenschaft mit einem Rückruf mit geänderter Eigenschaft zu registrieren. Die Implementierung des **OnLabelChanged** zeigt auch, wie einen abgeleiteten projizierten Typ von einem projizierten Basistyp abgerufen (Basis projizierten Typs **DependencyObject**, in diesem Fall ist). Und es zeigt, wie Sie dann einen Zeiger auf den Typ abrufen, die den projizierten Typ implementiert. Die zweite Vorgang wird natürlich nur im Projekt möglich sein, implementiert den projizierten Typ (d. h. das Projekt, das die Laufzeitklasse implementiert).

> [!NOTE]
> Wenn Sie die [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)installiert haben, oder höher ist, dann Sie [**winrt::get_self**](/uwp/cpp-ref-for-winrt/get-self) im Abhängigkeitseigenschaften Eigenschaft geänderte Ereignishandler oben anstelle von [**WinRT:: from_abi rufen**](/uwp/cpp-ref-for-winrt/from-abi).

## <a name="design-the-default-style-for-bglabelcontrol"></a>Entwerfen des Standardstils für **BgLabelControl**

Im Konstruktor legt **BgLabelControl** einen Standard-Stilschlüssel für sich selbst. Was *ist* jedoch ein Standardstil? Eine benutzerdefinierte (Steuerelementvorlage) benötigt einen Standardstil&mdash;, enthält eine standardmäßige Steuerelementvorlage&mdash;die sie verwenden können, um selbst mit zu rendern, für den Fall, dass der Consumer des Steuerelements einen Stil bzw. einen Vorlage festlegen nicht. In diesem Abschnitt fügen wir eine Markupdatei dem Projekt, enthält unsere Standardstil.

Klicken Sie unter Ihrem Projektknoten erstellen Sie einen neuen Ordner, und nennen Sie sie "Themes". Unter `Themes`, fügen Sie ein neues Element vom Typ **Visual C++** > **XAML** > **XAML-Ansicht**, und nennen Sie es "Generic.xaml". Die Ordner- und müssen wie folgt in der Reihenfolge für die XAML-Framework zur Suche nach der Standardstil für ein benutzerdefiniertes Steuerelement sein. Löschen Sie den Standardinhalt von `Generic.xaml`, und fügen Sie im Markup unten.

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

In diesem Fall ist die einzige Eigenschaft, die der Standardstil legt fest, die Steuerelementvorlage. Die Vorlage besteht aus ein Quadrat (dessen Hintergrund auf die **Hintergrund** -Eigenschaft, die alle Instanzen von den Typ des XAML- [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) gebunden ist), und ein Textelement (, dessen Text auf die Abhängigkeitseigenschaft **BgLabelControl::Label** gebunden ist).

## <a name="add-an-instance-of-bglabelcontrol-to-the-main-ui-page"></a>Fügen Sie eine Instanz des **BgLabelControl** auf die UI-Hauptseite

Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite. Unmittelbar nach dem **Button** -Element (innerhalb der **StackPanel**) fügen Sie das folgende Markup hinzu.

```xaml
<local:BgLabelControl Background="Red" Label="Hello, World!"/>
```

Fügen Sie außerdem die folgenden #include `MainPage.h` so, dass der **MainPage** -Typ (einer Kombination von XAML-Markup und imperativen Code Kompilieren) den Typ der benutzerdefinierten Steuerelements **BgLabelControl** bekannt sind.

```cppwinrt
// MainPage.h
...
#include "BgLabelControl.h"
...
```

Erstellen Sie nun das Projekt und führen Sie es aus. Sie sehen, dass die standardmäßige Steuerelementvorlage des Hintergrundpinsels und mit der Bezeichnung, die Instanz **BgLabelControl** im Markup gebunden werden.

In dieser exemplarischen Vorgehensweise gezeigt ein einfaches Beispiel für eine benutzerdefinierte (Steuerelementvorlage) in C++ / WinRT. Sie können Ihre eigenen benutzerdefinierten Steuerelemente willkürlich reichhaltige und mit vollem Funktionsumfang festlegen. Beispielsweise kann ein benutzerdefiniertes Steuerelement etwas so kompliziert ist wie ein Raster bearbeitbare Daten oder ein video-Player, eine Schnellansicht der 3D-Geometrie Form dauern.

## <a name="implementing-overridable-functions-such-as-measureoverride-and-onapplytemplate"></a>Implementieren von *überschreibbaren* Funktionen, z. B. **MeasureOverride** und **OnApplyTemplate**

Sie leiten ein benutzerdefiniertes Steuerelement von der [**Steuerelement**](/uwp/api/windows.ui.xaml.controls.control) -Runtime-Klasse, die selbst weiter Basis-Runtime-Klassen abgeleitet. Und es gibt überschreibbare Methoden eines **Steuerelements**, [**FrameworkElement**](/uwp/api/windows.ui.xaml.frameworkelement)und [**UIElement**](/uwp/api/windows.ui.xaml.uielement) , die Sie in Ihre abgeleitete Klasse überschreiben können. Hier ist ein Codebeispiel Sie wie das geht.

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

*Overridable* Funktionen vorhanden selbst unterschiedlich in verschiedenen sprachprojektionen. In c# werden z. B. überschreibbare Funktionen in der Regel als geschützte virtuelle Funktionen. In C++ / WinRT können sie virtuelle weder geschützten, aber Sie können weiterhin außer Kraft setzen, und eine eigene Implementierung bereitstellen, wie oben gezeigt.

## <a name="important-apis"></a>Wichtige APIs
* [Steuerelementklasse](/uwp/api/windows.ui.xaml.controls.control)
* [DependencyProperty-Klasse](/uwp/api/windows.ui.xaml.dependencyproperty)
* [FrameworkElement-Klasse](/uwp/api/windows.ui.xaml.frameworkelement)
* [UIElement-Klasse](/uwp/api/windows.ui.xaml.uielement)

## <a name="related-topics"></a>Verwandte Themen
* [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates)
* [Benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties)
