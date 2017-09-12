---
author: Jwmsft
Description: "Die Kalenderdatumsauswahl ist ein Dropdownsteuerelement, das für die Auswahl eines einzelnen Datums in einer Kalenderansicht optimiert ist, in der kontextbezogene Informationen wie der Wochentag oder die Belegung des Kalenders von Bedeutung sind."
title: Kalenderdatumsauswahl
ms.assetid: 9e0213e0-046a-4906-ba86-0b49be51ca99
label: Calendar date picker
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
ms.openlocfilehash: 88f60f60f272fb5501eb6c238cb0d9e5c01986a1
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="calendar-date-picker"></a><span data-ttu-id="435de-104">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="435de-104">Calendar date picker</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="435de-105">Die Kalenderdatumsauswahl ist ein Dropdownsteuerelement, das für die Auswahl eines einzelnen Datums in einer Kalenderansicht optimiert ist, in der kontextbezogene Informationen wie der Wochentag oder die Belegung des Kalenders von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="435de-105">The calendar date picker is a drop down control that’s optimized for picking a single date from a calendar view where contextual information like the day of the week or fullness of the calendar is important.</span></span> <span data-ttu-id="435de-106">Sie können den Kalender bearbeiten, um Kontext hinzuzufügen oder verfügbare Tage einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="435de-106">You can modify the calendar to provide additional context or to limit available dates.</span></span>

> <span data-ttu-id="435de-107">**Wichtige APIs:** [Klasse „CalendarDatePicker“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx), [Eigenschaft „Date“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), [Ereignis „DateChanged“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx)</span><span class="sxs-lookup"><span data-stu-id="435de-107">**Important APIs**: [CalendarDatePicker class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx), [Date property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), [DateChanged event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="435de-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="435de-108">Is this the right control?</span></span>
<span data-ttu-id="435de-109">Benutzer können in einer **Kalenderdatumsauswahl** in einer kontextbezogenen Kalenderansicht ein einzelnes Datum auswählen.</span><span class="sxs-lookup"><span data-stu-id="435de-109">Use a **calendar date picker** to let a user pick a single date from a contextual calendar view.</span></span> <span data-ttu-id="435de-110">Dies eignet sich beispielsweise, um Termine oder Abflugzeiten einzutragen.</span><span class="sxs-lookup"><span data-stu-id="435de-110">Use it for things like choosing an appointment or departure date.</span></span>

<span data-ttu-id="435de-111">Damit Benutzer ein bekanntes Datum wie etwa einen Geburtstag eintragen können, bei dem der Kalenderkontext unwichtig ist, könnte eine [Datumsauswahl](date-picker.md) von Vorteil sein.</span><span class="sxs-lookup"><span data-stu-id="435de-111">To let a user pick a known date, such as a date of birth, where the context of the calendar is not important, consider using a [date picker](date-picker.md).</span></span>

<span data-ttu-id="435de-112">Weitere Informationen zur Auswahl des passenden Steuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).</span><span class="sxs-lookup"><span data-stu-id="435de-112">For more info about choosing the right control, see the [Date and time controls](date-and-time.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="435de-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="435de-113">Examples</span></span>

<span data-ttu-id="435de-114">Der Einstiegspunkt zeigt Platzhaltertext an, falls kein Datum festgelegt wurde. Andernfalls wird das ausgewählte Datum angezeigt.</span><span class="sxs-lookup"><span data-stu-id="435de-114">The entry point displays placeholder text if a date has not been set; otherwise, it displays the chosen date.</span></span> <span data-ttu-id="435de-115">Wenn Benutzer den Einstiegspunkt auswählen, wird eine Kalenderansicht eingeblendet, damit sie ein Datum auswählen können.</span><span class="sxs-lookup"><span data-stu-id="435de-115">When the user selects the entry point, a calendar view expands for the user to make a date selection.</span></span> <span data-ttu-id="435de-116">Die Kalenderansicht überlagert andere Elemente der Benutzeroberfläche. Die anderen Elemente der Benutzeroberfläche werden dadurch jedoch nicht „beiseitegeschoben“.</span><span class="sxs-lookup"><span data-stu-id="435de-116">The calendar view overlays other UI; it doesn't push other UI out of the way.</span></span>

![Beispiel für Kalenderdatumsauswahl](images/calendar-date-picker-2-views.png)

## <a name="create-a-date-picker"></a><span data-ttu-id="435de-118">Erstellen einer Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="435de-118">Create a date picker</span></span>

```xaml
<CalendarDatePicker x:Name="arrivalCalendarDatePicker" Header="Arrival date"/>
```

```csharp
CalendarDatePicker arrivalCalendarDatePicker = new CalendarDatePicker();
arrivalCalendarDatePicker.Header = "Arrival date";
```

<span data-ttu-id="435de-119">Die fertige Kalenderdatumsauswahl sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="435de-119">The resulting calendar date picker looks like this:</span></span>

![Beispiel für Kalenderdatumsauswahl](images/calendar-date-picker-closed.png)

<span data-ttu-id="435de-121">Die Kalenderdatumsauswahl verfügt über eine interne Klasse [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx) zur Auswahl eines Datums.</span><span class="sxs-lookup"><span data-stu-id="435de-121">The calendar date picker has an internal [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx) for picking a date.</span></span> <span data-ttu-id="435de-122">In CalendarDatePicker ist eine Teilmenge von CalendarView-Eigenschaften, wie [IsTodayHighlighted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.istodayhighlighted.aspx) und [FirstDayOfWeek](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.firstdayofweek.aspx) vorhanden. Diese werden an die interne „CalendarView“-Klasse weitergeleitet, damit Sie sie ändern können.</span><span class="sxs-lookup"><span data-stu-id="435de-122">A subset of CalendarView properties, like [IsTodayHighlighted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.istodayhighlighted.aspx) and [FirstDayOfWeek](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.firstdayofweek.aspx), exist on CalendarDatePicker and are forwarded to the internal CalendarView to let you modify it.</span></span> 

<span data-ttu-id="435de-123">Sie können jedoch über die Eigenschaft [SelectionMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.selectionmode.aspx) der internen Klasse „CalendarView“ keine Mehrfachauswahl definieren.</span><span class="sxs-lookup"><span data-stu-id="435de-123">However, you can't change the [SelectionMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.selectionmode.aspx) of the internal CalendarView to allow multiple selection.</span></span> <span data-ttu-id="435de-124">Falls Benutzer mehrere Tage auswählen sollen oder permanent ein Kalender sichtbar sein muss, bietet sich möglicherweise anstelle der Kalenderdatumsauswahl eine Kalenderansicht an.</span><span class="sxs-lookup"><span data-stu-id="435de-124">If you need to let a user pick multiple dates or need a calendar to be always visible, consider using a calendar view instead of a calendar date picker.</span></span> <span data-ttu-id="435de-125">Weitere Informationen zum Ändern der Kalenderanzeige finden Sie im Artikel zur [Kalenderansicht](calendar-view.md).</span><span class="sxs-lookup"><span data-stu-id="435de-125">See the [Calendar view](calendar-view.md) article for more info on how you can modify the calendar display.</span></span>

### <a name="selecting-dates"></a><span data-ttu-id="435de-126">Auswählen von Tagen</span><span class="sxs-lookup"><span data-stu-id="435de-126">Selecting dates</span></span>

<span data-ttu-id="435de-127">Verwenden Sie die Eigenschaft [Date](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), um das ausgewählte Datum abzurufen oder festzulegen.</span><span class="sxs-lookup"><span data-stu-id="435de-127">Use the [Date](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx) property to get or set the selected date.</span></span> <span data-ttu-id="435de-128">Der Standardwert der „Date“-Eigenschaft lautet **null**.</span><span class="sxs-lookup"><span data-stu-id="435de-128">By default, the Date property is **null**.</span></span> <span data-ttu-id="435de-129">Wenn Benutzer ein Datum in der Kalenderansicht auswählen, wird diese Eigenschaft aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="435de-129">When a user selects a date in the calendar view, this property is updated.</span></span> <span data-ttu-id="435de-130">Benutzer können die Auswahl eines Datums aufheben, indem sie in der Kalenderansicht auf das Datum klicken.</span><span class="sxs-lookup"><span data-stu-id="435de-130">A user can clear the date by clicking the selected date in the calendar view to deselect it.</span></span> 

<span data-ttu-id="435de-131">Sie können das Datum im Code wie folgt festlegen.</span><span class="sxs-lookup"><span data-stu-id="435de-131">You can set the date in your code like this.</span></span>

```csharp
myCalendarDatePicker.Date = new DateTime(1977, 1, 5);
```

<span data-ttu-id="435de-132">Wenn Sie das Datum in Code festlegen, wird der Wert durch die Eigenschaften [MinDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.mindate.aspx) und [MaxDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.maxdate.aspx) beschränkt.</span><span class="sxs-lookup"><span data-stu-id="435de-132">When you set the Date in code, the value is constrained by the [MinDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.mindate.aspx) and [MaxDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.maxdate.aspx) properties.</span></span>
- <span data-ttu-id="435de-133">Wenn **Date** vor **MinDate** liegt, wird der Wert auf **MinDate** gesetzt.</span><span class="sxs-lookup"><span data-stu-id="435de-133">If **Date** is smaller than **MinDate**, the value is set to **MinDate**.</span></span>
- <span data-ttu-id="435de-134">Wenn **Date** nach **MaxDate** liegt, wird der Wert auf **MaxDate** gesetzt.</span><span class="sxs-lookup"><span data-stu-id="435de-134">If **Date** is greater than **MaxDate**, the value is set to **MaxDate**.</span></span>

<span data-ttu-id="435de-135">Über das Ereignis [DateChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx) können Sie sich bei Änderungen am Wert „Date“ benachrichtigen lassen.</span><span class="sxs-lookup"><span data-stu-id="435de-135">You can handle the [DateChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx) event to be notified when the Date value has changed.</span></span>

> [!NOTE]
<span data-ttu-id="435de-136">Wichtige Informationen zu Datumswerten finden Sie im Artikel zu Datums- und Uhrzeitsteuerelementen unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values).</span><span class="sxs-lookup"><span data-stu-id="435de-136">For important info about date values, see [DateTime and Calendar values](date-and-time.md#datetime-and-calendar-values) in the Date and time controls article.</span></span>

### <a name="setting-a-header-and-placeholder-text"></a><span data-ttu-id="435de-137">Festlegen von Kopfzeilen- und Platzhaltertext</span><span class="sxs-lookup"><span data-stu-id="435de-137">Setting a header and placeholder text</span></span>

<span data-ttu-id="435de-138">Sie können der Kalenderdatumsauswahl eine [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.header.aspx)-Eigenschaft (oder eine Beschriftung) und eine [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.placeholdertext.aspx)-Eigenschaft (oder ein Wasserzeichen) hinzufügen, um Benutzern einen Hinweis bezüglich des Verwendungszwecks zu geben.</span><span class="sxs-lookup"><span data-stu-id="435de-138">You can add a [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.header.aspx) (or label) and [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.placeholdertext.aspx) (or watermark) to the calendar date picker to give the user an indication of what it's used for.</span></span> <span data-ttu-id="435de-139">Wenn Sie das Erscheinungsbild der Kopfzeile anpassen möchten, können Sie anstelle der Eigenschaft „Header“ die Eigenschaft [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.headertemplate.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="435de-139">To customize the look of the header, you can set the [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.headertemplate.aspx) property instead of Header.</span></span>

<span data-ttu-id="435de-140">Als Standardtext für den Platzhalter wird „Datum auswählen“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="435de-140">The default placeholder text is "select a date".</span></span> <span data-ttu-id="435de-141">Sie können diesen Text entfernen, indem Sie die PlaceholderText-Eigenschaft auf eine leere Zeichenfolge festlegen. Alternativ können Sie wie hier gezeigt einen benutzerdefinierten Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="435de-141">You can remove this by setting the PlaceholderText property to an empty string, or you can provide custom text as shown here.</span></span>

```xaml
<CalendarDatePicker x:Name="arrivalCalendarDatePicker" Header="Arrival date" 
                    PlaceholderText="Choose your arrival date"/>
```

## <a name="get-the-sample-code"></a><span data-ttu-id="435de-142">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="435de-142">Get the sample code</span></span>
* [<span data-ttu-id="435de-143">Beispiel für XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="435de-143">XAML UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)


## <a name="related-articles"></a><span data-ttu-id="435de-144">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="435de-144">Related articles</span></span>

- [<span data-ttu-id="435de-145">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="435de-145">Date and time controls</span></span>](date-and-time.md)
- [<span data-ttu-id="435de-146">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="435de-146">Calendar view</span></span>](calendar-view.md)
- [<span data-ttu-id="435de-147">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="435de-147">Date picker</span></span>](date-picker.md)
- [<span data-ttu-id="435de-148">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="435de-148">Time picker</span></span>](time-picker.md)
