---
author: muhsinking
Description: The calendar date picker is a drop down control that’s optimized for picking a single date from a calendar view where contextual information like the day of the week or fullness of the calendar is important.
title: Kalenderdatumsauswahl
ms.assetid: 9e0213e0-046a-4906-ba86-0b49be51ca99
label: Calendar date picker
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 6756d8c64f33de8d16d6aa455c3fad694a6306d5
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7558544"
---
# <a name="calendar-date-picker"></a><span data-ttu-id="3a4bb-103">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="3a4bb-103">Calendar date picker</span></span>

 

<span data-ttu-id="3a4bb-104">Die Kalenderdatumsauswahl ist ein Dropdownsteuerelement, das für die Auswahl eines einzelnen Datums in einer Kalenderansicht optimiert ist, in der kontextbezogene Informationen wie der Wochentag oder die Belegung des Kalenders von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-104">The calendar date picker is a drop down control that’s optimized for picking a single date from a calendar view where contextual information like the day of the week or fullness of the calendar is important.</span></span> <span data-ttu-id="3a4bb-105">Sie können den Kalender bearbeiten, um Kontext hinzuzufügen oder verfügbare Tage einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-105">You can modify the calendar to provide additional context or to limit available dates.</span></span>

> <span data-ttu-id="3a4bb-106">**Wichtige APIs:** [Klasse „CalendarDatePicker“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx), [Eigenschaft „Date“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), [Ereignis „DateChanged“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx)</span><span class="sxs-lookup"><span data-stu-id="3a4bb-106">**Important APIs**: [CalendarDatePicker class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.aspx), [Date property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), [DateChanged event](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="3a4bb-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="3a4bb-107">Is this the right control?</span></span>
<span data-ttu-id="3a4bb-108">Benutzer können in einer **Kalenderdatumsauswahl** in einer kontextbezogenen Kalenderansicht ein einzelnes Datum auswählen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-108">Use a **calendar date picker** to let a user pick a single date from a contextual calendar view.</span></span> <span data-ttu-id="3a4bb-109">Dies eignet sich beispielsweise, um Termine oder Abflugzeiten einzutragen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-109">Use it for things like choosing an appointment or departure date.</span></span>

<span data-ttu-id="3a4bb-110">Damit Benutzer ein bekanntes Datum wie etwa einen Geburtstag eintragen können, bei dem der Kalenderkontext unwichtig ist, könnte eine [Datumsauswahl](date-picker.md) von Vorteil sein.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-110">To let a user pick a known date, such as a date of birth, where the context of the calendar is not important, consider using a [date picker](date-picker.md).</span></span>

<span data-ttu-id="3a4bb-111">Weitere Informationen zur Auswahl des passenden Steuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).</span><span class="sxs-lookup"><span data-stu-id="3a4bb-111">For more info about choosing the right control, see the [Date and time controls](date-and-time.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="3a4bb-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3a4bb-112">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="3a4bb-113">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="3a4bb-113">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="3a4bb-114">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/CalendarDatePicker">die App zu öffnen und CalendarDatePicker in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-114">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/CalendarDatePicker">open the app and see the CalendarDatePicker in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="3a4bb-115">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="3a4bb-115">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="3a4bb-116">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3a4bb-116">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="3a4bb-117">Der Einstiegspunkt zeigt Platzhaltertext an, falls kein Datum festgelegt wurde. Andernfalls wird das ausgewählte Datum angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-117">The entry point displays placeholder text if a date has not been set; otherwise, it displays the chosen date.</span></span> <span data-ttu-id="3a4bb-118">Wenn Benutzer den Einstiegspunkt auswählen, wird eine Kalenderansicht eingeblendet, damit sie ein Datum auswählen können.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-118">When the user selects the entry point, a calendar view expands for the user to make a date selection.</span></span> <span data-ttu-id="3a4bb-119">Die Kalenderansicht überlagert andere Elemente der Benutzeroberfläche. Die anderen Elemente der Benutzeroberfläche werden dadurch jedoch nicht „beiseitegeschoben“.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-119">The calendar view overlays other UI; it doesn't push other UI out of the way.</span></span>

![Beispiel für Kalenderdatumsauswahl](images/calendar-date-picker-2-views.png)

## <a name="create-a-date-picker"></a><span data-ttu-id="3a4bb-121">Erstellen einer Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="3a4bb-121">Create a date picker</span></span>

```xaml
<CalendarDatePicker x:Name="arrivalCalendarDatePicker" Header="Arrival date"/>
```

```csharp
CalendarDatePicker arrivalCalendarDatePicker = new CalendarDatePicker();
arrivalCalendarDatePicker.Header = "Arrival date";
```

<span data-ttu-id="3a4bb-122">Die fertige Kalenderdatumsauswahl sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3a4bb-122">The resulting calendar date picker looks like this:</span></span>

![Beispiel für Kalenderdatumsauswahl](images/calendar-date-picker-closed.png)

<span data-ttu-id="3a4bb-124">Die Kalenderdatumsauswahl verfügt über eine interne Klasse [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx) zur Auswahl eines Datums.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-124">The calendar date picker has an internal [CalendarView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.aspx) for picking a date.</span></span> <span data-ttu-id="3a4bb-125">In CalendarDatePicker ist eine Teilmenge von CalendarView-Eigenschaften, wie [IsTodayHighlighted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.istodayhighlighted.aspx) und [FirstDayOfWeek](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.firstdayofweek.aspx) vorhanden. Diese werden an die interne „CalendarView“-Klasse weitergeleitet, damit Sie sie ändern können.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-125">A subset of CalendarView properties, like [IsTodayHighlighted](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.istodayhighlighted.aspx) and [FirstDayOfWeek](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.firstdayofweek.aspx), exist on CalendarDatePicker and are forwarded to the internal CalendarView to let you modify it.</span></span> 

<span data-ttu-id="3a4bb-126">Sie können jedoch über die Eigenschaft [SelectionMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.selectionmode.aspx) der internen Klasse „CalendarView“ keine Mehrfachauswahl definieren.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-126">However, you can't change the [SelectionMode](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendarview.selectionmode.aspx) of the internal CalendarView to allow multiple selection.</span></span> <span data-ttu-id="3a4bb-127">Falls Benutzer mehrere Tage auswählen sollen oder permanent ein Kalender sichtbar sein muss, bietet sich möglicherweise anstelle der Kalenderdatumsauswahl eine Kalenderansicht an.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-127">If you need to let a user pick multiple dates or need a calendar to be always visible, consider using a calendar view instead of a calendar date picker.</span></span> <span data-ttu-id="3a4bb-128">Weitere Informationen zum Ändern der Kalenderanzeige finden Sie im Artikel zur [Kalenderansicht](calendar-view.md).</span><span class="sxs-lookup"><span data-stu-id="3a4bb-128">See the [Calendar view](calendar-view.md) article for more info on how you can modify the calendar display.</span></span>

### <a name="selecting-dates"></a><span data-ttu-id="3a4bb-129">Auswählen von Tagen</span><span class="sxs-lookup"><span data-stu-id="3a4bb-129">Selecting dates</span></span>

<span data-ttu-id="3a4bb-130">Verwenden Sie die Eigenschaft [Date](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx), um das ausgewählte Datum abzurufen oder festzulegen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-130">Use the [Date](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.date.aspx) property to get or set the selected date.</span></span> <span data-ttu-id="3a4bb-131">Der Standardwert der „Date“-Eigenschaft lautet **null**.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-131">By default, the Date property is **null**.</span></span> <span data-ttu-id="3a4bb-132">Wenn Benutzer ein Datum in der Kalenderansicht auswählen, wird diese Eigenschaft aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-132">When a user selects a date in the calendar view, this property is updated.</span></span> <span data-ttu-id="3a4bb-133">Benutzer können die Auswahl eines Datums aufheben, indem sie in der Kalenderansicht auf das Datum klicken.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-133">A user can clear the date by clicking the selected date in the calendar view to deselect it.</span></span> 

<span data-ttu-id="3a4bb-134">Sie können das Datum im Code wie folgt festlegen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-134">You can set the date in your code like this.</span></span>

```csharp
myCalendarDatePicker.Date = new DateTime(1977, 1, 5);
```

<span data-ttu-id="3a4bb-135">Wenn Sie das Datum in Code festlegen, wird der Wert durch die Eigenschaften [MinDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.mindate.aspx) und [MaxDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.maxdate.aspx) beschränkt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-135">When you set the Date in code, the value is constrained by the [MinDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.mindate.aspx) and [MaxDate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.maxdate.aspx) properties.</span></span>
- <span data-ttu-id="3a4bb-136">Wenn **Date** vor **MinDate** liegt, wird der Wert auf **MinDate** gesetzt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-136">If **Date** is smaller than **MinDate**, the value is set to **MinDate**.</span></span>
- <span data-ttu-id="3a4bb-137">Wenn **Date** nach **MaxDate** liegt, wird der Wert auf **MaxDate** gesetzt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-137">If **Date** is greater than **MaxDate**, the value is set to **MaxDate**.</span></span>

<span data-ttu-id="3a4bb-138">Über das Ereignis [DateChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx) können Sie sich bei Änderungen am Wert „Date“ benachrichtigen lassen.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-138">You can handle the [DateChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.datechanged.aspx) event to be notified when the Date value has changed.</span></span>

> [!NOTE]
<span data-ttu-id="3a4bb-139">Wichtige Informationen zu Datumswerten finden Sie im Artikel zu Datums- und Uhrzeitsteuerelementen unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values).</span><span class="sxs-lookup"><span data-stu-id="3a4bb-139">For important info about date values, see [DateTime and Calendar values](date-and-time.md#datetime-and-calendar-values) in the Date and time controls article.</span></span>

### <a name="setting-a-header-and-placeholder-text"></a><span data-ttu-id="3a4bb-140">Festlegen von Kopfzeilen- und Platzhaltertext</span><span class="sxs-lookup"><span data-stu-id="3a4bb-140">Setting a header and placeholder text</span></span>

<span data-ttu-id="3a4bb-141">Sie können der Kalenderdatumsauswahl eine [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.header.aspx)-Eigenschaft (oder eine Beschriftung) und eine [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.placeholdertext.aspx)-Eigenschaft (oder ein Wasserzeichen) hinzufügen, um Benutzern einen Hinweis bezüglich des Verwendungszwecks zu geben.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-141">You can add a [Header](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.header.aspx) (or label) and [PlaceholderText](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.placeholdertext.aspx) (or watermark) to the calendar date picker to give the user an indication of what it's used for.</span></span> <span data-ttu-id="3a4bb-142">Wenn Sie das Erscheinungsbild der Kopfzeile anpassen möchten, können Sie anstelle der Eigenschaft „Header“ die Eigenschaft [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.headertemplate.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-142">To customize the look of the header, you can set the [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.calendardatepicker.headertemplate.aspx) property instead of Header.</span></span>

<span data-ttu-id="3a4bb-143">Als Standardtext für den Platzhalter wird „Datum auswählen“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-143">The default placeholder text is "select a date".</span></span> <span data-ttu-id="3a4bb-144">Sie können diesen Text entfernen, indem Sie die PlaceholderText-Eigenschaft auf eine leere Zeichenfolge festlegen. Alternativ können Sie wie hier gezeigt einen benutzerdefinierten Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-144">You can remove this by setting the PlaceholderText property to an empty string, or you can provide custom text as shown here.</span></span>

```xaml
<CalendarDatePicker x:Name="arrivalCalendarDatePicker" Header="Arrival date" 
                    PlaceholderText="Choose your arrival date"/>
```

## <a name="get-the-sample-code"></a><span data-ttu-id="3a4bb-145">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="3a4bb-145">Get the sample code</span></span>

- <span data-ttu-id="3a4bb-146">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3a4bb-146">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="3a4bb-147">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="3a4bb-147">Related articles</span></span>

- [<span data-ttu-id="3a4bb-148">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="3a4bb-148">Date and time controls</span></span>](date-and-time.md)
- [<span data-ttu-id="3a4bb-149">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="3a4bb-149">Calendar view</span></span>](calendar-view.md)
- [<span data-ttu-id="3a4bb-150">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="3a4bb-150">Date picker</span></span>](date-picker.md)
- [<span data-ttu-id="3a4bb-151">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="3a4bb-151">Time picker</span></span>](time-picker.md)
