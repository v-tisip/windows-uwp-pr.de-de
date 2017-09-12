---
author: Jwmsft
ms.assetid: DA562509-D893-425A-AAE6-B2AE9E9F8A19
Description: "Der Textblock ist das wichtigste Steuerelement zum Anzeigen von schreibgeschütztem Text in Apps."
title: Textblock
label: Text block
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.openlocfilehash: 0ee72a3111fd64fc4cd17a9a0a4283255ce2d3ff
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="text-block"></a><span data-ttu-id="aa217-104">Textblock</span><span class="sxs-lookup"><span data-stu-id="aa217-104">Text block</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

 <span data-ttu-id="aa217-105">Der Textblock ist das wichtigste Steuerelement zum Anzeigen von schreibgeschütztem Text in Apps.</span><span class="sxs-lookup"><span data-stu-id="aa217-105">Text block is the primary control for displaying read-only text in apps.</span></span> <span data-ttu-id="aa217-106">Sie können es zum Anzeigen von einzeiligem oder mehrzeiligem Text, Inlinelinks und Text mit Formatierung, z.B. fett, kursiv oder unterstrichen, verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa217-106">You can use it to display single-line or multi-line text, inline hyperlinks, and text with formatting like bold, italic, or underlined.</span></span>
 
 > <span data-ttu-id="aa217-107">**Wichtige APIs**: [TextBlock-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [Text-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx), [Inlines-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.inlines.aspx)</span><span class="sxs-lookup"><span data-stu-id="aa217-107">**Important APIs**: [TextBlock class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [Text property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx), [Inlines property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.inlines.aspx)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="aa217-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="aa217-108">Is this the right control?</span></span>

<span data-ttu-id="aa217-109">Ein Textblock ist in der Regel einfacher zu verwenden und bietet eine bessere Leistung beim Rendern von Text als ein Rich-Text-Block. Daher wird er in der Regel für App-UI-Text bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="aa217-109">A text block is typically easier to use and provides better text rendering performance than a rich text block, so it's preferred for most app UI text.</span></span> <span data-ttu-id="aa217-110">Sie können über einen Textblock in Ihrer App ganz einfach auf den Text zugreifen und ihn verwenden, indem Sie den Wert der [Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx)-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="aa217-110">You can easily access and use text from a text block in your app by getting the value of the [Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx) property.</span></span> <span data-ttu-id="aa217-111">Er enthält außerdem viele der gleichen Formatierungsoptionen zum Anpassen des Renderns von Text.</span><span class="sxs-lookup"><span data-stu-id="aa217-111">It also provides many of the same formatting options for customizing how your text is rendered.</span></span>

<span data-ttu-id="aa217-112">Sie können zwar Zeilenumbrüche in den Text einfügen, jedoch ist der Textblock zum Anzeigen eines einzelnen Absatzes vorgesehen und unterstützt keinen Texteinzug.</span><span class="sxs-lookup"><span data-stu-id="aa217-112">Although you can put line breaks in the text, text block is designed to display a single paragraph and doesn’t support text indentation.</span></span> <span data-ttu-id="aa217-113">Verwenden Sie **RichTextBlock**, wenn Sie Unterstützung für mehrere Absätze, mehrspaltigen Text, andere komplexe Textlayouts oder Inline-UI-Elemente, z.B. Bilder, benötigen.</span><span class="sxs-lookup"><span data-stu-id="aa217-113">Use a **RichTextBlock** when you need support for multiple paragraphs, multi-column text or other complex text layouts, or inline UI elements like images.</span></span>

<span data-ttu-id="aa217-114">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aa217-114">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="create-a-text-block"></a><span data-ttu-id="aa217-115">Erstellen eines Textblocks</span><span class="sxs-lookup"><span data-stu-id="aa217-115">Create a text block</span></span>

<span data-ttu-id="aa217-116">Im Folgenden wird veranschaulicht, wie Sie ein einfaches TextBlock-Steuerelement definieren und seine Text-Eigenschaft auf eine Zeichenfolge festlegen.</span><span class="sxs-lookup"><span data-stu-id="aa217-116">Here's how to define a simple TextBlock control and set its Text property to a string.</span></span>

```xaml
<TextBlock Text="Hello, world!" />
```

```csharp
TextBlock textBlock1 = new TextBlock();
textBlock1.Text = "Hello, world!";
```

    <TextBlock Text="Hello, world!" />

    TextBlock textBlock1 = new TextBlock();
    textBlock1.Text = "Hello, world!";

### <a name="content-model"></a><span data-ttu-id="aa217-117">Inhaltsmodell</span><span class="sxs-lookup"><span data-stu-id="aa217-117">Content model</span></span>

<span data-ttu-id="aa217-118">Es gibt zwei Eigenschaften, die Sie verwenden können, um einem TextBlock Inhalt hinzuzufügen: [Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx) und [Inlines](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.inlines.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa217-118">There are two properties you can use to add content to a TextBlock: [Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx) and [Inlines](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.inlines.aspx).</span></span>

<span data-ttu-id="aa217-119">Das häufigste Verfahren zum Anzeigen von Text ist das Festlegen der Text-Eigenschaft auf einen Zeichenfolgenwert, wie im vorherigen Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa217-119">The most common way to display text is to set the Text property to a string value, as shown in the previous example.</span></span>

<span data-ttu-id="aa217-120">Sie können auch Inhalte hinzufügen, indem Sie wie hier gezeigt Elemente mit fließendem Inlineinhalt in die TextBox.Inlines-Eigenschaft einfügen.</span><span class="sxs-lookup"><span data-stu-id="aa217-120">You can also add content by placing inline flow content elements in the TextBox.Inlines property, like this.</span></span>
```xaml
<TextBlock><Run>Text can be <Bold>bold</Bold>, <Italic>italic</Italic>, or <Bold><Italic>both</Italic></Bold>.</Run></TextBlock>
```

<span data-ttu-id="aa217-121">Von der Inline-Klasse abgeleitete Elemente, z.B. Bold, Italic, Run, Span und LineBreak, ermöglichen unterschiedliche Formatierungen für unterschiedliche Teile des Texts.</span><span class="sxs-lookup"><span data-stu-id="aa217-121">Elements derived from the Inline class, such as Bold, Italic, Run, Span, and LineBreak, enable different formatting for different parts of the text.</span></span> <span data-ttu-id="aa217-122">Weitere Informationen finden Sie im Abschnitt [Formatieren von Text]().</span><span class="sxs-lookup"><span data-stu-id="aa217-122">For more info, see the [Formatting text]() section.</span></span> <span data-ttu-id="aa217-123">Mit dem Inline-Hyperlink-Element können Sie dem Text einen Link hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa217-123">The inline Hyperlink element lets you add a hyperlink to your text.</span></span> <span data-ttu-id="aa217-124">Durch die Verwendung von Inlines wird jedoch auch das Rendern von Text im schnellen Pfad deaktiviert, wie im nächsten Abschnitt erläutert.</span><span class="sxs-lookup"><span data-stu-id="aa217-124">However, using Inlines also disables fast path text rendering, which is discussed in the next section.</span></span>


## <a name="performance-considerations"></a><span data-ttu-id="aa217-125">Leistungsaspekte</span><span class="sxs-lookup"><span data-stu-id="aa217-125">Performance considerations</span></span>

<span data-ttu-id="aa217-126">XAML verwendet, wenn möglich, einen effizienteren Codepfad für Layouttext.</span><span class="sxs-lookup"><span data-stu-id="aa217-126">Whenever possible, XAML uses a more efficient code path to layout text.</span></span> <span data-ttu-id="aa217-127">Dieser schnelle Pfad verringert die gesamte Arbeitsspeicherauslastung und reduziert erheblich die CPU-Zeit für die Abmessung und Anordnung von Text.</span><span class="sxs-lookup"><span data-stu-id="aa217-127">This fast path both decreases overall memory use and greatly reduces the CPU time to do text measuring and arranging.</span></span> <span data-ttu-id="aa217-128">Dieser schnelle Pfad gilt nur für TextBlock und sollte deshalb nach Möglichkeit RichtTextBlock gegenüber bevorzugt werden.</span><span class="sxs-lookup"><span data-stu-id="aa217-128">This fast path applies only to TextBlock, so it should be preferred when possible over RichTextBlock.</span></span>

<span data-ttu-id="aa217-129">Bestimmte Bedingungen erfordern TextBlock, um auf einen prozessorintensiven Codepfad mit zahlreichen Funktionen zum Rendern von Text zurückzugreifen.</span><span class="sxs-lookup"><span data-stu-id="aa217-129">Certain conditions require TextBlock to fall back to a more feature-rich and CPU intensive code path for text rendering.</span></span> <span data-ttu-id="aa217-130">Damit das Rendern von Text im schnellen Pfad weiterhin ausgeführt wird, beachten Sie beim Festlegen der Eigenschaften unbedingt die im Folgenden aufgeführten Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="aa217-130">To keep text rendering on the fast path, be sure to follow these guidelines when setting the properties listed here.</span></span>
- <span data-ttu-id="aa217-131">[Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx): Die wichtigste Bedingung ist, dass der schnelle Pfad nur dann verwendet wird, wenn Sie Text durch explizites Definieren der Text-Eigenschaft festlegen, entweder in XAML oder im Code (wie in den vorherigen Beispielen dargestellt).</span><span class="sxs-lookup"><span data-stu-id="aa217-131">[Text](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.text.aspx): The most important condition is that the fast path is used only when you set text by explicitly setting the Text property, either in XAML or in code (as shown in the previous examples).</span></span> <span data-ttu-id="aa217-132">Beim Festlegen des Textes über die Inlines-Sammlung von TextBlock (z.B. `<TextBlock>Inline text</TextBlock>` wird der schnelle Pfad aufgrund der potenziellen Komplexität mehrerer Formate deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="aa217-132">Setting the text via TextBlock’s Inlines collection (such as `<TextBlock>Inline text</TextBlock>`) will disable the fast path, due to the potential complexity of multiple formats.</span></span>
- <span data-ttu-id="aa217-133">[CharacterSpacing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.characterspacing.aspx): Nur der Standardwert 0 ist ein schneller Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa217-133">[CharacterSpacing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.characterspacing.aspx): Only the default value of 0 is fast path.</span></span>
- <span data-ttu-id="aa217-134">[TextTrimming](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.texttrimming.aspx): Nur die Werte **None**, **CharacterEllipsis** und **WordEllipsis** sind schnelle Pfade.</span><span class="sxs-lookup"><span data-stu-id="aa217-134">[TextTrimming](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.texttrimming.aspx): Only the **None**, **CharacterEllipsis**, and **WordEllipsis** values are fast path.</span></span> <span data-ttu-id="aa217-135">Der **Clip**-Wert deaktiviert den schnellen Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa217-135">The **Clip** value disables the fast path.</span></span>

> <span data-ttu-id="aa217-136">**Hinweis**&nbsp;&nbsp;Vor Windows 10, Version 1607 wird der schnelle Pfad durch weitere Eigenschaften beeinflusst.</span><span class="sxs-lookup"><span data-stu-id="aa217-136">**Note**&nbsp;&nbsp;Prior to Windows 10, version 1607, additional properties also affect the fast path.</span></span> <span data-ttu-id="aa217-137">Wenn Ihre App unter einer früheren Windows-Version ausgeführt wird, wird Text unter diesen Bedingungen auf dem langsamen Pfad gerendert.</span><span class="sxs-lookup"><span data-stu-id="aa217-137">If your app is run on an earlier version of Windows, these conditions will also cause your text to render on the slow path.</span></span> <span data-ttu-id="aa217-138">Weitere Informationen zu Versionen finden Sie unter „Versionsadaptiver Code“.</span><span class="sxs-lookup"><span data-stu-id="aa217-138">For more info about versions, see Version adaptive code.</span></span>
- <span data-ttu-id="aa217-139">[Typographie](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx): Nur die Standardwerte für die verschiedenen Typographie-Eigenschaften sind schnelle Pfade.</span><span class="sxs-lookup"><span data-stu-id="aa217-139">[Typography](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx): Only the default values for the various Typography properties are fast path.</span></span>
- <span data-ttu-id="aa217-140">[LineStackingStrategy](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.linestackingstrategy.aspx): Wenn [LineHeight](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.lineheight.aspx) nicht 0 ist, deaktivieren die **BaselineToBaseline**- und **MaxHeight**-Werte den schnellen Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa217-140">[LineStackingStrategy](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.linestackingstrategy.aspx): If [LineHeight](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.lineheight.aspx) is not 0, the **BaselineToBaseline** and **MaxHeight** values disable the fast path.</span></span>
- <span data-ttu-id="aa217-141">[IsTextSelectionEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.istextselectionenabled.aspx): Nur **false** ist ein schneller Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa217-141">[IsTextSelectionEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.istextselectionenabled.aspx): Only **false** is fast path.</span></span> <span data-ttu-id="aa217-142">Wenn diese Eigenschaft auf **true** festgelegt wird, wird der schnelle Pfad deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="aa217-142">Setting this property to **true** disables the fast path.</span></span>

<span data-ttu-id="aa217-143">Sie können die [DebugSettings.IsTextPerformanceVisualizationEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.debugsettings.istextperformancevisualizationenabled.aspx)-Eigenschaft während des Debuggens auf **true** festlegen, um festzustellen, ob das Rendern von Text im schnellen Pfad erfolgt.</span><span class="sxs-lookup"><span data-stu-id="aa217-143">You can set the [DebugSettings.IsTextPerformanceVisualizationEnabled](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.debugsettings.istextperformancevisualizationenabled.aspx) property to **true** during debugging to determine whether text is using fast path rendering.</span></span> <span data-ttu-id="aa217-144">Wenn diese Eigenschaft auf „true“ festgelegt ist, wird der Text im schnellen Pfad in Hellgrün angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa217-144">When this property is set to true, the text that is on the fast path displays in a bright green color.</span></span>

><span data-ttu-id="aa217-145">**Tipp**&nbsp;&nbsp;Dieses Feature wird in der folgenden Sitzung aus Build 2015 ausführlich erläutert: [XAML-Leistung – Techniken zum Optimieren der Umgebung einer Universellen Windows-App, die mit XAML erstellt wurde](https://channel9.msdn.com/Events/Build/2015/3-698).</span><span class="sxs-lookup"><span data-stu-id="aa217-145">**Tip**&nbsp;&nbsp;This feature is explained in depth in this session from Build 2015- [XAML Performance: Techniques for Maximizing Universal Windows App Experiences Built with XAML](https://channel9.msdn.com/Events/Build/2015/3-698).</span></span>



<span data-ttu-id="aa217-146">Debugeinstellungen legen Sie in der Regel wie folgt in der [OnLaunched](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.application.onlaunched.aspx)-Methodenüberschreibung in der CodeBehind-Seite für „App.xaml” fest.</span><span class="sxs-lookup"><span data-stu-id="aa217-146">You typically set debug settings in the [OnLaunched](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.application.onlaunched.aspx) method override in the code-behind page for App.xaml, like this.</span></span>
```csharp
protected override void OnLaunched(LaunchActivatedEventArgs e)
{
#if DEBUG
    if (System.Diagnostics.Debugger.IsAttached)
    {
        this.DebugSettings.IsTextPerformanceVisualizationEnabled = true;
    }
#endif

// ...

}
```

<span data-ttu-id="aa217-147">In diesem Beispiel wird die erste TextBlock-Klasse unter Verwendung des schnellen Pfads gerendert, während dies bei der zweiten nicht der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="aa217-147">In this example, the first TextBlock is rendered using the fast path, while the second is not.</span></span>
```xaml
<StackPanel>
    <TextBlock Text="This text is on the fast path."/>
    <TextBlock>This text is NOT on the fast path.</TextBlock>
<StackPanel/>
```

<span data-ttu-id="aa217-148">Wenn Sie diesen XAML-Code im Debugmodus mit der auf „true“ festgelegten IsTextPerformanceVisualizationEnabled-Eigenschaft ausführen, sieht das Ergebnis wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="aa217-148">When you run this XAML in debug mode with IsTextPerformanceVisualizationEnabled set to true, the result looks like this.</span></span>

![Im Debugmodus gerenderter Text](images/text-block-rendering-performance.png)

><span data-ttu-id="aa217-150">**Achtung**&nbsp;&nbsp;Die Farbe von Text, der nicht im schnellen Pfad enthalten ist, wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="aa217-150">**Caution**&nbsp;&nbsp;The color of text that is not on the fast path is not changed.</span></span> <span data-ttu-id="aa217-151">Wenn die Farbe von Text in der App als Hellgrün angegeben ist, wird der Text auch noch in Hellgrün angezeigt, wenn er sich im langsameren Renderingpfad befindet.</span><span class="sxs-lookup"><span data-stu-id="aa217-151">If you have text in your app with its color specified as bright green, it is still displayed in bright green when it's on the slower rendering path.</span></span> <span data-ttu-id="aa217-152">Verwechseln Sie Text, der in der App auf Grün festgelegt ist, nicht mit Text im schnellen Pfad, der aufgrund der Debugeinstellungen grün ist.</span><span class="sxs-lookup"><span data-stu-id="aa217-152">Be careful to not confuse text that is set to green in the app with text that is on the fast path and green because of the debug settings.</span></span>

## <a name="formatting-text"></a><span data-ttu-id="aa217-153">Formatieren von Text</span><span class="sxs-lookup"><span data-stu-id="aa217-153">Formatting text</span></span>

<span data-ttu-id="aa217-154">Obwohl die Text-Eigenschaft Nur-Text speichert, können Sie verschiedene Formatierungsoptionen auf das TextBlock-Steuerelement anwenden, um das Rendern des Texts in der App anzupassen.</span><span class="sxs-lookup"><span data-stu-id="aa217-154">Although the Text property stores plain text, you can apply various formatting options to the TextBlock control to customize how the text is rendered in your app.</span></span> <span data-ttu-id="aa217-155">Sie können Standard-Steuerelementeigenschaften, z.B. FontFamily, FontSize, FontStyle, Foreground und CharacterSpacing festlegen, um das Erscheinungsbild des Texts zu ändern.</span><span class="sxs-lookup"><span data-stu-id="aa217-155">You can set standard control properties like FontFamily, FontSize, FontStyle, Foreground, and CharacterSpacing to change the look of the text.</span></span> <span data-ttu-id="aa217-156">Sie können den Text auch mit Inlinetextelementen und angefügten Typografie-Eigenschaften formatieren.</span><span class="sxs-lookup"><span data-stu-id="aa217-156">You can also use inline text elements and Typography attached properties to format your text.</span></span> <span data-ttu-id="aa217-157">Diese Optionen beeinflussen nur die lokale Anzeige des Texts im TextBlock. Wenn Sie den Text kopieren und z.B. in ein Rich-Text-Steuerelement einfügen, wird daher keine Formatierung angewendet.</span><span class="sxs-lookup"><span data-stu-id="aa217-157">These options affect only how the TextBlock displays the text locally, so if you copy and paste the text into a rich text control, for example, no formatting is applied.</span></span>

><span data-ttu-id="aa217-158">**Hinweis**&nbsp;&nbsp;Beachten Sie, dass Inlinetextelemente und nicht standardmäßige Typografiewerte nicht im schnellen Pfad gerendert werden (dies wurde im vorherigen Abschnitt erläutert).</span><span class="sxs-lookup"><span data-stu-id="aa217-158">**Note**&nbsp;&nbsp;Remember, as noted in the previous section, inline text elements and non-default typography values are not rendered on the fast path.</span></span>


### <a name="inline-elements"></a><span data-ttu-id="aa217-159">Inline-Elemente</span><span class="sxs-lookup"><span data-stu-id="aa217-159">Inline elements</span></span>

<span data-ttu-id="aa217-160">Der [Windows.UI.Xaml.Documents](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.aspx)-Namespace bietet eine Vielzahl von Inlinetextelementen, mit denen Sie Text formatieren können, z.B. Bold, Italic, Run, Span und LineBreak.</span><span class="sxs-lookup"><span data-stu-id="aa217-160">The [Windows.UI.Xaml.Documents](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.aspx) namespace provides a variety of inline text elements that you can use to format your text, such as Bold, Italic, Run, Span, and LineBreak.</span></span>

<span data-ttu-id="aa217-161">Sie können in einem TextBlock auch mehrere Zeichenfolgen anzeigen und jede Zeichenfolge anders formatieren.</span><span class="sxs-lookup"><span data-stu-id="aa217-161">You can display a series of strings in a TextBlock, where each string has different formatting.</span></span> <span data-ttu-id="aa217-162">Dazu verwenden Sie ein Run-Element für die Anzeige der einzelnen Zeichenfolgen mit der zugehörigen Formatierung. Trennen Sie die einzelnen Run-Elemente dann mit einem LineBreak-Element.</span><span class="sxs-lookup"><span data-stu-id="aa217-162">You can do this by using a Run element to display each string with its formatting and by separating each Run element with a LineBreak element.</span></span>

<span data-ttu-id="aa217-163">So definieren Sie unterschiedlich formatierte Textzeichenfolgen in einem TextBlock mit Run-Objekten, die durch einen LineBreak voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="aa217-163">Here's how to define several differently formatted text strings in a TextBlock by using Run objects separated with a LineBreak.</span></span>
```xaml
<TextBlock FontFamily="Segoe UI" Width="400" Text="Sample text formatting runs">
    <LineBreak/>
    <Run Foreground="Gray" FontFamily="Segoe UI Light" FontSize="24">
        Segoe UI Light 24
    </Run>
    <LineBreak/>
    <Run Foreground="Teal" FontFamily="Georgia" FontSize="18" FontStyle="Italic">
        Georgia Italic 18
    </Run>
    <LineBreak/>
    <Run Foreground="Black" FontFamily="Arial" FontSize="14" FontWeight="Bold">
        Arial Bold 14
    </Run>
</TextBlock>
```

<span data-ttu-id="aa217-164">Dies ist das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="aa217-164">Here's the result.</span></span>

![Mit Run-Elementen formatierter Text](images/text-block-run-examples.png)

### <a name="typography"></a><span data-ttu-id="aa217-166">Typografie</span><span class="sxs-lookup"><span data-stu-id="aa217-166">Typography</span></span>

<span data-ttu-id="aa217-167">Die angefügten Eigenschaften der [Typografie](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx)-Klasse ermöglichen den Zugriff auf eine Reihe von Microsoft OpenType-Typografieeigenschaften.</span><span class="sxs-lookup"><span data-stu-id="aa217-167">The attached properties of the [Typography](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx) class provide access to a set of Microsoft OpenType typography properties.</span></span> <span data-ttu-id="aa217-168">Sie können diese angefügten Eigenschaften entweder für das TextBlock-Element oder für einzelne Inlinetextelemente festlegen.</span><span class="sxs-lookup"><span data-stu-id="aa217-168">You can set these attached properties either on the TextBlock, or on individual inline text elements.</span></span> <span data-ttu-id="aa217-169">In diesen Beispielen wird beides gezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa217-169">These examples show both.</span></span>
```xaml
<TextBlock Text="Hello, world!"
           Typography.Capitals="SmallCaps"
           Typography.StylisticSet4="True"/>
```

```csharp
TextBlock textBlock1 = new TextBlock();
textBlock1.Text = "Hello, world!";
Windows.UI.Xaml.Documents.Typography.SetCapitals(textBlock1, FontCapitals.SmallCaps);
Windows.UI.Xaml.Documents.Typography.SetStylisticSet4(textBlock1, true);
```

```xaml
<TextBlock>12 x <Run Typography.Fraction="Slashed">1/3</Run> = 4.</TextBlock>
```


## <a name="related-articles"></a><span data-ttu-id="aa217-170">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="aa217-170">Related articles</span></span>

- [<span data-ttu-id="aa217-171">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="aa217-171">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="aa217-172">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="aa217-172">Guidelines for spell checking</span></span>](spell-checking-and-prediction.md)
- [<span data-ttu-id="aa217-173">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="aa217-173">Adding search</span></span>](search.md)
- [<span data-ttu-id="aa217-174">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="aa217-174">Guidelines for text input</span></span>](text-controls.md)
- [<span data-ttu-id="aa217-175">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="aa217-175">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="aa217-176">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="aa217-176">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)
- [<span data-ttu-id="aa217-177">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="aa217-177">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length(v=vs.110).aspx)
