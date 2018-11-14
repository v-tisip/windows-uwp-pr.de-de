---
author: jwmsft
title: xPhase-Attribut
description: Verwenden Sie xPhase mit der xBind-Markuperweiterung zum inkrementellen Rendern von ListView- und GridView-Elementen und zur Verbesserung des Verschiebens.
ms.assetid: BD17780E-6A34-4A38-8D11-9703107E247E
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 17ee99553b5713acb1917ccb697abb2387d00da2
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6262974"
---
# <a name="xphase-attribute"></a><span data-ttu-id="d4508-104">x:Phase-Attribut</span><span class="sxs-lookup"><span data-stu-id="d4508-104">x:Phase attribute</span></span>


<span data-ttu-id="d4508-105">Verwenden Sie **x:Phase** mit der [{x:Bind}-Markuperweiterung](x-bind-markup-extension.md) zum inkrementellen Rendern von [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) und [**GridView**](https://msdn.microsoft.com/library/windows/apps/br242705)-Elementen und zur Verbesserung des Verschiebungserlebnisses.</span><span class="sxs-lookup"><span data-stu-id="d4508-105">Use **x:Phase** with the [{x:Bind} markup extension](x-bind-markup-extension.md) to render [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) and [**GridView**](https://msdn.microsoft.com/library/windows/apps/br242705) items incrementally and improve the panning experience.</span></span> <span data-ttu-id="d4508-106">**x:Phase** bietet eine deklarative Möglichkeit, die gleiche Wirkung zu erzielen wie bei Verwendung des [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/dn298914)-Ereignisses zum manuellen Steuern des Renderns von Listenelementen.</span><span class="sxs-lookup"><span data-stu-id="d4508-106">**x:Phase** provides a declarative way of achieving the same effect as using the [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/dn298914) event to manually control the rendering of list items.</span></span> <span data-ttu-id="d4508-107">Weitere Informationen finden Sie auch unter [Inkrementelles Aktualisieren von ListView- und GridView-Elementen](../debug-test-perf/optimize-gridview-and-listview.md#update-items-incrementally).</span><span class="sxs-lookup"><span data-stu-id="d4508-107">Also see [Update ListView and GridView items incrementally](../debug-test-perf/optimize-gridview-and-listview.md#update-items-incrementally).</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="d4508-108">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="d4508-108">XAML attribute usage</span></span>


``` syntax
<object x:Phase="PhaseValue".../>
```

## <a name="xaml-values"></a><span data-ttu-id="d4508-109">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="d4508-109">XAML values</span></span>


| <span data-ttu-id="d4508-110">Benennung</span><span class="sxs-lookup"><span data-stu-id="d4508-110">Term</span></span> | <span data-ttu-id="d4508-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d4508-111">Description</span></span> |
|------|-------------|
| <span data-ttu-id="d4508-112">PhaseValue</span><span class="sxs-lookup"><span data-stu-id="d4508-112">PhaseValue</span></span> | <span data-ttu-id="d4508-113">Eine Zahl, die die Phase gibt an, in der das Element verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="d4508-113">A number that indicates the phase in which the element will be processed.</span></span> <span data-ttu-id="d4508-114">Der Standardwert ist 0.</span><span class="sxs-lookup"><span data-stu-id="d4508-114">The default is 0.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="d4508-115">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="d4508-115">Remarks</span></span>

<span data-ttu-id="d4508-116">Wenn eine Liste mit Toucheingabe oder mit dem Mausrad schnell verschoben wird, ist die Liste je nach Komplexität der Datenvorlage möglicherweise nicht in der Lage, Elemente schnell genug zu rendern, um mit der Geschwindigkeit des Bildlaufs Schritt zu halten.</span><span class="sxs-lookup"><span data-stu-id="d4508-116">If a list is panned fast with touch, or using the mouse wheel, then depending on the complexity of the data template, the list may not be able to render items fast enough to keep up with the speed of scrolling.</span></span> <span data-ttu-id="d4508-117">Das gilt besonders für ein tragbares Gerät mit einer energieeffizienten CPU, z. B. ein Telefon oder ein Tablet.</span><span class="sxs-lookup"><span data-stu-id="d4508-117">This is particularly true for a portable device with a power-efficient CPU such as a phone or a tablet.</span></span>

<span data-ttu-id="d4508-118">Phasing ermöglicht das inkrementelle Rendern der Datenvorlage, sodass der Inhalt priorisiert werden kann und die wichtigsten Elemente zuerst gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="d4508-118">Phasing enables incremental rendering of the data template so that the contents can be prioritized, and the most important elements rendered first.</span></span> <span data-ttu-id="d4508-119">Dadurch kann die Liste beim schnellen Verschieben für jedes Element einige Inhalte anzeigen und mehr Elemente für jede Vorlage rendern, falls die Zeit dies zulässt.</span><span class="sxs-lookup"><span data-stu-id="d4508-119">This enables the list to show some content for each item if panning fast, and will render more elements of each template as time permits.</span></span>

## <a name="example"></a><span data-ttu-id="d4508-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d4508-120">Example</span></span>

```xml
<DataTemplate x:Key="PhasedFileTemplate" x:DataType="model:FileItem">
    <Grid Width="200" Height="80">
        <Grid.ColumnDefinitions>
           <ColumnDefinition Width="75" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>
        <Image Grid.RowSpan="4" Source="{x:Bind ImageData}" MaxWidth="70" MaxHeight="70" x:Phase="3"/>
        <TextBlock Text="{x:Bind DisplayName}" Grid.Column="1" FontSize="12"/>
        <TextBlock Text="{x:Bind prettyDate}"  Grid.Column="1"  Grid.Row="1" FontSize="12" x:Phase="1"/>
        <TextBlock Text="{x:Bind prettyFileSize}"  Grid.Column="1"  Grid.Row="2" FontSize="12" x:Phase="2"/>
        <TextBlock Text="{x:Bind prettyImageSize}"  Grid.Column="1"  Grid.Row="3" FontSize="12" x:Phase="2"/>
    </Grid>
</DataTemplate>
```

<span data-ttu-id="d4508-121">Die Datenvorlage beschreibt vier Phasen:</span><span class="sxs-lookup"><span data-stu-id="d4508-121">The data template describes 4 phases:</span></span>

1.  <span data-ttu-id="d4508-122">Stellt den DisplayName-Textblock dar.</span><span class="sxs-lookup"><span data-stu-id="d4508-122">Presents the DisplayName text block.</span></span> <span data-ttu-id="d4508-123">Alle Steuerelemente ohne Phase werden implizit als zur Phase 0 zugehörig betrachtet.</span><span class="sxs-lookup"><span data-stu-id="d4508-123">All controls without a phase specified will be implicitly considered to be part of phase 0.</span></span>
2.  <span data-ttu-id="d4508-124">Zeigt den prettyDate-Textblock.</span><span class="sxs-lookup"><span data-stu-id="d4508-124">Shows the prettyDate text block.</span></span>
3.  <span data-ttu-id="d4508-125">Zeigt die prettyFileSize- und prettyImageSize-Textblöcke.</span><span class="sxs-lookup"><span data-stu-id="d4508-125">Shows the prettyFileSize and prettyImageSize text blocks.</span></span>
4.  <span data-ttu-id="d4508-126">Zeigt das Bild.</span><span class="sxs-lookup"><span data-stu-id="d4508-126">Shows the image.</span></span>

<span data-ttu-id="d4508-127">Phasing ist eine Funktion von [{x:Bind}](x-bind-markup-extension.md), die aus [**ListViewBase**](https://msdn.microsoft.com/library/windows/apps/br242879) abgeleitete Steuerelemente verwendet und die Elementvorlage für die Datenbindung inkrementell verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d4508-127">Phasing is a feature of [{x:Bind}](x-bind-markup-extension.md) that works with controls derived from [**ListViewBase**](https://msdn.microsoft.com/library/windows/apps/br242879) and that incrementally processes the item template for data binding.</span></span> <span data-ttu-id="d4508-128">Beim Rendern von Listenelementen stellt **ListViewBase** eine einzelne Phase für alle Elemente in der Ansicht dar, bevor der Wechsel zur nächsten Phase erfolgt.</span><span class="sxs-lookup"><span data-stu-id="d4508-128">When rendering list items, **ListViewBase** renders a single phase for all items in the view before moving onto the next phase.</span></span> <span data-ttu-id="d4508-129">Das Rendern wird in zeitlich unterteilten Stapeln ausgeführt, damit die erforderliche Arbeit bei einem Listenbildlauf neu analysiert und nicht für Elemente ausgeführt werden kann, die nicht mehr sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="d4508-129">The rendering work is performed in time-sliced batches so that as the list is scrolled, the work required can be re-assessed, and not performed for items that are no longer visible.</span></span>

<span data-ttu-id="d4508-130">Das **x:Phase**-Attribut kann für jedes Element in einer Datenvorlage, die [{x:Bind}](x-bind-markup-extension.md) verwendet, angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d4508-130">The **x:Phase** attribute can be specified on any element in a data template that uses [{x:Bind}](x-bind-markup-extension.md).</span></span> <span data-ttu-id="d4508-131">Wenn ein Element eine andere Phase als 0 aufweist, wird das Element aus der Ansicht ausgeblendet (über **Opacity**, nicht über **Visibility**), bis diese Phase verarbeitet wird und Bindungen aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="d4508-131">When an element has a phase other than 0, the element will be hidden from view (via **Opacity**, not **Visibility**) until that phase is processed and bindings are updated.</span></span> <span data-ttu-id="d4508-132">Wenn für ein von [**ListViewBase**](https://msdn.microsoft.com/library/windows/apps/br242879) abgeleitetes Steuerelement ein Bildlauf durchgeführt wird, verwendet es die Elementvorlagen von Elementen, die nicht mehr auf dem Bildschirm sind, erneut, um die neu sichtbaren Elemente zu rendern.</span><span class="sxs-lookup"><span data-stu-id="d4508-132">When a [**ListViewBase**](https://msdn.microsoft.com/library/windows/apps/br242879)-derived control is scrolled, it will recycle the item templates from items that are no longer on screen to render the newly visible items.</span></span> <span data-ttu-id="d4508-133">UI-Elemente in der Vorlage behalten ihre alten Werte bei, bis sie erneut an Daten gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="d4508-133">UI elements within the template will retain their old values until they are data-bound again.</span></span> <span data-ttu-id="d4508-134">Phasing verursacht das Verzögern dieses Datenbindungsschritts, sodass Phasing die UI-Elemente für den Fall, dass sie veraltet sind, ausblenden muss.</span><span class="sxs-lookup"><span data-stu-id="d4508-134">Phasing causes that data-binding step to be delayed, and therefore phasing needs to hide the UI elements in case they are stale.</span></span>

<span data-ttu-id="d4508-135">Für jedes UI-Element darf nur eine Phase angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d4508-135">Each UI element may have only one phase specified.</span></span> <span data-ttu-id="d4508-136">Diese gilt dann für alle Bindungen des Elements.</span><span class="sxs-lookup"><span data-stu-id="d4508-136">If so, that will apply to all bindings on the element.</span></span> <span data-ttu-id="d4508-137">Wenn keine Phase angegeben ist, wird die Phase 0 angenommen.</span><span class="sxs-lookup"><span data-stu-id="d4508-137">If a phase is not specified, phase 0 is assumed.</span></span>

<span data-ttu-id="d4508-138">Phasennummern müssen nicht fortlaufend sein und sind mit den Wert der [**ContainerContentChangingEventArgs.Phase**](https://msdn.microsoft.com/library/windows/apps/dn298493) identisch.</span><span class="sxs-lookup"><span data-stu-id="d4508-138">Phase numbers do not need to be contiguous and are the same as the value of [**ContainerContentChangingEventArgs.Phase**](https://msdn.microsoft.com/library/windows/apps/dn298493).</span></span> <span data-ttu-id="d4508-139">Das [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/dn298914)-Ereignis wird für jede Phase vor der Verarbeitung der **x:Phase**-Bindungen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d4508-139">The [**ContainerContentChanging**](https://msdn.microsoft.com/library/windows/apps/dn298914) event will be raised for each phase before the **x:Phase** bindings are processed.</span></span>

<span data-ttu-id="d4508-140">Phasing wirkt sich nur auf [{x:Bind}](x-bind-markup-extension.md) -Bindungen aus, nicht auf [{Binding}](binding-markup-extension.md)-Bindungen.</span><span class="sxs-lookup"><span data-stu-id="d4508-140">Phasing only affects [{x:Bind}](x-bind-markup-extension.md) bindings, not [{Binding}](binding-markup-extension.md) bindings.</span></span>

<span data-ttu-id="d4508-141">Phasing gilt nur, wenn die Elementvorlage mithilfe eines Steuerelements gerendert wird, das Phasing erkennt.</span><span class="sxs-lookup"><span data-stu-id="d4508-141">Phasing will only apply when the item template is rendered using a control that is aware of phasing.</span></span> <span data-ttu-id="d4508-142">Für Windows 10 bedeutet dies, [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) und [**GridView**](https://msdn.microsoft.com/library/windows/apps/br242705).</span><span class="sxs-lookup"><span data-stu-id="d4508-142">For Windows10, that means [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) and [**GridView**](https://msdn.microsoft.com/library/windows/apps/br242705).</span></span> <span data-ttu-id="d4508-143">Phasing gilt nicht für Datenvorlagen, die in anderen Elementsteuerelementen verwendet werden, oder für andere Szenarien, wie zum Beispiel die Abschnitte [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/br209369) oder [**Hub**](https://msdn.microsoft.com/library/windows/apps/dn251843) – in diesen Fällen werden alle UI-Elemente auf einmal an Daten gebunden.</span><span class="sxs-lookup"><span data-stu-id="d4508-143">Phasing will not apply to data templates used in other item controls, or for other scenarios such as [**ContentTemplate**](https://msdn.microsoft.com/library/windows/apps/br209369) or [**Hub**](https://msdn.microsoft.com/library/windows/apps/dn251843) sections—in those cases, all the UI elements will be data bound at once.</span></span>

