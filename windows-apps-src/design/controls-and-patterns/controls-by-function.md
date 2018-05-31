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
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 21539d625dc70ded7bec77b9916c7ea4bff72536
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
ms.locfileid: "1396809"
---
# <a name="controls-by-function"></a><span data-ttu-id="41c28-103">Steuerelemente nach Funktion</span><span class="sxs-lookup"><span data-stu-id="41c28-103">Controls by function</span></span>

 

<span data-ttu-id="41c28-104">Das XAML-Benutzeroberflächenframework für Windows bietet eine umfangreiche Bibliothek von Steuerelementen, welche die Entwicklung von Benutzeroberflächen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="41c28-104">The XAML UI framework for Windows provides an extensive library of controls that support UI development.</span></span> <span data-ttu-id="41c28-105">Einige dieser Steuerelemente weisen eine visuelle Darstellung auf. Andere fungieren als Container für andere Steuerelemente oder Inhalte (z.B. Bilder und Medien).</span><span class="sxs-lookup"><span data-stu-id="41c28-105">Some of these controls have a visual representation; others function as the containers for other controls or content, such as images and media.</span></span> 

<span data-ttu-id="41c28-106">Laden Sie das [Beispiel für XAML-UI-Grundlagen](http://go.microsoft.com/fwlink/p/?LinkId=619992) herunter, um sich zahlreiche Windows-UI-Steuerelemente in Aktion anzusehen.</span><span class="sxs-lookup"><span data-stu-id="41c28-106">You can see many of the Windows UI controls in action by downloading the [XAML UI Basics sample](http://go.microsoft.com/fwlink/p/?LinkId=619992).</span></span> 

<span data-ttu-id="41c28-107">Die folgende nach Funktionen geordnete Liste enthält die allgemeinen XAML-Steuerelemente, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="41c28-107">Here's a list by function of the common XAML controls you can use in your app.</span></span> 

## <a name="appbars-and-commands"></a><span data-ttu-id="41c28-108">App-Leisten und -Befehle</span><span class="sxs-lookup"><span data-stu-id="41c28-108">Appbars and commands</span></span>

### <a name="app-bar"></a><span data-ttu-id="41c28-109">App-Leiste</span><span class="sxs-lookup"><span data-stu-id="41c28-109">App bar</span></span>
<span data-ttu-id="41c28-110">Eine Symbolleiste für anwendungsspezifische Befehle.</span><span class="sxs-lookup"><span data-stu-id="41c28-110">A toolbar for displaying application-specific commands.</span></span> <span data-ttu-id="41c28-111">Siehe Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="41c28-111">See Command bar.</span></span>

<span data-ttu-id="41c28-112">Referenz: [AppBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-112">Reference: [AppBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbar.aspx)</span></span> 

### <a name="app-bar-button"></a><span data-ttu-id="41c28-113">App-Leistenschaltfläche</span><span class="sxs-lookup"><span data-stu-id="41c28-113">App bar button</span></span>
<span data-ttu-id="41c28-114">Eine Schaltfläche, die Befehle in Form einer App-Leiste anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-114">A button for showing commands using app bar styling.</span></span>

![Symbole für App-Leistenschaltflächen](images/controls/app-bar-buttons.png) 

<span data-ttu-id="41c28-116">Referenz: [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [SymbolIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.symbolicon.aspx), [BitmapIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.bitmapicon.aspx), [FontIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.fonticon.aspx), [PathIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pathicon.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-116">Reference: [AppBarButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx), [SymbolIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.symbolicon.aspx), [BitmapIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.bitmapicon.aspx), [FontIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.fonticon.aspx), [PathIcon](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pathicon.aspx)</span></span> 

<span data-ttu-id="41c28-117">Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-117">Design and how-to: [App bar and command bar control guide](app-bars.md)</span></span> 

<span data-ttu-id="41c28-118">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="41c28-118">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="app-bar-separator"></a><span data-ttu-id="41c28-119">Trennzeichen der App-Leiste</span><span class="sxs-lookup"><span data-stu-id="41c28-119">App bar separator</span></span>
<span data-ttu-id="41c28-120">Trennt Befehlsgruppen in einer Befehlsleiste grafisch.</span><span class="sxs-lookup"><span data-stu-id="41c28-120">Visually separates groups of commands in a command bar.</span></span>

<span data-ttu-id="41c28-121">Referenz: [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-121">Reference: [AppBarSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarseparator.aspx)</span></span> 

<span data-ttu-id="41c28-122">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="41c28-122">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="app-bar-toggle-button"></a><span data-ttu-id="41c28-123">Umschaltfläche der App-Leiste</span><span class="sxs-lookup"><span data-stu-id="41c28-123">App bar toggle button</span></span>
<span data-ttu-id="41c28-124">Eine Schaltfläche zum Wechseln zwischen den Befehlen in einer Befehlsleiste.</span><span class="sxs-lookup"><span data-stu-id="41c28-124">A button for toggling commands in a command bar.</span></span>

<span data-ttu-id="41c28-125">Referenz: [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-125">Reference: [AppBarToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbartogglebutton.aspx)</span></span> 

<span data-ttu-id="41c28-126">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="41c28-126">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

### <a name="command-bar"></a><span data-ttu-id="41c28-127">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="41c28-127">Command bar</span></span>
<span data-ttu-id="41c28-128">Eine spezielle App-Leiste zum Ändern der Größe von Schaltflächenelementen auf der App-Leiste.</span><span class="sxs-lookup"><span data-stu-id="41c28-128">A specialized app bar that handles the resizing of app bar button elements.</span></span>

![Befehlsleistensteuerelement](images/command-bar-compact.png)

```xaml
<CommandBar>
    <AppBarButton Icon="Back" Label="Back" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Stop" Label="Stop" Click="AppBarButton_Click"/>
    <AppBarButton Icon="Play" Label="Play" Click="AppBarButton_Click"/>
</CommandBar>
```
<span data-ttu-id="41c28-130">Referenz: [CommandBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-130">Reference: [CommandBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx)</span></span> 

<span data-ttu-id="41c28-131">Design und Vorgehensweise: [App-Leiste und Befehlsleiste](app-bars.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-131">Design and how-to: [App bar and command bar control guide](app-bars.md)</span></span>

<span data-ttu-id="41c28-132">Beispielcode: [Beispiel für XAML-Befehle](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span><span class="sxs-lookup"><span data-stu-id="41c28-132">Sample code: [XAML Commanding sample](http://go.microsoft.com/fwlink/p/?LinkId=620019)</span></span>

## <a name="buttons"></a><span data-ttu-id="41c28-133">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="41c28-133">Buttons</span></span>

### <a name="button"></a><span data-ttu-id="41c28-134">Button</span><span class="sxs-lookup"><span data-stu-id="41c28-134">Button</span></span>
<span data-ttu-id="41c28-135">Ein Steuerelement, das auf Benutzereingaben reagiert und ein **Click**-Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="41c28-135">A control that responds to user input and raises a **Click** event.</span></span>

![Standardschaltfläche](images/controls/button.png)

```xaml
<Button x:Name="button1" Content="Button" 
        Click="Button_Click" />
```

<span data-ttu-id="41c28-137">Referenz: [Button](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.button.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-137">Reference: [Button](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.button.aspx)</span></span> 

<span data-ttu-id="41c28-138">Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-138">Design and how-to: [Buttons control guide](buttons.md)</span></span> 

### <a name="hyperlink"></a><span data-ttu-id="41c28-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="41c28-139">Hyperlink</span></span>
<span data-ttu-id="41c28-140">Siehe „Linkschaltfläche“.</span><span class="sxs-lookup"><span data-stu-id="41c28-140">See Hyperlink button.</span></span>

### <a name="hyperlink-button"></a><span data-ttu-id="41c28-141">Linkschaltfläche</span><span class="sxs-lookup"><span data-stu-id="41c28-141">Hyperlink button</span></span>
<span data-ttu-id="41c28-142">Eine Schaltfläche, die als markierter Text dargestellt wird und den angegebenen URI in einem Browser öffnet.</span><span class="sxs-lookup"><span data-stu-id="41c28-142">A button that appears as marked up text and opens the specified URI in a browser.</span></span>

![Linkschaltfläche](images/controls/hyperlink-button.png)

```xaml
<HyperlinkButton Content="www.microsoft.com" 
                 NavigateUri="http://www.microsoft.com"/>
```

<span data-ttu-id="41c28-144">Referenz: [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hyperlinkbutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-144">Reference: [HyperlinkButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hyperlinkbutton.aspx)</span></span> 

<span data-ttu-id="41c28-145">Design und Vorgehensweise: [Richtlinien für Hyperlinks](hyperlinks.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-145">Design and how-to: [Hyperlinks control guide](hyperlinks.md)</span></span>

### <a name="repeat-button"></a><span data-ttu-id="41c28-146">Wiederholungsschaltfläche</span><span class="sxs-lookup"><span data-stu-id="41c28-146">Repeat button</span></span>
<span data-ttu-id="41c28-147">Eine Schaltfläche, die ihr **Click**-Ereignis auslöst, das andauert, solange die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="41c28-147">A button that raises its **Click** event repeatedly from the time it's pressed until it's released.</span></span> 

![Ein Schaltflächen-Steuerelement zum Wiederholen](images/controls/repeat-button.png) 

```xaml
<RepeatButton x:Name="repeatButton1" Content="Repeat Button" 
              Click="RepeatButton_Click" />
```

<span data-ttu-id="41c28-149">Referenz: [RepeatButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.repeatbutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-149">Reference: [RepeatButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.repeatbutton.aspx)</span></span> 

<span data-ttu-id="41c28-150">Design und Vorgehensweise: [Richtlinien für Schaltflächen](buttons.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-150">Design and how-to: [Buttons control guide](buttons.md)</span></span> 

## <a name="collectiondata-controls"></a><span data-ttu-id="41c28-151">Sammlungs-/Datensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-151">Collection/data controls</span></span>

### <a name="flip-view"></a><span data-ttu-id="41c28-152">Flip-Ansicht</span><span class="sxs-lookup"><span data-stu-id="41c28-152">Flip view</span></span>
<span data-ttu-id="41c28-153">Ein Steuerelement, das eine Sammlung von Elementen darstellt, durch die der Benutzer jeweils einzeln blättern kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-153">A control that presents a collection of items that the user can flip through, one item at a time.</span></span>

```xaml
<FlipView x:Name="flipView1" SelectionChanged="FlipView_SelectionChanged">
    <Image Source="Assets/Logo.png" />
    <Image Source="Assets/SplashScreen.png" />
    <Image Source="Assets/SmallLogo.png" />
</FlipView>
```

<span data-ttu-id="41c28-154">Referenz: [FlipView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-154">Reference: [FlipView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview.aspx)</span></span> 

<span data-ttu-id="41c28-155">Design und Vorgehensweise: [Richtlinien für Flip-Ansicht](flipview.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-155">Design and how-to: [Flip view control guide](flipview.md)</span></span> 

### <a name="grid-view"></a><span data-ttu-id="41c28-156">Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="41c28-156">Grid view</span></span>
<span data-ttu-id="41c28-157">Ein Steuerelement, das eine Sammlung von Elementen in Zeilen und Spalten darstellt, für die ein vertikaler Bildlauf durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-157">A control that presents a collection of items in rows and columns that can scroll vertically.</span></span>

```xaml
<GridView x:Name="gridView1" SelectionChanged="GridView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</GridView>
```

<span data-ttu-id="41c28-158">Referenz: [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-158">Reference: [GridView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.gridview.aspx)</span></span> 

<span data-ttu-id="41c28-159">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-159">Design and how-to: [Lists](lists.md)</span></span> 

<span data-ttu-id="41c28-160">Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span><span class="sxs-lookup"><span data-stu-id="41c28-160">Sample code: [ListView sample](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span></span>

### <a name="items-control"></a><span data-ttu-id="41c28-161">Elementsteuerelement</span><span class="sxs-lookup"><span data-stu-id="41c28-161">Items control</span></span>
<span data-ttu-id="41c28-162">Ein Steuerelement, das eine Sammlung von Elementen auf einer Benutzeroberfläche darstellt, die durch eine Datenvorlage angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="41c28-162">A control that presents a collection of items in a UI specified by a data template.</span></span> 

```xaml
<ItemsControl/>
```

<span data-ttu-id="41c28-163">Referenz: [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-163">Reference: [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx)</span></span> 

### <a name="list-view"></a><span data-ttu-id="41c28-164">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="41c28-164">List view</span></span>
<span data-ttu-id="41c28-165">Ein Steuerelement, das eine Sammlung von Elementen in einer Liste darstellt, für die ein horizontaler Bildlauf durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-165">A control that presents a collection of items in a list that can scroll vertically.</span></span>

```xaml
<ListView x:Name="listView1" SelectionChanged="ListView_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
</ListView>
```

<span data-ttu-id="41c28-166">Referenz: [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-166">Reference: [ListView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listview.aspx)</span></span> 

<span data-ttu-id="41c28-167">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-167">Design and how-to: [Lists](lists.md)</span></span> 

<span data-ttu-id="41c28-168">Beispielcode: [ListView-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span><span class="sxs-lookup"><span data-stu-id="41c28-168">Sample code: [ListView sample](http://go.microsoft.com/fwlink/p/?LinkId=619900)</span></span>

## <a name="date-and-time-controls"></a><span data-ttu-id="41c28-169">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-169">Date and time controls</span></span>

### <a name="calendar-date-picker"></a><span data-ttu-id="41c28-170">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="41c28-170">Calendar date picker</span></span>
<span data-ttu-id="41c28-171">Ein Steuerelement, mit dem Benutzer ein Datum über eine Kalender-Dropdownanzeige auswählen können.</span><span class="sxs-lookup"><span data-stu-id="41c28-171">A control that lets a user select a date using a drop-down calendar display.</span></span>

![Kalenderdatumsauswahl mit offener Kalenderansicht](images/controls/calendar-date-picker-open.png)

```xaml
<CalendarDatePicker/>
```

<span data-ttu-id="41c28-173">Referenz: [CalendarDatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-173">Reference: [CalendarDatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx)</span></span> 

<span data-ttu-id="41c28-174">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-174">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>
 
### <a name="calendar-view"></a><span data-ttu-id="41c28-175">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="41c28-175">Calendar view</span></span>
<span data-ttu-id="41c28-176">Eine konfigurierbare Kalenderanzeige, in der Benutzer ein einzelnes Datum oder mehrere Daten auswählen können.</span><span class="sxs-lookup"><span data-stu-id="41c28-176">A configurable calendar display that lets a user select single or multiple dates.</span></span>

```xaml
<CalendarView/>
```

<span data-ttu-id="41c28-177">Referenz: [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-177">Reference: [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx)</span></span> 

<span data-ttu-id="41c28-178">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-178">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span> 

### <a name="date-picker"></a><span data-ttu-id="41c28-179">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="41c28-179">Date picker</span></span>
<span data-ttu-id="41c28-180">Ein Steuerelement, mit dem ein Benutzer ein Datum auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-180">A control that lets a user select a date.</span></span>

![Datumsauswahlsteuerelement](images/controls/date-picker.png)

```xaml
<DatePicker Header="Arrival Date"/>
```

<span data-ttu-id="41c28-182">Referenz: [DatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-182">Reference: [DatePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx)</span></span> 

<span data-ttu-id="41c28-183">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-183">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>
 
### <a name="time-picker"></a><span data-ttu-id="41c28-184">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="41c28-184">Time picker</span></span>
<span data-ttu-id="41c28-185">Ein Steuerelement, mit dem ein Benutzer einen Zeitwert auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-185">A control that lets a user set a time value.</span></span>

![TimePicker-Steuerelement](images/controls/time-picker.png) 

```xaml
<TimePicker Header="Arrival Time"/>
```

<span data-ttu-id="41c28-187">Referenz: [TimePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-187">Reference: [TimePicker](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx)</span></span> 

<span data-ttu-id="41c28-188">Design und Vorgehensweise: [Richtlinien für Datums- und Uhrzeitsteuerelemente](date-and-time.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-188">Design and how-to: [Calendar, date, and time controls](date-and-time.md)</span></span>

## <a name="flyouts"></a><span data-ttu-id="41c28-189">Flyouts</span><span class="sxs-lookup"><span data-stu-id="41c28-189">Flyouts</span></span>

### <a name="context-menu"></a><span data-ttu-id="41c28-190">Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="41c28-190">Context menu</span></span>
<span data-ttu-id="41c28-191">Siehe „Menü-Flyout“ und „Popupmenü“.</span><span class="sxs-lookup"><span data-stu-id="41c28-191">See Menu flyout and Popup menu.</span></span>

### <a name="flyout"></a><span data-ttu-id="41c28-192">Flyout</span><span class="sxs-lookup"><span data-stu-id="41c28-192">Flyout</span></span>
<span data-ttu-id="41c28-193">Zeigt eine Meldung an, die einen Benutzereingriff erfordert.</span><span class="sxs-lookup"><span data-stu-id="41c28-193">Displays a message that requires user interaction.</span></span> <span data-ttu-id="41c28-194">(Im Gegensatz zu einem Dialogfeld wird von einem Flyout kein separates Fenster erstellt und keine Benutzerinteraktion blockiert.)</span><span class="sxs-lookup"><span data-stu-id="41c28-194">(Unlike a dialog, a flyout does not create a separate window, and does not block other user interaction.)</span></span>

![Flyout-Steuerelement](images/controls/flyout.png)

```xaml
<Flyout>
    <StackPanel>
        <TextBlock Text="All items will be removed. Do you want to continue?"/>
        <Button Click="DeleteConfirmation_Click" Content="Yes, empty my cart"/>
    </StackPanel>
</Flyout>
```

<span data-ttu-id="41c28-196">Referenz: [Flyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flyout.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-196">Reference: [Flyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flyout.aspx)</span></span> 

<span data-ttu-id="41c28-197">Design und Vorgehensweise: [Kontextmenüs und Dialogfelder](dialogs.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-197">Design and how-to: [Context menus and dialogs](dialogs.md)</span></span> 

### <a name="menu-flyout"></a><span data-ttu-id="41c28-198">Menü-Flyout</span><span class="sxs-lookup"><span data-stu-id="41c28-198">Menu flyout</span></span>
<span data-ttu-id="41c28-199">Zeigt vorübergehend eine Liste der Befehle oder Optionen im Kontext der Benutzeraktion an.</span><span class="sxs-lookup"><span data-stu-id="41c28-199">Temporarily displays a list of commands or options related to what the user is currently doing.</span></span>

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

<span data-ttu-id="41c28-201">Referenz: [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyout.aspx), [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-201">Reference: [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyout.aspx), [MenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutitem.aspx), [MenuFlyoutSeparator](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.menuflyoutseparator.aspx), [ToggleMenuFlyoutItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.togglemenuflyoutitem.aspx)</span></span> 

<span data-ttu-id="41c28-202">Design und Vorgehensweise: [Kontextmenüs und Dialogfelder](dialogs.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-202">Design and how-to: [Context menus and dialogs](dialogs.md)</span></span> 

<span data-ttu-id="41c28-203">Beispielcode: [Beispiel für XAML-Kontextmenü](http://go.microsoft.com/fwlink/p/?LinkId=620021)</span><span class="sxs-lookup"><span data-stu-id="41c28-203">Sample code: [XAML Context Menu sample](http://go.microsoft.com/fwlink/p/?LinkId=620021)</span></span>

### <a name="popup-menu"></a><span data-ttu-id="41c28-204">Popupmenü</span><span class="sxs-lookup"><span data-stu-id="41c28-204">Popup menu</span></span>
<span data-ttu-id="41c28-205">Ein benutzerdefiniertes Menü mit von Ihnen angegebenen Befehlen.</span><span class="sxs-lookup"><span data-stu-id="41c28-205">A custom menu that presents commands that you specify.</span></span>

<span data-ttu-id="41c28-206">Referenz: [PopupMenu](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.popups.popupmenu.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-206">Reference: [PopupMenu](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.popups.popupmenu.aspx)</span></span> 

<span data-ttu-id="41c28-207">Design und Vorgehensweise: [Kontextmenüs und Dialogfelder](dialogs.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-207">Design and how-to: [Context menus and dialogs](dialogs.md)</span></span> 

### <a name="tooltip"></a><span data-ttu-id="41c28-208">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="41c28-208">Tooltip</span></span>
<span data-ttu-id="41c28-209">Ein Popupfenster, das Informationen zu einem Element anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-209">A pop-up window that displays information for an element.</span></span> 
 
![QuickInfo-Steuerelement](images/controls/tool-tip.png)

```xaml
<Button Content="Button" Click="Button_Click" 
        ToolTipService.ToolTip="Click to perform action" />
```

<span data-ttu-id="41c28-211">Referenz: [ToolTip](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltip.aspx), [ToolTipService](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltipservice.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-211">Reference: [ToolTip](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltip.aspx), [ToolTipService](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.tooltipservice.aspx)</span></span> 

<span data-ttu-id="41c28-212">Design und Vorgehensweise: Richtlinien für QuickInfos</span><span class="sxs-lookup"><span data-stu-id="41c28-212">Design and how-to: Guidelines for tooltips</span></span> 

## <a name="images"></a><span data-ttu-id="41c28-213">Bilder</span><span class="sxs-lookup"><span data-stu-id="41c28-213">Images</span></span>

### <a name="image"></a><span data-ttu-id="41c28-214">Image</span><span class="sxs-lookup"><span data-stu-id="41c28-214">Image</span></span>
<span data-ttu-id="41c28-215">Ein Steuerelement, das ein Bild darstellt.</span><span class="sxs-lookup"><span data-stu-id="41c28-215">A control that presents an image.</span></span>

```xaml
<Image Source="Assets/Logo.png" />
```

<span data-ttu-id="41c28-216">Referenz: [Image](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.image.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-216">Reference: [Image](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.image.aspx)</span></span> 

<span data-ttu-id="41c28-217">Design und Vorgehensweise: [Image und ImageBrush](images-imagebrushes.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-217">Design and how-to: [Image and ImageBrush](images-imagebrushes.md)</span></span> 

<span data-ttu-id="41c28-218">Beispielcode: [Beispiel für XAML-Bilder](http://go.microsoft.com/fwlink/p/?linkid=226867)</span><span class="sxs-lookup"><span data-stu-id="41c28-218">Sample code: [XAML images sample](http://go.microsoft.com/fwlink/p/?linkid=226867)</span></span>

## <a name="graphics-and-ink"></a><span data-ttu-id="41c28-219">Grafiken und Freihandstriche</span><span class="sxs-lookup"><span data-stu-id="41c28-219">Graphics and ink</span></span>

### <a name="inkcanvas"></a><span data-ttu-id="41c28-220">InkCanvas</span><span class="sxs-lookup"><span data-stu-id="41c28-220">InkCanvas</span></span>
<span data-ttu-id="41c28-221">Ein Steuerelement, das Freihandstriche empfängt und anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-221">A control that receives and displays ink strokes.</span></span>

```xaml
<InkCanvas/>
```

<span data-ttu-id="41c28-222">Referenz: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.inkcanvas.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-222">Reference: [InkCanvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.inkcanvas.aspx)</span></span> 

### <a name="shapes"></a><span data-ttu-id="41c28-223">Formen</span><span class="sxs-lookup"><span data-stu-id="41c28-223">Shapes</span></span>
<span data-ttu-id="41c28-224">Verschiedene grafische Speichermodusobjekte, die als Ellipsen, Rechtecke, Linien, Bézierpfade usw. dargestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="41c28-224">Various retained mode graphical objects that can be presented like ellipses, rectangles, lines, Bezier paths, etc.</span></span>

![<span data-ttu-id="41c28-225">Ein Polygon](images/controls/shapes-polygon.png) 
![Ein Pfad</span><span class="sxs-lookup"><span data-stu-id="41c28-225">A polygon](images/controls/shapes-polygon.png) 
![A path</span></span>](images/controls/shapes-path.png) 

```xaml
<Ellipse/>
<Path/>
<Rectangle/>
```

<span data-ttu-id="41c28-226">Referenz: [Shapes](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.shapes.shape.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-226">Reference: [Shapes](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.shapes.shape.aspx)</span></span> 

<span data-ttu-id="41c28-227">So wird's gemacht: [Zeichnen von Formen](../../graphics/drawing-shapes.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-227">How to: [Drawing shapes](../../graphics/drawing-shapes.md)</span></span> 

<span data-ttu-id="41c28-228">Beispielcode: [Beispiel für vektorbasierte XAML-Zeichnung](http://go.microsoft.com/fwlink/p/?linkid=226866)</span><span class="sxs-lookup"><span data-stu-id="41c28-228">Sample code: [XAML vector-based drawing sample](http://go.microsoft.com/fwlink/p/?linkid=226866)</span></span>

## <a name="layout-controls"></a><span data-ttu-id="41c28-229">Layoutsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-229">Layout controls</span></span>

### <a name="border"></a><span data-ttu-id="41c28-230">Rahmen</span><span class="sxs-lookup"><span data-stu-id="41c28-230">Border</span></span>
<span data-ttu-id="41c28-231">Ein Containersteuerelement, das einen Rahmen, einen Hintergrund oder beides um ein anderes Objekt herum zeichnet.</span><span class="sxs-lookup"><span data-stu-id="41c28-231">A container control that draws a border, background, or both, around another object.</span></span>

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

<span data-ttu-id="41c28-233">Referenz: [Border](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.border.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-233">Reference: [Border](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.border.aspx)</span></span>

### <a name="canvas"></a><span data-ttu-id="41c28-234">Canvas</span><span class="sxs-lookup"><span data-stu-id="41c28-234">Canvas</span></span>
<span data-ttu-id="41c28-235">Ein Layoutpanel, das die absolute Positionierung untergeordneter Elemente relativ zur oberen linken Ecke der Canvas unterstützt.</span><span class="sxs-lookup"><span data-stu-id="41c28-235">A layout panel that supports the absolute positioning of child elements relative to the top left corner of the canvas.</span></span>
 
![Canvas-Layoutpanel](images/controls/canvas.png) 

```xaml
<Canvas Width="120" Height="120">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" Canvas.Left="20" Canvas.Top="20"/>
    <Rectangle Fill="Green" Canvas.Left="40" Canvas.Top="40"/>
    <Rectangle Fill="Orange" Canvas.Left="60" Canvas.Top="60"/>
</Canvas>
```

<span data-ttu-id="41c28-237">Referenz: [Canvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.canvas.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-237">Reference: [Canvas](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.canvas.aspx)</span></span>
 
### <a name="grid"></a><span data-ttu-id="41c28-238">Raster</span><span class="sxs-lookup"><span data-stu-id="41c28-238">Grid</span></span>
<span data-ttu-id="41c28-239">Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="41c28-239">A layout panel that supports the arranging of child elements in rows and columns.</span></span>

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

<span data-ttu-id="41c28-241">Referenz: [Grid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-241">Reference: [Grid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)</span></span>
 
### <a name="panning-scroll-viewer"></a><span data-ttu-id="41c28-242">Verschiebungs-Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="41c28-242">Panning scroll viewer</span></span>
<span data-ttu-id="41c28-243">Siehe „Bildlaufanzeige“.</span><span class="sxs-lookup"><span data-stu-id="41c28-243">See Scroll viewer.</span></span>

### <a name="relativepanel"></a><span data-ttu-id="41c28-244">RelativePanel</span><span class="sxs-lookup"><span data-stu-id="41c28-244">RelativePanel</span></span>
<span data-ttu-id="41c28-245">Ein Bereich, in dem Sie untergeordnete Objekte relativ zueinander oder in Relation zum übergeordneten Objekt positionieren und ausrichten können.</span><span class="sxs-lookup"><span data-stu-id="41c28-245">A panel that lets you position and align child objects in relation to each other or the parent panel.</span></span>

![RelativePanel-Layoutpanel](images/controls/relative-panel.png) 

```xaml
<RelativePanel>
    <TextBox x:Name="textBox1" RelativePanel.AlignLeftWithPanel="True"/>
    <Button Content="Submit" RelativePanel.Below="textBox1"/>
</RelativePanel>
```

<span data-ttu-id="41c28-247">Referenz: [RelativePanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.relativepanel.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-247">Reference: [RelativePanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.relativepanel.aspx)</span></span>

### <a name="scroll-bar"></a><span data-ttu-id="41c28-248">Bildlaufleiste</span><span class="sxs-lookup"><span data-stu-id="41c28-248">Scroll bar</span></span>
<span data-ttu-id="41c28-249">Siehe Bildlaufanzeige.</span><span class="sxs-lookup"><span data-stu-id="41c28-249">See scroll viewer.</span></span> <span data-ttu-id="41c28-250">(ScrollBar ist ein Element von ScrollViewer.</span><span class="sxs-lookup"><span data-stu-id="41c28-250">(ScrollBar is an element of ScrollViewer.</span></span> <span data-ttu-id="41c28-251">Es wird normalerweise nicht als eigenständiges Steuerelement verwendet.)</span><span class="sxs-lookup"><span data-stu-id="41c28-251">You don't typically use it as a stand-alone control.)</span></span>

<span data-ttu-id="41c28-252">Referenz: [ScrollBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-252">Reference: [ScrollBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.scrollbar.aspx)</span></span>
 
### <a name="scroll-viewer"></a><span data-ttu-id="41c28-253">Bildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="41c28-253">Scroll viewer</span></span>
<span data-ttu-id="41c28-254">Ein Containersteuerelement, mit dem der Benutzer Inhalte verschieben und vergrößern/verkleinern kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-254">A container control that lets the user pan and zoom its content.</span></span>

```xaml
<ScrollViewer ZoomMode="Enabled" MaxZoomFactor="10" 
              HorizontalScrollMode="Enabled" 
              HorizontalScrollBarVisibility="Visible"
              Height="200" Width="200">
    <Image Source="Assets/Logo.png" Height="400" Width="400"/>
</ScrollViewer>
```

<span data-ttu-id="41c28-255">Referenz: [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-255">Reference: [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.scrollviewer.aspx)</span></span>

<span data-ttu-id="41c28-256">Design und Vorgehensweise: [Bildlaufleisten](scroll-controls.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-256">Design and how-to: [Scroll and panning controls guide](scroll-controls.md)</span></span> 

<span data-ttu-id="41c28-257">Beispielcode: [Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom](http://go.microsoft.com/fwlink/p/?linkid=238577)</span><span class="sxs-lookup"><span data-stu-id="41c28-257">Sample code: [XAML scrolling, panning and zooming sample](http://go.microsoft.com/fwlink/p/?linkid=238577)</span></span>

### <a name="stack-panel"></a><span data-ttu-id="41c28-258">StackPanel</span><span class="sxs-lookup"><span data-stu-id="41c28-258">Stack panel</span></span>
<span data-ttu-id="41c28-259">Ein Layoutpanel, das untergeordnete Elemente in einer einzelnen Zeile anordnet. Die Zeile kann horizontal oder vertikal ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="41c28-259">A layout panel that arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>

![StackPanel-Layoutsteuerelement](images/controls/stack-panel.png) 

```xaml
<StackPanel>
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue"/>
    <Rectangle Fill="Green"/>
    <Rectangle Fill="Orange"/>
</StackPanel>
```

<span data-ttu-id="41c28-261">Referenz: [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-261">Reference: [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)</span></span>
 
### <a name="variablesizedwrapgrid"></a><span data-ttu-id="41c28-262">VariableSizedWrapGrid</span><span class="sxs-lookup"><span data-stu-id="41c28-262">VariableSizedWrapGrid</span></span>
<span data-ttu-id="41c28-263">Ein Layoutpanel, das die Anordnung von untergeordneten Elementen in Zeilen und Spalten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="41c28-263">A layout panel that supports the arranging of child elements in rows and columns.</span></span> <span data-ttu-id="41c28-264">Jedes untergeordnete Element kann sich über mehrere Zeilen und Spalten erstrecken.</span><span class="sxs-lookup"><span data-stu-id="41c28-264">Each child element can span multiple rows and columns.</span></span>

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

<span data-ttu-id="41c28-266">Referenz: [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.variablesizedwrapgrid.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-266">Reference: [VariableSizedWrapGrid](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.variablesizedwrapgrid.aspx)</span></span>

### <a name="viewbox"></a><span data-ttu-id="41c28-267">Viewbox</span><span class="sxs-lookup"><span data-stu-id="41c28-267">Viewbox</span></span>
<span data-ttu-id="41c28-268">Ein Containersteuerelement, das seinen Inhalt auf eine angegebene Größe skaliert.</span><span class="sxs-lookup"><span data-stu-id="41c28-268">A container control that scales its content to a specified size.</span></span>

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

<span data-ttu-id="41c28-270">Referenz: [Viewbox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.viewbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-270">Reference: [Viewbox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.viewbox.aspx)</span></span>
 
### <a name="zooming-scroll-viewer"></a><span data-ttu-id="41c28-271">Zoombildlaufanzeige</span><span class="sxs-lookup"><span data-stu-id="41c28-271">Zooming scroll viewer</span></span>
<span data-ttu-id="41c28-272">Siehe „Bildlaufanzeige“.</span><span class="sxs-lookup"><span data-stu-id="41c28-272">See Scroll viewer.</span></span>

## <a name="media-controls"></a><span data-ttu-id="41c28-273">Mediensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-273">Media controls</span></span>

### <a name="audio"></a><span data-ttu-id="41c28-274">Audio</span><span class="sxs-lookup"><span data-stu-id="41c28-274">Audio</span></span>
<span data-ttu-id="41c28-275">Siehe „Medienelement“.</span><span class="sxs-lookup"><span data-stu-id="41c28-275">See Media element.</span></span>

### <a name="media-element"></a><span data-ttu-id="41c28-276">Medienelement</span><span class="sxs-lookup"><span data-stu-id="41c28-276">Media element</span></span>
<span data-ttu-id="41c28-277">Ein Steuerelement, das Audio- und Videoinhalte wiedergibt.</span><span class="sxs-lookup"><span data-stu-id="41c28-277">A control that plays audio and video content.</span></span>

```xaml
<MediaElement x:Name="myMediaElement"/>
```

<span data-ttu-id="41c28-278">Referenz: [MediaElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediaelement.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-278">Reference: [MediaElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediaelement.aspx)</span></span> 

<span data-ttu-id="41c28-279">Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-279">Design and how-to: [Media element control guide](media-playback.md)</span></span>

### <a name="mediatransportcontrols"></a><span data-ttu-id="41c28-280">MediaTransportControls</span><span class="sxs-lookup"><span data-stu-id="41c28-280">MediaTransportControls</span></span>
<span data-ttu-id="41c28-281">Ein Steuerelement, das Wiedergabesteuerelemente für eine „MediaElement“-Klasse bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="41c28-281">A control that provides playback controls for a MediaElement.</span></span>

![Medienelement mit Transportsteuerelementen](images/controls/media-transport-controls.png) 

```xaml
<MediaTransportControls MediaElement="myMediaElement"/>
```

<span data-ttu-id="41c28-283">Referenz: [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-283">Reference: [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)</span></span> 

<span data-ttu-id="41c28-284">Design und Vorgehensweise: [Richtlinien für Mediaplayer](media-playback.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-284">Design and how-to: [Media element control guide](media-playback.md)</span></span> 

<span data-ttu-id="41c28-285">Beispielcode: [Beispiel für die Steuerelemente für den Medientransport](http://go.microsoft.com/fwlink/p/?LinkId=620023)</span><span class="sxs-lookup"><span data-stu-id="41c28-285">Sample code: [Media Transport Controls sample](http://go.microsoft.com/fwlink/p/?LinkId=620023)</span></span>

### <a name="video"></a><span data-ttu-id="41c28-286">Video</span><span class="sxs-lookup"><span data-stu-id="41c28-286">Video</span></span>
<span data-ttu-id="41c28-287">Siehe „Medienelement“.</span><span class="sxs-lookup"><span data-stu-id="41c28-287">See Media element.</span></span>

## <a name="navigation"></a><span data-ttu-id="41c28-288">Navigation</span><span class="sxs-lookup"><span data-stu-id="41c28-288">Navigation</span></span>

### <a name="hub"></a><span data-ttu-id="41c28-289">Hub</span><span class="sxs-lookup"><span data-stu-id="41c28-289">Hub</span></span>
<span data-ttu-id="41c28-290">Ein Containersteuerelement, mit dem der Benutzer verschiedene Abschnitte des Inhalts anzeigen und zu ihnen navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-290">A container control that lets the user view and navigate to different sections of content.</span></span>

```xaml
<Hub>
    <HubSection>
        <!--- hub section content -->
    </HubSection>
    <HubSection>
        <!--- hub section content -->
    </HubSection>
</Hub>
```

<span data-ttu-id="41c28-291">Referenz: [Hub](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hub.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-291">Reference: [Hub](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.hub.aspx)</span></span> 

<span data-ttu-id="41c28-292">Design und Vorgehensweise: [Richtlinien für Hub-Steuerelement](hub.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-292">Design and how-to: [Hub control guide](hub.md)</span></span> 

<span data-ttu-id="41c28-293">Beispielcode: [Beispiel für das XAML-Hub-Steuerelement](http://go.microsoft.com/fwlink/p/?LinkID=309828)</span><span class="sxs-lookup"><span data-stu-id="41c28-293">Sample code:[XAML Hub control sample](http://go.microsoft.com/fwlink/p/?LinkID=309828)</span></span>

### <a name="pivot"></a><span data-ttu-id="41c28-294">Pivot</span><span class="sxs-lookup"><span data-stu-id="41c28-294">Pivot</span></span>
<span data-ttu-id="41c28-295">Ein Vollbild-Container und Navigationsmodell, das auch eine schnelle Methode zum Wechseln zwischen verschiedenen Pivots (Ansichten oder Filtern) bereitstellt, die sich üblicherweise im gleichen Datensatz befinden.</span><span class="sxs-lookup"><span data-stu-id="41c28-295">A full-screen container and navigation model that also provides a quick way to move between different pivots (views or filters), typically in the same set of data.</span></span>

<span data-ttu-id="41c28-296">Das „Pivot“-Steuerelement kann mit einem Registerkartenlayout formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="41c28-296">The Pivot control can be styled to have a "tab" layout.</span></span>

<span data-ttu-id="41c28-297">Referenz: [Pivot](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-297">Reference: [Pivot](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.aspx)</span></span> 

<span data-ttu-id="41c28-298">Design und Vorgehensweise: [Richtlinien für Pivots](tabs-pivot.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-298">Design and how-to: [Tabs and pivot control guide](tabs-pivot.md)</span></span> 

<span data-ttu-id="41c28-299">Beispielcode: [Pivot-Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=619903&amp;clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="41c28-299">Sample code: [Pivot sample](http://go.microsoft.com/fwlink/p/?LinkId=619903&amp;clcid=0x409)</span></span>

### <a name="semantic-zoom"></a><span data-ttu-id="41c28-300">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="41c28-300">Semantic zoom</span></span>
<span data-ttu-id="41c28-301">Ein Containersteuerelement, das es dem Benutzer ermöglicht, zwischen zwei Ansichten einer Sammlung zu zoomen.</span><span class="sxs-lookup"><span data-stu-id="41c28-301">A container control that lets the user zoom between two views of a collection of items.</span></span>

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

<span data-ttu-id="41c28-302">Referenz: [SemanticZoom](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-302">Reference: [SemanticZoom](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.semanticzoom.aspx)</span></span> 

<span data-ttu-id="41c28-303">Design und Vorgehensweise: [Richtlinien für den semantischen Zoom](semantic-zoom.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-303">Design and how-to: [Semantic zoom control guide](semantic-zoom.md)</span></span> 

<span data-ttu-id="41c28-304">Beispielcode: [Beispiel für XAML-GridView-Gruppierung und -SemanticZoom](http://go.microsoft.com/fwlink/p/?linkid=226564)</span><span class="sxs-lookup"><span data-stu-id="41c28-304">Sample code: [XAML GridView grouping and SemanticZoom sample](http://go.microsoft.com/fwlink/p/?linkid=226564)</span></span>

### <a name="splitview"></a><span data-ttu-id="41c28-305">SplitView</span><span class="sxs-lookup"><span data-stu-id="41c28-305">SplitView</span></span>
<span data-ttu-id="41c28-306">Ein Containersteuerelement mit zwei Ansichten: einer Ansicht für den Hauptinhalt und einer weiteren Ansicht, die in der Regel für ein Navigationsmenü verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="41c28-306">A container control with two views; one view for the main content and another view that is typically used for a navigation menu.</span></span>

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

<span data-ttu-id="41c28-308">Referenz: [SplitView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.splitview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-308">Reference: [SplitView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.splitview.aspx)</span></span> 

<span data-ttu-id="41c28-309">Design und Vorgehensweise: [Richtlinien für das Steuerelement für die geteilte Ansicht](split-view.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-309">Design and how-to: [Split view control guide](split-view.md)</span></span>

### <a name="web-view"></a><span data-ttu-id="41c28-310">Webansicht</span><span class="sxs-lookup"><span data-stu-id="41c28-310">Web view</span></span>
<span data-ttu-id="41c28-311">Ein Containersteuerelement, das Webinhalt hostet.</span><span class="sxs-lookup"><span data-stu-id="41c28-311">A container control that hosts web content.</span></span>

```xaml
<WebView x:Name="webView1" Source="http://dev.windows.com" 
         Height="400" Width="800"/>
```

<span data-ttu-id="41c28-312">Referenz: [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-312">Reference: [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)</span></span> 

<span data-ttu-id="41c28-313">Design und Vorgehensweise: Richtlinien für Webansichten</span><span class="sxs-lookup"><span data-stu-id="41c28-313">Design and how-to: Guidelines for Web views</span></span> 

<span data-ttu-id="41c28-314">Beispielcode: [Beispiel für XAML-WebView-Steuerelement](http://go.microsoft.com/fwlink/p/?linkid=238582)</span><span class="sxs-lookup"><span data-stu-id="41c28-314">Sample code: [XAML WebView control sample](http://go.microsoft.com/fwlink/p/?linkid=238582)</span></span>

## <a name="progress-controls"></a><span data-ttu-id="41c28-315">Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-315">Progress controls</span></span>

### <a name="progress-bar"></a><span data-ttu-id="41c28-316">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="41c28-316">Progress bar</span></span>
<span data-ttu-id="41c28-317">Ein Steuerelement, das den Fortschritt durch Anzeigen einer Leiste angibt.</span><span class="sxs-lookup"><span data-stu-id="41c28-317">A control that indicates progress by displaying a bar.</span></span>

![Statusleistensteuerelement](images/controls/progress-bar-determinate.png)

<span data-ttu-id="41c28-319">Eine Fortschrittsleiste, die einen bestimmten Wert anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-319">A progress bar that shows a specific value.</span></span>

```xaml
<ProgressBar x:Name="progressBar1" Value="50" Width="100"/>
```

![Steuerelement für unbestimmte Statusanzeige](images/controls/progress-bar-indeterminate.png)

<span data-ttu-id="41c28-321">Eine Fortschrittsleiste, die einen unbestimmten Fortschritt anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-321">A progress bar that shows indeterminate progress.</span></span>

```xaml
<ProgressBar x:Name="indeterminateProgressBar1" IsIndeterminate="True" Width="100"/>
```

<span data-ttu-id="41c28-322">Referenz: [ProgressBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-322">Reference: [ProgressBar](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressbar.aspx)</span></span> 

<span data-ttu-id="41c28-323">Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-323">Design and how-to: [Progress controls guide](progress-controls.md)</span></span> 

### <a name="progress-ring"></a><span data-ttu-id="41c28-324">Statusring</span><span class="sxs-lookup"><span data-stu-id="41c28-324">Progress ring</span></span>
<span data-ttu-id="41c28-325">Ein Steuerelement, das den Status durch Anzeigen eines Rings angibt.</span><span class="sxs-lookup"><span data-stu-id="41c28-325">A control that indicates indeterminate progress by displaying a ring.</span></span> 

![Statusringsteuerelement](images/controls/progress-ring.png) 

```xaml
<ProgressRing x:Name="progressRing1" IsActive="True"/>
```

<span data-ttu-id="41c28-327">Referenz: [ProgressRing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-327">Reference: [ProgressRing](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.progressring.aspx)</span></span> 

<span data-ttu-id="41c28-328">Design und Vorgehensweise: [Richtlinien für Statussteuerelemente](progress-controls.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-328">Design and how-to: [Progress controls guide](progress-controls.md)</span></span> 

## <a name="text-controls"></a><span data-ttu-id="41c28-329">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-329">Text controls</span></span>

### <a name="auto-suggest-box"></a><span data-ttu-id="41c28-330">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="41c28-330">Auto suggest box</span></span>
<span data-ttu-id="41c28-331">Ein Texteingabefeld, das Text vorschlägt, während der Benutzer Zeichen eingibt.</span><span class="sxs-lookup"><span data-stu-id="41c28-331">A text input box that provides suggested text as the user types.</span></span>

![Feld mit automatischen Vorschlägen für die Suche](images/controls/auto-suggest-box.png) 

<span data-ttu-id="41c28-333">Referenz: [AutoSuggestBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-333">Reference: [AutoSuggestBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.autosuggestbox.aspx)</span></span>

<span data-ttu-id="41c28-334">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Feldsteuerelement mit automatischen Vorschlägen](auto-suggest-box.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-334">Design and how-to: [Text controls](text-controls.md), [Auto suggest box control guide](auto-suggest-box.md)</span></span>

<span data-ttu-id="41c28-335">Beispielcode: [Beispiel für AutoSuggestBox-Migration](http://go.microsoft.com/fwlink/p/?LinkId=619996)</span><span class="sxs-lookup"><span data-stu-id="41c28-335">Sample code: [AutoSuggestBox migration sample](http://go.microsoft.com/fwlink/p/?LinkId=619996)</span></span>

### <a name="multi-line-text-box"></a><span data-ttu-id="41c28-336">Mehrzeiliges Textfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-336">Multi-line text box</span></span>
<span data-ttu-id="41c28-337">Siehe „Textfeld“.</span><span class="sxs-lookup"><span data-stu-id="41c28-337">See Text box.</span></span>

### <a name="password-box"></a><span data-ttu-id="41c28-338">Kennwortfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-338">Password box</span></span>
<span data-ttu-id="41c28-339">Ein Steuerelement für die Kennworteingabe.</span><span class="sxs-lookup"><span data-stu-id="41c28-339">A control for entering passwords.</span></span>

 ![Ein Kennwortfeld](images/controls/password-box.png)

```xaml
<PasswordBox x:Name="passwordBox1" 
             PasswordChanged="PasswordBox_PasswordChanged" />
```

<span data-ttu-id="41c28-341">Referenz: [PasswordBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-341">Reference: [PasswordBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.passwordbox.aspx)</span></span> 

<span data-ttu-id="41c28-342">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für Kennwortfelder](password-box.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-342">Design and how-to: [Text controls](text-controls.md), [Password box control guide](password-box.md)</span></span> 

<span data-ttu-id="41c28-343">Beispielcode: [Beispiel für die XAML-Textanzeige](http://go.microsoft.com/fwlink/p/?linkid=238579), [Beispiel für die XAML-Textbearbeitung](http://go.microsoft.com/fwlink/p/?linkid=251417)</span><span class="sxs-lookup"><span data-stu-id="41c28-343">Sample code: [XAML text display sample](http://go.microsoft.com/fwlink/p/?linkid=238579), [XAML text editing sample](http://go.microsoft.com/fwlink/p/?linkid=251417)</span></span>

### <a name="rich-edit-box"></a><span data-ttu-id="41c28-344">Rich-Edit-Feld</span><span class="sxs-lookup"><span data-stu-id="41c28-344">Rich edit box</span></span>
<span data-ttu-id="41c28-345">Ein Steuerelement, mit dem der Benutzer Rich-Text-Dokumente mit Inhalten wie formatiertem Text, Links und Bildern bearbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-345">A control that lets a user edit rich text documents with content like formatted text, hyperlinks, and images.</span></span>

```xaml
<RichEditBox />
```

<span data-ttu-id="41c28-346">Referenz: [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-346">Reference: [RichEditBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richeditbox.aspx)</span></span> 

<span data-ttu-id="41c28-347">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [Richtlinien für RichEditBox-Steuerelement](rich-edit-box.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-347">Design and how-to: [Text controls](text-controls.md), [Rich edit box control guide](rich-edit-box.md)</span></span>

<span data-ttu-id="41c28-348">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="41c28-348">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

### <a name="search-box"></a><span data-ttu-id="41c28-349">Suchfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-349">Search box</span></span>
<span data-ttu-id="41c28-350">Siehe „Feld mit automatischen Vorschlägen“.</span><span class="sxs-lookup"><span data-stu-id="41c28-350">See Auto suggest box.</span></span>

### <a name="single-line-text-box"></a><span data-ttu-id="41c28-351">Einzeiliges Textfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-351">Single-line text box</span></span>
<span data-ttu-id="41c28-352">Siehe „Textfeld“.</span><span class="sxs-lookup"><span data-stu-id="41c28-352">See Text box.</span></span>

### <a name="static-textparagraph"></a><span data-ttu-id="41c28-353">Statischer Text/Absatz</span><span class="sxs-lookup"><span data-stu-id="41c28-353">Static text/paragraph</span></span>
<span data-ttu-id="41c28-354">Siehe „Textblock“.</span><span class="sxs-lookup"><span data-stu-id="41c28-354">See Text block.</span></span>

### <a name="text-block"></a><span data-ttu-id="41c28-355">Textblock</span><span class="sxs-lookup"><span data-stu-id="41c28-355">Text block</span></span>
<span data-ttu-id="41c28-356">Ein Steuerelement, das Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="41c28-356">A control that displays text.</span></span>

![Textblocksteuerelement](images/controls/text-block.png) 

```xaml
<TextBlock x:Name="textBlock1" Text="I am a TextBlock"/>
```

<span data-ttu-id="41c28-358">Referenz: [TextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-358">Reference: [TextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textblock.aspx), [RichTextBlock](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.richtextblock.aspx)</span></span> 

<span data-ttu-id="41c28-359">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBlock](text-block.md), [Richtlinie für Rich-Text-Blocksteuerelemente](rich-text-block.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-359">Design and how-to: [Text controls](text-controls.md), [Text block control guide](text-block.md), [Rich text block control guide](rich-text-block.md)</span></span>

<span data-ttu-id="41c28-360">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="41c28-360">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

### <a name="text-box"></a><span data-ttu-id="41c28-361">Textfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-361">Text box</span></span>
<span data-ttu-id="41c28-362">Ein einzeiliges oder mehrzeiliges Nur-Text-Feld.</span><span class="sxs-lookup"><span data-stu-id="41c28-362">A single-line or multi-line plain text field.</span></span>

![Textfeldsteuerelement](images/controls/text-box.png) 

```xaml
<TextBox x:Name="textBox1" Text="I am a TextBox" 
         TextChanged="TextBox_TextChanged"/>
```

<span data-ttu-id="41c28-364">Referenz: [TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-364">Reference: [TextBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.textbox.aspx)</span></span> 

<span data-ttu-id="41c28-365">Design und Vorgehensweise: [Textsteuerelemente](text-controls.md), [TextBox](text-box.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-365">Design and how-to: [Text controls](text-controls.md), [Text box control guide](text-box.md)</span></span> 

<span data-ttu-id="41c28-366">Beispielcode: [Beispiel für XAML-Text](http://go.microsoft.com/fwlink/p/?linkid=238578)</span><span class="sxs-lookup"><span data-stu-id="41c28-366">Sample code: [XAML text sample](http://go.microsoft.com/fwlink/p/?linkid=238578)</span></span>

## <a name="selection-controls"></a><span data-ttu-id="41c28-367">Auswahlsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="41c28-367">Selection controls</span></span>

### <a name="check-box"></a><span data-ttu-id="41c28-368">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="41c28-368">Check box</span></span>
<span data-ttu-id="41c28-369">Ein Steuerelement, das der Benutzer aktivieren und deaktivieren kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-369">A control that a user can select or clear.</span></span>

![Die drei Zustände eines Kontrollkästchens](images/templates-checkbox-states-default.png)

```xaml
<CheckBox x:Name="checkbox1" Content="CheckBox" 
          Checked="CheckBox_Checked"/>
```

<span data-ttu-id="41c28-371">Referenz: [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-371">Reference: [CheckBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.checkbox.aspx)</span></span> 

<span data-ttu-id="41c28-372">Design und Vorgehensweise: [Richtlinien für Kontrollkästchen](checkbox.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-372">Design and how-to: [Check box control guide](checkbox.md)</span></span> 

### <a name="combo-box"></a><span data-ttu-id="41c28-373">Kombinationsfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-373">Combo box</span></span>
<span data-ttu-id="41c28-374">Eine Dropdownliste mit Elementen, in der ein Benutzer eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-374">A drop-down list of items a user can select from.</span></span>

![Offenes Kombinationsfeld](images/controls/combo-box-open.png) 

```xaml
<ComboBox x:Name="comboBox1" Width="100"
          SelectionChanged="ComboBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ComboBox>
```

<span data-ttu-id="41c28-376">Referenz: [ComboBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.combobox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-376">Reference: [ComboBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.combobox.aspx)</span></span> 

<span data-ttu-id="41c28-377">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-377">Design and how-to: [Lists](lists.md)</span></span> 

### <a name="list-box"></a><span data-ttu-id="41c28-378">Listenfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-378">List box</span></span>
<span data-ttu-id="41c28-379">Ein Steuerelement, das eine Inlineliste mit Elementen darstellt, aus der ein Benutzer eine Auswahl treffen kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-379">A control that presents an inline list of items that the user can select from.</span></span> 

![Listenfeldsteuerelement](images/controls/list-box.png)

```xaml
<ListBox x:Name="listBox1" Width="100"
         SelectionChanged="ListBox_SelectionChanged">
    <x:String>Item 1</x:String>
    <x:String>Item 2</x:String>
    <x:String>Item 3</x:String>
</ListBox>
```

<span data-ttu-id="41c28-381">Referenz: [ListBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listbox.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-381">Reference: [ListBox](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.listbox.aspx)</span></span> 

<span data-ttu-id="41c28-382">Design und Vorgehensweise: [Listen](lists.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-382">Design and how-to: [Lists](lists.md)</span></span> 

### <a name="radio-button"></a><span data-ttu-id="41c28-383">Optionsfeld</span><span class="sxs-lookup"><span data-stu-id="41c28-383">Radio button</span></span>
<span data-ttu-id="41c28-384">Ein Steuerelement, das es einem Benutzer ermöglicht, eine einzelne Option aus einer Gruppe von Optionen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="41c28-384">A control that allows a user to select a single option from a group of options.</span></span> <span data-ttu-id="41c28-385">Gruppierte Optionsfelder schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="41c28-385">When radio buttons are grouped together, they are mutually exclusive.</span></span>

![Optionsfeldsteuerelemente](images/controls/radio-button.png)

```xaml
<RadioButton x:Name="radioButton1" Content="RadioButton 1" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
<RadioButton x:Name="radioButton2" Content="RadioButton 2" GroupName="Group1" 
             Checked="RadioButton_Checked" IsChecked="True"/>
<RadioButton x:Name="radioButton3" Content="RadioButton 3" GroupName="Group1" 
             Checked="RadioButton_Checked"/>
```

<span data-ttu-id="41c28-387">Referenz: [RadioButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.radiobutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-387">Reference: [RadioButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.radiobutton.aspx)</span></span> 

<span data-ttu-id="41c28-388">Design und Vorgehensweise: [Richtlinien für Optionsfelder](radio-button.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-388">Design and how-to: [Radio button control guide](radio-button.md)</span></span>
 
### <a name="slider"></a><span data-ttu-id="41c28-389">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="41c28-389">Slider</span></span>
<span data-ttu-id="41c28-390">Ein Steuerelement, über das der Benutzer aus einer Reihe von Werten auswählen kann, indem er ein Schiebereglersteuerelement über einen Bereich verschiebt.</span><span class="sxs-lookup"><span data-stu-id="41c28-390">A control that lets the user select from a range of values by moving a Thumb control along a track.</span></span>

![Schiebereglersteuerelement](images/controls/slider.png)

```xaml
<Slider x:Name="slider1" Width="100" ValueChanged="Slider_ValueChanged" />
```

<span data-ttu-id="41c28-392">Referenz: [Slider](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-392">Reference: [Slider](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx)</span></span> 

<span data-ttu-id="41c28-393">Design und Vorgehensweise: [Richtlinien für Schieberegler](slider.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-393">Design and how-to: [Slider control guide](slider.md)</span></span> 

### <a name="toggle-button"></a><span data-ttu-id="41c28-394">Umschalter</span><span class="sxs-lookup"><span data-stu-id="41c28-394">Toggle button</span></span>
<span data-ttu-id="41c28-395">Eine Schaltfläche, mit der zwischen zwei Zuständen gewechselt werden kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-395">A button that can be toggled between 2 states.</span></span>

```xaml
<ToggleButton x:Name="toggleButton1" Content="Button" 
              Checked="ToggleButton_Checked"/>
```

<span data-ttu-id="41c28-396">Referenz: [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-396">Reference: [ToggleButton](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.togglebutton.aspx)</span></span>

<span data-ttu-id="41c28-397">Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-397">Design and how-to: [Toggle control guide](toggles.md)</span></span> 

### <a name="toggle-switch"></a><span data-ttu-id="41c28-398">Umschalter</span><span class="sxs-lookup"><span data-stu-id="41c28-398">Toggle switch</span></span>
<span data-ttu-id="41c28-399">Ein Schalter, mit dem zwischen zwei Zuständen hin und her geschaltet werden kann.</span><span class="sxs-lookup"><span data-stu-id="41c28-399">A switch that can be toggled between 2 states.</span></span>

![Umschaltersteuerelement](images/controls/toggle-switch.png) 

```xaml
<ToggleSwitch x:Name="toggleSwitch1" Header="ToggleSwitch" 
              OnContent="On" OffContent="Off" 
              Toggled="ToggleSwitch_Toggled"/>
```

<span data-ttu-id="41c28-401">Referenz: [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.toggleswitch.aspx)</span><span class="sxs-lookup"><span data-stu-id="41c28-401">Reference: [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.toggleswitch.aspx)</span></span> 

<span data-ttu-id="41c28-402">Design und Vorgehensweise: [Richtlinien für Umschaltsteuerelemente](toggles.md)</span><span class="sxs-lookup"><span data-stu-id="41c28-402">Design and how-to: [Toggle control guide](toggles.md)</span></span> 
