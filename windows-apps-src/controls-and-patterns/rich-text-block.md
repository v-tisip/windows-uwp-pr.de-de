---
author: Jwmsft
Description: Verwenden Sie ein RichTextBlock-Element mit RichTextBlockOverflow-Elementen, um erweiterte Textlayouts zu erstellen.
title: RichTextBlock
ms.assetid: E4BE4B1B-418E-4075-88F1-22C09DDF8E45
label: Rich text block
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.openlocfilehash: af9a6883ac20d59c319c663c1f489247e2bb6f2e
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="rich-text-block"></a><span data-ttu-id="3e6d7-104">Rich-Text-Block</span><span class="sxs-lookup"><span data-stu-id="3e6d7-104">Rich text block</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="3e6d7-105">Rich-Text-Blöcke bieten verschiedene Features für erweitertes Textlayout, die Sie verwenden können, wenn Sie Unterstützung für Absätze, Inline-UI-Elemente oder komplexe Textlayouts benötigen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-105">Rich text blocks provide several features for advanced text layout that you can use when you need support for paragraphs, inline UI elements, or complex text layouts.</span></span>

> <span data-ttu-id="3e6d7-106">**Wichtige APIs**: [RichTextBlock-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx), [RichTextBlockOverflow-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx), [Paragraph-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx), [Typography-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx)</span><span class="sxs-lookup"><span data-stu-id="3e6d7-106">**Important APIs**: [RichTextBlock class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx), [RichTextBlockOverflow class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx), [Paragraph class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx), [Typography class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx)</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="3e6d7-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="3e6d7-107">Is this the right control?</span></span>

<span data-ttu-id="3e6d7-108">Verwenden Sie **RichTextBlock**, wenn Sie Unterstützung für mehrere Absätze, mehrspaltige oder andere komplexe Textlayouts oder Inline-UI-Elemente wie Bilder benötigen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-108">Use a **RichTextBlock** when you need support for multiple paragraphs, multi-column or other complex text layouts, or inline UI elements like images.</span></span>

<span data-ttu-id="3e6d7-109">Mit **TextBlock** können Sie die meisten schreibgeschützten Texte in Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-109">Use a **TextBlock** to display most read-only text in your app.</span></span> <span data-ttu-id="3e6d7-110">Sie können es zum Anzeigen von einzeiligem oder mehrzeiligem Text, Inlinelinks und Text mit Formatierung, z. B. fett, kursiv oder unterstrichen, verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-110">You can use it to display single-line or multi-line text, inline hyperlinks, and text with formatting like bold, italic, or underlined.</span></span> <span data-ttu-id="3e6d7-111">TextBlock stellt ein einfacheres Inhaltsmodell bereit. Daher ist er in der Regel einfacher zu verwenden und bietet eine bessere Leistung beim Rendern von Text als RichTextBlock.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-111">TextBlock provides a simpler content model, so it’s typically easier to use, and it can provide better text rendering performance than RichTextBlock.</span></span> <span data-ttu-id="3e6d7-112">Er wird für den meisten UI-Text in Apps bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-112">It's preferred for most app UI text.</span></span> <span data-ttu-id="3e6d7-113">Sie können zwar Zeilenumbrüche in den Text einfügen, jedoch ist TextBlock zum Anzeigen eines einzelnen Absatzes vorgesehen und unterstützt keinen Texteinzug.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-113">Although you can put line breaks in the text, TextBlock is designed to display a single paragraph and doesn’t support text indentation.</span></span>

<span data-ttu-id="3e6d7-114">Weitere Informationen zur Auswahl des passenden Textsteuerelements finden Sie im Artikel über [Textsteuerelemente](text-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3e6d7-114">For more info about choosing the right text control, see the [Text controls](text-controls.md) article.</span></span>

## <a name="create-a-rich-text-block"></a><span data-ttu-id="3e6d7-115">Erstellen eines Rich-Text-Blocks</span><span class="sxs-lookup"><span data-stu-id="3e6d7-115">Create a rich text block</span></span>

<span data-ttu-id="3e6d7-116">Die Inhaltseigenschaft von RichTextBlock ist die [Blocks](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.blocks.aspx)-Eigenschaft, die über das [Paragraph](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx)-Element absatzbasierten Text unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-116">The content property of RichTextBlock is the [Blocks](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.blocks.aspx) property, which supports paragraph based text via the [Paragraph](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx) element.</span></span> <span data-ttu-id="3e6d7-117">Es gibt keine **Text**-Eigenschaft, die Sie für einen bequemen Zugriff auf den Textinhalt des Steuerelements in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-117">It doesn't have a **Text** property that you can use to easily access the control's text content in your app.</span></span> <span data-ttu-id="3e6d7-118">RichTextBlock bietet jedoch verschiedene einzigartige Features, die TextBlock nicht bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-118">However, RichTextBlock provides several unique features that TextBlock doesn’t provide.</span></span> 

<span data-ttu-id="3e6d7-119">Von RichTextBlock unterstützte Features:</span><span class="sxs-lookup"><span data-stu-id="3e6d7-119">RichTextBlock supports:</span></span>
- <span data-ttu-id="3e6d7-120">Mehrere Absätze.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-120">Multiple paragraphs.</span></span> <span data-ttu-id="3e6d7-121">Legen Sie den Einzug für Absätze mit der [TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.textindent.aspx)-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-121">Set the indentation for paragraphs by setting the [TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.textindent.aspx) property.</span></span>
- <span data-ttu-id="3e6d7-122">Inline-UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-122">Inline UI elements.</span></span> <span data-ttu-id="3e6d7-123">Verwenden Sie einen [InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.inlineuicontainer.aspx), um UI-Elemente, z. B. Bilder, inline im Text anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-123">Use an [InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.inlineuicontainer.aspx) to display UI elements, such as images, inline with your text.</span></span>
- <span data-ttu-id="3e6d7-124">Überlaufcontainer.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-124">Overflow containers.</span></span> <span data-ttu-id="3e6d7-125">Verwenden Sie [RichTextBlockOverflow](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx)-Elemente, um mehrspaltige Textlayouts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-125">Use [RichTextBlockOverflow](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx) elements to create multi-column text layouts.</span></span>

### <a name="paragraphs"></a><span data-ttu-id="3e6d7-126">Absätze</span><span class="sxs-lookup"><span data-stu-id="3e6d7-126">Paragraphs</span></span>

<span data-ttu-id="3e6d7-127">Sie definieren mit [Paragraph](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx)-Elementen die Textblöcke, die in einem RichTextBlock-Steuerelement angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-127">You use [Paragraph](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.aspx) elements to define the blocks of text to display within a RichTextBlock control.</span></span> <span data-ttu-id="3e6d7-128">Jeder RichTextBlock sollte mindestens einen Paragraph enthalten.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-128">Every RichTextBlock should include at least one Paragraph.</span></span> 

<span data-ttu-id="3e6d7-129">Mit der [RichTextBlock.TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.textindent.aspx)-Eigenschaft können Sie die Größe des Einzugs für alle Absätze in einem RichTextBlock festlegen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-129">You can set the indent amount for all paragraphs in a RichTextBlock by setting the [RichTextBlock.TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.textindent.aspx) property.</span></span> <span data-ttu-id="3e6d7-130">Sie können diese Einstellung für bestimmte Absätze in einem RichTextBlock überschreiben, indem Sie die [Paragraph.TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.textindent.aspx)-Eigenschaft auf einen anderen Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-130">You can override this setting for specific paragraphs in a RichTextBlock by setting the [Paragraph.TextIndent](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.paragraph.textindent.aspx) property to a different value.</span></span>

```xaml
<RichTextBlock TextIndent="12">
  <Paragraph TextIndent="24">First paragraph.</Paragraph>
  <Paragraph>Second paragraph.</Paragraph>
  <Paragraph>Third paragraph. <Bold>With an inline.</Bold></Paragraph>
</RichTextBlock>
```

### <a name="inline-ui-elements"></a><span data-ttu-id="3e6d7-131">Inline-UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="3e6d7-131">Inline UI elements</span></span>

<span data-ttu-id="3e6d7-132">Mit der [InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.inlineuicontainer.aspx)-Klasse können Sie jedes UIElement inline im Text einbetten.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-132">The [InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.inlineuicontainer.aspx) class lets you embed any UIElement inline with your text.</span></span> <span data-ttu-id="3e6d7-133">Ein gängiges Szenario ist das Einfügen eines Inline-Elements vom Typ „Image“ in den Text. Sie können aber natürlich auch interaktive Elemente wie „Button“ oder „CheckBox“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-133">A common scenario is to place an Image inline with your text, but you can also use interactive elements, like a Button or CheckBox.</span></span>

<span data-ttu-id="3e6d7-134">Wenn Sie mehrere Elemente inline an der gleichen Position einbetten möchten, können Sie ein Panel als einzelnes untergeordnetes InlineUIContainer-Element verwenden und dann mehrere Elemente in diesem Panel platzieren.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-134">If you want to embed more than one element inline in the same position, consider using a panel as the single InlineUIContainer child, and then place the multiple elements within that panel.</span></span>

<span data-ttu-id="3e6d7-135">In diesem Beispiel wird veranschaulicht, wie mithilfe eines InlineUIContainer ein Bild in einen RichTextBlock eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-135">This example shows how to use an InlineUIContainer to insert an image into a RichTextBlock.</span></span> 

```xaml
<RichTextBlock>
    <Paragraph>
        <Italic>This is an inline image.</Italic>
        <InlineUIContainer>
            <Image Source="Assets/Square44x44Logo.png" Height="30" Width="30"/>
        </InlineUIContainer>
        Mauris auctor tincidunt auctor.
    </Paragraph>
</RichTextBlock>
```

## <a name="overflow-containers"></a><span data-ttu-id="3e6d7-136">Überlaufcontainer</span><span class="sxs-lookup"><span data-stu-id="3e6d7-136">Overflow containers</span></span>

<span data-ttu-id="3e6d7-137">Sie können einen RichTextBlock mit [RichTextBlockOverflow](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx)-Elementen verwenden, um mehrspaltige Seitenlayouts oder andere erweiterte Seitenlayouts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-137">You can use a RichTextBlock with [RichTextBlockOverflow](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblockoverflow.aspx) elements to create multi-column or other advanced page layouts.</span></span> <span data-ttu-id="3e6d7-138">Der Inhalt für ein RichTextBlockOverflow-Element stammt immer aus einem RichTextBlock-Element.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-138">The content for a RichTextBlockOverflow element always comes from a RichTextBlock element.</span></span> <span data-ttu-id="3e6d7-139">Sie verknüpfen RichTextBlockOverflow-Elemente, indem Sie sie als OverflowContentTarget eines RichTextBlock-Elements oder eines anderen RichTextBlockOverflow-Elements festlegen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-139">You link RichTextBlockOverflow elements by setting them as the OverflowContentTarget of a RichTextBlock or another RichTextBlockOverflow.</span></span>

<span data-ttu-id="3e6d7-140">Hier ist ein einfaches Beispiel, in dem ein zweispaltiges Layout erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-140">Here's a simple example that creates a two column layout.</span></span> <span data-ttu-id="3e6d7-141">Ein komplexeres Beispiel finden Sie im Abschnitt „Beispiele“.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-141">See the Examples section for a more complex example.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition/>
        <ColumnDefinition/>
    </Grid.ColumnDefinitions>
    <RichTextBlock Grid.Column="0" 
                   OverflowContentTarget="{Binding ElementName=overflowContainer}" >
        <Paragraph>
            Proin ac metus at quam luctus ultricies.
        </Paragraph>
    </RichTextBlock>
    <RichTextBlockOverflow x:Name="overflowContainer" Grid.Column="1"/>
</Grid>
```

## <a name="formatting-text"></a><span data-ttu-id="3e6d7-142">Formatieren von Text</span><span class="sxs-lookup"><span data-stu-id="3e6d7-142">Formatting text</span></span>

<span data-ttu-id="3e6d7-143">Obwohl der RichTextBlock Nur-Text speichert, können Sie verschiedene Formatierungsoptionen anwenden, um das Rendern des Texts in der App anzupassen.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-143">Although the RichTextBlock stores plain text, you can apply various formatting options to customize how the text is rendered in your app.</span></span> <span data-ttu-id="3e6d7-144">Sie können Standard-Steuerelementeigenschaften, z. B. FontFamily, FontSize, FontStyle, Foreground und CharacterSpacing, festlegen, um das Erscheinungsbild des Texts zu ändern.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-144">You can set standard control properties like FontFamily, FontSize, FontStyle, Foreground, and CharacterSpacing to change the look of the text.</span></span> <span data-ttu-id="3e6d7-145">Sie können den Text auch mit Inlinetextelementen und angefügten Typography-Eigenschaften formatieren.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-145">You can also use inline text elements and Typography attached properties to format your text.</span></span> <span data-ttu-id="3e6d7-146">Diese Optionen beeinflussen nur die lokale Anzeige des Texts im RichTextBlock. Wenn Sie den Text kopieren und z. B. in ein Rich-Text-Steuerelement einfügen, wird daher keine Formatierung angewendet.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-146">These options affect only how the RichTextBlock displays the text locally, so if you copy and paste the text into a rich text control, for example, no formatting is applied.</span></span>

### <a name="inline-elements"></a><span data-ttu-id="3e6d7-147">Inline-Elemente</span><span class="sxs-lookup"><span data-stu-id="3e6d7-147">Inline elements</span></span>

<span data-ttu-id="3e6d7-148">Der [Windows.UI.Xaml.Documents](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.aspx)-Namespace bietet eine Vielzahl von Inlinetextelementen, mit denen Sie Text formatieren können, z. B. Bold, Italic, Run, Span und LineBreak.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-148">The [Windows.UI.Xaml.Documents](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.aspx) namespace provides a variety of inline text elements that you can use to format your text, such as Bold, Italic, Run, Span, and LineBreak.</span></span> <span data-ttu-id="3e6d7-149">Ein typisches Verfahren zum Formatieren von Textabschnitten ist das Einfügen des Texts in ein Run-Element oder Span-Element und das anschließende Festlegen der Eigenschaften für das Element.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-149">A typical way to apply formatting to sections of text is to place the text in a Run or Span element, and then set properties on that element.</span></span>

<span data-ttu-id="3e6d7-150">Dies ist ein Paragraph, in dem der erste Ausdruck als fett formatierter blauer Text mit dem Schriftgrad 16 pt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-150">Here's a Paragraph with the first phrase shown in bold, blue, 16pt text.</span></span>

```xaml
<Paragraph>
    <Bold><Span Foreground="DarkSlateBlue" FontSize="16">Lorem ipsum dolor sit amet</Span></Bold>
    , consectetur adipiscing elit.
</Paragraph>
```

### <a name="typography"></a><span data-ttu-id="3e6d7-151">Typografie</span><span class="sxs-lookup"><span data-stu-id="3e6d7-151">Typography</span></span>

<span data-ttu-id="3e6d7-152">Die angefügten Eigenschaften der [Typography](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx)-Klasse ermöglichen den Zugriff auf eine Reihe von Microsoft OpenType-Typografieeigenschaften.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-152">The attached properties of the [Typography](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.documents.typography.aspx) class provide access to a set of Microsoft OpenType typography properties.</span></span> <span data-ttu-id="3e6d7-153">Sie können diese angefügten Eigenschaften entweder für den RichTextBlock oder für einzelne Inlinetextelemente festlegen, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-153">You can set these attached properties either on the RichTextBlock, or on individual inline text elements, as shown here.</span></span>

```xaml
<RichTextBlock Typography.StylisticSet4="True">
    <Paragraph>
        <Span Typography.Capitals="SmallCaps">Lorem ipsum dolor sit amet</Span>
        , consectetur adipiscing elit.
    </Paragraph>
</RichTextBlock>
```

## <a name="recommendations"></a><span data-ttu-id="3e6d7-154">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="3e6d7-154">Recommendations</span></span>

<span data-ttu-id="3e6d7-155">Siehe „Typografie“ und „Richtlinien für Schriftarten“.</span><span class="sxs-lookup"><span data-stu-id="3e6d7-155">See Typography and Guidelines for fonts.</span></span>



## <a name="related-articles"></a><span data-ttu-id="3e6d7-156">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="3e6d7-156">Related articles</span></span>

[<span data-ttu-id="3e6d7-157">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="3e6d7-157">Text controls</span></span>](text-controls.md)

**<span data-ttu-id="3e6d7-158">Für Designer</span><span class="sxs-lookup"><span data-stu-id="3e6d7-158">For designers</span></span>**
- [<span data-ttu-id="3e6d7-159">Richtlinien für die Rechtschreibprüfung</span><span class="sxs-lookup"><span data-stu-id="3e6d7-159">Guidelines for spell checking</span></span>](spell-checking-and-prediction.md)
- [<span data-ttu-id="3e6d7-160">Hinzufügen von Suchfunktionen</span><span class="sxs-lookup"><span data-stu-id="3e6d7-160">Adding search</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465231)
- [<span data-ttu-id="3e6d7-161">Richtlinien für die Texteingabe</span><span class="sxs-lookup"><span data-stu-id="3e6d7-161">Guidelines for text input</span></span>](text-controls.md)

**<span data-ttu-id="3e6d7-162">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="3e6d7-162">For developers (XAML)</span></span>**
- [<span data-ttu-id="3e6d7-163">TextBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="3e6d7-163">TextBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209683)
- [<span data-ttu-id="3e6d7-164">Windows.UI.Xaml.Controls PasswordBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="3e6d7-164">Windows.UI.Xaml.Controls PasswordBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br227519)


**<span data-ttu-id="3e6d7-165">Für Entwickler (Sonstige)</span><span class="sxs-lookup"><span data-stu-id="3e6d7-165">For developers (other)</span></span>**
- [<span data-ttu-id="3e6d7-166">StringLength-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3e6d7-166">String.Length property</span></span>](https://msdn.microsoft.com/library/system.string.length(v=vs.110).aspx)
