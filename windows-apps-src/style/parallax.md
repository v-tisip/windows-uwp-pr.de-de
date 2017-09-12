---
author: mijacobs
Description: "Verwenden Sie das ParallaxView-Steuerelement, um Tiefe und Bewegung zu Ihrer App hinzuzufügen."
title: "Richtlinien für die Verwendung des ParallaxView-Steuerelements"
ms.assetid: 
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
ms.openlocfilehash: b99b4ca3f3e16a127472633fc3c800db2d773b8c
ms.sourcegitcommit: 0d5b3daddb3ae74f91178c58e35cbab33854cb7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="parallax"></a><span data-ttu-id="7c593-104">Parallax</span><span class="sxs-lookup"><span data-stu-id="7c593-104">Parallax</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c593-105">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden.</span><span class="sxs-lookup"><span data-stu-id="7c593-105">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="7c593-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="7c593-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="7c593-107">Parallax ist ein visueller Effekt, bei dem sich Elemente, die näher am Betrachter liegen, schneller als Elemente im Hintergrund bewegen.</span><span class="sxs-lookup"><span data-stu-id="7c593-107">Parallax is a visual effect where items closer to the viewer move faster than items in the background.</span></span> <span data-ttu-id="7c593-108">Parallax erzeugt ein Gefühl von Tiefe, Perspektive und Bewegung.</span><span class="sxs-lookup"><span data-stu-id="7c593-108">Parallax creates a feeling of depth, perspective, and movement.</span></span> <span data-ttu-id="7c593-109">In einer UWP-App können Sie das ParallaxView-Steuerelement verwenden, um einen Parallax-Effekt zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="7c593-109">In a UWP app, you can use the ParallaxView control to create a parallax effect.</span></span>  

> <span data-ttu-id="7c593-110">**Wichtige APIs**: [ParallaxView-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview), [VerticalShift-Eigenschaft](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_VerticalShift), [HorizontalShift-Eigenschaft](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_HorizontalShift)</span><span class="sxs-lookup"><span data-stu-id="7c593-110">**Important APIs**: [ParallaxView class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview), [VerticalShift property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_VerticalShift), [HorizontalShift property](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_HorizontalShift)</span></span>

## <a name="parallax-and-the-fluent-design-system"></a><span data-ttu-id="7c593-111">Parallax und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="7c593-111">Parallax and the Fluent Design System</span></span>

 <span data-ttu-id="7c593-112">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="7c593-112">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="7c593-113">Parallax ist eine Komponente des Fluent Design-Systems, die Bewegung, Tiefe und Skalierungsmöglichkeiten in Ihre App bringt.</span><span class="sxs-lookup"><span data-stu-id="7c593-113">Parallax is a Fluent Design System component that adds motion, depth, and scale to your app.</span></span> 

## <a name="how-it-works-in-a-user-interface"></a><span data-ttu-id="7c593-114">Funktionsweise in einer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="7c593-114">How it works in a user interface</span></span>

<span data-ttu-id="7c593-115">In einer Benutzeroberfläche lassen sich Parallax-Effekte erzeugen, indem bei einem Bildlauf oder Schwenken der Benutzeroberfläche verschiedene Objekte unterschiedlich schnell bewegt werden.</span><span class="sxs-lookup"><span data-stu-id="7c593-115">In a UI, you can create a parallax effect by moving different objects at different rates when the UI scrolls or pans.</span></span> <!-- Parallax is an important tool in adding depth to applications along with other techniques like transition animations, perspective tilt, and layering. --> <span data-ttu-id="7c593-116">Um dies zu veranschaulichen, sehen wir uns zwei Inhaltsebenen an, eine Liste und ein Hintergrundbild.</span><span class="sxs-lookup"><span data-stu-id="7c593-116">To demonstrate, let’s look at two layers of content, a list and a background image.</span></span>  <span data-ttu-id="7c593-117">Die Liste befindet sich über dem Hintergrundbild. Dadurch wird bereits der Eindruck vermittelt, dass die Liste sich näher am Betrachter befindet.</span><span class="sxs-lookup"><span data-stu-id="7c593-117">The list is placed on top of the background image which already gives the illusion that the list might be closer to the viewer.</span></span>  <span data-ttu-id="7c593-118">Um jetzt den Parallax-Effekt zu erzielen, soll sich das Objekt, welches uns am nächsten liegt, „schneller” bewegen als das Objekt, welches weiter entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="7c593-118">Now, to achieve the parallax effect, we want the object closest to us to travel “faster” than the object that is farther away.</span></span>  <span data-ttu-id="7c593-119">Wenn der Benutzer einen Bildlauf in der Oberfläche durchführt, bewegt sich die Liste schneller als das Hintergrundbild, wodurch eine Illusion von Tiefe erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="7c593-119">As the user scrolls the interface, the list moves at a faster rate than the background image, which creates the illusion of depth.</span></span>

 ![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](images/_Parallax_v2.gif)

 
## <a name="using-the-parallaxview-control-to-create-a-parallax-effect"></a><span data-ttu-id="7c593-121">Verwenden des ParallaxView-Steuerelements zum Erzeugen eines Parallax-Effekts</span><span class="sxs-lookup"><span data-stu-id="7c593-121">Using the ParallaxView control to create a parallax effect</span></span>

<span data-ttu-id="7c593-122">Um einen Parallax-Effekt zu erzeugen, verwenden Sie das [ParallaxView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="7c593-122">To create a parallax effect, you use the [ParallaxView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview) control.</span></span> <span data-ttu-id="7c593-123">Dieses Steuerelement verbindet die Bildlaufposition eines Vordergrundelements, z.B. einer Liste, mit einem Hintergrundelement, z.B. einem Bild.</span><span class="sxs-lookup"><span data-stu-id="7c593-123">This control ties the scroll position of a foreground element, such as a list, to a background element, such as an image.</span></span> <span data-ttu-id="7c593-124">Bei einem Bildlauf durch das Vordergrundelement wird das Hintergrundelement animiert, um einen Parallax-Effekt zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="7c593-124">As you scroll through the foreground element, it animates the background element to create a parallax effect.</span></span> 

<span data-ttu-id="7c593-125">Um das ParallaxView-Steuerelement zu verwenden, stellen Sie ein Quellelement und ein Hintergrundelement bereit und legen für die Eigenschaften [VerticalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_VerticalShift) (für den vertikalen Bildlauf) und/oder [HorizontalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_HorizontalShift) (für den horizontalen Bildlauf) einen größeren Wert als Null fest.</span><span class="sxs-lookup"><span data-stu-id="7c593-125">To use the ParallaxView control, you provide a Source element, a background element, and set the [VerticalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_VerticalShift) (for vertical scrolling) and/or [HorizontalShift](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview#Windows_UI_Xaml_Controls_ParallaxView_HorizontalShift) (for horizontal scrolling) properties to a value greater than zero.</span></span> 
* <span data-ttu-id="7c593-126">Die Quelleigenschaft akzeptiert einen Verweis auf das Vordergrundelement.</span><span class="sxs-lookup"><span data-stu-id="7c593-126">The Source property takes a reference to the foreground element.</span></span> <span data-ttu-id="7c593-127">Damit der Parallax-Effekt auftritt, sollte sich im Vordergrund ein [ScrollViewer](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer)- oder ein anderes Element befinden, das ein ScrollViewer-Element enthält, z.B. [ListView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listview) oder [RichTextBox](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichEditBox).</span><span class="sxs-lookup"><span data-stu-id="7c593-127">For the parallax effect to occur, the foreground should be a [ScrollViewer](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer) or an element that contains a ScrollViewer, such as a [ListView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.listview) or a [RichTextBox](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichEditBox).</span></span> 

* <span data-ttu-id="7c593-128">Um das Hintergrundelement festzulegen, fügen Sie dieses Element als untergeordnetes Element zum ParallaxView-Steuerelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="7c593-128">To set the background element, you add that element as a child of the ParallaxView control.</span></span> <span data-ttu-id="7c593-129">Das Hintergrundelement kann ein beliebiges [UIElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement) sein, z.B. ein [Bild](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Image) oder ein Panel, das zusätzliche UI-Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="7c593-129">The background element can be any [UIElement](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement), such as an [Image](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Image) or a panel that contains additional UI elements.</span></span> 

<span data-ttu-id="7c593-130">Um einen Parallax-Effekt zu erstellen, muss sich ParallaxView hinter dem Vordergrundelement befinden.</span><span class="sxs-lookup"><span data-stu-id="7c593-130">To create a parallax effect, the ParallaxView must be behind the foreground element.</span></span> <span data-ttu-id="7c593-131">Mithilfe des [Raster](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid)- und des [Canvas](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.canvas)-Panels können Sie Elemente übereinanderstapeln, damit sie sich gut mit dem ParallaxView-Steuerelement verwenden lassen.</span><span class="sxs-lookup"><span data-stu-id="7c593-131">The [Grid](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.grid) and [Canvas](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.canvas) panels let you layer items on top of each other, so they work well with the ParallaxView control.</span></span>  

<span data-ttu-id="7c593-132">In diesem Beispiel wird ein Parallax-Effekt für eine Liste erstellt:</span><span class="sxs-lookup"><span data-stu-id="7c593-132">This example creates a parallax effect for a list:</span></span>
 
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

<span data-ttu-id="7c593-133">ParallaxView passt die Größe des Bilds automatisch an den entsprechenden Parallax-Vorgang an. Sie müssen sich also keine Sorgen machen, dass das Bild beim Bildlauf aus dem Sichtfeld verschwindet.</span><span class="sxs-lookup"><span data-stu-id="7c593-133">The ParallaxView automatically adjusts the size of the image so it works for the parallax operation so you don’t have to worry about the image scrolling out of view.</span></span>

## <a name="customizing-the-parallax-effect"></a><span data-ttu-id="7c593-134">Anpassen des Parallax-Effekts</span><span class="sxs-lookup"><span data-stu-id="7c593-134">Customizing the parallax effect</span></span> 

<span data-ttu-id="7c593-135">Mithilfe der Eigenschaften VerticalShift und HorizontalShift können Sie das Ausmaß des Parallax-Effekts steuern.</span><span class="sxs-lookup"><span data-stu-id="7c593-135">The VerticalShift and HorizontalShift properties let you control degree of the parallax effect.</span></span>

* <span data-ttu-id="7c593-136">Die VerticalShift-Eigenschaft gibt an, wie weit der Hintergrund während des gesamten Parallax-Vorgangs vertikal verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="7c593-136">The VerticalShift property specifies how far we want the background to vertically shift during the entire parallax operation.</span></span> <span data-ttu-id="7c593-137">Der Wert 0 bedeutet, dass der Hintergrund überhaupt nicht verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="7c593-137">A value of 0 means the the background doesn't move at all.</span></span>
* <span data-ttu-id="7c593-138">Die HorizontalShift-Eigenschaft gibt an, wie weit der Hintergrund während des gesamten Parallax-Vorgangs horizontal verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="7c593-138">The HorizontalShift property specifies how far we want the background to horizontally shift during the entire parallax operation.</span></span> <span data-ttu-id="7c593-139">Der Wert 0 bedeutet, dass der Hintergrund überhaupt nicht verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="7c593-139">A value of 0 means the the background doesn't move at all.</span></span>

<span data-ttu-id="7c593-140">Mit höheren Werten lassen sich dramatischere Effekte erzeugen.</span><span class="sxs-lookup"><span data-stu-id="7c593-140">Larger values create a more dramatic effect.</span></span> 

<span data-ttu-id="7c593-141">Die vollständige Liste der Methoden zum Anpassen von Parallax finden Sie in der ParallaxView-Klasse.</span><span class="sxs-lookup"><span data-stu-id="7c593-141">For the complete list of ways to customize parallax, see the ParallaxView class.</span></span> 

## <a name="dos-and-donts"></a><span data-ttu-id="7c593-142">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="7c593-142">Do’s and don’ts</span></span>
- <span data-ttu-id="7c593-143">Verwenden Sie Parallax in Listen mit einem Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="7c593-143">Use parallax in lists with a background image</span></span>
- <span data-ttu-id="7c593-144">Verwenden Sie Parallax gegebenenfalls in ListViewItems, wenn ListViewItems ein Bild enthalten.</span><span class="sxs-lookup"><span data-stu-id="7c593-144">Consider using parallax in ListViewItems when ListViewItems contain an image</span></span>
- <span data-ttu-id="7c593-145">Verwenden Sie es nicht überall. Eine übermäßige Verwendung kann den Effekt verringern.</span><span class="sxs-lookup"><span data-stu-id="7c593-145">Don’t use it everywhere, overuse can diminish its impact</span></span>

## <a name="related-articles"></a><span data-ttu-id="7c593-146">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7c593-146">Related articles</span></span>
- **[<span data-ttu-id="7c593-147">ParallaxView-Klasse</span><span class="sxs-lookup"><span data-stu-id="7c593-147">ParallaxView class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Parallaxview)** 
