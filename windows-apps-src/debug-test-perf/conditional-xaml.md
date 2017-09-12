---
author: jwmsft
title: Bedingte XAML
description: "Verwenden neuer APIs in XAML-Markup bei gleichzeitiger Gewährleistung der Kompatibilität mit früheren Versionen"
ms.author: jimwalk
ms.date: 07/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: b6fad82b8610367f5a69b236c1783106454374f3
ms.sourcegitcommit: 73ea31d42a9b352af38b5eb5d3c06504b50f6754
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="conditional-xaml"></a>Bedingte XAML

*Bedingte XAML* bietet eine Möglichkeit, die Methode [ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsApiContractPresent_System_String_System_UInt16_) in XAML-Markup zu verwenden. Sie sind damit in der Lage, im Markup nur dann Eigenschaften festzulegen und Objekte zu initialisieren, wenn die entsprechende API vorhanden ist, ohne Code-Behind zu verwenden. Elemente oder Attribute werden selektiv analysiert, um zu bestimmen, ob sie zur Laufzeit zur Verfügung stehen. Bedingte Anweisungen werden zur Laufzeit ausgewertet, und Elemente, die mit einem bedingten XAML-Tag gekennzeichnet sind, werden analysiert, wenn ihre Auswertung **true** ergibt. Andernfalls werden sie ignoriert.

Bedingte XAML ist ab dem Creators-Update (Version 1703, Build 15063) verfügbar. Die Verwendung bedingter XAML setzt voraus, dass Sie in Ihrem Visual Studio-Projekt Build 15063 (Creators Update) oder höher als Mindestversion und eine höhere Version als Zielversion festlegen. Weitere Informationen zum Konfigurieren Ihres Visual Studio-Projekts finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).

> [!IMPORTANT]
> **VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) verwenden und [Insider-Builds 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) oder höher ausführen, um bedingte XAML nutzen zu können

> [!NOTE]
> Sie müssen zum Erstellen einer versionsadaptiven App mit einer Mindestversion kleiner als Build 15063 [versionsadaptiven Code](version-adaptive-code.md) und nicht XAML verwenden.

Wichtige Hintergrundinformationen über ApiInformation und API-Verträge finden Sie unter [Versionsadaptive Apps](version-adaptive-apps.md).

## <a name="conditional-namespaces"></a>Bedingte Namespaces

Um eine Bedingung in XAML zu verwenden, müssen Sie zuerst einen bedingten [XAML-Namespace](../xaml-platform/xaml-namespaces-and-namespace-mapping.md) am Beginn der Seite deklarieren. Hier ein Pseudocodebeispiel für einen bedingten Namespace:

```xaml
xmlns:myNamespace="schema?conditionalMethod(parameter)"
```

Ein bedingter Namespace besteht aus zwei Teilen, die durch das Zeichen '?' getrennt sind. Der Inhalt vor dem Trennzeichen gibt den Namespace oder das Schema an, in dem die referenzierte API enthalten ist. Der Inhalt nach dem Trennzeichen '?' stellt die bedingte Methode dar, die bestimmt, ob die Auswertung für den bedingten Namespace **true** oder **false** ergibt.

In den meisten Fällen wird das Schema der standardmäßige XAML-Namespace sein:

```xaml
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
```

Bedingte XAML unterstützt die folgenden bedingten Methoden:

Methode | Umkehrung
------ | -------
IsApiContractPresent(ContractName, VersionNumber) | IsApiContractNotPresent(ContractName, VersionNumber)
IsTypePresent(ControlType) | IsTypeNotPresent(ControlType)
IsPropertyPresent(ControlType, PropertyName) | IsPropertyNotPresent(ControlType, PropertyName)

(Weitere Informationen zu diesen Methoden finden Sie in den folgenden Abschnitten.)

> [!NOTE] 
> Es wird empfohlen, dass Sie IsApiContractPresent und IsApiContractNotPresent verwenden. Andere Bedingungen werden im Visual Studio-Entwurf nicht vollständig unterstützt.

## <a name="create-a-namespace-and-set-a-property"></a>Erstellen eines Namespace und Festlegen einer Eigenschaft

In diesem Beispiel zeigen Sie „Hello, Windows-Insider” als Inhalt eines Textblocks an, wenn die App unter der Windows Insider Preview (Fall Creators Update) ausgeführt wird, und standardmäßig keinen Inhalt, wenn eine frühere Version vorliegt.

Zuerst definieren Sie einen benutzerdefinierten Namespace mit dem Präfix „Insider” und verwenden den standardmäßigen XAML-Namespace (http://schemas.microsoft.com/winfx/2006/xaml/presentation) als das Schema, das die Eigenschaft [TextBlock.Text](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textblock#Windows_UI_Xaml_Controls_TextBlock_Text) enthält. Um daraus einen bedingten Namespace zu machen, fügen Sie das Trennzeichen '?' nach dem Schema ein.

Dann definieren Sie eine Bedingung, die **true** auf Geräten zurückgibt, die Windows Insider Preview ausführen. Sie können die ApiInformation-Methode **IsApiContractPresent** verwenden, um zu prüfen, ob die 5. Version von UniversalApiContract vorliegt. Version 5 von UniversalApiContract wurde mit Windows Insider Preview (Fall Creators Update) veröffentlicht.

```xaml
xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
```

Nachdem der Namespace definiert ist, stellen Sie das Namespacepräfix der Text-Eigenschaft Ihrer TextBox voran, um sie als Eigenschaft auszuzeichnen, die bedingt zur Laufzeit festgelegt werden soll.

```xaml
<TextBlock insider:Text="Hello, Windows Insider"/>
```

Hier die gesamte XAML.

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <TextBlock x:Name="textBlock" insider:Text="Hello, Windows Insider"/>
    </Grid>
</Page>
```

Wenn Sie dieses Beispiel unter der Insider Preview ausführen, wird der Text „I am a Windows Insider” angezeigt. Wenn Sie es unter dem Creators Update ausführen, wird kein Text angezeigt.

Mit bedingter XAML können Sie die API-Prüfungen statt im Code in Ihrem Markup ausführen. Hier der entsprechende Code für dieses Beispiel.

```csharp
if (ApiInformation.IsApiContractPresent("Windows.Foundation.UniversalApiContract", 5))
{
    textBlock.Text = "Hello, Windows Insider";
}
```

Beachten Sie: Obwohl die Methode IsApiContractPresent eine Zeichenfolge für den Parameter *contractName* erwartet, wird diese in der XAML-Namespace-Deklaration nicht in Anführungszeichen ("") gesetzt.

## <a name="use-ifelse-conditions"></a>Verwenden von if/else-Bedingungen

Im vorherigen Beispiel wird die Text-Eigenschaft nur festgelegt, wenn die App mit der Insider Preview ausgeführt wird. Wie ist aber vorzugehen, um einen alternativen Text anzuzeigen, wenn das Creators Update ausgeführt wird? Sie können versuchen, die Text-Eigenschaft wie folgt ohne einen bedingten Qualifizierer festzulegen.

```xaml
<!-- DO NOT USE -->
<TextBlock Text="Hello, World" insider:Text="Hello, Windows Insider"/>
```

Dies funktioniert unter dem Creators Update, aber mit der Insider Preview erhalten Sie eine Fehlermeldung, die besagt, dass die Text-Eigenschaft mehrmals festgelegt wurde.

Um unterschiedliche Texte festzulegen für den Fall, dass die App unter verschiedenen Versionen von Windows10 ausgeführt wird, benötigen Sie eine andere Bedingung. Bedingte XAML bietet eine Umkehrung jeder unterstützten ApiInformation-Methode, damit Sie wie folgt if/else-Szenarien erstellen können.
 
Die Methode IsApiContractPresent liefert **true**, wenn das aktuelle Gerät die angegebene Vertrags- und Versionsnummer enthält. Wenn Ihre App beispielsweise unter dem Creators-Update ausgeführt wird, hat der universelle API-Vertrag die Versionsnummer 4.

Verschiedene Aufrufe von IsApiContractPresent würden diese Ergebnisse liefern:

- IsApiContractPresent(Windows.Foundation.UniversalApiContract, 5) = **false**
- IsApiContractPresent(Windows.Foundation.UniversalApiContract, 4) = true
- IsApiContractPresent(Windows.Foundation.UniversalApiContract, 3) = true
- IsApiContractPresent(Windows.Foundation.UniversalApiContract, 2) = true
- IsApiContractPresent(Windows.Foundation.UniversalApiContract, 1) = true.

IsApiContractNotPresent liefert die Umkehrung von IsApiContractPresent. Aufrufe von IsApiContractNotPresent würden folgende Ergebnisse liefern:

- IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 5) = **true**
- IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 4) = false
- IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 3) = false
- IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 2) = false
- IsApiContractNotPresent(Windows.Foundation.UniversalApiContract, 1) = false

Um die umgekehrte Bedingung zu verwenden, erstellen Sie einen zweiten bedingten XAML-Namespace, der die Bedingung **IsApiContractNotPresent** verwendet In diesem Fall hat sie das Präfix „notInsider”.

```xaml
xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"

xmlns:notInsider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)"
```

Sind beide Namespaces definiert, können Sie die Text-Eigenschaft doppelt festlegen, solange Sie Qualifizierer voranstellen, die gewährleisten, dass zur Laufzeit nur eine Einstellung der Eigenschaft verwendet wird. Beispiel:

```xaml
<TextBlock notInsider:Text="Hello, World" 
           insider:Text="Hello, Windows Insider"/>
```

Hier ist ein weiteres Beispiel, das die Hintergrundfarbe einer Schaltfläche festlegt. Das Feature [Acryl-Material](../style/acrylic.md) ist mit der Insider Preview (Fall Creators Update) verfügbar. Sie verwenden also Acryl für den Hintergrund, wenn die App unter der Insider Preview ausgeführt wird. Unter früheren Versionen ist Acryl nicht verfügbar; in diesen Fällen legen Sie die Hintergrundfarbe auf Rot fest.

```xaml
<Button Content="Button"
        notInsider:Background="Red"
        insider:Background="{ThemeResource SystemControlAcrylicElementBrush}"/>
```

## <a name="create-controls-and-bind-properties"></a>Erstellen von Steuerelementen und Binden von Eigenschaften

Bisher haben Sie erfahren, wie Eigenschaften mithilfe bedingter XAML festgelegt werden. Sie können aber auch Steuerelemente bedingt instanziieren, je nach dem API-Vertrag, der zur Laufzeit verfügbar ist

Hier wird ein [ColorPicker](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker) instanziiert, wenn die App unter der Insider Preview ausgeführt wird, in der das Steuerelement verfügbar ist. Der ColorPicker ist erst ab der Insider Preview verfügbar. Wenn die App unter früheren Versionen ausgeführt wird, verwenden Sie eine [ComboBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.combobox), um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.

```xaml
<insider:ColorPicker x:Name="colorPicker" Grid.Column="1"/>

<notInsider:ComboBox x:Name="colorComboBox" PlaceholderText="Pick a color"
                     Grid.Column="1" VerticalAlignment="Center">
```

Sie können bedingte Qualifizierer mit unterschiedlichen Arten von [XAML-Syntax für Eigenschaften](../xaml-platform/xaml-syntax-guide.md) verwenden. Hier wird für die Insider Preview die Fill-Eigenschaft des Rechtecks mit Syntax für Eigenschaftselemente festgelegt und für frühere Versionen mithilfe der Attributsyntax.

```xaml
<Rectangle x:Name="colorRectangle" Width="200" Height="200"
           notInsider:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
    <insider:Rectangle.Fill>
        <SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
    </insider:Rectangle.Fill>
</Rectangle>
```

Wenn Sie eine Eigenschaft an eine anderen Eigenschaft binden, die von einem bedingten Namespace abhängig ist, müssen Sie dieselbe Bedingung für beide Eigenschaften verwenden. Hier ist `colorPicker.Color` vom bedingten „Insider”-Namespace abhängig, sodass Sie das Präfix „Insider” auch für Eigenschaft SolidColorBrush.Color verwenden müssen. (Oder verwenden Sie das Präfix „Insider” mit der Eigenschaft SolidColorBrush statt mit der Color-Eigenschaft.) Andernfalls tritt während der Kompilierung ein Fehler auf.

```xaml
<SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
```

Hier folgt der vollständige XAML-Code, der diese Szenarien veranschaulicht. Dieses Beispiel enthält ein Rechteck und eine Benutzeroberfläche, mit der Sie die Farbe des Rechtecks festlegen können.

Wenn die App unter der Insider Preview ausgeführt wird, verwenden Sie einen ColorPicker, um dem Benutzer die Farbauswahl zu ermöglichen. Da der ColorPicker erst ab der Insider Preview verfügbar ist, verwenden Sie, wenn die App unter einer früheren Version ausgeführt wird, eine ComboBox, um eine vereinfachte Farbauswahl für den Benutzer bereitzustellen.

```xaml
<Page
    x:Class="ConditionalTest.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:insider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractPresent(Windows.Foundation.UniversalApiContract,5)"
    xmlns:notInsider="http://schemas.microsoft.com/winfx/2006/xaml/presentation?IsApiContractNotPresent(Windows.Foundation.UniversalApiContract,5)">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>

        <Rectangle x:Name="colorRectangle" Width="200" Height="200"
                   notInsider:Fill="{x:Bind ((SolidColorBrush)((FrameworkElement)colorComboBox.SelectedItem).Tag), Mode=OneWay}">
            <insider:Rectangle.Fill>
                <SolidColorBrush insider:Color="{x:Bind colorPicker.Color, Mode=OneWay}"/>
            </insider:Rectangle.Fill>
        </Rectangle>

        <insider:ColorPicker x:Name="colorPicker" Grid.Column="1"/>

        <notInsider:ComboBox x:Name="colorComboBox" PlaceholderText="Pick a color"
                     Grid.Column="1" VerticalAlignment="Center">
            <ComboBoxItem>Red
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Red"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
            <ComboBoxItem>Blue
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Blue"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
            <ComboBoxItem>Green
                <ComboBoxItem.Tag>
                    <SolidColorBrush Color="Green"/>
                </ComboBoxItem.Tag>
            </ComboBoxItem>
        </notInsider:ComboBox>
    </Grid>
</Page>
```

## <a name="related-articles"></a>Verwandte Artikel

- [Anleitung für UWP-Apps](https://msdn.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)
- [Dynamically detecting features with API contracts (Dynamisches Erkennen von Features mithilfe von API-Verträgen)](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/)
- [API-Verträge](https://channel9.msdn.com/Events/Build/2015/3-733) (Video für Build 2015)