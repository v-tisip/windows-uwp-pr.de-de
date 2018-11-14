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
ms.openlocfilehash: aa235086f2410fb97ea60e35fb03c586824928a2
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6194174"
---
# <a name="text-input-with-the-handwriting-view"></a><span data-ttu-id="6e847-103">Texteingabe mit der Handschrift-Ansicht</span><span class="sxs-lookup"><span data-stu-id="6e847-103">Text input with the handwriting view</span></span>

![Textfeld wird erweitert, wenn mit einem Stift darauf getippt wird](images/handwritingview/handwritingview2.gif)

<span data-ttu-id="6e847-105">Anpassen der integrierten Handschrift Ansicht für Freihandeingaben für Texteingabe, die von UWP-Textsteuerelemente wie z. B. [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox), [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox)unterstützt, und Steuerelemente von diese z. B. die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="6e847-105">Customize the built-in handwriting view for ink to text input supported by UWP text controls such as the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox), [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox), and controls derived from these such as the [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox).</span></span>

## <a name="overview"></a><span data-ttu-id="6e847-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="6e847-106">Overview</span></span>

<span data-ttu-id="6e847-107">XAML-Texteingabefelder über eine integrierte Unterstützung für Stifteingaben mit [Windows Ink](../input/pen-and-stylus-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="6e847-107">XAML text input boxes feature embedded support for pen input using [Windows Ink](../input/pen-and-stylus-interactions.md).</span></span> <span data-ttu-id="6e847-108">Wenn ein Benutzer in ein Texteingabefeld mit einem Windows-Stift tippt, transformiert das Textfeld in einer Oberfläche Handschrift, anstatt einen separaten Eingabebereich öffnen.</span><span class="sxs-lookup"><span data-stu-id="6e847-108">When a user taps into a text input box using a Windows pen, the text box transforms into a handwriting surface, rather than opening a separate input panel.</span></span>

<span data-ttu-id="6e847-109">Text wird erkannt, während der Benutzer an einer beliebigen Stelle in das Textfeld ein, und ein Kandidat schreibt, dass die Erkennungsergebnisse zeigt.</span><span class="sxs-lookup"><span data-stu-id="6e847-109">Text is recognized as the user writes anywhere in the text box, and a candidate window shows the recognition results.</span></span> <span data-ttu-id="6e847-110">Der Benutzer kann auf ein Ergebnis tippen, um es auszuwählen, oder er kann den Schreibvorgang fortsetzen, um das vorgeschlagene Wort zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="6e847-110">The user can tap a result to choose it, or continue writing to accept the proposed candidate.</span></span> <span data-ttu-id="6e847-111">Die literalen Erkennungsergebnisse (buchstabenweise) sind im Kandidatenfenster enthalten, somit ist die Erkennung nicht auf Wörter in einem Wörterbuch beschränkt.</span><span class="sxs-lookup"><span data-stu-id="6e847-111">The literal (letter-by-letter) recognition results are included in the candidate window, so recognition is not restricted to words in a dictionary.</span></span> <span data-ttu-id="6e847-112">Während der Benutzer schreibt, wird die akzeptierte Texteingabe in ein Schriftzeichen konvertiert, das das Verhalten der natürlichen Schreibweise beibehält.</span><span class="sxs-lookup"><span data-stu-id="6e847-112">As the user writes, the accepted text input is converted to a script font that retains the feel of natural writing.</span></span>

> [!NOTE]
> <span data-ttu-id="6e847-113">Die Handschrift-Ansicht ist standardmäßig aktiviert, aber Sie können pro Steuerelement zu deaktivieren und stattdessen die zu den Text Texteingabebereich zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="6e847-113">The handwriting view is enabled by default, but you can disable it on a per-control basis and revert to the text input panel instead.</span></span>

![Textfeld mit Freihandeingabe und Vorschläge](images/handwritingview/handwritingview-inksuggestion1.gif)

<span data-ttu-id="6e847-115">Ein Benutzer kann seinen Text mithilfe der folgenden Standardgesten und -aktionen bearbeiten:</span><span class="sxs-lookup"><span data-stu-id="6e847-115">A user can edit their text using standard gestures and actions, like these:</span></span>

- <span data-ttu-id="6e847-116">_Durchstreichen_ oder _Ausstreichen_ – Ermöglicht das Durchziehen eines Strichs, um ein Wort oder einen Teil eines Wortes zu löschen.</span><span class="sxs-lookup"><span data-stu-id="6e847-116">_strike through_ or _scratch out_ - draw through to delete a word or part of a word</span></span>
- <span data-ttu-id="6e847-117">_Verknüpfen_ – Zeichnet einen Bogen zwischen Wörtern, um den Abstand zwischen ihnen zu löschen.</span><span class="sxs-lookup"><span data-stu-id="6e847-117">_join_ - draw an arc between words to delete the space between them</span></span>
- <span data-ttu-id="6e847-118">_Einfügen_ – Ermöglicht das Zeichnen eines Caret-Symbols, um ein Leerzeichen einzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e847-118">_insert_ - draw a caret symbol to insert a space</span></span>
- <span data-ttu-id="6e847-119">_Überschreiben_ – Überschreibt vorhandenen Text, um ihn zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="6e847-119">_overwrite_ - write over existing text to replace it</span></span>

![Textfeld mit Freihandeingabe Korrektur](images/handwritingview/handwritingview-inkcorrection1.gif)

## <a name="disable-the-handwriting-view"></a><span data-ttu-id="6e847-121">Deaktivieren der Handschrift-Ansicht</span><span class="sxs-lookup"><span data-stu-id="6e847-121">Disable the handwriting view</span></span>

<span data-ttu-id="6e847-122">Die integrierte Handschrift-Ansicht ist standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6e847-122">The built-in handwriting view is enabled by default.</span></span>

<span data-ttu-id="6e847-123">Sie sollten die Handschrift-Ansicht zu deaktivieren, wenn Sie bereits entsprechende Ink-zu-Text-Funktionalität in Ihrer Anwendung oder der Text-Eingabe-Erfahrung auf irgendeine Art von Formatierung oder Sonderzeichen Zeichen (z. B. eine Registerkarte) über Handschrift nicht verfügbar basiert.</span><span class="sxs-lookup"><span data-stu-id="6e847-123">You might want to disable the handwriting view if you already provide equivalent ink-to-text functionality in your application, or your text input experience relies on some kind of formatting or special character (such as a tab) not available through handwriting.</span></span>

<span data-ttu-id="6e847-124">In diesem Beispiel deaktivieren wir die Handschrift-Ansicht, indem Sie die Eigenschaft [IsHandwritingViewEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.ishandwritingviewenabled) das [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) -Steuerelement auf "false".</span><span class="sxs-lookup"><span data-stu-id="6e847-124">In this example, we disable the handwriting view by setting the [IsHandwritingViewEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.ishandwritingviewenabled) property of the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) control to false.</span></span> <span data-ttu-id="6e847-125">Alle Textsteuerelemente, die Unterstützung der Handschrift Ansicht unterstützen eine ähnliche Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="6e847-125">All text controls that support the handwriting view support a similar property.</span></span>

```xaml
<TextBox Name="SampleTextBox"
    Height="50" Width="500" 
    FontSize="36" FontFamily="Segoe UI" 
    PlaceholderText="Try taping with your pen" 
    IsHandwritingViewEnabled="False">
</TextBox>
```

## <a name="specify-the-alignment-of-the-handwriting-view"></a><span data-ttu-id="6e847-126">Geben Sie die Ausrichtung der Ansicht Handschrift</span><span class="sxs-lookup"><span data-stu-id="6e847-126">Specify the alignment of the handwriting view</span></span>

<span data-ttu-id="6e847-127">Die Handschrift Ansicht befindet sich über das zugrunde liegende Textsteuerelement und angepasst, um den Einstellungen des Benutzers Handschrift aufzunehmen (finden Sie unter \*\*-Einstellungen, die Geräte -> -> Stift & Windows Ink-Handschrift > -> Schriftgrad, wenn Sie direkt in das Textfeld schreiben \*\*).</span><span class="sxs-lookup"><span data-stu-id="6e847-127">The handwriting view is located above the underlying text control and sized to accommodate the user's handwriting preferences (see **Settings -> Devices -> Pen & Windows Ink -> Handwriting -> Size of font when writing directly into text field**).</span></span> <span data-ttu-id="6e847-128">Die Ansicht wird auch automatisch relativ zu den Text-Steuerelement und seine Position innerhalb der app ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="6e847-128">The view is also automatically aligned relative to the text control and its location within the app.</span></span>

<span data-ttu-id="6e847-129">Der Benutzeroberfläche die Anwendung wird nicht umgebrochen, um das Steuerelement größere Rechnung zu tragen, damit das System die Ansicht verdeckt wichtige Elemente der UI beeinträchtigen kann.</span><span class="sxs-lookup"><span data-stu-id="6e847-129">The application UI does not reflow to accommodate the larger control, so the system might cause the view to occlude important UI.</span></span>

<span data-ttu-id="6e847-130">Hier zeigen wir so verwenden Sie die Eigenschaft [PlacementAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.placementalignment) ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) angeben, welche Ankerpunkt für das zugrunde liegende Textsteuerelement verwendet wird, um die Ansicht Handschrift ausrichten.</span><span class="sxs-lookup"><span data-stu-id="6e847-130">Here, we show how to use the [PlacementAlignment](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.placementalignment) property of a [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to specify which anchor on the underlying text control is used to align the handwriting view.</span></span>

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

## <a name="disable-auto-completion-candidates"></a><span data-ttu-id="6e847-131">Deaktivieren der automatischen Vervollständigung Kandidaten</span><span class="sxs-lookup"><span data-stu-id="6e847-131">Disable auto-completion candidates</span></span>

<span data-ttu-id="6e847-132">Der Text Vorschlag Popup ist standardmäßig aktiviert, um eine Liste der wichtigsten Ink Erkennung Kandidaten bereitzustellen, aus denen der Benutzer auswählen kann, für den Fall, dass der obere Kandidat falsch ist.</span><span class="sxs-lookup"><span data-stu-id="6e847-132">The text suggestion popup is enabled by default to provide a list of top ink recognition candidates from which the user can select in case the top candidate is incorrect.</span></span>

<span data-ttu-id="6e847-133">Wenn die Anwendung bereits stabile bereitstellt, benutzerdefinierten Erkennung-Funktionen, die [AreCandidatesEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.arecandidatesenabled) -Eigenschaft können Sie so deaktivieren Sie die integrierte Vorschläge, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="6e847-133">If your application already provides robust, custom recognition functionality, you can use the [AreCandidatesEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.arecandidatesenabled) property to disable the built-in suggestions, as shown in the following example.</span></span>

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

## <a name="use-handwriting-font-preferences"></a><span data-ttu-id="6e847-134">Verwenden Sie Voreinstellungen für Handschrift Schriften</span><span class="sxs-lookup"><span data-stu-id="6e847-134">Use handwriting font preferences</span></span>

<span data-ttu-id="6e847-135">Benutzer kann aus einer vordefinierten Auflistung von Handschrift-basierten Schriftarten zu verwenden, wenn Rendern von Text basierend auf Ink-Erkennung auswählen (finden Sie unter **Einstellungen -> Geräte -> Stift & Windows Ink-Handschrift > -> Schriftart bei Verwendung von Handschrift**).</span><span class="sxs-lookup"><span data-stu-id="6e847-135">A user can choose from a pre-defined collection of handwriting-based fonts to use when rendering text based on ink recognition (see **Settings -> Devices -> Pen & Windows Ink -> Handwriting -> Font when using handwriting**).</span></span>

> [!NOTE]
> <span data-ttu-id="6e847-136">Benutzer können sogar eine Schriftart basierend auf ihren eigenen Handschrift erstellen.</span><span class="sxs-lookup"><span data-stu-id="6e847-136">Users can even create a font based on their own handwriting.</span></span>
> [!VIDEO https://www.youtube.com/embed/YRR4qd4HCw8]

<span data-ttu-id="6e847-137">Die app kann Zugriff auf diese Einstellung und die ausgewählte Schriftart für den erkannten Text im Textfeld-Steuerelement verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e847-137">Your app can access this setting and use the selected font for the recognized text in the text control.</span></span>

<span data-ttu-id="6e847-138">In diesem Beispiel haben wir Lauschen auf das [TextChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.textchanged) -Ereignis ein [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) und ausgewählte Schriftart des Benutzers gelten, wenn die Änderung der Text aus der HandwritingView (oder einer Standardschriftart, falls nicht) stammt.</span><span class="sxs-lookup"><span data-stu-id="6e847-138">In this example, we listen for the [TextChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.textbox.textchanged) event of a [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) and apply the user's selected font if the text change originated from the HandwritingView (or a default font, if not).</span></span>

```csharp
private void SampleTextBox_TextChanged(object sender, TextChangedEventArgs e)
{
    ((TextBox)sender).FontFamily = 
        ((TextBox)sender).HandwritingView.IsOpen ?
            new FontFamily(PenAndInkSettings.GetDefault().FontFamilyName) : 
            new FontFamily("Segoe UI");
}
```

## <a name="access-the-handwritingview-in-composite-controls"></a><span data-ttu-id="6e847-139">Zugriff auf die HandwritingView in zusammengesetzten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="6e847-139">Access the HandwritingView in composite controls</span></span>

<span data-ttu-id="6e847-140">Zusammengesetzte Steuerelemente, die auch, die [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) oder [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox) -Steuerelemente, z. B. [AutoSuggestBox verwenden](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) unterstützen eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview).</span><span class="sxs-lookup"><span data-stu-id="6e847-140">Composite controls that use the [TextBox](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.textbox) or [RichEditBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.richeditbox) controls, such as [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) also support a [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview).</span></span>

<span data-ttu-id="6e847-141">Verwenden Sie die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) in einem zusammengesetzten Steuerelement für den Zugriff auf die [VisualTreeHelper](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper) API.</span><span class="sxs-lookup"><span data-stu-id="6e847-141">To access the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) in a composite control, use the [VisualTreeHelper](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.visualtreehelper) API.</span></span>

<span data-ttu-id="6e847-142">Der folgende XAML-Codeausschnitt zeigt ein [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) -Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="6e847-142">The following XAML snippet displays an [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox) control.</span></span>

```xaml
<AutoSuggestBox Name="SampleAutoSuggestBox" 
    Height="50" Width="500" 
    PlaceholderText="Auto Suggest Example" 
    FontSize="16" FontFamily="Segoe UI"  
    Loaded="SampleAutoSuggestBox_Loaded">
</AutoSuggestBox>
```

<span data-ttu-id="6e847-143">In der entsprechende Code-Behind zeigen wir, wie die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf die [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox)deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="6e847-143">In the corresponding code-behind, we show how to disable the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) on the [AutoSuggestBox](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.autosuggestbox).</span></span>

1. <span data-ttu-id="6e847-144">Zunächst behandeln wir die Anwendung Loaded-Ereignis aufgerufen wird, in denen eine FindInnerTextBox-Funktion zum Durchlaufen der visuellen Struktur zu starten.</span><span class="sxs-lookup"><span data-stu-id="6e847-144">First, we handle the application's Loaded event where we call a FindInnerTextBox function to start the visual tree traversal.</span></span>

    ```csharp
    private void SampleAutoSuggestBox_Loaded(object sender, RoutedEventArgs e)
    {
        if (FindInnerTextBox((AutoSuggestBox)sender))
            autoSuggestInnerTextBox.IsHandwritingViewEnabled = false;
    }
    ```

2. <span data-ttu-id="6e847-145">Wir beginnen dann mit der visuellen Struktur (beginnend mit ein autosuggestbox-Element) in der FindInnerTextBox-Funktion mit einem Aufruf von FindVisualChildByName durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="6e847-145">We then begin iterating through the visual tree (starting at an AutoSuggestBox) in the FindInnerTextBox function with a call to FindVisualChildByName.</span></span>

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

3. <span data-ttu-id="6e847-146">Diese Funktion durchläuft schließlich der visuellen Struktur bis das TextBox-Element abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6e847-146">Finally, this function iterates through the visual tree until the TextBox is retrieved.</span></span>

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

## <a name="reposition-the-handwritingview"></a><span data-ttu-id="6e847-147">Ändern der Position der HandwritingView</span><span class="sxs-lookup"><span data-stu-id="6e847-147">Reposition the HandwritingView</span></span>

<span data-ttu-id="6e847-148">In einigen Fällen müssen Sie sicherstellen, dass die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) UI-Elemente abdeckt, die es andernfalls nicht kann.</span><span class="sxs-lookup"><span data-stu-id="6e847-148">In some cases, you might need to ensure that the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) covers UI elements that it otherwise might not.</span></span>

<span data-ttu-id="6e847-149">Hier erstellen wir ein TextBox-Element, das Diktieren (durch platzieren ein Textfeld und eine Schaltfläche zum Diktieren in einem StackPanel implementiert) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e847-149">Here, we create a TextBox that supports dictation (implemented by placing a TextBox and a dictation button into a StackPanel).</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

<span data-ttu-id="6e847-151">Wie StackPanel jetzt größer als das TextBox-Element ist, kann die [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) aller der zusammengesetzten Cotnrol nicht verdeckt.</span><span class="sxs-lookup"><span data-stu-id="6e847-151">As the StackPanel is now larger than the TextBox, the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) might not occlude all of the composite cotnrol.</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview.png)

<span data-ttu-id="6e847-153">Dieses Problem umgehen, legen Sie die Eigenschaft PlacementTarget der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) auf das UI-Element, an dem es ausgerichtet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6e847-153">To address this, set the PlacementTarget property of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to the UI element to which it should be aligned.</span></span>

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

## <a name="resize-the-handwritingview"></a><span data-ttu-id="6e847-154">Ändern der Größe der HandwritingView</span><span class="sxs-lookup"><span data-stu-id="6e847-154">Resize the HandwritingView</span></span>

<span data-ttu-id="6e847-155">Sie können auch Festlegen der Größe der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview), die beim müssen Sie sicherstellen, dass die Ansicht wichtig UI verdecken nicht hilfreich sein können.</span><span class="sxs-lookup"><span data-stu-id="6e847-155">You can also set the size of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview), which can be useful when you need to ensure the view doesn't occlude important UI.</span></span>

<span data-ttu-id="6e847-156">Wie im vorherigen Beispiel erstellen wir ein TextBox-Element, das Diktieren (durch platzieren ein Textfeld und eine Schaltfläche zum Diktieren in einem StackPanel implementiert) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e847-156">Like the previous example, we create a TextBox that supports dictation (implemented by placing a TextBox and a dictation button into a StackPanel).</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation.png)

<span data-ttu-id="6e847-158">In diesem Fall möchten wir sicherstellen, dass die Schaltfläche Diktat immer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="6e847-158">In this case, we want to ensure that the dictation button is always visible.</span></span>

![TextBox mit diktieren](images/handwritingview/textbox-with-dictation-handwritingview-resize.png)

<span data-ttu-id="6e847-160">Zu diesem Zweck binden wir die MaxWidth-Eigenschaft der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) an die Breite des UI-Element, das es verdeckt sollten.</span><span class="sxs-lookup"><span data-stu-id="6e847-160">To do this, we bind the MaxWidth property of the [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) to the width of the UI element that it should occlude.</span></span>

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

## <a name="reposition-custom-ui"></a><span data-ttu-id="6e847-161">Positionieren Sie benutzerdefinierte Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="6e847-161">Reposition custom UI</span></span>

<span data-ttu-id="6e847-162">Wenn Sie benutzerdefinierte Benutzeroberfläche verfügen, die in Reaktion auf die Texteingabe, z. B. eine Informations-Popup angezeigt wird, müssen Sie die Benutzeroberfläche neu zu positionieren, damit sie die Ansicht Handschrift verdecken nicht.</span><span class="sxs-lookup"><span data-stu-id="6e847-162">If you have custom UI that appears in response to text input, such as an informational popup, you might need to reposition that UI so it doesn't occlude the handwriting view.</span></span>

![TextBox mit benutzerdefinierte Benutzeroberfläche](images/handwritingview/textbox-with-customui.png)

<span data-ttu-id="6e847-164">Das folgende Beispiel zeigt, wie die [Opened](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.opened) [geschlossen](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.closed
)und [SizeChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.sizechanged) der [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) zum Festlegen der Position eines ein [Popup](https://docs.microsoft.com/uwp/api/windows.ui.popups)-Ereignisse überwacht.</span><span class="sxs-lookup"><span data-stu-id="6e847-164">The following example shows how to listen for the [Opened](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.opened), [Closed](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview.closed
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

## <a name="retemplate-the-handwritingview-control"></a><span data-ttu-id="6e847-165">Das Steuerelement HandwritingView Vorlage</span><span class="sxs-lookup"><span data-stu-id="6e847-165">Retemplate the HandwritingView control</span></span>

<span data-ttu-id="6e847-166">Wie bei allen XAML-Framework-Steuerelemente, können Sie die visuelle Struktur und das visuelle Verhalten eines eine [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) für Ihre spezifischen Anforderungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="6e847-166">As with all XAML framework controls, you can customize both the visual structure and visual behavior of a [HandwritingView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.handwritingview) for your specific requirements.</span></span>

<span data-ttu-id="6e847-167">Um ein vollständiges Beispiel für das Erstellen eines benutzerdefinierten Vorlage Auschecken die Vorgehensweise zum [Erstellen benutzerdefinierter Transportsteuerelemente](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/custom-transport-controls) oder das [Beispiel für ein benutzerdefiniertes Bearbeitungssteuerelement](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6e847-167">To see a full example of creating a custom template check out the [Create custom transport controls](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/custom-transport-controls) how-to or the [Custom Edit Control sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>







