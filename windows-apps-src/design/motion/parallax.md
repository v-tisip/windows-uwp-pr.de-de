---
author: mijacobs
Description: Use the ParallaxView control to add depth and movement to your app.
title: So verwenden Sie das ParallaxView-Steuerelement, um Tiefe und Bewegung zu Ihrer App hinzuzufügen.
ms.assetid: ''
label: Parallax View
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: conrwi
dev-contact: stpete
doc-status: Published
ms.localizationpriority: high
ms.openlocfilehash: 69bb202a7e13f087ead7ea2a379f803219bbd2d4
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="parallax"></a><span data-ttu-id="fade3-103">Parallax</span><span class="sxs-lookup"><span data-stu-id="fade3-103">Parallax</span></span>

<span data-ttu-id="fade3-104">Parallax ist ein visueller Effekt, bei dem sich Elemente, die näher am Betrachter liegen, schneller als Elemente im Hintergrund bewegen.</span><span class="sxs-lookup"><span data-stu-id="fade3-104">Parallax is a visual effect where items closer to the viewer move faster than items in the background.</span></span> <span data-ttu-id="fade3-105">Parallax erzeugt ein Gefühl von Tiefe, Perspektive und Bewegung.</span><span class="sxs-lookup"><span data-stu-id="fade3-105">Parallax creates a feeling of depth, perspective, and movement.</span></span> <span data-ttu-id="fade3-106">In einer UWP-App können Sie das ParallaxView-Steuerelement verwenden, um einen Parallax-Effekt zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="fade3-106">In a UWP app, you can use the ParallaxView control to create a parallax effect.</span></span>  

> <span data-ttu-id="fade3-107">**Wichtige APIs**: [ParallaxView-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview), [VerticalShift-Eigenschaft](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.VerticalShift), [HorizontalShift-Eigenschaft](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.HorizontalShift)</span><span class="sxs-lookup"><span data-stu-id="fade3-107">**Important APIs**: [ParallaxView class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview), [VerticalShift property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.VerticalShift), [HorizontalShift property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.HorizontalShift)</span></span>

## <a name="examples"></a><span data-ttu-id="fade3-108">Beispiele</span><span class="sxs-lookup"><span data-stu-id="fade3-108">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="fade3-109">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="fade3-109">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="fade3-110">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ParallaxView">die App zu öffnen und ParallaxView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="fade3-110">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ParallaxView">open the app and see the ParallaxView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="fade3-111">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="fade3-111">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="fade3-112">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="fade3-112">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="parallax-and-the-fluent-design-system"></a><span data-ttu-id="fade3-113">Parallax und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="fade3-113">Parallax and the Fluent Design System</span></span>

 <span data-ttu-id="fade3-114">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="fade3-114">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="fade3-115">Parallax ist eine Komponente des Fluent Design-Systems, die Bewegung, Tiefe und Skalierungsmöglichkeiten in Ihre App bringt.</span><span class="sxs-lookup"><span data-stu-id="fade3-115">Parallax is a Fluent Design System component that adds motion, depth, and scale to your app.</span></span> <span data-ttu-id="fade3-116">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="fade3-116">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="how-it-works-in-a-user-interface"></a><span data-ttu-id="fade3-117">Funktionsweise in einer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="fade3-117">How it works in a user interface</span></span>

<span data-ttu-id="fade3-118">In einer Benutzeroberfläche lassen sich Parallax-Effekte erzeugen, indem bei einem Bildlauf oder Schwenken der Benutzeroberfläche verschiedene Objekte unterschiedlich schnell bewegt werden.</span><span class="sxs-lookup"><span data-stu-id="fade3-118">In a UI, you can create a parallax effect by moving different objects at different rates when the UI scrolls or pans.</span></span> <!-- Parallax is an important tool in adding depth to applications along with other techniques like transition animations, perspective tilt, and layering. --> <span data-ttu-id="fade3-119">Um dies zu veranschaulichen, sehen wir uns zwei Inhaltsebenen an, eine Liste und ein Hintergrundbild.</span><span class="sxs-lookup"><span data-stu-id="fade3-119">To demonstrate, let’s look at two layers of content, a list and a background image.</span></span>  <span data-ttu-id="fade3-120">Die Liste befindet sich über dem Hintergrundbild. Dadurch wird bereits der Eindruck vermittelt, dass die Liste sich näher am Betrachter befindet.</span><span class="sxs-lookup"><span data-stu-id="fade3-120">The list is placed on top of the background image which already gives the illusion that the list might be closer to the viewer.</span></span>  <span data-ttu-id="fade3-121">Um jetzt den Parallax-Effekt zu erzielen, soll sich das Objekt, welches uns am nächsten liegt, „schneller” bewegen als das Objekt, welches weiter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="fade3-121">Now, to achieve the parallax effect, we want the object closest to us to travel “faster” than the object that is farther away.</span></span>  <span data-ttu-id="fade3-122">Wenn der Benutzer einen Bildlauf in der Oberfläche durchführt, bewegt sich die Liste schneller als das Hintergrundbild, wodurch eine Illusion von Tiefe erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="fade3-122">As the user scrolls the interface, the list moves at a faster rate than the background image, which creates the illusion of depth.</span></span>

 ![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](images/_Parallax_v2.gif)

 
## <a name="using-the-parallaxview-control-to-create-a-parallax-effect"></a><span data-ttu-id="fade3-124">Verwenden des ParallaxView-Steuerelements zum Erzeugen eines Parallax-Effekts</span><span class="sxs-lookup"><span data-stu-id="fade3-124">Using the ParallaxView control to create a parallax effect</span></span>

<span data-ttu-id="fade3-125">Um einen Parallax-Effekt zu erzeugen, verwenden Sie das [ParallaxView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="fade3-125">To create a parallax effect, you use the [ParallaxView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview) control.</span></span> <span data-ttu-id="fade3-126">Dieses Steuerelement verbindet die Bildlaufposition eines Vordergrundelements, z.B. einer Liste, mit einem Hintergrundelement, z.B. einem Bild.</span><span class="sxs-lookup"><span data-stu-id="fade3-126">This control ties the scroll position of a foreground element, such as a list, to a background element, such as an image.</span></span> <span data-ttu-id="fade3-127">Bei einem Bildlauf durch das Vordergrundelement wird das Hintergrundelement animiert, um einen Parallax-Effekt zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="fade3-127">As you scroll through the foreground element, it animates the background element to create a parallax effect.</span></span> 

<span data-ttu-id="fade3-128">Um das ParallaxView-Steuerelement zu verwenden, stellen Sie ein Quellelement und ein Hintergrundelement bereit und legen für die Eigenschaften [VerticalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.VerticalShift) (für den vertikalen Bildlauf) und/oder [HorizontalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.HorizontalShift) (für den horizontalen Bildlauf) einen größeren Wert als Null fest.</span><span class="sxs-lookup"><span data-stu-id="fade3-128">To use the ParallaxView control, you provide a Source element, a background element, and set the [VerticalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.VerticalShift) (for vertical scrolling) and/or [HorizontalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview.HorizontalShift) (for horizontal scrolling) properties to a value greater than zero.</span></span> 
* <span data-ttu-id="fade3-129">Die Quelleigenschaft akzeptiert einen Verweis auf das Vordergrundelement.</span><span class="sxs-lookup"><span data-stu-id="fade3-129">The Source property takes a reference to the foreground element.</span></span> <span data-ttu-id="fade3-130">Damit der Parallax-Effekt auftritt, sollte sich im Vordergrund ein [ScrollViewer](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer)- oder ein anderes Element befinden, das ein ScrollViewer-Element enthält, z.B. [ListView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listview) oder [RichTextBox](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichEditBox).</span><span class="sxs-lookup"><span data-stu-id="fade3-130">For the parallax effect to occur, the foreground should be a [ScrollViewer](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer) or an element that contains a ScrollViewer, such as a [ListView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listview) or a [RichTextBox](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichEditBox).</span></span> 

* <span data-ttu-id="fade3-131">Um das Hintergrundelement festzulegen, fügen Sie dieses Element als untergeordnetes Element zum ParallaxView-Steuerelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="fade3-131">To set the background element, you add that element as a child of the ParallaxView control.</span></span> <span data-ttu-id="fade3-132">Das Hintergrundelement kann ein beliebiges [UIElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement) sein, z.B. ein [Bild](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Image) oder ein Panel, das zusätzliche UI-Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="fade3-132">The background element can be any [UIElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement), such as an [Image](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Image) or a panel that contains additional UI elements.</span></span> 

<span data-ttu-id="fade3-133">Um einen Parallax-Effekt zu erstellen, muss sich ParallaxView hinter dem Vordergrundelement befinden.</span><span class="sxs-lookup"><span data-stu-id="fade3-133">To create a parallax effect, the ParallaxView must be behind the foreground element.</span></span> <span data-ttu-id="fade3-134">Mithilfe des [Raster](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid)- und des [Canvas](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.canvas)-Panels können Sie Elemente übereinanderstapeln, damit sie sich gut mit dem ParallaxView-Steuerelement verwenden lassen.</span><span class="sxs-lookup"><span data-stu-id="fade3-134">The [Grid](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid) and [Canvas](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.canvas) panels let you layer items on top of each other, so they work well with the ParallaxView control.</span></span>  

<span data-ttu-id="fade3-135">In diesem Beispiel wird ein Parallax-Effekt für eine Liste erstellt:</span><span class="sxs-lookup"><span data-stu-id="fade3-135">This example creates a parallax effect for a list:</span></span>
 
```xaml
<Grid>
    <ParallaxView Source="{x:Bind ForegroundElement}" VerticalShift="50"> 
    
        <!-- Background element --> 
        <Image x:Name="BackgroundImage" Source="Assets/turntable.png"
               Stretch="UniformToFill"/>
    </ParallaxView>
    
    <!-- Foreground element -->
    <ListView x:Name="ForegroundElement">
       <x:String>Item 1</x:String> 
       <x:String>Item 2</x:String> 
       <x:String>Item 3</x:String> 
       <x:String>Item 4</x:String> 
       <x:String>Item 5</x:String>  
       <x:String>Item 6</x:String> 
       <x:String>Item 7</x:String> 
       <x:String>Item 8</x:String> 
       <x:String>Item 9</x:String> 
       <x:String>Item 10</x:String>     
       <x:String>Item 11</x:String> 
       <x:String>Item 13</x:String> 
       <x:String>Item 14</x:String> 
       <x:String>Item 15</x:String> 
       <x:String>Item 16</x:String>     
       <x:String>Item 17</x:String> 
       <x:String>Item 18</x:String> 
       <x:String>Item 19</x:String> 
       <x:String>Item 20</x:String> 
       <x:String>Item 21</x:String>        
    </ListView>
</Grid>
``` 

<span data-ttu-id="fade3-136">ParallaxView passt die Größe des Bilds automatisch an den entsprechenden Parallax-Vorgang an. Sie müssen sich also keine Sorgen machen, dass das Bild beim Bildlauf aus dem Sichtfeld verschwindet.</span><span class="sxs-lookup"><span data-stu-id="fade3-136">The ParallaxView automatically adjusts the size of the image so it works for the parallax operation so you don’t have to worry about the image scrolling out of view.</span></span>

## <a name="customizing-the-parallax-effect"></a><span data-ttu-id="fade3-137">Anpassen des Parallax-Effekts</span><span class="sxs-lookup"><span data-stu-id="fade3-137">Customizing the parallax effect</span></span> 

<span data-ttu-id="fade3-138">Mithilfe der Eigenschaften VerticalShift und HorizontalShift können Sie das Ausmaß des Parallax-Effekts steuern.</span><span class="sxs-lookup"><span data-stu-id="fade3-138">The VerticalShift and HorizontalShift properties let you control degree of the parallax effect.</span></span>

* <span data-ttu-id="fade3-139">Die VerticalShift-Eigenschaft gibt an, wie weit der Hintergrund während des gesamten Parallax-Vorgangs vertikal verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="fade3-139">The VerticalShift property specifies how far we want the background to vertically shift during the entire parallax operation.</span></span> <span data-ttu-id="fade3-140">Der Wert 0 bedeutet, dass der Hintergrund überhaupt nicht verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="fade3-140">A value of 0 means the the background doesn't move at all.</span></span>
* <span data-ttu-id="fade3-141">Die HorizontalShift-Eigenschaft gibt an, wie weit der Hintergrund während des gesamten Parallax-Vorgangs horizontal verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="fade3-141">The HorizontalShift property specifies how far we want the background to horizontally shift during the entire parallax operation.</span></span> <span data-ttu-id="fade3-142">Der Wert 0 bedeutet, dass der Hintergrund überhaupt nicht verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="fade3-142">A value of 0 means the the background doesn't move at all.</span></span>

<span data-ttu-id="fade3-143">Mit höheren Werten lassen sich dramatischere Effekte erzeugen.</span><span class="sxs-lookup"><span data-stu-id="fade3-143">Larger values create a more dramatic effect.</span></span> 

<span data-ttu-id="fade3-144">Die vollständige Liste der Methoden zum Anpassen von Parallax finden Sie in der ParallaxView-Klasse.</span><span class="sxs-lookup"><span data-stu-id="fade3-144">For the complete list of ways to customize parallax, see the ParallaxView class.</span></span> 

## <a name="dos-and-donts"></a><span data-ttu-id="fade3-145">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="fade3-145">Do’s and don’ts</span></span>

- <span data-ttu-id="fade3-146">Verwenden Sie Parallax in Listen mit einem Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="fade3-146">Use parallax in lists with a background image</span></span>
- <span data-ttu-id="fade3-147">Verwenden Sie Parallax gegebenenfalls in ListViewItems, wenn ListViewItems ein Bild enthalten.</span><span class="sxs-lookup"><span data-stu-id="fade3-147">Consider using parallax in ListViewItems when ListViewItems contain an image</span></span>
- <span data-ttu-id="fade3-148">Verwenden Sie es nicht überall. Eine übermäßige Verwendung kann den Effekt verringern.</span><span class="sxs-lookup"><span data-stu-id="fade3-148">Don’t use it everywhere, overuse can diminish its impact</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="fade3-149">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="fade3-149">Get the sample code</span></span>

- <span data-ttu-id="fade3-150">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fade3-150">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="fade3-151">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fade3-151">Related articles</span></span>

- [<span data-ttu-id="fade3-152">ParallaxView-Klasse</span><span class="sxs-lookup"><span data-stu-id="fade3-152">ParallaxView class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview) 
- [<span data-ttu-id="fade3-153">Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="fade3-153">Fluent Design for UWP</span></span>](../fluent-design-system/index.md)
- [<span data-ttu-id="fade3-154">Wissenschaft im System: Fluent Design und Tiefe</span><span class="sxs-lookup"><span data-stu-id="fade3-154">Science in the System: Fluent Design and Depth</span></span>](https://medium.com/microsoft-design/science-in-the-system-fluent-design-and-depth-fb6d0f23a53f)
