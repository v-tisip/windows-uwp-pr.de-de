---
author: jwmsft
title: xLoad-Attribut
description: xLoad ermöglicht die dynamische Erstellung und Zerstörung eines Elements und seiner untergeordneten Elemente verzögert und damit Startzeit Nutzung von Zeit und Arbeitsspeicher. 
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d9659d183c020c579aa0a21fe179a69c1d9997c5
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5987014"
---
# <a name="xload-attribute"></a>x:Load-Attribut

**X: Load** können Sie um die Startzeit, visuelle Struktur Erstellung und Speicherverwendung für Ihre XAML-app zu optimieren. Verwendung von **X: Load** wirkt sich visual aus, **Sichtbarkeit**, mit der Ausnahme, dass, wenn das Element nicht geladen wird, der Speicher freigegeben wird ein kleiner Platzhalter wird intern verwendet, um seine Position in der visuellen Struktur markieren.

Das UI-Element mit X: Load attributierte möglich geladen und entladen über Code oder mithilfe eines [X: Bind](x-bind-markup-extension.md) -Ausdrucks. Dies ist zur Reduzierung der Kosten für Elemente nützlich, die selten oder nur bedingt angezeigt werden. Wenn Sie X: Load auf einem Container wie Raster oder StackPanel verwenden, der Container und alle untergeordneten Elemente geladen oder als Gruppe entladen.

Die Verfolgung von verzögerten Elementen durch das XAML-Framework fügt ca. 600 Bytes zur Speicherverwendung für jedes Element attributierten mit X: Load, um den Platzhalter zu berücksichtigen. Aus diesem Grund ist es möglich, dieses Attribut durch eine übermäßige Verwendung, in dem Maße, tatsächlich die Leistung beeinträchtigt wird. Es wird empfohlen, mit denen Sie nur für Elemente, die ausgeblendet werden müssen. Wenn Sie X: Load auf einem Container verwenden, wird der Aufwand nur für das Element mit dem das Attribut X: Load abgewickelt.

> [!IMPORTANT]
> Das Attribut X: Load ist ab Windows 10, Version 1703 (Creators Update) verfügbar. Die Mindestversion, auf die Ihr Visual Studio-Projekt abzielt, muss *Windows 10 Creators Update (10.0, Build 15063)* sein, damit x:Load verwendet werden kann.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:Load="True" .../>
<object x:Load="False" .../>
<object x:Load="{x:Bind Path.to.a.boolean, Mode=OneWay}" .../>
```

## <a name="loading-elements"></a>Laden von Elementen

Es gibt mehrere Möglichkeiten zum Laden der Elemente:

- Verwenden eines [X: Bind](x-bind-markup-extension.md) -Ausdrucks angeben des Zustands laden. Der Ausdruck sollte **"true"** zum Laden und **"false",** um das Element zu entladen zurückgeben.
- Rufen Sie [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) mit dem Namen auf, der für das Element definiert wurde.
- Rufen Sie [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) mit dem Namen auf, der für das Element definiert wurde.
- Verwenden Sie in einer [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007)eine [**Setter**](https://msdn.microsoft.com/library/windows/apps/br208817) oder das **Storyboard** -Animation, die das X: Load-Element ausgerichtet ist.
- Das entladene Element in jeder **Storyboard**als Ziel.

> HINWEIS: Nach Start der Instanziierung eines Elements wird es im Benutzeroberflächen-Thread erstellt. Dies kann ggf. bewirken, dass die Oberfläche ruckelt, wenn zu viele auf einmal erstellt werden.

Wenn ein verzögertes Element mit einer der oben aufgeführten Methoden erstellt wurde, passiert Folgendes:

- Das [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723)-Ereignis für das Element wird ausgelöst.
- Das Feld für X: Name wird festgelegt.
- Alle X: Bind-Bindungen für das Element werden ausgewertet.
- Wenn Sie sich für den Empfang von Benachrichtigungen über Änderungen an der Eigenschaft, die die verzögerten Elemente enthält, registriert haben, wird die Benachrichtigung ausgelöst.

## <a name="unloading-elements"></a>Entladen Elemente

Um ein Element zu entladen:

- Verwenden eines X: Bind-Ausdrucks angeben des Zustands laden. Der Ausdruck sollte **"true"** zum Laden und **"false",** um das Element zu entladen zurückgeben.
- Rufen Sie in eine Seiten- oder "UserControl" **UnloadObject auf** , und übergeben Sie den Objektverweis
- Rufen Sie **Windows.UI.Xaml.Markup.XamlMarkupHelper.UnloadObject** und übergeben Sie den Objektverweis

Wenn ein Objekt entladen wird, wird es mit einem Platzhalter in der Struktur ersetzt. Die Objektinstanz verbleibt im Arbeitsspeicher, bis alle Verweise freigegeben wurden. UnloadObject API auf einer Seite "/" UserControl "wurde entwickelt, die Verweise frei, Codegen für X: Name und X: Bind freizugeben. Wenn Sie zusätzliche Verweise in app-Code enthalten, müssen sie auch freigegeben werden.

Wenn ein Element entladen wird, alle Zustände, die dem Element zugeordnete werden verworfen, also bei Verwendung von X: Load als eine optimierte Version von Sichtbarkeit, dann sicherstellen, dass alle Zustand über Bindungen angewendet wird, oder wird vom Code erneut angewendet, wenn das Loaded-Ereignis ausgelöst wird.

## <a name="restrictions"></a>Einschränkungen

Die Einschränkungen für die Verwendung von **X: Load** sind:

- Definieren Sie ein [X: Name](x-name-attribute.md)für das Element, da dieses muss das Element später gefunden werden.
- Sie können nur X: Load für Typen verwenden, die von [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) oder [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249)abgeleitet werden.
- Sie können keine X: Load auf Stammelemente in einer [**Seite**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page)oder ein [**"UserControl"**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol), einem [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/br242348)verwenden.
- Sie können nicht auf Elemente in einem [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)X: Load verwenden.
- X: Load können keine losen XAML mit [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048)geladen.
- Verschieben eines übergeordneten Elements werden alle Elemente gelöscht, die nicht geladen wurden.

## <a name="remarks"></a>Hinweise

Sie können X: Load auf geschachtelte Elemente verwenden, jedoch müssen Sie vom äußersten Element im erkannt werden. Wenn Sie versuchen, ein untergeordnetes Element zu erkennen, bevor das übergeordnete Element erkannt wurde, wird eine Ausnahme ausgelöst.

In der Regel wird empfohlen, dass Sie Elemente zurückstellen, die nicht im ersten Frame angezeigt werden.Bei der Suche nach zu verzögernden Kandidaten empfiehlt es sich, nach Elementen zu suchen, die mit reduzierter [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992) erstellt werden. Eine Benutzeroberfläche, die durch eine Benutzerinteraktion ausgelöst wird, ist außerdem ein guter Ort zum Suchen nach Elementen, die zurückgestellt werden können.

Seien Sie vorsichtig beim Verzögern von Elementen in einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), da so die Startzeit verringert, aber auch die Leistung beim Verschieben reduziert werden kann – je nachdem, was Sie erstellen. Wenn Sie die Leistung beim Verschieben erhöhen möchten, finden Sie in den Dokumentationen [{x:Bind}-Markuperweiterung](x-bind-markup-extension.md) und [x:Phase-Attribut](x-phase-attribute.md) weitere Informationen.

Wenn das [X: Phase-Attribut](x-phase-attribute.md) in Verbindung mit **X: Load** dann verwendet wird, wenn ein Element oder eine Elementstruktur realisiert wird, werden die Bindungen bis zu und einschließlich zur aktuellen Phase angewendet. Die Phase für **X: Phase** angegeben beeinflussen oder steuern den Zustand beim Laden des Elements. Wenn ein Listenelement als Teil der Verschiebung wiederverwendet wird, realisierte Elemente verhält sich auf die gleiche Weise wie andere Elemente, und kompilierte Bindungen (**{X: Bind}** Bindungen) werden unter Verwendung der gleichen Regeln einschließlich phasing verarbeitet.

Eine allgemeine Richtlinie besteht darin, die Leistung Ihrer App vorher und nachher zu messen, um sicherzustellen, das Sie die gewünschte Leistung erhalten.

## <a name="example"></a>Beispiel

```xml
<StackPanel>
    <Grid x:Name="DeferredGrid" x:Load="False">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>

        <Rectangle Height="100" Width="100" Fill="Orange" Margin="0,0,4,4"/>
        <Rectangle Height="100" Width="100" Fill="Green" Grid.Column="1" Margin="4,0,0,4"/>
        <Rectangle Height="100" Width="100" Fill="Blue" Grid.Row="1" Margin="0,4,4,0"/>
        <Rectangle Height="100" Width="100" Fill="Gold" Grid.Row="1" Grid.Column="1" Margin="4,4,0,0"
                   x:Name="one" x:Load="{x:Bind (x:Boolean)CheckBox1.IsChecked, Mode=OneWay}"/>
        <Rectangle Height="100" Width="100" Fill="Silver" Grid.Row="1" Grid.Column="1" Margin="4,4,0,0"
                   x:Name="two" x:Load="{x:Bind Not(CheckBox1.IsChecked), Mode=OneWay}"/>
    </Grid>

    <Button Content="Load elements" Click="LoadElements_Click"/>
    <Button Content="Unload elements" Click="UnloadElements_Click"/>
    <CheckBox x:Name="CheckBox1" Content="Swap Elements" />
</StackPanel>
```

```csharp
// This is used by the bindings between the rectangles and check box.
private bool Not(bool? value) { return !(value==true); }

private void LoadElements_Click(object sender, RoutedEventArgs e)
{
    // This will load the deferred grid, but not the nested
    // rectangles that have x:Load attributes.
    this.FindName("DeferredGrid"); 
}

private void UnloadElements_Click(object sender, RoutedEventArgs e)
{
     // This will unload the grid and all its child elements.
     this.UnloadObject(DeferredGrid);
}
```

