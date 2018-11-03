---
author: Jwmsft
Description: Provides a list by function of some of the controls that you can use in your apps.
title: Steuerelemente nach Funktion
ms.assetid: 8DB4347B-91D6-4659-91F2-80ECF7BBB596
label: Controls by function
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 50d2d5d6dd53ffcb14ed6223e2fd0f85324a8438
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5996396"
---
# <a name="controls-by-function"></a><span data-ttu-id="a4cf8-103">Steuerelemente nach Funktion</span><span class="sxs-lookup"><span data-stu-id="a4cf8-103">Controls by function</span></span>

<span data-ttu-id="a4cf8-104">Das XAML-Benutzeroberflächenframework für Windows bietet eine umfangreiche Bibliothek von Steuerelementen, welche die Entwicklung von Benutzeroberflächen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-104">The XAML UI framework for Windows provides an extensive library of controls that support UI development.</span></span> <span data-ttu-id="a4cf8-105">Einige dieser Steuerelemente weisen eine visuelle Darstellung auf. Andere fungieren als Container für andere Steuerelemente oder Inhalte (z.B. Bilder und Medien).</span><span class="sxs-lookup"><span data-stu-id="a4cf8-105">Some of these controls have a visual representation; others function as the containers for other controls or content, such as images and media.</span></span> 

<span data-ttu-id="a4cf8-106">Laden Sie das [Beispiel für XAML-UI-Grundlagen](http://go.microsoft.com/fwlink/p/?LinkId=619992) herunter, um sich zahlreiche Windows-UI-Steuerelemente in Aktion anzusehen.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-106">You can see many of the Windows UI controls in action by downloading the [XAML UI Basics sample](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span></span>

<table>
<th align="left"><span data-ttu-id="a4cf8-107">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="a4cf8-107">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="a4cf8-108">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die app zu öffnen und finden Sie unter der NavigationView in Aktion zu sehen</a></span><span class="sxs-lookup"><span data-stu-id="a4cf8-108">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/NavigationView">open the app and see the NavigationView in action</a></span></span> </p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="a4cf8-109">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-109">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="a4cf8-110">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-110">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>


<span data-ttu-id="a4cf8-111">Die folgende nach Funktionen geordnete Liste enthält die allgemeinen XAML-Steuerelemente, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-111">Here's a list by function of the common XAML controls you can use in your app.</span></span>

## <a name="appbars-and-commands"></a><span data-ttu-id="a4cf8-112">App-Leisten und -Befehle</span><span class="sxs-lookup"><span data-stu-id="a4cf8-112">Appbars and commands</span></span>

### <a name="app-bar"></a><span data-ttu-id="a4cf8-113">App-Leiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-113">App bar</span></span>
<span data-ttu-id="a4cf8-114">Eine Symbolleiste für anwendungsspezifische Befehle.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-114">A toolbar for displaying application-specific commands.</span></span> <span data-ttu-id="a4cf8-115">Siehe Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-115">See Command bar.</span></span>

<span data-ttu-id="a4cf8-116">Referenz: [AppBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-116">Reference: [AppBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.aspx)</span></span> 

### <a name="app-bar-button"></a><span data-ttu-id="a4cf8-117">App-Leistenschaltfläche</span><span class="sxs-lookup"><span data-stu-id="a4cf8-117">App bar button</span></span>
<span data-ttu-id="a4cf8-118">Eine Schaltfläche, die Befehle in Form einer App-Leiste anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-118">A button for showing commands using app bar styling.</span></span>

![Symbole für App-Leistenschaltflächen](images/controls/app-bar-buttons.png) 

<span data-ttu-id="a4cf8-120">Referenz: [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [SymbolIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.symbolicon.aspx), [BitmapIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.bitmapicon.aspx), [FontIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.fonticon.aspx), [PathIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pathicon.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-120">Reference: [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [SymbolIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.symbolicon.aspx), [BitmapIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.bitmapicon.aspx), [FontIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.fonticon.aspx), [PathIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pathicon.aspx)</span></span> 

<span data-ttu-id="a4cf8-121">Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-121">Design and how-to: [App bar and command bar control guide](app-bars.md)</span></span> 

<span data-ttu-id="a4cf8-122">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-122">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="app-bar-separator"></a><span data-ttu-id="a4cf8-123">Trennzeichen der App-Leiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-123">App bar separator</span></span>
<span data-ttu-id="a4cf8-124">Trennt Befehlsgruppen in einer Befehlsleiste grafisch.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-124">Visually separates groups of commands in a command bar.</span></span>

<span data-ttu-id="a4cf8-125">Referenz: [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-125">Reference: [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx)</span></span> 

<span data-ttu-id="a4cf8-126">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-126">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="app-bar-toggle-button"></a><span data-ttu-id="a4cf8-127">Umschaltfläche der App-Leiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-127">App bar toggle button</span></span>
<span data-ttu-id="a4cf8-128">Eine Schaltfläche zum Wechseln zwischen den Befehlen in einer Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-128">A button for toggling commands in a command bar.</span></span>

<span data-ttu-id="a4cf8-129">Referenz: [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-129">Reference: [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)</span></span> 

<span data-ttu-id="a4cf8-130">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-130">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="command-bar"></a><span data-ttu-id="a4cf8-131">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-131">Command bar</span></span>
<span data-ttu-id="a4cf8-132">Eine spezielle App-Leiste zum Ändern der Größe von Schaltflächenelementen auf der App-Leiste.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-132">A specialized app bar that handles the resizing of app bar button elements.</span></span>

![Befehlsleistensteuerelement](images/command-bar-compact.png)

```xaml
<CommandBar>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
</CommandBar>
```
<span data-ttu-id="a4cf8-134">Referenz: [CommandBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-134">Reference: [CommandBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx)</span></span> 

<span data-ttu-id="a4cf8-135">Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-135">Design and how-to: [App bar and command bar control guide](app-bars.md)</span></span>

<span data-ttu-id="a4cf8-136">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-136">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

## <a name="buttons"></a><span data-ttu-id="a4cf8-137">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="a4cf8-137">Buttons</span></span>

### <a name="button"></a><span data-ttu-id="a4cf8-138">Button</span><span class="sxs-lookup"><span data-stu-id="a4cf8-138">Button</span></span>
<span data-ttu-id="a4cf8-139">Ein Steuerelement, das auf Benutzereingaben reagiert und ein **Click**-Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-139">A control that responds to user input and raises a **Click** event.</span></span>

![Standardschaltfläche](images/controls/button.png)

```xaml
<Button x:Name="button1" Content="Button" 
        Click="Button_Click" />
```

<span data-ttu-id="a4cf8-141">Referenz: [Button](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.button.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-141">Reference: [Button](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.button.aspx)</span></span> 

<span data-ttu-id="a4cf8-142">Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-142">Design and how-to: [Buttons control guide](buttons.md)</span></span> 

### <a name="hyperlink"></a><span data-ttu-id="a4cf8-143">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="a4cf8-143">Hyperlink</span></span>
<span data-ttu-id="a4cf8-144">Siehe „Linkschaltfläche“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-144">See Hyperlink button.</span></span>

### <a name="hyperlink-button"></a><span data-ttu-id="a4cf8-145">Linkschaltfläche</span><span class="sxs-lookup"><span data-stu-id="a4cf8-145">Hyperlink button</span></span>
<span data-ttu-id="a4cf8-146">Eine Schaltfläche, die als markierter Text dargestellt wird und den angegebenen URI in einem Browser öffnet.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-146">A button that appears as marked up text and opens the specified URI in a browser.</span></span>

![Linkschaltfläche](images/controls/hyperlink-button.png)

```xaml
<HyperlinkButton Content="www.microsoft.com" 
                 NavigateUri="http://www.microsoft.com"/>
```

<span data-ttu-id="a4cf8-148">Referenz: [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hyperlinkbutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-148">Reference: [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hyperlinkbutton.aspx)</span></span> 

<span data-ttu-id="a4cf8-149">Design und Vorgehensweise: [Richtlinien für Hyperlinks](hyperlinks.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-149">Design and how-to: [Hyperlinks control guide](hyperlinks.md)</span></span>

### <a name="repeat-button"></a><span data-ttu-id="a4cf8-150">Wiederholungsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="a4cf8-150">Repeat button</span></span>
<span data-ttu-id="a4cf8-151">Eine Schaltfläche, die ihr **Click**-Ereignis auslöst, das andauert, solange die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-151">A button that raises its **Click** event repeatedly from the time it's pressed until it's released.</span></span> 

![Ein Schaltflächen-Steuerelement zum Wiederholen](images/controls/repeat-button.png) 

```xaml
<RepeatButton x:Name="repeatButton1" Content="Repeat Button" 
              Click="RepeatButton_Click" />
```

<span data-ttu-id="a4cf8-153">Referenz: [RepeatButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.repeatbutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-153">Reference: [RepeatButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.repeatbutton.aspx)</span></span> 

<span data-ttu-id="a4cf8-154">Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-154">Design and how-to: [Buttons control guide](buttons.md)</span></span> 

## <a name="collectiondata-controls"></a><span data-ttu-id="a4cf8-155">Sammlungs-/Datensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-155">Collection/data controls</span></span>

### <a name="flip-view"></a><span data-ttu-id="a4cf8-156">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="a4cf8-156">Flip view</span></span>
<span data-ttu-id="a4cf8-157">Ein Steuerelement, das eine Sammlung von Elementen darstellt, durch die der Benutzer jeweils einzeln blättern kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-157">A control that presents a collection of items that the user can flip through, one item at a time.</span></span>

```xaml
<FlipView x:Name="flipView1" SelectionChanged="FlipView_SelectionChanged">
    <Image Source="Assets/Logo.png" />
    <Image Source="Assets/SplashScreen.png" />
    <Image Source="Assets/SmallLogo.png" />
</FlipView>
```

<span data-ttu-id="a4cf8-158">Referenz: [FlipView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-158">Reference: [FlipView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview.aspx)</span></span> 

<span data-ttu-id="a4cf8-159">Design und Vorgehensweise: [Richtlinien für Flip-Ansicht](flipview.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-159">Design and how-to: [Flip view control guide](flipview.md)</span></span> 

### <a name="grid-view"></a><span data-ttu-id="a4cf8-160">Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="a4cf8-160">Grid view</span></span>
<span data-ttu-id="a4cf8-161">Ein Steuerelement, das eine Sammlung von Elementen in Zeilen und Spalten darstellt, für die ein vertikaler Bildlauf durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-161">A control that presents a collection of items in rows and columns that can scroll vertically.</span></span>

```xaml
<GridView x:Name="gridView1" SelectionChanged="GridView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</GridView>
```

<span data-ttu-id="a4cf8-162">Referenz: [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-162">Reference: [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span></span> 

<span data-ttu-id="a4cf8-163">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-163">Design and how-to: [Lists](lists.md)</span></span> 

<span data-ttu-id="a4cf8-164">Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-164">Sample code: [ListView sample](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span></span>

### <a name="items-control"></a><span data-ttu-id="a4cf8-165">Elementsteuerelement</span><span class="sxs-lookup"><span data-stu-id="a4cf8-165">Items control</span></span>
<span data-ttu-id="a4cf8-166">Ein Steuerelement, das eine Sammlung von Elementen auf einer Benutzeroberfläche darstellt, die durch eine Datenvorlage angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-166">A control that presents a collection of items in a UI specified by a data template.</span></span> 

```xaml
<ItemsControl/>
```

<span data-ttu-id="a4cf8-167">Referenz: [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-167">Reference: [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx)</span></span> 

### <a name="list-view"></a><span data-ttu-id="a4cf8-168">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="a4cf8-168">List view</span></span>
<span data-ttu-id="a4cf8-169">Ein Steuerelement, das eine Sammlung von Elementen in einer Liste darstellt, für die ein horizontaler Bildlauf durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-169">A control that presents a collection of items in a list that can scroll vertically.</span></span>

```xaml
<ListView x:Name="listView1" SelectionChanged="ListView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</ListView>
```

<span data-ttu-id="a4cf8-170">Referenz: [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-170">Reference: [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx)</span></span> 

<span data-ttu-id="a4cf8-171">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-171">Design and how-to: [Lists](lists.md)</span></span> 

<span data-ttu-id="a4cf8-172">Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-172">Sample code: [ListView sample](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span></span>

## <a name="date-and-time-controls"></a><span data-ttu-id="a4cf8-173">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-173">Date and time controls</span></span>

### <a name="calendar-date-picker"></a><span data-ttu-id="a4cf8-174">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="a4cf8-174">Calendar date picker</span></span>
<span data-ttu-id="a4cf8-175">Ein Steuerelement, mit dem Benutzer ein Datum über eine Kalender-Dropdownanzeige auswählen können.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-175">A control that lets a user select a date using a drop-down calendar display.</span></span>

![Kalenderdatumsauswahl mit offener Kalenderansicht](images/controls/calendar-date-picker-open.png)

```xaml
<CalendarDatePicker/>
```

<span data-ttu-id="a4cf8-177">Referenz: [CalendarDatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-177">Reference: [CalendarDatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx)</span></span> 

<span data-ttu-id="a4cf8-178">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-178">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>
 
### <a name="calendar-view"></a><span data-ttu-id="a4cf8-179">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="a4cf8-179">Calendar view</span></span>
<span data-ttu-id="a4cf8-180">Eine konfigurierbare Kalenderanzeige, in der Benutzer ein einzelnes Datum oder mehrere Daten auswählen können.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-180">A configurable calendar display that lets a user select single or multiple dates.</span></span>

```xaml
<CalendarView/>
```

<span data-ttu-id="a4cf8-181">Referenz: [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-181">Reference: [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx)</span></span> 

<span data-ttu-id="a4cf8-182">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-182">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span> 

### <a name="date-picker"></a><span data-ttu-id="a4cf8-183">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="a4cf8-183">Date picker</span></span>
<span data-ttu-id="a4cf8-184">Ein Steuerelement, mit dem ein Benutzer ein Datum auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-184">A control that lets a user select a date.</span></span>

![Datumsauswahlsteuerelement](images/controls/date-picker.png)

```xaml
<DatePicker Header="Arrival Date"/>
```

<span data-ttu-id="a4cf8-186">Referenz: [DatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-186">Reference: [DatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx)</span></span> 

<span data-ttu-id="a4cf8-187">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-187">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>
 
### <a name="time-picker"></a><span data-ttu-id="a4cf8-188">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="a4cf8-188">Time picker</span></span>
<span data-ttu-id="a4cf8-189">Ein Steuerelement, mit dem ein Benutzer einen Zeitwert auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-189">A control that lets a user set a time value.</span></span>

![TimePicker-Steuerelement](images/controls/time-picker.png) 

```xaml
<TimePicker Header="Arrival Time"/>
```

<span data-ttu-id="a4cf8-191">Referenz: [TimePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-191">Reference: [TimePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx)</span></span> 

<span data-ttu-id="a4cf8-192">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-192">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>

## <a name="flyouts"></a><span data-ttu-id="a4cf8-193">Flyouts</span><span class="sxs-lookup"><span data-stu-id="a4cf8-193">Flyouts</span></span>

### <a name="context-menu"></a><span data-ttu-id="a4cf8-194">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="a4cf8-194">Context menu</span></span>
<span data-ttu-id="a4cf8-195">Siehe „Menü-Flyout“ und „Popupmenü“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-195">See Menu flyout and Popup menu.</span></span>

### <a name="flyout"></a><span data-ttu-id="a4cf8-196">Flyout</span><span class="sxs-lookup"><span data-stu-id="a4cf8-196">Flyout</span></span>
<span data-ttu-id="a4cf8-197">Zeigt eine Meldung an, die einen Benutzereingriff erfordert.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-197">Displays a message that requires user interaction.</span></span> <span data-ttu-id="a4cf8-198">(Im Gegensatz zu einem Dialogfeld wird von einem Flyout kein separates Fenster erstellt und keine Benutzerinteraktion blockiert.)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-198">(Unlike a dialog, a flyout does not create a separate window, and does not block other user interaction.)</span></span>

![Flyout-Steuerelement](images/controls/flyout.png)

```xaml
<Flyout>
    <StackPanel>
        <TextBlock Text="All items will be removed. Do you want to continue?"/>
        <Button Click="DeleteConfirmation_Click" Content="Yes, empty my cart"/>
    </StackPanel>
</Flyout>
```

<span data-ttu-id="a4cf8-200">Referenz: [Flyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flyout.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-200">Reference: [Flyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flyout.aspx)</span></span> 

<span data-ttu-id="a4cf8-201">Design und Vorgehensweise: [Flyouts](dialogs-and-flyouts/flyouts.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-201">Design and how-to: [Flyouts](dialogs-and-flyouts/flyouts.md)</span></span> 

### <a name="menu-flyout"></a><span data-ttu-id="a4cf8-202">Menü-Flyout</span><span class="sxs-lookup"><span data-stu-id="a4cf8-202">Menu flyout</span></span>
<span data-ttu-id="a4cf8-203">Zeigt vorübergehend eine Liste der Befehle oder Optionen im Kontext der Benutzeraktion an.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-203">Temporarily displays a list of commands or options related to what the user is currently doing.</span></span>

![Menü-Flyoutsteuerelement](images/controls/menu-flyout.png) 

```xaml
<MenuFlyout>
    <MenuFlyoutItem Text="Reset" Click="Reset_Click"/>
    <MenuFlyoutSeparator/>
    <ToggleMenuFlyoutItem Text="Shuffle" 
                          IsChecked="{Binding IsShuffleEnabled, Mode=TwoWay}"/>
    <ToggleMenuFlyoutItem Text="Repeat" 
                          IsChecked="{Binding IsRepeatEnabled, Mode=TwoWay}"/>
</MenuFlyout>
```

<span data-ttu-id="a4cf8-205">Referenz: [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyout.aspx), [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-205">Reference: [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyout.aspx), [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)</span></span> 

<span data-ttu-id="a4cf8-206">Design und Vorgehensweise: [Menüs und Kontextmenüs](menus.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-206">Design and how-to: [Menus and context menus](menus.md)</span></span> 

<span data-ttu-id="a4cf8-207">Beispielcode: [Beispiel für XAML-Kontextmenü](http://go.microsoft.com/fwlink/p/?LinkId=620021)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-207">Sample code: [XAML Context Menu sample](http://go.microsoft.com/fwlink/p/?LinkId=620021)</span></span>

### <a name="popup-menu"></a><span data-ttu-id="a4cf8-208">Popupmenü</span><span class="sxs-lookup"><span data-stu-id="a4cf8-208">Popup menu</span></span>
<span data-ttu-id="a4cf8-209">Ein benutzerdefiniertes Menü mit von Ihnen angegebenen Befehlen.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-209">A custom menu that presents commands that you specify.</span></span>

<span data-ttu-id="a4cf8-210">Referenz: [PopupMenu](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.popups.popupmenu.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-210">Reference: [PopupMenu](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.popups.popupmenu.aspx)</span></span> 

<span data-ttu-id="a4cf8-211">Design und Vorgehensweise: [Dialogfelder](dialogs-and-flyouts/dialogs.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-211">Design and how-to: [Dialogs](dialogs-and-flyouts/dialogs.md)</span></span> 

### <a name="tooltip"></a><span data-ttu-id="a4cf8-212">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="a4cf8-212">Tooltip</span></span>
<span data-ttu-id="a4cf8-213">Ein Popupfenster, das Informationen zu einem Element anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-213">A pop-up window that displays information for an element.</span></span> 
 
![QuickInfo-Steuerelement](images/controls/tool-tip.png)

```xaml
<Button Content="Button" Click="Button_Click" 
        ToolTipService.ToolTip="Click to perform action" />
```

<span data-ttu-id="a4cf8-215">Referenz: [ToolTip](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltip.aspx), [ToolTipService](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltipservice.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-215">Reference: [ToolTip](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltip.aspx), [ToolTipService](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltipservice.aspx)</span></span> 

<span data-ttu-id="a4cf8-216">Design und Vorgehensweise: Richtlinien für QuickInfos</span><span class="sxs-lookup"><span data-stu-id="a4cf8-216">Design and how-to: Guidelines for tooltips</span></span> 

## <a name="images"></a><span data-ttu-id="a4cf8-217">Bilder</span><span class="sxs-lookup"><span data-stu-id="a4cf8-217">Images</span></span>

### <a name="image"></a><span data-ttu-id="a4cf8-218">Image</span><span class="sxs-lookup"><span data-stu-id="a4cf8-218">Image</span></span>
<span data-ttu-id="a4cf8-219">Ein Steuerelement, das ein Bild darstellt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-219">A control that presents an image.</span></span>

```xaml
<Image Source="Assets/Logo.png" />
```

<span data-ttu-id="a4cf8-220">Referenz: [Image](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.image.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-220">Reference: [Image](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.image.aspx)</span></span> 

<span data-ttu-id="a4cf8-221">Design und Vorgehensweise: [Image und ImageBrush](images-imagebrushes.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-221">Design and how-to: [Image and ImageBrush](images-imagebrushes.md)</span></span> 

<span data-ttu-id="a4cf8-222">Beispielcode: [Beispiel für XAML-Bilder](http://go.microsoft.com/fwlink/p/?linkid=226867)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-222">Sample code: [XAML images sample](http://go.microsoft.com/fwlink/p/?linkid=226867)</span></span>

## <a name="graphics-and-ink"></a><span data-ttu-id="a4cf8-223">Grafiken und Freihandstriche</span><span class="sxs-lookup"><span data-stu-id="a4cf8-223">Graphics and ink</span></span>

### <a name="inkcanvas"></a><span data-ttu-id="a4cf8-224">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="a4cf8-224">InkCanvas</span></span>
<span data-ttu-id="a4cf8-225">Ein Steuerelement, das Freihandstriche empfängt und anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-225">A control that receives and displays ink strokes.</span></span>

```xaml
<InkCanvas/>
```

<span data-ttu-id="a4cf8-226">Referenz: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.inkcanvas.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-226">Reference: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.inkcanvas.aspx)</span></span> 

### <a name="shapes"></a><span data-ttu-id="a4cf8-227">Formen</span><span class="sxs-lookup"><span data-stu-id="a4cf8-227">Shapes</span></span>
<span data-ttu-id="a4cf8-228">Verschiedene grafische Speichermodusobjekte, die als Ellipsen, Rechtecke, Linien, Bézierpfade usw. dargestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-228">Various retained mode graphical objects that can be presented like ellipses, rectangles, lines, Bezier paths, etc.</span></span>

![<span data-ttu-id="a4cf8-229">Ein Polygon](images/controls/shapes-polygon.png) 
![Ein Pfad</span><span class="sxs-lookup"><span data-stu-id="a4cf8-229">A polygon](images/controls/shapes-polygon.png) 
![A path</span></span>](images/controls/shapes-path.png) 

```xaml
<Ellipse/>
<Path/>
<Rectangle/>
```

<span data-ttu-id="a4cf8-230">Referenz: [Shapes](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.shapes.shape.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-230">Reference: [Shapes](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.shapes.shape.aspx)</span></span> 

<span data-ttu-id="a4cf8-231">So wird's gemacht: [Zeichnen von Formen](../../graphics/drawing-shapes.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-231">How to: [Drawing shapes](../../graphics/drawing-shapes.md)</span></span> 

<span data-ttu-id="a4cf8-232">Beispielcode: [Beispiel für vektorbasierte XAML-Zeichnung](http://go.microsoft.com/fwlink/p/?linkid=226866)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-232">Sample code: [XAML vector-based drawing sample](http://go.microsoft.com/fwlink/p/?linkid=226866)</span></span>

## <a name="layout-controls"></a><span data-ttu-id="a4cf8-233">Layoutsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-233">Layout controls</span></span>

### <a name="border"></a><span data-ttu-id="a4cf8-234">Rahmen</span><span class="sxs-lookup"><span data-stu-id="a4cf8-234">Border</span></span>
<span data-ttu-id="a4cf8-235">Ein Containersteuerelement, das einen Rahmen, einen Hintergrund oder beides um ein anderes Objekt herum zeichnet.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-235">A container control that draws a border, background, or both, around another object.</span></span>

![Ein Rahmen um zwei Rechtecke](images/controls/border.png) 

```xaml
<Border BorderBrush="Blue" BorderThickness="4" 
        Height="108" Width="64" 
        Padding="8" CornerRadius="4">
    <Canvas>
        <Rectangle Fill="Orange"/>
        <Rectangle Fill="Green" Margin="0,44"/>
    </Canvas>
</Border>
```

<span data-ttu-id="a4cf8-237">Referenz: [Border](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.border.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-237">Reference: [Border](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.border.aspx)</span></span>

### <a name="canvas"></a><span data-ttu-id="a4cf8-238">Canvas</span><span class="sxs-lookup"><span data-stu-id="a4cf8-238">Canvas</span></span>
<span data-ttu-id="a4cf8-239">Ein Layoutpanel, das die absolute Positionierung untergeordneter Elemente relativ zur oberen linken Ecke der Canvas unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-239">A layout panel that supports the absolute positioning of child elements relative to the top left corner of the canvas.</span></span>
 
![Canvas-Layoutpanel](images/controls/canvas.png) 

```xaml
<Canvas Width="120" Height="120">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Canvas.Left="20" Canvas.Top="20"/>
    <Rectangle Fill="Green" Canvas.Left="40" Canvas.Top="40"/>
    <Rectangle Fill="Orange" Canvas.Left="60" Canvas.Top="60"/>
</Canvas>
```

<span data-ttu-id="a4cf8-241">Referenz: [Canvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.canvas.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-241">Reference: [Canvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.canvas.aspx)</span></span>
 
### <a name="grid"></a><span data-ttu-id="a4cf8-242">Raster</span><span class="sxs-lookup"><span data-stu-id="a4cf8-242">Grid</span></span>
<span data-ttu-id="a4cf8-243">Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-243">A layout panel that supports the arranging of child elements in rows and columns.</span></span>

![Raster-Layoutpanel](images/controls/grid.png) 

```xaml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="50"/>
        <RowDefinition Height="50"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="50"/>
        <ColumnDefinition Width="50"/>
    </Grid.ColumnDefinitions>
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Grid.Row="1"/>
    <Rectangle Fill="Green" Grid.Column="1"/>
    <Rectangle Fill="Orange" Grid.Row="1" Grid.Column="1"/>
</Grid>
```

<span data-ttu-id="a4cf8-245">Referenz: [Grid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-245">Reference: [Grid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)</span></span>
 
### <a name="panning-scroll-viewer"></a><span data-ttu-id="a4cf8-246">Verschiebungs-Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="a4cf8-246">Panning scroll viewer</span></span>
<span data-ttu-id="a4cf8-247">Siehe „Bildlaufanzeige“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-247">See Scroll viewer.</span></span>

### <a name="relativepanel"></a><span data-ttu-id="a4cf8-248">RelativePanel</span><span class="sxs-lookup"><span data-stu-id="a4cf8-248">RelativePanel</span></span>
<span data-ttu-id="a4cf8-249">Ein Bereich, in dem Sie untergeordnete Objekte relativ zueinander oder in Relation zum übergeordneten Objekt positionieren und ausrichten können.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-249">A panel that lets you position and align child objects in relation to each other or the parent panel.</span></span>

![RelativePanel-Layoutpanel](images/controls/relative-panel.png) 

```xaml
<RelativePanel>
    <TextBox x:Name="textBox1" RelativePanel.AlignLeftWithPanel="True"/>
    <Button Content="Submit" RelativePanel.Below="textBox1"/>
</RelativePanel>
```

<span data-ttu-id="a4cf8-251">Referenz: [RelativePanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.relativepanel.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-251">Reference: [RelativePanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.relativepanel.aspx)</span></span>

### <a name="scroll-bar"></a><span data-ttu-id="a4cf8-252">Bildlaufleiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-252">Scroll bar</span></span>
<span data-ttu-id="a4cf8-253">Siehe Bildlaufanzeige.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-253">See scroll viewer.</span></span> <span data-ttu-id="a4cf8-254">(ScrollBar ist ein Element von ScrollViewer.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-254">(ScrollBar is an element of ScrollViewer.</span></span> <span data-ttu-id="a4cf8-255">Es wird normalerweise nicht als eigenständiges Steuerelement verwendet.)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-255">You don't typically use it as a stand-alone control.)</span></span>

<span data-ttu-id="a4cf8-256">Referenz: [ScrollBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-256">Reference: [ScrollBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span></span>
 
### <a name="scroll-viewer"></a><span data-ttu-id="a4cf8-257">Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="a4cf8-257">Scroll viewer</span></span>
<span data-ttu-id="a4cf8-258">Ein Containersteuerelement, mit dem der Benutzer Inhalte verschieben und vergrößern/verkleinern kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-258">A container control that lets the user pan and zoom its content.</span></span>

```xaml
<ScrollViewer ZoomMode="Enabled" MaxZoomFactor="10" 
              HorizontalScrollMode="Enabled" 
              HorizontalScrollBarVisibility="Visible"
              Height="200" Width="200">
    <Image Source="Assets/Logo.png" Height="400" Width="400"/>
</ScrollViewer>
```

<span data-ttu-id="a4cf8-259">Referenz: [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-259">Reference: [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.aspx)</span></span>

<span data-ttu-id="a4cf8-260">Design und Vorgehensweise: [Bildlaufleisten](scroll-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-260">Design and how-to: [Scroll and panning controls guide](scroll-controls.md)</span></span> 

<span data-ttu-id="a4cf8-261">Beispielcode: [Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom](http://go.microsoft.com/fwlink/p/?linkid=238577)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-261">Sample code: [XAML scrolling, panning and zooming sample](http://go.microsoft.com/fwlink/p/?linkid=238577)</span></span>

### <a name="stack-panel"></a><span data-ttu-id="a4cf8-262">StackPanel</span><span class="sxs-lookup"><span data-stu-id="a4cf8-262">Stack panel</span></span>
<span data-ttu-id="a4cf8-263">Ein Layoutpanel, das untergeordnete Elemente in einer einzelnen Zeile anordnet. Die Zeile kann horizontal oder vertikal ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-263">A layout panel that arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>

![StackPanel-Layoutsteuerelement](images/controls/stack-panel.png) 

```xaml
<StackPanel>
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue"/>
    <Rectangle Fill="Green"/>
    <Rectangle Fill="Orange"/>
</StackPanel>
```

<span data-ttu-id="a4cf8-265">Referenz: [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-265">Reference: [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)</span></span>
 
### <a name="variablesizedwrapgrid"></a><span data-ttu-id="a4cf8-266">VariableSizedWrapGrid</span><span class="sxs-lookup"><span data-stu-id="a4cf8-266">VariableSizedWrapGrid</span></span>
<span data-ttu-id="a4cf8-267">Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-267">A layout panel that supports the arranging of child elements in rows and columns.</span></span> <span data-ttu-id="a4cf8-268">Jedes untergeordnete Element kann sich über mehrere Zeilen und Spalten erstrecken.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-268">Each child element can span multiple rows and columns.</span></span>

![Umbruchraster-Layoutpanel mit variabler Größe](images/controls/variable-sized-wrap-grid.png) 

```xaml
<VariableSizedWrapGrid MaximumRowsOrColumns="3" ItemHeight="44" ItemWidth="44">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Height="80" 
               VariableSizedWrapGrid.RowSpan="2"/>
    <Rectangle Fill="Green" Width="80" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
    <Rectangle Fill="Orange" Height="80" Width="80" 
               VariableSizedWrapGrid.RowSpan="2" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
</VariableSizedWrapGrid>
```

<span data-ttu-id="a4cf8-270">Referenz: [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.variablesizedwrapgrid.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-270">Reference: [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.variablesizedwrapgrid.aspx)</span></span>

### <a name="viewbox"></a><span data-ttu-id="a4cf8-271">Viewbox</span><span class="sxs-lookup"><span data-stu-id="a4cf8-271">Viewbox</span></span>
<span data-ttu-id="a4cf8-272">Ein Containersteuerelement, das seinen Inhalt auf eine angegebene Größe skaliert.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-272">A container control that scales its content to a specified size.</span></span>

![Viewbox-Steuerelement](images/controls/view-box.png) 

```xaml
<Viewbox MaxWidth="25" MaxHeight="25">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
<Viewbox MaxWidth="75" MaxHeight="75">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
<Viewbox MaxWidth="150" MaxHeight="150">
    <Image Source="Assets/Logo.png"/>
</Viewbox>
```

<span data-ttu-id="a4cf8-274">Referenz: [Viewbox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.viewbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-274">Reference: [Viewbox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.viewbox.aspx)</span></span>
 
### <a name="zooming-scroll-viewer"></a><span data-ttu-id="a4cf8-275">Zoombildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="a4cf8-275">Zooming scroll viewer</span></span>
<span data-ttu-id="a4cf8-276">Siehe „Bildlaufanzeige“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-276">See Scroll viewer.</span></span>

## <a name="media-controls"></a><span data-ttu-id="a4cf8-277">Mediensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-277">Media controls</span></span>

### <a name="audio"></a><span data-ttu-id="a4cf8-278">Audio</span><span class="sxs-lookup"><span data-stu-id="a4cf8-278">Audio</span></span>
<span data-ttu-id="a4cf8-279">Siehe „Medienelement“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-279">See Media element.</span></span>

### <a name="media-element"></a><span data-ttu-id="a4cf8-280">Medienelement</span><span class="sxs-lookup"><span data-stu-id="a4cf8-280">Media element</span></span>
<span data-ttu-id="a4cf8-281">Ein Steuerelement, das Audio- und Videoinhalte wiedergibt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-281">A control that plays audio and video content.</span></span>

```xaml
<MediaElement x:Name="myMediaElement"/>
```

<span data-ttu-id="a4cf8-282">Referenz: [MediaElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediaelement.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-282">Reference: [MediaElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediaelement.aspx)</span></span> 

<span data-ttu-id="a4cf8-283">Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-283">Design and how-to: [Media element control guide](media-playback.md)</span></span>

### <a name="mediatransportcontrols"></a><span data-ttu-id="a4cf8-284">MediaTransportControls</span><span class="sxs-lookup"><span data-stu-id="a4cf8-284">MediaTransportControls</span></span>
<span data-ttu-id="a4cf8-285">Ein Steuerelement, das Wiedergabesteuerelemente für eine „MediaElement“-Klasse bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-285">A control that provides playback controls for a MediaElement.</span></span>

![Medienelement mit Transportsteuerelementen](images/controls/media-transport-controls.png) 

```xaml
<MediaTransportControls MediaElement="myMediaElement"/>
```

<span data-ttu-id="a4cf8-287">Referenz: [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-287">Reference: [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)</span></span> 

<span data-ttu-id="a4cf8-288">Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-288">Design and how-to: [Media element control guide](media-playback.md)</span></span> 

<span data-ttu-id="a4cf8-289">Beispielcode: [Beispiel für die Steuerelemente für den Medientransport](http://go.microsoft.com/fwlink/p/?LinkId=620023)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-289">Sample code: [Media Transport Controls sample](http://go.microsoft.com/fwlink/p/?LinkId=620023)</span></span>

### <a name="video"></a><span data-ttu-id="a4cf8-290">Video</span><span class="sxs-lookup"><span data-stu-id="a4cf8-290">Video</span></span>
<span data-ttu-id="a4cf8-291">Siehe „Medienelement“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-291">See Media element.</span></span>

## <a name="navigation"></a><span data-ttu-id="a4cf8-292">Navigation</span><span class="sxs-lookup"><span data-stu-id="a4cf8-292">Navigation</span></span>

### <a name="navigationview"></a><span data-ttu-id="a4cf8-293">NavigationView</span><span class="sxs-lookup"><span data-stu-id="a4cf8-293">NavigationView</span></span>

<span data-ttu-id="a4cf8-294">Eine anpassungsfähige Container und flexible Navigationsmodell, der im linken Navigationsbereich, oberen Navigationsleiste und registerkartenmuster implementiert.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-294">An adaptable container and flexible navigation model that implements the left navigation pane, top navigation and tabs pattern.</span></span>

<span data-ttu-id="a4cf8-295">Referenz: [NavigationView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-295">Reference: [NavigationView](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)</span></span>

<span data-ttu-id="a4cf8-296">Design und Vorgehensweise: [Feldsteuerelement NavigationView](navigationview.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-296">Design and how-to: [NavigationView control guide](navigationview.md)</span></span>

### <a name="splitview"></a><span data-ttu-id="a4cf8-297">SplitView</span><span class="sxs-lookup"><span data-stu-id="a4cf8-297">SplitView</span></span>

<span data-ttu-id="a4cf8-298">Ein Containersteuerelement mit zwei Ansichten: einer Ansicht für den Hauptinhalt und einer weiteren Ansicht, die in der Regel für ein Navigationsmenü verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-298">A container control with two views; one view for the main content and another view that is typically used for a navigation menu.</span></span>

![Steuerelement für geteilte Ansicht](images/controls/split-view.png) 

```xaml
<SplitView>
    <SplitView.Pane>
        <!-- Menu content -->
    </SplitView.Pane>
    <SplitView.Content>
        <!-- Main content -->
    </SplitView.Content>
</SplitView>
```

<span data-ttu-id="a4cf8-300">Referenz: [SplitView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.splitview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-300">Reference: [SplitView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.splitview.aspx)</span></span> 

<span data-ttu-id="a4cf8-301">Design und Vorgehensweise: [Richtlinien für das Steuerelement für die geteilte Ansicht](split-view.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-301">Design and how-to: [Split view control guide](split-view.md)</span></span>

### <a name="web-view"></a><span data-ttu-id="a4cf8-302">Webansicht</span><span class="sxs-lookup"><span data-stu-id="a4cf8-302">Web view</span></span>

<span data-ttu-id="a4cf8-303">Ein Containersteuerelement, das Webinhalt hostet.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-303">A container control that hosts web content.</span></span>

```xaml
<WebView x:Name="webView1" Source="http://dev.windows.com" 
         Height="400" Width="800"/>
```

<span data-ttu-id="a4cf8-304">Referenz: [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-304">Reference: [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)</span></span> 

<span data-ttu-id="a4cf8-305">Design und Vorgehensweise: Richtlinien für Webansichten</span><span class="sxs-lookup"><span data-stu-id="a4cf8-305">Design and how-to: Guidelines for Web views</span></span> 

<span data-ttu-id="a4cf8-306">Beispielcode: [Beispiel für XAML-WebView-Steuerelement](http://go.microsoft.com/fwlink/p/?linkid=238582)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-306">Sample code: [XAML WebView control sample](http://go.microsoft.com/fwlink/p/?linkid=238582)</span></span>

### <a name="semantic-zoom"></a><span data-ttu-id="a4cf8-307">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="a4cf8-307">Semantic zoom</span></span>

<span data-ttu-id="a4cf8-308">Ein Containersteuerelement, das es dem Benutzer ermöglicht, zwischen zwei Ansichten einer Sammlung zu zoomen.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-308">A container control that lets the user zoom between two views of a collection of items.</span></span>

```xaml
<SemanticZoom>
    <ZoomedInView>
        <GridView></GridView>
    </ZoomedInView>
    <ZoomedOutView>
        <GridView></GridView>
    </ZoomedOutView>
</SemanticZoom>
```

<span data-ttu-id="a4cf8-309">Referenz: [SemanticZoom](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-309">Reference: [SemanticZoom](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.aspx)</span></span> 

<span data-ttu-id="a4cf8-310">Design und Vorgehensweise: [Richtlinien für den semantischen Zoom](semantic-zoom.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-310">Design and how-to: [Semantic zoom control guide](semantic-zoom.md)</span></span>

<span data-ttu-id="a4cf8-311">Beispielcode: [Beispiel für XAML-GridView-Gruppierung und -SemanticZoom](http://go.microsoft.com/fwlink/p/?linkid=226564)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-311">Sample code: [XAML GridView grouping and SemanticZoom sample](http://go.microsoft.com/fwlink/p/?linkid=226564)</span></span>

## <a name="progress-controls"></a><span data-ttu-id="a4cf8-312">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-312">Progress controls</span></span>

### <a name="progress-bar"></a><span data-ttu-id="a4cf8-313">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="a4cf8-313">Progress bar</span></span>
<span data-ttu-id="a4cf8-314">Ein Steuerelement, das den Fortschritt durch Anzeigen einer Leiste angibt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-314">A control that indicates progress by displaying a bar.</span></span>

![Statusleistensteuerelement](images/controls/progress-bar-determinate.png)

<span data-ttu-id="a4cf8-316">Eine Fortschrittsleiste, die einen bestimmten Wert anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-316">A progress bar that shows a specific value.</span></span>

```xaml
<ProgressBar x:Name="progressBar1" Value="50" Width="100"/>
```

![Steuerelement für unbestimmte Statusanzeige](images/controls/progress-bar-indeterminate.png)

<span data-ttu-id="a4cf8-318">Eine Fortschrittsleiste, die einen unbestimmten Fortschritt anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-318">A progress bar that shows indeterminate progress.</span></span>

```xaml
<ProgressBar x:Name="indeterminateProgressBar1" IsIndeterminate="True" Width="100"/>
```

<span data-ttu-id="a4cf8-319">Referenz: [ProgressBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-319">Reference: [ProgressBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx)</span></span> 

<span data-ttu-id="a4cf8-320">Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-320">Design and how-to: [Progress controls guide](progress-controls.md)</span></span> 

### <a name="progress-ring"></a><span data-ttu-id="a4cf8-321">Statusring</span><span class="sxs-lookup"><span data-stu-id="a4cf8-321">Progress ring</span></span>
<span data-ttu-id="a4cf8-322">Ein Steuerelement, das den Status durch Anzeigen eines Rings angibt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-322">A control that indicates indeterminate progress by displaying a ring.</span></span> 

![Statusringsteuerelement](images/controls/progress-ring.png) 

```xaml
<ProgressRing x:Name="progressRing1" IsActive="True"/>
```

<span data-ttu-id="a4cf8-324">Referenz: [ProgressRing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-324">Reference: [ProgressRing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx)</span></span> 

<span data-ttu-id="a4cf8-325">Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-325">Design and how-to: [Progress controls guide](progress-controls.md)</span></span> 

## <a name="text-controls"></a><span data-ttu-id="a4cf8-326">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-326">Text controls</span></span>

### <a name="auto-suggest-box"></a><span data-ttu-id="a4cf8-327">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="a4cf8-327">Auto suggest box</span></span>
<span data-ttu-id="a4cf8-328">Ein Texteingabefeld, das Text vorschlägt, während der Benutzer Zeichen eingibt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-328">A text input box that provides suggested text as the user types.</span></span>

![Feld mit automatischen Vorschlägen für die Suche](images/controls/auto-suggest-box.png) 

<span data-ttu-id="a4cf8-330">Referenz: [AutoSuggestBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-330">Reference: [AutoSuggestBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx)</span></span>

<span data-ttu-id="a4cf8-331">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Feldsteuerelement mit automatischen Vorschlägen](auto-suggest-box.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-331">Design and how-to: [Text controls](text-controls.md), [Auto suggest box control guide](auto-suggest-box.md)</span></span>

<span data-ttu-id="a4cf8-332">Beispielcode: [Beispiel für AutoSuggestBox-Migration](http://go.microsoft.com/fwlink/p/?LinkId=619996)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-332">Sample code: [AutoSuggestBox migration sample](http://go.microsoft.com/fwlink/p/?LinkId=619996)</span></span>

### <a name="multi-line-text-box"></a><span data-ttu-id="a4cf8-333">Mehrzeiliges Textfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-333">Multi-line text box</span></span>
<span data-ttu-id="a4cf8-334">Siehe „Textfeld“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-334">See Text box.</span></span>

### <a name="password-box"></a><span data-ttu-id="a4cf8-335">Kennwortfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-335">Password box</span></span>
<span data-ttu-id="a4cf8-336">Ein Steuerelement für die Kennworteingabe.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-336">A control for entering passwords.</span></span>

 ![Ein Kennwortfeld](images/controls/password-box.png)

```xaml
<PasswordBox x:Name="passwordBox1" 
             PasswordChanged="PasswordBox_PasswordChanged" />
```

<span data-ttu-id="a4cf8-338">Referenz: [PasswordBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-338">Reference: [PasswordBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx)</span></span> 

<span data-ttu-id="a4cf8-339">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Kennwortfelder](password-box.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-339">Design and how-to: [Text controls](text-controls.md), [Password box control guide](password-box.md)</span></span> 

<span data-ttu-id="a4cf8-340">Beispielcode: [Beispiel für die XAML-Textanzeige](http://go.microsoft.com/fwlink/p/?linkid=238579), [Beispiel für die XAML-Textbearbeitung](http://go.microsoft.com/fwlink/p/?linkid=251417)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-340">Sample code: [XAML text display sample](http://go.microsoft.com/fwlink/p/?linkid=238579), [XAML text editing sample](http://go.microsoft.com/fwlink/p/?linkid=251417)</span></span>

### <a name="rich-edit-box"></a><span data-ttu-id="a4cf8-341">Rich-Edit-Feld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-341">Rich edit box</span></span>
<span data-ttu-id="a4cf8-342">Ein Steuerelement, mit dem der Benutzer Rich-Text-Dokumente mit Inhalten wie formatiertem Text, Links und Bildern bearbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-342">A control that lets a user edit rich text documents with content like formatted text, hyperlinks, and images.</span></span>

```xaml
<RichEditBox />
```

<span data-ttu-id="a4cf8-343">Referenz: [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-343">Reference: [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx)</span></span> 

<span data-ttu-id="a4cf8-344">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für RichEditBox-Steuerelement](rich-edit-box.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-344">Design and how-to: [Text controls](text-controls.md), [Rich edit box control guide](rich-edit-box.md)</span></span>

<span data-ttu-id="a4cf8-345">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-345">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

### <a name="search-box"></a><span data-ttu-id="a4cf8-346">Suchfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-346">Search box</span></span>
<span data-ttu-id="a4cf8-347">Siehe „Feld mit automatischen Vorschlägen“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-347">See Auto suggest box.</span></span>

### <a name="single-line-text-box"></a><span data-ttu-id="a4cf8-348">Einzeiliges Textfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-348">Single-line text box</span></span>
<span data-ttu-id="a4cf8-349">Siehe „Textfeld“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-349">See Text box.</span></span>

### <a name="static-textparagraph"></a><span data-ttu-id="a4cf8-350">Statischer Text/Absatz</span><span class="sxs-lookup"><span data-stu-id="a4cf8-350">Static text/paragraph</span></span>
<span data-ttu-id="a4cf8-351">Siehe „Textblock“.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-351">See Text block.</span></span>

### <a name="text-block"></a><span data-ttu-id="a4cf8-352">Textblock</span><span class="sxs-lookup"><span data-stu-id="a4cf8-352">Text block</span></span>
<span data-ttu-id="a4cf8-353">Ein Steuerelement, das Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-353">A control that displays text.</span></span>

![Textblocksteuerelement](images/controls/text-block.png) 

```xaml
<TextBlock x:Name="textBlock1" Text="I am a TextBlock"/>
```

<span data-ttu-id="a4cf8-355">Referenz: [TextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-355">Reference: [TextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx)</span></span> 

<span data-ttu-id="a4cf8-356">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBlock](text-block.md), [Richtlinie für Rich-Text-Blocksteuerelemente](rich-text-block.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-356">Design and how-to: [Text controls](text-controls.md), [Text block control guide](text-block.md), [Rich text block control guide](rich-text-block.md)</span></span>

<span data-ttu-id="a4cf8-357">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-357">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

### <a name="text-box"></a><span data-ttu-id="a4cf8-358">Textfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-358">Text box</span></span>
<span data-ttu-id="a4cf8-359">Ein einzeiliges oder mehrzeiliges Nur-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-359">A single-line or multi-line plain text field.</span></span>

![Textfeldsteuerelement](images/controls/text-box.png) 

```xaml
<TextBox x:Name="textBox1" Text="I am a TextBox" 
         TextChanged="TextBox_TextChanged"/>
```

<span data-ttu-id="a4cf8-361">Referenz: [TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-361">Reference: [TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx)</span></span> 

<span data-ttu-id="a4cf8-362">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBox](text-box.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-362">Design and how-to: [Text controls](text-controls.md), [Text box control guide](text-box.md)</span></span> 

<span data-ttu-id="a4cf8-363">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-363">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

## <a name="selection-controls"></a><span data-ttu-id="a4cf8-364">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a4cf8-364">Selection controls</span></span>

### <a name="check-box"></a><span data-ttu-id="a4cf8-365">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="a4cf8-365">Check box</span></span>
<span data-ttu-id="a4cf8-366">Ein Steuerelement, das der Benutzer aktivieren und deaktivieren kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-366">A control that a user can select or clear.</span></span>

![Die drei Zustände eines Kontrollkästchens](images/templates-checkbox-states-default.png)

```xaml
<CheckBox x:Name="checkbox1" Content="CheckBox" 
          Checked="CheckBox_Checked"/>
```

<span data-ttu-id="a4cf8-368">Referenz: [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-368">Reference: [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)</span></span> 

<span data-ttu-id="a4cf8-369">Design und Vorgehensweise: [Richtlinien für Kontrollkästchen](checkbox.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-369">Design and how-to: [Check box control guide](checkbox.md)</span></span> 

### <a name="combo-box"></a><span data-ttu-id="a4cf8-370">Kombinationsfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-370">Combo box</span></span>
<span data-ttu-id="a4cf8-371">Eine Dropdownliste mit Elementen, in der ein Benutzer eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-371">A drop-down list of items a user can select from.</span></span>

![Offenes Kombinationsfeld](images/controls/combo-box-open.png) 

```xaml
<ComboBox x:Name="comboBox1" Width="100"
          SelectionChanged="ComboBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ComboBox>
```

<span data-ttu-id="a4cf8-373">Referenz: [ComboBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.combobox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-373">Reference: [ComboBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.combobox.aspx)</span></span> 

<span data-ttu-id="a4cf8-374">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-374">Design and how-to: [Lists](lists.md)</span></span> 

### <a name="list-box"></a><span data-ttu-id="a4cf8-375">Listenfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-375">List box</span></span>
<span data-ttu-id="a4cf8-376">Ein Steuerelement, das eine Inlineliste mit Elementen darstellt, aus der ein Benutzer eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-376">A control that presents an inline list of items that the user can select from.</span></span> 

![Listenfeldsteuerelement](images/controls/list-box.png)

```xaml
<ListBox x:Name="listBox1" Width="100"
         SelectionChanged="ListBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ListBox>
```

<span data-ttu-id="a4cf8-378">Referenz: [ListBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-378">Reference: [ListBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listbox.aspx)</span></span> 

<span data-ttu-id="a4cf8-379">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-379">Design and how-to: [Lists](lists.md)</span></span> 

### <a name="radio-button"></a><span data-ttu-id="a4cf8-380">Optionsfeld</span><span class="sxs-lookup"><span data-stu-id="a4cf8-380">Radio button</span></span>
<span data-ttu-id="a4cf8-381">Ein Steuerelement, das es einem Benutzer ermöglicht, eine einzelne Option aus einer Gruppe von Optionen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-381">A control that allows a user to select a single option from a group of options.</span></span> <span data-ttu-id="a4cf8-382">Gruppierte Optionsfelder schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-382">When radio buttons are grouped together, they are mutually exclusive.</span></span>

![Optionsfeldsteuerelemente](images/controls/radio-button.png)

```xaml
<RadioButton x:Name="radioButton1" Content="RadioButton 1" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
<RadioButton x:Name="radioButton2" Content="RadioButton 2" GroupName="Group1" 
             Checked="RadioButton_Checked" IsChecked="True"/>
<RadioButton x:Name="radioButton3" Content="RadioButton 3" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
```

<span data-ttu-id="a4cf8-384">Referenz: [RadioButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.radiobutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-384">Reference: [RadioButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.radiobutton.aspx)</span></span> 

<span data-ttu-id="a4cf8-385">Design und Vorgehensweise: [Richtlinien für Optionsfelder](radio-button.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-385">Design and how-to: [Radio button control guide](radio-button.md)</span></span>
 
### <a name="slider"></a><span data-ttu-id="a4cf8-386">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="a4cf8-386">Slider</span></span>
<span data-ttu-id="a4cf8-387">Ein Steuerelement, über das der Benutzer aus einer Reihe von Werten auswählen kann, indem er ein Schiebereglersteuerelement über einen Bereich verschiebt.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-387">A control that lets the user select from a range of values by moving a Thumb control along a track.</span></span>

![Schiebereglersteuerelement](images/controls/slider.png)

```xaml
<Slider x:Name="slider1" Width="100" ValueChanged="Slider_ValueChanged" />
```

<span data-ttu-id="a4cf8-389">Referenz: [Slider](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-389">Reference: [Slider](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx)</span></span> 

<span data-ttu-id="a4cf8-390">Design und Vorgehensweise: [Richtlinien für Schieberegler](slider.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-390">Design and how-to: [Slider control guide](slider.md)</span></span> 

### <a name="toggle-button"></a><span data-ttu-id="a4cf8-391">Umschalter</span><span class="sxs-lookup"><span data-stu-id="a4cf8-391">Toggle button</span></span>
<span data-ttu-id="a4cf8-392">Eine Schaltfläche, mit der zwischen zwei Zuständen gewechselt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-392">A button that can be toggled between 2 states.</span></span>

```xaml
<ToggleButton x:Name="toggleButton1" Content="Button" 
              Checked="ToggleButton_Checked"/>
```

<span data-ttu-id="a4cf8-393">Referenz: [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-393">Reference: [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx)</span></span>

<span data-ttu-id="a4cf8-394">Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-394">Design and how-to: [Toggle control guide](toggles.md)</span></span> 

### <a name="toggle-switch"></a><span data-ttu-id="a4cf8-395">Umschalter</span><span class="sxs-lookup"><span data-stu-id="a4cf8-395">Toggle switch</span></span>
<span data-ttu-id="a4cf8-396">Ein Schalter, mit dem zwischen zwei Zuständen hin und her geschaltet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a4cf8-396">A switch that can be toggled between 2 states.</span></span>

![Umschaltersteuerelement](images/controls/toggle-switch.png) 

```xaml
<ToggleSwitch x:Name="toggleSwitch1" Header="ToggleSwitch" 
              OnContent="On" OffContent="Off" 
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="a4cf8-398">Referenz: [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.toggleswitch.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-398">Reference: [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.toggleswitch.aspx)</span></span> 

<span data-ttu-id="a4cf8-399">Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md)</span><span class="sxs-lookup"><span data-stu-id="a4cf8-399">Design and how-to: [Toggle control guide](toggles.md)</span></span> 
