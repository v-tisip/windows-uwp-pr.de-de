---
author: Karl-Bridge-Microsoft
Description: Customize the built-in handwriting view for ink to text input that is supported by UWP text controls such as the TextBox, RichEditBox (and controls like the AutoSuggestBox that provide a similar text input experience).
title: Texteingabe mit der Handschrift-Ansicht
label: Text input with the handwriting view
template: detail.hbs
ms.author: kbridge
ms.date: 10/13/18
ms.topic: article
keywords: Windows10, UWP
pm-contact: sewen
design-contact: minah.kim
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 889683d83f1e592e2ce94f3fce63ca0b2c8bbdcb
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5598140"
---
# <a name="text-input-with-the-handwriting-view"></a><span data-ttu-id="07acc-103">Texteingabe mit der Handschrift-Ansicht</span><span class="sxs-lookup"><span data-stu-id="07acc-103">Text input with the handwriting view</span></span>

![Textfeld wird erweitert, wenn mit einem Stift darauf getippt wird](images/handwritingview/handwritingview2.gif)

<span data-ttu-id="07acc-105">Passen Sie die integrierte Handschrift Ansicht für Freihandeingaben für Texteingabe, die von UWP-Textsteuerelemente wie z. B. [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox), [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox)und andere Steuerelemente, die Text input vergleichbar (z. B. die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)) unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="07acc-105">Customize the built-in handwriting view for ink to text input that is supported by UWP text controls such as the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox), [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox), and other controls that provide a similar text input experience (like the [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)).</span></span>

## <a name="overview"></a><span data-ttu-id="07acc-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="07acc-106">Overview</span></span>

<span data-ttu-id="07acc-107">XAML-Texteingabefelder über eine integrierte Unterstützung für Stifteingaben mit [Windows Ink](../input/pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="07acc-107">XAML text input boxes feature embedded support for pen input using [Windows Ink](../input/pen-and-stylus-interactions.md).</span></span> <span data-ttu-id="07acc-108">Wenn ein Benutzer in ein Texteingabefeld mit einem Windows-Stift tippt, transformiert das Textfeld in einer Oberfläche Handschrift, anstatt einen separaten Eingabebereich öffnen.</span><span class="sxs-lookup"><span data-stu-id="07acc-108">When a user taps into a text input box using a Windows pen, the text box transforms into a handwriting surface, rather than opening a separate input panel.</span></span>

<span data-ttu-id="07acc-109">Text wird erkannt, während der Benutzer an einer beliebigen Stelle in das Textfeld ein, und ein Kandidat schreibt, dass Fenster die Erkennungsergebnisse anzeigt.</span><span class="sxs-lookup"><span data-stu-id="07acc-109">Text is recognized as the user writes anywhere in the text box, and a candidate window shows the recognition results.</span></span> <span data-ttu-id="07acc-110">Der Benutzer kann auf ein Ergebnis tippen, um es auszuwählen, oder er kann den Schreibvorgang fortsetzen, um das vorgeschlagene Wort zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="07acc-110">The user can tap a result to choose it, or continue writing to accept the proposed candidate.</span></span> <span data-ttu-id="07acc-111">Die literalen Erkennungsergebnisse (buchstabenweise) sind im Kandidatenfenster enthalten, somit ist die Erkennung nicht auf Wörter in einem Wörterbuch beschränkt.</span><span class="sxs-lookup"><span data-stu-id="07acc-111">The literal (letter-by-letter) recognition results are included in the candidate window, so recognition is not restricted to words in a dictionary.</span></span> <span data-ttu-id="07acc-112">Während der Benutzer schreibt, wird die akzeptierte Texteingabe in ein Schriftzeichen konvertiert, das das Verhalten der natürlichen Schreibweise beibehält.</span><span class="sxs-lookup"><span data-stu-id="07acc-112">As the user writes, the accepted text input is converted to a script font that retains the feel of natural writing.</span></span>

> [!NOTE]
> <span data-ttu-id="07acc-113">Die Handschrift Ansicht ist standardmäßig aktiviert, aber Sie können pro Steuerelement zu deaktivieren und stattdessen auf den Eingabebereich Text zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="07acc-113">The handwriting view is enabled by default, but you can disable it on a per-control basis and revert to the text input panel instead.</span></span>

![Textfeld mit Freihandeingabe und Vorschläge](images/handwritingview/handwritingview-inksuggestion1.gif)

<span data-ttu-id="07acc-115">Ein Benutzer kann seinen Text mithilfe der folgenden Standardgesten und -aktionen bearbeiten:</span><span class="sxs-lookup"><span data-stu-id="07acc-115">A user can edit their text using standard gestures and actions, like these:</span></span>

- <span data-ttu-id="07acc-116">_Durchstreichen_ oder _Ausstreichen_ – Ermöglicht das Durchziehen eines Strichs, um ein Wort oder einen Teil eines Wortes zu löschen.</span><span class="sxs-lookup"><span data-stu-id="07acc-116">_strike through_ or _scratch out_ - draw through to delete a word or part of a word</span></span>
- <span data-ttu-id="07acc-117">_Verknüpfen_ – Zeichnet einen Bogen zwischen Wörtern, um den Abstand zwischen ihnen zu löschen.</span><span class="sxs-lookup"><span data-stu-id="07acc-117">_join_ - draw an arc between words to delete the space between them</span></span>
- <span data-ttu-id="07acc-118">_Einfügen_ – Ermöglicht das Zeichnen eines Caret-Symbols, um ein Leerzeichen einzufügen.</span><span class="sxs-lookup"><span data-stu-id="07acc-118">_insert_ - draw a caret symbol to insert a space</span></span>
- <span data-ttu-id="07acc-119">_Überschreiben_ – Überschreibt vorhandenen Text, um ihn zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="07acc-119">_overwrite_ - write over existing text to replace it</span></span>

![Textfeld mit Freihandeingabe Korrektur](images/handwritingview/handwritingview-inkcorrection1.gif)

## <a name="disable-the-handwriting-view"></a><span data-ttu-id="07acc-121">Deaktivieren Sie die Ansicht Handschrift</span><span class="sxs-lookup"><span data-stu-id="07acc-121">Disable the handwriting view</span></span>

<span data-ttu-id="07acc-122">Die integrierten Handschrift Ansicht ist standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="07acc-122">The built-in handwriting view is enabled by default.</span></span>

<span data-ttu-id="07acc-123">Sie sollten die Handschrift Ansicht deaktivieren, wenn Sie bereits entsprechende Ink-zu-Text-Funktionalität in Ihrer Anwendung oder der Eingabe Text-Erfahrung auf irgendeine Art von Formatierung oder Sonderzeichen Zeichen (z. B. eine Registerkarte) über Handschrift nicht verfügbar basiert.</span><span class="sxs-lookup"><span data-stu-id="07acc-123">You might want to disable the handwriting view if you already provide equivalent ink-to-text functionality in your application, or your text input experience relies on some kind of formatting or special character (such as a tab) not available through handwriting.</span></span>

<span data-ttu-id="07acc-124">In diesem Beispiel deaktivieren wir die Handschrift Ansicht, indem Sie die [IsHandwritingViewEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.ishandwritingviewenabled) -Eigenschaft des [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) -Steuerelements auf "false" festlegen.</span><span class="sxs-lookup"><span data-stu-id="07acc-124">In this example, we disable the handwriting view by setting the [IsHandwritingViewEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.ishandwritingviewenabled) property of the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) control to false.</span></span> <span data-ttu-id="07acc-125">Alle Textsteuerelemente, die Unterstützung der Handschrift Ansicht unterstützen eine ähnliche Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="07acc-125">All text controls that support the handwriting view support a similar property.</span></span>

```xaml
<TextBox Name="SampleTextBox"
    Height="50" Width="500" 
    FontSize="36" FontFamily="Segoe UI" 
    PlaceholderText="Try taping with your pen" 
    IsHandwritingViewEnabled="False">
</TextBox>
```

## <a name="specify-the-alignment-of-the-handwriting-view"></a><span data-ttu-id="07acc-126">Geben Sie die Ausrichtung der Handschrift Ansicht an</span><span class="sxs-lookup"><span data-stu-id="07acc-126">Specify the alignment of the handwriting view</span></span>

<span data-ttu-id="07acc-127">Die Handschrift Ansicht über das zugrunde liegende Textsteuerelement befindet, und angepasst, um den Einstellungen des Benutzers Handschrift aufzunehmen (finden Sie unter \*\*-Einstellungen, die Geräte -> -> Stift & Windows Ink-Handschrift > -> Schriftgrad, wenn Sie direkt in das Textfeld schreiben \*\*).</span><span class="sxs-lookup"><span data-stu-id="07acc-127">The handwriting view is located above the underlying text control and sized to accommodate the user's handwriting preferences (see **Settings -> Devices -> Pen & Windows Ink -> Handwriting -> Size of font when writing directly into text field**).</span></span> <span data-ttu-id="07acc-128">Die Ansicht wird automatisch auch relativ zum Textfeld-Steuerelement und seine Position innerhalb der app ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="07acc-128">The view is also automatically aligned relative to the text control and its location within the app.</span></span>

<span data-ttu-id="07acc-129">Der Benutzeroberfläche die Anwendung wird nicht umgebrochen, um die größeren Steuerelements Rechnung zu tragen, damit das System die Ansicht verdeckt wichtige Elemente der UI beeinträchtigen kann.</span><span class="sxs-lookup"><span data-stu-id="07acc-129">The application UI does not reflow to accommodate the larger control, so the system might cause the view to occlude important UI.</span></span>

<span data-ttu-id="07acc-130">Hier zeigen wir, wie Sie die Eigenschaft [PlacementAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.placementalignment) ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) angeben, welche Ankerpunkt für das zugrunde liegende Textsteuerelement verwendet wird, um die Ansicht Handschrift ausrichten.</span><span class="sxs-lookup"><span data-stu-id="07acc-130">Here, we show how to use the [PlacementAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.placementalignment) property of a [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to specify which anchor on the underlying text control is used to align the handwriting view.</span></span>

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

## <a name="disable-auto-completion-candidates"></a><span data-ttu-id="07acc-131">Deaktivieren der automatischen Vervollständigung Kandidaten</span><span class="sxs-lookup"><span data-stu-id="07acc-131">Disable auto-completion candidates</span></span>

<span data-ttu-id="07acc-132">Das Text Vorschlag Popup ist standardmäßig aktiviert, um eine Liste der wichtigsten Ink Erkennung Kandidaten bereitzustellen aus denen der Benutzer auswählen kann, für den Fall, dass der obere Kandidat nicht korrekt ist.</span><span class="sxs-lookup"><span data-stu-id="07acc-132">The text suggestion popup is enabled by default to provide a list of top ink recognition candidates from which the user can select in case the top candidate is incorrect.</span></span>

<span data-ttu-id="07acc-133">Wenn die Anwendung bereits stabile bereitstellt, benutzerdefinierten Erkennung Funktionen, die [AreCandidatesEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.arecandidatesenabled) -Eigenschaft können Sie so deaktivieren Sie die integrierte Vorschläge, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="07acc-133">If your application already provides robust, custom recognition functionality, you can use the [AreCandidatesEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.arecandidatesenabled) property to disable the built-in suggestions, as shown in the following example.</span></span>

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

## <a name="use-handwriting-font-preferences"></a><span data-ttu-id="07acc-134">Verwenden Sie Voreinstellungen für Handschrift Schriften</span><span class="sxs-lookup"><span data-stu-id="07acc-134">Use handwriting font preferences</span></span>

<span data-ttu-id="07acc-135">Benutzer kann aus einer vordefinierten Auflistung von Handschrift-basierten Schriftarten zu verwenden, wenn Rendern von Text basierend auf Ink Erkennung auswählen (finden Sie unter **Einstellungen -> Geräte -> Stift & Windows Ink -> Handschrift Schriftart bei Verwendung von Handschrift ->**).</span><span class="sxs-lookup"><span data-stu-id="07acc-135">A user can choose from a pre-defined collection of handwriting-based fonts to use when rendering text based on ink recognition (see **Settings -> Devices -> Pen & Windows Ink -> Handwriting -> Font when using handwriting**).</span></span>

> [!NOTE]
> <span data-ttu-id="07acc-136">Benutzer können sogar eine Schriftart basierend auf ihren eigenen Handschrift erstellen.</span><span class="sxs-lookup"><span data-stu-id="07acc-136">Users can even create a font based on their own handwriting.</span></span>
> [!VIDEO https://www.youtube.com/embed/YRR4qd4HCw8]

<span data-ttu-id="07acc-137">Ihre app kann Zugriff auf diese Einstellung und verwenden Sie die ausgewählte Schriftart für den erkannten Text im Textfeld-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="07acc-137">Your app can access this setting and use the selected font for the recognized text in the text control.</span></span>

<span data-ttu-id="07acc-138">In diesem Beispiel haben wir Lauschen auf das [TextChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.textchanged) -Ereignis ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) und des Benutzers ausgewählte Schriftart anwenden, wenn die Änderung der Text aus der HandwritingView (oder einer Standardschriftart, falls nicht) stammt.</span><span class="sxs-lookup"><span data-stu-id="07acc-138">In this example, we listen for the [TextChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.textchanged) event of a [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) and apply the user's selected font if the text change originated from the HandwritingView (or a default font, if not).</span></span>

```csharp
private void SampleTextBox_TextChanged(object sender, TextChangedEventArgs e)
{
    ((TextBox)sender).FontFamily = 
        ((TextBox)sender).HandwritingView.IsOpen ?
            new FontFamily(PenAndInkSettings.GetDefault().FontFamilyName) : 
            new FontFamily("Segoe UI");
}
```

## <a name="access-the-handwritingview-in-composite-controls"></a><span data-ttu-id="07acc-139">Zugriff auf die HandwritingView in zusammengesetzten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="07acc-139">Access the HandwritingView in composite controls</span></span>

<span data-ttu-id="07acc-140">Zusammengesetzte Steuerelemente, die auch, die [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) oder [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox) -Steuerelemente, z. B. [AutoSuggestBox verwenden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) unterstützen eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview).</span><span class="sxs-lookup"><span data-stu-id="07acc-140">Composite controls that use the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) or [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox) controls, such as [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) also support a [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview).</span></span>

<span data-ttu-id="07acc-141">Verwenden Sie zum Zugreifen auf die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) in eines zusammengesetzten Steuerelements [VisualTreeHelper](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper) API.</span><span class="sxs-lookup"><span data-stu-id="07acc-141">To access the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) in a composite control, use the [VisualTreeHelper](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper) API.</span></span>

<span data-ttu-id="07acc-142">Der folgende XAML-Codeausschnitt zeigt ein [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) -Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="07acc-142">The following XAML snippet displays an [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) control.</span></span>

```xaml
<AutoSuggestBox Name="SampleAutoSuggestBox" 
    Height="50" Width="500" 
    PlaceholderText="Auto Suggest Example" 
    FontSize="16" FontFamily="Segoe UI"  
    Loaded="SampleAutoSuggestBox_Loaded">
</AutoSuggestBox>
```

<span data-ttu-id="07acc-143">In der entsprechende Code-Behind zeigen wir, wie die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="07acc-143">In the corresponding code-behind, we show how to disable the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) on the [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox).</span></span>

1. <span data-ttu-id="07acc-144">Erstens behandeln wir die Anwendung Loaded-Ereignis aufgerufen wird, in denen eine FindInnerTextBox-Funktion zum Durchlaufen der visuellen Struktur starten.</span><span class="sxs-lookup"><span data-stu-id="07acc-144">First, we handle the application's Loaded event where we call a FindInnerTextBox function to start the visual tree traversal.</span></span>

    ```csharp
    private void SampleAutoSuggestBox_Loaded(object sender, RoutedEventArgs e)
    {
        if (FindInnerTextBox((AutoSuggestBox)sender))
            autoSuggestInnerTextBox.IsHandwritingViewEnabled = false;
    }
    ```

2. <span data-ttu-id="07acc-145">Wir beginnen dann mit der visuellen Struktur (beginnend mit ein autosuggestbox-Element) in der Funktion FindInnerTextBox mit einem Aufruf von FindVisualChildByName durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="07acc-145">We then begin iterating through the visual tree (starting at an AutoSuggestBox) in the FindInnerTextBox function with a call to FindVisualChildByName.</span></span>

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

3. <span data-ttu-id="07acc-146">Schließlich werden diese Funktion Durchlaufen der visuellen Struktur, bis das TextBox-Element abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="07acc-146">Finally, this function iterates through the visual tree until the TextBox is retrieved.</span></span>

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

## <a name="reposition-the-handwritingview"></a><span data-ttu-id="07acc-147">Ändern der Position der HandwritingView</span><span class="sxs-lookup"><span data-stu-id="07acc-147">Reposition the HandwritingView</span></span>

<span data-ttu-id="07acc-148">In einigen Fällen müssen Sie sicherstellen, dass die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) UI-Elemente abdeckt, die es andernfalls nicht kann.</span><span class="sxs-lookup"><span data-stu-id="07acc-148">In some cases, you might need to ensure that the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) covers UI elements that it otherwise might not.</span></span>

<span data-ttu-id="07acc-149">Hier erstellen wir ein "TextBox", das Diktieren (durch ein "TextBox" und eine Schaltfläche zum Diktieren in einem StackPanel platzieren implementiert) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="07acc-149">Here, we create a TextBox that supports dictation (implemented by placing a TextBox and a dictation button into a StackPanel).</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

<span data-ttu-id="07acc-151">Wie StackPanel jetzt größer als das TextBox-Element ist, kann der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) aller zusammengesetzte Cotnrol nicht verdecken.</span><span class="sxs-lookup"><span data-stu-id="07acc-151">As the StackPanel is now larger than the TextBox, the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) might not occlude all of the composite cotnrol.</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview.png)

<span data-ttu-id="07acc-153">Dieses Problem umgehen, setzen Sie die Eigenschaft PlacementTarget der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf das UI-Element, an dem es ausgerichtet werden soll.</span><span class="sxs-lookup"><span data-stu-id="07acc-153">To address this, set the PlacementTarget property of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to the UI element to which it should be aligned.</span></span>

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

## <a name="resize-the-handwritingview"></a><span data-ttu-id="07acc-154">Ändern der Größe der HandwritingView</span><span class="sxs-lookup"><span data-stu-id="07acc-154">Resize the HandwritingView</span></span>

<span data-ttu-id="07acc-155">Sie können auch festlegen die Größe der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview), die beim müssen Sie sicherstellen, dass die Ansicht wichtige Elemente der UI verdecken nicht hilfreich sein können.</span><span class="sxs-lookup"><span data-stu-id="07acc-155">You can also set the size of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview), which can be useful when you need to ensure the view doesn't occlude important UI.</span></span>

<span data-ttu-id="07acc-156">Wie im vorherigen Beispiel erstellen wir ein "TextBox", das Diktieren (durch ein "TextBox" und eine Schaltfläche zum Diktieren in einem StackPanel platzieren implementiert) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="07acc-156">Like the previous example, we create a TextBox that supports dictation (implemented by placing a TextBox and a dictation button into a StackPanel).</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

<span data-ttu-id="07acc-158">In diesem Fall möchten wir sicherstellen, dass die Schaltfläche "Diktat" immer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="07acc-158">In this case, we want to ensure that the dictation button is always visible.</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview-resize.png)

<span data-ttu-id="07acc-160">Zu diesem Zweck binden wir die Eigenschaft "MaxWidth" die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) an die Breite des UI-Element, das es verdecken sollten.</span><span class="sxs-lookup"><span data-stu-id="07acc-160">To do this, we bind the MaxWidth property of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to the width of the UI element that it should occlude.</span></span>

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

## <a name="reposition-custom-ui"></a><span data-ttu-id="07acc-161">Ändern der Position benutzerdefinierte Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="07acc-161">Reposition custom UI</span></span>

<span data-ttu-id="07acc-162">Wenn Sie benutzerdefinierte Benutzeroberfläche verfügen, die in Reaktion auf die Texteingabe, z. B. eine Informations-Popup angezeigt wird, müssen Sie die Benutzeroberfläche neu zu positionieren, damit sie die Ansicht Handschrift verdecken nicht.</span><span class="sxs-lookup"><span data-stu-id="07acc-162">If you have custom UI that appears in response to text input, such as an informational popup, you might need to reposition that UI so it doesn't occlude the handwriting view.</span></span>

![TextBox mit benutzerdefinierten Benutzeroberfläche](images/handwritingview/textbox-with-customui.png)

<span data-ttu-id="07acc-164">Das folgende Beispiel zeigt, wie die [Opened](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.opened) [geschlossen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.closed
)und [SizeChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.sizechanged) der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) zum Festlegen der Position eines ein [Popup](https://docs.microsoft.com/uwp/api/windows.ui.popups)-Ereignisse überwacht.</span><span class="sxs-lookup"><span data-stu-id="07acc-164">The following example shows how to listen for the [Opened](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.opened), [Closed](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.closed
), and [SizeChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.sizechanged) events of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to set the position of a [Popup](https://docs.microsoft.com/uwp/api/windows.ui.popups).</span></span>

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

## <a name="retemplate-the-handwritingview-control"></a><span data-ttu-id="07acc-165">Das Steuerelement HandwritingView Vorlage</span><span class="sxs-lookup"><span data-stu-id="07acc-165">Retemplate the HandwritingView control</span></span>

<span data-ttu-id="07acc-166">Wie bei allen XAML-Framework-Steuerelementen können Sie die visuelle Struktur und das visuelle Verhalten eines eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) für Ihre spezifischen Anforderungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="07acc-166">As with all XAML framework controls, you can customize both the visual structure and visual behavior of a [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) for your specific requirements.</span></span>

<span data-ttu-id="07acc-167">Um ein vollständiges Beispiel für das Erstellen eines benutzerdefinierten Vorlage Auschecken die Vorgehensweise zum [Erstellen benutzerdefinierter Transportsteuerelemente](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/custom-transport-controls) oder das [Beispiel für ein benutzerdefiniertes Bearbeitungssteuerelement](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="07acc-167">To see a full example of creating a custom template check out the [Create custom transport controls](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/custom-transport-controls) how-to or the [Custom Edit Control sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>







