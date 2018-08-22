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
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "2795462"
---
# <a name="xaml-custom-templated-controls-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>XAML-benutzerdefinierte (mit Vorlagen) Steuerelemente mit [C + / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

Eine der nützlichsten Merkmale von universellen Windows Plattform (UWP) ist die Flexibilität, die die Benutzeroberfläche (UI) Stack bereitgestellt werden, um benutzerdefinierte Steuerelemente basierend auf dem Typ XAML- [Steuerelement](/uwp/api/windows.ui.xaml.controls.control) zu erstellen. Framework der XAML-UI bietet Funktionen wie [benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties) und angefügte Eigenschaften und [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates), die zum Erstellen von Steuerelementen funktionsreiche und anpassbarer erleichtern. In diesem Thema führt Sie durch die Schritte zum Erstellen einer benutzerdefinierten (Steuerelementvorlage) mit C + / WinRT.

## <a name="create-a-blank-app-bglabelcontrolapp"></a>Erstellen Sie eine leere App (BgLabelControlApp)
Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen einer **Visual C++ leere App (C + / WinRT)** project, und nennen Sie es *BgLabelControlApp*.

Wir werden das Erstellen einer neuen Klasse zur Darstellung einer benutzerdefinierten (Steuerelementvorlage). Wir erstellen und nutzen die Klasse innerhalb derselben Kompilierungseinheit. Aber wir möchten möglicherweise instanziieren Sie diese Klasse von XAML-Markup und für, die Ursache, dass es eine Runtime-Klasse werden soll. Und wir werden C++/WinRT verwenden, um diese zu schreiben und zu nutzen.

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

Die oben stehenden Codebeispiel zeigt das Muster, das Sie befolgen, wenn Sie eine Abhängigkeitseigenschaft (DP) zu deklarieren. Es gibt zwei Datenelemente auf jedem DP. Deklarieren Sie Sie zunächst eine schreibgeschützte statische Eigenschaft vom Typ ["DependencyProperty"](/uwp/api/windows.ui.xaml.dependencyproperty). Der Name der Ihre DP plus *Eigenschaft*besitzt. Verwenden Sie diese statische Eigenschaft in der Implementierung. Zweitens deklarieren Sie eine Instanz der Lese-/ Schreibzugriff-Eigenschaft mit dem Typ und Namen von Ihrer DP.

> [!NOTE]
> Wenn Sie eine DP mit einem Gleitkomma-Typ möchten, legen Sie es `double` (`Double` in [MIDL 3.0](/uwp/midl-3/)). Deklarieren und Implementieren einer DP vom Typ `float` (`Single` in MIDL), und klicken Sie dann Festlegen eines Werts für diese DP in XAML-Markup führt zu folgender Fehlermeldung *konnte nicht aus dem Text einer 'Windows.Foundation.Single' erstellen '<NUMBER>'*.

Speichern Sie die Datei, und erstellen Sie das Projekt. Während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um eine Windows-Runtime-Metadaten-Datei (`\BgLabelControlApp\Debug\BgLabelControlApp\Unmerged\BgLabelControl.winmd`) zu erstellen, die die Laufzeitklasse beschreibt. Dann wird das `cppwinrt.exe`-Tool ausgeführt, um Quellcodedateien zu erzeugen, die Sie bei der Erstellung und Nutzung Ihrer Laufzeitklasse unterstützen. Diese Dateien enthalten Stubs, um Ihnen den Einstieg Implementieren der **BgLabelControl** Runtime-Klasse, die Sie in Ihre IDL deklariert zu erhalten. Diese Stubs sind `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\BgLabelControl.h` und `BgLabelControl.cpp`.

Kopieren Sie die Stub-Dateien `BgLabelControl.h` und `BgLabelControl.cpp` von `\BgLabelControlApp\BgLabelControlApp\Generated Files\sources\` in den Projektordner `\BgLabelControlApp\BgLabelControlApp\`. Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist. Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**.

## <a name="implement-the-bglabelcontrol-custom-control-class"></a>Implementieren der benutzerdefinierten Steuerelementklasse **BgLabelControl**
Nun öffnen wir `\BgLabelControlApp\BgLabelControlApp\BgLabelControl.h` und `BgLabelControl.cpp` und implementieren unsere Laufzeitklasse. In `BgLabelControl.h`, ändern Sie den Konstruktor zum Festlegen des standardmäßigen Style-Schlüssels, **Beschriftung** und **LabelProperty**implementieren, fügen Sie einen statische Ereignishandler mit dem Namen **OnLabelChanged** zum Verarbeiten von Änderungen an den Wert der Abhängigkeitseigenschaft, und fügen Sie einen privaten Member das zugrunde liegende Feld für **LabelProperty**gespeichert.

In dieser exemplarischen Vorgehensweise wird nicht **OnLabelChanged**verwenden. Es ist jedoch vorhanden, sodass Sie sehen können, wie Sie zum Registrieren einer Abhängigkeitseigenschaft mit einem Rückruf-Eigenschaft geändert.

Nach dem Hinzufügen, Ihre `BgLabelControl.h` wie folgt.

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

In `BgLabelControl.cpp`, die statische Member wie folgt definieren.

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

## <a name="design-the-default-style-for-bglabelcontrol"></a>Entwerfen der Standardformatvorlage für **BgLabelControl**

In seinem Konstruktor wird **BgLabelControl** einen standardmäßigen Style-Schlüssel für sich selbst. Aber was *ist* ein Standardformat? Eine benutzerdefinierte (Steuerelementvorlage) muss ein Standardformat haben&mdash;mit einer standardmäßigen Steuerelementvorlage&mdash;es selbst mit Rendern für den Fall, dass der Consumer des Steuerelements eine Formatvorlage und/oder der Vorlage festlegen nicht verwenden können. In diesem Abschnitt fügen wir eine Markupdatei um dem Projekt mit unserem Standardformat.

Erstellen Sie unter den Projektknoten einen neuen Ordner, und nennen Sie sie "Designs". Klicken Sie unter `Themes`, fügen Sie ein neues Element vom Typ **Visual C++** > **XAML** > **XAML-Ansicht**, und nennen Sie sie "Generic.xaml". Die Ordner und die Dateinamen müssen wie folgt in der Reihenfolge für die XAML-Framework Standardformatvorlage für ein benutzerdefiniertes Steuerelement gefunden werden. Löschen der Standardinhalt des `Generic.xaml`, und fügen Sie im Markup unten.

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

In diesem Fall ist die einzige Eigenschaft, die die Standardformatvorlage festlegt, die Steuerelementvorlage. Die Vorlage besteht aus einem Quadrat (, deren Hintergrund an die **Background** -Eigenschaft, die alle Instanzen des Typs XAML- [Steuerelement](/uwp/api/windows.ui.xaml.controls.control) gebunden ist) und ein Textelement (, dessen Text auf die Abhängigkeitseigenschaft **BgLabelControl::Label** gebunden ist).

## <a name="add-an-instance-of-bglabelcontrol-to-the-main-ui-page"></a>Fügen Sie eine Instanz des **BgLabelControl** zur Hauptseite der Benutzeroberfläche

Öffnen Sie `MainPage.xaml` mit dem XAML-Markup für unsere UI-Hauptseite. Fügen Sie unmittelbar nach der (inside **StackPanel**) **Button** -Element das folgende Markup hinzu.

```xaml
<local:BgLabelControl Background="Red" Label="Hello, World!"/>
```

Darüber hinaus hinzufügen die folgenden #include `MainPage.h` , damit der **MainPage** -Typ (eine Kombination der Kompilierung von XAML-Markup und imperative Code) des Typs benutzerdefiniertes Steuerelement **BgLabelControl** kennt.

```cppwinrt
// MainPage.h
...
#include "BgLabelControl.h"
...
```

Erstellen Sie nun das Projekt und führen Sie es aus. Sie sehen, dass die standardmäßige Steuerelementvorlage auf den Hintergrundpinsel, und klicken Sie auf die Beschriftung der **BgLabelControl** -Instanz im Markup gebunden werden.

In dieser exemplarischen Vorgehensweise bedeutete für ein einfaches Beispiel für einen benutzerdefinierten (Steuerelementvorlage) in C + / WinRT. Sie können Ihre eigenen benutzerdefinierten Steuerelemente willkürlich umfassende und vollem Funktionsumfang tätigen. Beispielsweise kann ein benutzerdefiniertes Steuerelement Form etwas so kompliziert ist wie ein bearbeitbaren Datenraster, einen Videoplayer oder eine Schnellansicht 3D Geometrie dauern.

## <a name="important-apis"></a>Wichtige APIs
* [Steuerelement](/uwp/api/windows.ui.xaml.controls.control)
* [DependencyProperty](/uwp/api/windows.ui.xaml.dependencyproperty)

## <a name="related-topics"></a>Verwandte Themen
* [Steuerelementvorlagen](/windows/uwp/design/controls-and-patterns/control-templates)
* [Benutzerdefinierte Abhängigkeitseigenschaften](/windows/uwp/xaml-platform/custom-dependency-properties)
