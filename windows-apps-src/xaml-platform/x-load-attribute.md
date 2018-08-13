---
author: jwmsft
title: xLoad-Attribut
description: xLoad ermöglicht die dynamische beim Erstellen und Löschen eines Elements und untergeordneten Verringern der Zeit und Speicherverwendung starten.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8f34ea43b981de65c81e9cce2b8a896c3577e595
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "610789"
---
# <a name="xload-attribute"></a>x:Load-Attribut

**X: Laden** können Sie um zum Starten des, visuelle Struktur Erstellung und Speicherverwendung Ihrer App XAML zu optimieren. Mithilfe von **X: Laden** hat einen ähnlichen visuellen Effekt an **Sichtbarkeit**, außer dass, wenn das Element nicht geladen wird, der Speicher freigegeben wird und ein kleiner Platzhalter intern verwendet wird, um seine Position in der visuellen Struktur markieren.

Das Element der Benutzeroberfläche Ergebnisarray als Attribut zugewiesen mit X: laden kann geladen und entladen über Code oder mithilfe eines Ausdrucks [X binden:](x-bind-markup-extension.md) sein. Dies ist zur Reduzierung der Kosten für Elemente nützlich, die selten oder nur bedingt angezeigt werden. Wenn Sie für einen Container wie Raster oder StackPanel X: Laden verwenden, dem Container und alle untergeordneten geladen oder entladen als Gruppe.

Die Überwachung der zurückgestellte Elemente von XAML-Framework hinzugefügt für jedes Element Ergebnisarray als Attribut zugewiesen mit X: Laden, um den Platzhalter berücksichtigt die Speicherverwendung ungefähr 600 Bytes. Aus diesem Grund ist es möglich, dieses Attribut zu viele, tatsächlich die Leistung beeinträchtigt wird. Es wird empfohlen, dass Sie nur für Elemente verwenden, die ausgeblendet werden müssen. Wenn Sie für einen Container X: Laden verwenden, wird der Aufwand nur für das Element mit dem Attribut X: Laden gezahlt.

> [!IMPORTANT]
> Das Attribut X: Laden steht in Windows 10, Version 1703 (Aktualisierung vom Ersteller) ab. Die Mindestversion, auf die Ihr Visual Studio-Projekt abzielt, muss *Windows 10 Creators Update (10.0, Build 15063)* sein, damit x:Load verwendet werden kann.

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:Load="True" .../>
<object x:Load="False" .../>
<object x:Load="{x:Bind Path.to.a.boolean, Mode=OneWay}" .../>
```

## <a name="loading-elements"></a>Laden von Elementen

Es gibt verschiedene Möglichkeiten zum Laden der Elemente:

- Verwenden Sie einen Ausdruck [X: Binden](x-bind-markup-extension.md) , um die Ladestatus anzugeben. Der Ausdruck sollte **true** zum Laden und **false** , wenn das Element entladen zurückgeben.
- Rufen Sie [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) mit dem Namen auf, der für das Element definiert wurde.
- Rufen Sie [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) mit dem Namen auf, der für das Element definiert wurde.
- Verwenden Sie in einer [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007), eine [**Set-Methode**](https://msdn.microsoft.com/library/windows/apps/br208817) oder das **Storyboard** Animation, die das Element X: Laden beruht.
- Ziel der entladen-Element in eine beliebige **Storyboard**.

> HINWEIS: Nach Start der Instanziierung eines Elements wird es im Benutzeroberflächen-Thread erstellt. Dies kann ggf. bewirken, dass die Oberfläche ruckelt, wenn zu viele auf einmal erstellt werden.

Wenn ein verzögertes Element mit einer der oben aufgeführten Methoden erstellt wurde, passiert Folgendes:

- Das [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723)-Ereignis für das Element wird ausgelöst.
- Das Feld für X: Name ist festgelegt.
- Alle Bindungen X: Binden auf das Element werden ausgewertet.
- Wenn Sie sich für den Empfang von Benachrichtigungen über Änderungen an der Eigenschaft, die die verzögerten Elemente enthält, registriert haben, wird die Benachrichtigung ausgelöst.

## <a name="unloading-elements"></a>Entladen Elemente

So entfernen Sie ein Element:

- Verwenden Sie einen Ausdruck X: binden, um die Ladestatus anzugeben. Der Ausdruck sollte **true** zum Laden und **false** , wenn das Element entladen zurückgeben.
- Rufen Sie in einer Seite oder UserControl **UnloadObject an** , und übergeben Sie die Objektreferenz
- Rufen Sie **Windows.UI.Xaml.Markup.XamlMarkupHelper.UnloadObject** und übergeben Sie die Objektreferenz

Wenn ein Objekt entladen wird, wird es in der Struktur mit einem Platzhalter ersetzt. Die Objektinstanz bleibt im Arbeitsspeicher, bis alle Verweise veröffentlicht wurden. Die UnloadObject-API auf einer Seite/UserControl soll die Verweise frei, Codegen für X: Name und x binden: freigeben. Wenn Sie zusätzliche Verweise in app-Code enthalten, müssen sie auch freigegeben werden muss.

Wenn ein Element entladen wird, alle dem Element zugeordnete Zustände verworfen, also wenn X: Laden als eine optimierte Version von Sichtbarkeit, verwenden klicken Sie dann stellen Sie sicher, alle state über Bindungen angewendet wird oder wird erneut durch Code angewendet, wenn das Loaded-Ereignis ausgelöst wird.

## <a name="restrictions"></a>Einschränkungen

Die Einschränkungen für die Verwendung von **X: Laden** sind:

- Definieren Sie einen [x:Name](x-name-attribute.md) für das Element, da dieses Element später gefunden werden muss.
- Sie können nur X: Laden auf Typen, die von [**der Benutzeroberflächenelemente**](https://msdn.microsoft.com/library/windows/apps/br208911) oder [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249)abgeleitet werden.
- Sie können nicht auf Stammelemente in eine [**Seite**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page), ein [**UserControl**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol)oder einer [**Datenvorlage**](https://msdn.microsoft.com/library/windows/apps/br242348)X: Laden verwenden.
- Sie können nicht auf Elemente in einem [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)X: Laden verwenden.
- X: Laden können keine zu weit XAML mit [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048)geladen.
- Verschieben ein übergeordnetes Element löscht alle Elemente, die nicht geladen wurden.

## <a name="remarks"></a>Hinweise

X: Laden können auf geschachtelten Elemente jedoch aus dem Element äußerste in realisiert werden muss.  Wenn Sie versuchen, ein untergeordnetes Element zu erkennen, bevor das übergeordnete Element erkannt wurde, wird eine Ausnahme ausgelöst.

In der Regel wird empfohlen, dass Sie Elemente zurückstellen, die nicht im ersten Frame angezeigt werden. Bei der Suche nach zu verzögernden Kandidaten empfiehlt es sich, nach Elementen zu suchen, die mit reduzierter [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992) erstellt werden. Eine Benutzeroberfläche, die durch eine Benutzerinteraktion ausgelöst wird, ist außerdem ein guter Ort zum Suchen nach Elementen, die zurückgestellt werden können.

Seien Sie vorsichtig beim Verzögern von Elementen in einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), da so die Startzeit verringert, aber auch die Leistung beim Verschieben reduziert werden kann – je nachdem, was Sie erstellen. Wenn Sie die Leistung beim Verschieben erhöhen möchten, finden Sie in den Dokumentationen [{x:Bind}-Markuperweiterung](x-bind-markup-extension.md) und [x:Phase-Attribut](x-phase-attribute.md) weitere Informationen.

Wenn das [Attribut X: Phase](x-phase-attribute.md) in Verbindung mit **X: Laden** Sie dann verwendet wird, wenn ein Element oder einer Struktur realisiert wird, werden die Bindungen sowie die aktuelle Phase angewendet. Die Phase für **X: Phase** angegeben beeinflussen oder steuern den Status beim Laden des Elements. Wenn ein Listenelement wiederverwendeten als Teil von Balance handelt, realisiert Elemente verhält sich auf die gleiche Weise wie andere aktive Elemente und kompilierte Bindungen (**{X: Binden}** Bindungen) mit den gleichen Regeln, einschließlich können verarbeitet werden.

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

