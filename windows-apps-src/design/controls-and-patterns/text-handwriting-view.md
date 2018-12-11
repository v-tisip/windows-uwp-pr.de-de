---
Description: Customize the built-in handwriting view for ink to text input that is supported by UWP text controls such as the TextBox, RichEditBox (and controls like the AutoSuggestBox that provide a similar text input experience).
title: Texteingabe mit der Handschrift-Ansicht
label: Text input with the handwriting view
template: detail.hbs
ms.date: 10/13/18
ms.topic: article
keywords: Windows10, UWP
pm-contact: sewen
design-contact: minah.kim
doc-status: Draft
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 3660586b856205721bfa8e9cbb3e72df4fd3ad43
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8899338"
---
# <a name="text-input-with-the-handwriting-view"></a>Texteingabe mit der Handschrift-Ansicht

![Textfeld wird erweitert, wenn mit einem Stift darauf getippt wird](images/handwritingview/handwritingview2.gif)

Anpassen der integrierten Handschrift Ansicht für Freihandeingaben für Texteingabe, die von UWP-Textsteuerelemente wie z. B. [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox), [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox)unterstützt und Steuerelemente von diese z. B. die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)abgeleitet.

## <a name="overview"></a>Übersicht

XAML-Texteingabefelder über eine integrierte Unterstützung für Stifteingaben mit [Windows Ink](../input/pen-and-stylus-interactions.md). Wenn ein Benutzer in ein Texteingabefeld mit einem Windows-Stift tippt, transformiert das Textfeld eine Oberfläche Handschrift, anstatt einen separaten Eingabebereich öffnen.

Text wird erkannt, während der Benutzer an einer beliebigen Stelle in das Textfeld ein, und ein Kandidat schreibt, dass die Ergebnisse der Erkennung zeigt. Der Benutzer kann auf ein Ergebnis tippen, um es auszuwählen, oder er kann den Schreibvorgang fortsetzen, um das vorgeschlagene Wort zu akzeptieren. Die literalen Erkennungsergebnisse (buchstabenweise) sind im Kandidatenfenster enthalten, somit ist die Erkennung nicht auf Wörter in einem Wörterbuch beschränkt. Während der Benutzer schreibt, wird die akzeptierte Texteingabe in ein Schriftzeichen konvertiert, das das Verhalten der natürlichen Schreibweise beibehält.

> [!NOTE]
> Die Handschrift-Ansicht ist standardmäßig aktiviert, aber Sie können pro Steuerelement zu deaktivieren und stattdessen die zu der Text Texteingabebereich zurückkehren.

![Textfeld mit Freihandeingabe und Vorschläge](images/handwritingview/handwritingview-inksuggestion1.gif)

Ein Benutzer kann seinen Text mithilfe der folgenden Standardgesten und -aktionen bearbeiten:

- _Durchstreichen_ oder _Ausstreichen_ – Ermöglicht das Durchziehen eines Strichs, um ein Wort oder einen Teil eines Wortes zu löschen.
- _Verknüpfen_ – Zeichnet einen Bogen zwischen Wörtern, um den Abstand zwischen ihnen zu löschen.
- _Einfügen_ – Ermöglicht das Zeichnen eines Caret-Symbols, um ein Leerzeichen einzufügen.
- _Überschreiben_ – Überschreibt vorhandenen Text, um ihn zu ersetzen.

![Textfeld mit Freihandeingabe Korrektur](images/handwritingview/handwritingview-inkcorrection1.gif)

## <a name="disable-the-handwriting-view"></a>Deaktivieren Sie die Ansicht der Handschrift

Die integrierte Handschrift-Ansicht ist standardmäßig aktiviert.

Sie sollten die Handschrift-Ansicht zu deaktivieren, wenn Sie bereits den Ink-zu-Text-Funktionen in Ihrer Anwendung oder der Text-Eingabe-Erfahrung auf einer Art von Formatierung oder Sonderzeichen Zeichen (z. B. eine Registerkarte) über Handschrift nicht verfügbar basiert.

In diesem Beispiel deaktivieren wir die Handschrift-Ansicht, indem Sie die Eigenschaft [IsHandwritingViewEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.ishandwritingviewenabled) dem [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) -Steuerelement auf "false". Alle Textsteuerelemente, die Unterstützung der Handschrift Ansicht unterstützen eine ähnliche Eigenschaft.

```xaml
<TextBox Name="SampleTextBox"
    Height="50" Width="500" 
    FontSize="36" FontFamily="Segoe UI" 
    PlaceholderText="Try taping with your pen" 
    IsHandwritingViewEnabled="False">
</TextBox>
```

## <a name="specify-the-alignment-of-the-handwriting-view"></a>Geben Sie die Ausrichtung der Ansicht Handschrift

Die Handschrift Ansicht befindet sich über das zugrunde liegende Textsteuerelement und Größe entsprechend den Einstellungen des Benutzers Handschrift (finden Sie unter **-Einstellungen, die Geräte -> -> Stift & Windows Ink-Handschrift > -> Schriftgrad, wenn Sie direkt in das Textfeld schreiben **). Die Ansicht wird automatisch auch relativ zu den Text-Steuerelement und seine Position innerhalb der app ausgerichtet.

Der Benutzeroberfläche die Anwendung wird nicht umgebrochen, um das Steuerelement größeren Rechnung zu tragen, damit das System die Ansicht verdeckt wichtige Elemente der UI beeinträchtigen kann.

Hier zeigen wir so verwenden Sie die Eigenschaft [PlacementAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.placementalignment) ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) angeben, welche Ankerpunkt für das zugrunde liegende Textsteuerelement verwendet wird, um die Ansicht Handschrift ausrichten.

```xaml
<TextBox Name="SampleTextBox"
    Height="50" Width="500" 
    FontSize="36" FontFamily="Segoe UI" 
    PlaceholderText="Try taping with your pen">
        <TextBox.HandwritingView>
            <HandwritingView PlacementAlignment="TopLeft"/>
        </TextBox.HandwritingView>
</TextBox>
```

## <a name="disable-auto-completion-candidates"></a>Deaktivieren der automatischen Vervollständigung Kandidaten

Der Text Vorschlag Popup ist standardmäßig aktiviert, eine Liste der wichtigsten Ink Erkennung Kandidaten bereitstellen, aus denen der Benutzer auswählen kann, für den Fall, dass der obere Kandidat nicht korrekt ist.

Wenn die Anwendung bereits stabile bereitstellt, benutzerdefinierten Erkennung-Funktionen, die Eigenschaft [AreCandidatesEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.arecandidatesenabled) können Sie so deaktivieren Sie die integrierte Vorschläge, wie im folgenden Beispiel gezeigt.

```xaml
<TextBox Name="SampleTextBox"
    Height="50" Width="500" 
    FontSize="36" FontFamily="Segoe UI" 
    PlaceholderText="Try taping with your pen">
        <TextBox.HandwritingView>
            <HandwritingView AreCandidatesEnabled="False"/>
        </TextBox.HandwritingView>
</TextBox>
```

## <a name="use-handwriting-font-preferences"></a>Verwenden Sie Handschrift Schriftart-Einstellungen

Benutzer können aus einer vordefinierten Auflistung der Handschrift-basierten Schriftarten zu verwenden, wenn Rendern von Text basierend auf Ink-Erkennung (finden Sie unter **Einstellungen -> Geräte -> Stift & Windows Ink-Handschrift > -> Schriftart Verwendung Handschrift**).

> [!NOTE]
> Benutzer können auch eine Schriftart basierend auf ihren eigenen Handschrift erstellen.
> [!VIDEO https://www.youtube.com/embed/YRR4qd4HCw8]

Die app kann Zugriff auf diese Einstellung und die ausgewählte Schriftart für den erkannten Text im Textfeld-Steuerelement verwenden.

In diesem Beispiel haben wir Lauschen auf das [TextChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.textchanged) -Ereignis ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) und ausgewählte Schriftart des Benutzers anwenden, wenn die Änderung von Text aus der HandwritingView (oder einer Standardschriftart, falls nicht) stammt.

```csharp
private void SampleTextBox_TextChanged(object sender, TextChangedEventArgs e)
{
    ((TextBox)sender).FontFamily = 
        ((TextBox)sender).HandwritingView.IsOpen ?
            new FontFamily(PenAndInkSettings.GetDefault().FontFamilyName) : 
            new FontFamily("Segoe UI");
}
```

## <a name="access-the-handwritingview-in-composite-controls"></a>Zugriff auf die HandwritingView in zusammengesetzten Steuerelemente

Zusammengesetzte Steuerelemente, die auch, die [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) oder [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox) -Steuerelemente, z. B. [AutoSuggestBox verwenden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) unterstützen eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview).

Verwenden Sie den Zugriff auf die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) in eines zusammengesetzten Steuerelements [VisualTreeHelper](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper) API.

Der folgende XAML-Codeausschnitt zeigt ein [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) -Steuerelement.

```xaml
<AutoSuggestBox Name="SampleAutoSuggestBox" 
    Height="50" Width="500" 
    PlaceholderText="Auto Suggest Example" 
    FontSize="16" FontFamily="Segoe UI"  
    Loaded="SampleAutoSuggestBox_Loaded">
</AutoSuggestBox>
```

In der entsprechende Code-Behind zeigen wir, wie die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)deaktivieren.

1. Zunächst behandeln wir die Anwendung Loaded-Ereignis aufgerufen wird, in denen eine FindInnerTextBox-Funktion, zum Durchlaufen der visuellen Struktur zu starten.

    ```csharp
    private void SampleAutoSuggestBox_Loaded(object sender, RoutedEventArgs e)
    {
        if (FindInnerTextBox((AutoSuggestBox)sender))
            autoSuggestInnerTextBox.IsHandwritingViewEnabled = false;
    }
    ```

2. Wir beginnen dann durchlaufen der visuellen Struktur (beginnend mit ein autosuggestbox-Element) in der Funktion FindInnerTextBox mit einem Aufruf von FindVisualChildByName.

    ```csharp
    private bool FindInnerTextBox(AutoSuggestBox autoSuggestBox)
    {
        if (autoSuggestInnerTextBox == null)
        {
            // Cache textbox to avoid multiple tree traversals. 
            autoSuggestInnerTextBox = 
                (TextBox)FindVisualChildByName<TextBox>(autoSuggestBox);
        }
        return (autoSuggestInnerTextBox != null);
    }
    ```

3. Schließlich durchläuft diese Funktion über die visuelle Struktur, bis das TextBox-Element abgerufen wird.

    ```csharp
    private FrameworkElement FindVisualChildByName<T>(DependencyObject obj)
    {
        FrameworkElement element = null;
        int childrenCount = 
            VisualTreeHelper.GetChildrenCount(obj);
        for (int i = 0; (i < childrenCount) && (element == null); i++)
        {
            FrameworkElement child = 
                (FrameworkElement)VisualTreeHelper.GetChild(obj, i);
            if ((child.GetType()).Equals(typeof(T)) || (child.GetType().GetTypeInfo().IsSubclassOf(typeof(T))))
            {
                element = child;
            }
            else
            {
                element = FindVisualChildByName<T>(child);
            }
        }
        return (element);
    }
    ```

## <a name="reposition-the-handwritingview"></a>Ändern der Position der HandwritingView

In einigen Fällen müssen Sie sicherstellen, dass die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) UI-Elemente behandelt, die sie andernfalls nicht kann.

Hier erstellen wir TextBox-Element, das Diktieren (durch platzieren ein Textfeld und eine Schaltfläche zum Diktieren in einem StackPanel implementiert) unterstützt.

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

Wie StackPanel jetzt größer als das TextBox-Element ist, kann die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) nicht alle von der zusammengesetzten Cotnrol verdeckt.

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview.png)

Um dies zu beheben, legen Sie die PlacementTarget-Eigenschaft der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf UI-Element, an dem es ausgerichtet werden soll.

```xaml
<StackPanel Name="DictationBox" 
    Orientation="Horizontal" 
    VerticalAlignment="Top" 
    HorizontalAlignment="Left" 
    BorderThickness="1" BorderBrush="DarkGray" 
    Height="55" Width="500" Margin="50">
    <TextBox Name="DictationTextBox" 
        Width="450" BorderThickness="0" 
        FontSize="24" VerticalAlignment="Center">
        <TextBox.HandwritingView>
            <HandwritingView PlacementTarget="{Binding ElementName=DictationBox}"/>
        </TextBox.HandwritingView>
    </TextBox>
    <Button Name="DictationButton" 
        Height="48" Width="48" 
        FontSize="24" 
        FontFamily="Segoe MDL2 Assets" 
        Content="&#xE720;" 
        Background="White" Foreground="DarkGray"     Tapped="DictationButton_Tapped" />
</StackPanel>
```

## <a name="resize-the-handwritingview"></a>Ändern der Größe der HandwritingView

Sie können auch Festlegen der Größe der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview), die beim müssen Sie sicherstellen, dass die Ansicht wichtig UI verdecken nicht hilfreich sein können.

Wie im vorherigen Beispiel erstellen wir TextBox-Element, das Diktieren (durch platzieren ein Textfeld und eine Schaltfläche zum Diktieren in einem StackPanel implementiert) unterstützt.

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

In diesem Fall möchten wir sicherstellen, dass die Schaltfläche Diktat immer sichtbar ist.

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview-resize.png)

Zu diesem Zweck binden wir die MaxWidth-Eigenschaft der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) an die Breite des UI-Elements, das es verdeckt sollten.

```xaml
<StackPanel Name="DictationBox" 
    Orientation="Horizontal" 
    VerticalAlignment="Top" 
    HorizontalAlignment="Left" 
    BorderThickness="1" 
    BorderBrush="DarkGray" 
    Height="55" Width="500" 
    Margin="50">
    <TextBox Name="DictationTextBox" 
        Width="450" 
        BorderThickness="0" 
        FontSize="24" 
        VerticalAlignment="Center">
        <TextBox.HandwritingView>
            <HandwritingView 
                PlacementTarget="{Binding ElementName=DictationBox}“
                MaxWidth="{Binding ElementName=DictationTextBox, Path=Width"/>
        </TextBox.HandwritingView>
    </TextBox>
    <Button Name="DictationButton" 
        Height="48" Width="48" 
        FontSize="24" 
        FontFamily="Segoe MDL2 Assets" 
        Content="&#xE720;" 
        Background="White" Foreground="DarkGray" 
        Tapped="DictationButton_Tapped" />
</StackPanel>
```

## <a name="reposition-custom-ui"></a>Ändern der Position benutzerdefinierte Benutzeroberfläche

Wenn Sie benutzerdefinierte Benutzeroberfläche verfügen, die in Reaktion auf Texteingabe, z. B. eine Informations-Popup angezeigt wird, müssen Sie die Benutzeroberfläche neu zu positionieren, damit sie die Ansicht Handschrift verdecken nicht.

![TextBox mit benutzerdefinierte Benutzeroberfläche](images/handwritingview/textbox-with-customui.png)

Das folgende Beispiel zeigt, wie die [geöffnet](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.opened)und [geschlossen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.closed
) [SizeChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.sizechanged) die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) zum Festlegen der Position der ein [Popup](https://docs.microsoft.com/uwp/api/windows.ui.popups)-Ereignisse überwacht.

```csharp
private void Search_HandwritingViewOpened(
    HandwritingView sender, HandwritingPanelOpenedEventArgs args)
{
    UpdatePopupPositionForHandwritingView();
}

private void Search_HandwritingViewClosed(
    HandwritingView sender, HandwritingPanelClosedEventArgs args)
{
    UpdatePopupPositionForHandwritingView();
}

private void Search_HandwritingViewSizeChanged(
    object sender, SizeChangedEventArgs e)
{
    UpdatePopupPositionForHandwritingView();
}

private void UpdatePopupPositionForHandwritingView()
{
if (CustomSuggestionUI.IsOpen)
    CustomSuggestionUI.VerticalOffset = GetPopupVerticalOffset();
}

private double GetPopupVerticalOffset()
{
    if (SearchTextBox.HandwritingView.IsOpen)
        return (SearchTextBox.Margin.Top + SearchTextBox.HandwritingView.ActualHeight);
    else
        return (SearchTextBox.Margin.Top + SearchTextBox.ActualHeight);    
}
```

## <a name="retemplate-the-handwritingview-control"></a>Das Steuerelement HandwritingView-Vorlage

Wie bei allen XAML-Framework-Steuerelementen können Sie die visuelle Struktur und das visuelle Verhalten eines eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) für Ihren Anforderungen anpassen.

Um ein vollständiges Beispiel für das Erstellen einer benutzerdefinierten Vorlage finden Sie unter der Vorgehensweise [Erstellen benutzerdefinierter Transportsteuerelemente](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/custom-transport-controls) oder das [Beispiel für ein benutzerdefiniertes Bearbeitungssteuerelement](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)anzuzeigen.








