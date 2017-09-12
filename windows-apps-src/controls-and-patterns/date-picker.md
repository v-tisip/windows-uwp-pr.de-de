---
author: Jwmsft
Description: "Mit der Datumsauswahl verfügen Sie über eine standardisierte Methode, Benutzern die Möglichkeit zu bieten, einen lokalisierten Datumswert per Touch-, Maus- oder Tastatureingabe auszuwählen."
title: Datumsauswahl
ms.assetid: d4a01425-4dee-4de3-9a05-3e85c3fc03cb
isNew: True
label: Date picker
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
pm-contact: kisai
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
ms.openlocfilehash: 25c49681085946e145d4feb4c8f93d2908f7bcbd
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="date-picker"></a><span data-ttu-id="e0764-104">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="e0764-104">Date picker</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="e0764-105">Mit der Datumsauswahl verfügen Sie über eine standardisierte Methode, Benutzern die Möglichkeit zu bieten, einen lokalisierten Datumswert per Touch-, Maus- oder Tastatureingabe auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="e0764-105">The date picker gives you a standardized way to let users pick a localized date value using touch, mouse, or keyboard input.</span></span> 

> <span data-ttu-id="e0764-106">**Wichtige APIs:** [Klasse „DatePicker“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx), [Eigenschaft „Date“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.date.aspx)</span><span class="sxs-lookup"><span data-stu-id="e0764-106">**Important APIs**: [DatePicker class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx), [Date property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.date.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="e0764-107">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="e0764-107">Is this the right control?</span></span>
<span data-ttu-id="e0764-108">Verwenden Sie eine Datumsauswahl, damit Benutzer ein bekanntes Datum wie etwa einen Geburtstag auswählen können, bei dem der Kalenderkontext unwichtig ist.</span><span class="sxs-lookup"><span data-stu-id="e0764-108">Use a date picker to let a user pick a known date, such as a date of birth, where the context of the calendar is not important.</span></span>

<span data-ttu-id="e0764-109">Weitere Informationen zur Auswahl des richtigen Datumssteuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).</span><span class="sxs-lookup"><span data-stu-id="e0764-109">For more info about choosing the right date control, see the [Date and time controls](date-and-time.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="e0764-110">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e0764-110">Examples</span></span>

<span data-ttu-id="e0764-111">Der Einstiegspunkt zeigt das ausgewählte Datum an, und wenn der Benutzer den Einstiegspunkt auswählt, wird eine Auswahloberfläche von der Bildschirmmitte aus vertikal erweitert, damit eine Auswahl getroffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e0764-111">The entry point displays the chosen date, and when the user selects the entry point, a picker surface expands vertically from the middle for the user to make a selection.</span></span> <span data-ttu-id="e0764-112">Die Datumsauswahl überlagert andere Elemente der Benutzeroberfläche; die anderen Elemente der Benutzeroberfläche werden jedoch nicht „beiseitegeschoben“.</span><span class="sxs-lookup"><span data-stu-id="e0764-112">The date picker overlays other UI; it doesn't push other UI out of the way.</span></span>

![Beispiel für die Erweiterung der Datumsauswahl](images/controls_datepicker_expand.png)

## <a name="create-a-date-picker"></a><span data-ttu-id="e0764-114">Erstellen einer Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="e0764-114">Create a date picker</span></span>

<span data-ttu-id="e0764-115">Dieses Beispiel zeigt, wie Sie eine einfache Datumsauswahl mit einer Kopfzeile erstellen.</span><span class="sxs-lookup"><span data-stu-id="e0764-115">This example shows how to create a simple date picker with a header.</span></span>

```xaml
<DatePicker x:Name=birthDatePicker Header="Date of birth"/>
```

```csharp
DatePicker birthDatePicker = new DatePicker();
birthDatePicker.Header = "Date of birth";
```

<span data-ttu-id="e0764-116">Die fertige Datumsauswahl sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e0764-116">The resulting date picker looks like this:</span></span>

![Beispiel für eine Datumsauswahl](images/date-picker-closed.png)

> <span data-ttu-id="e0764-118">**Hinweis**&nbsp;&nbsp;Wichtige Informationen zu Datumswerten finden Sie im Artikel zu Datums- und Uhrzeitsteuerelementen unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values).</span><span class="sxs-lookup"><span data-stu-id="e0764-118">**Note**&nbsp;&nbsp;For important info about date values, see [DateTime and Calendar values](date-and-time.md#datetime-and-calendar-values) in the Date and time controls article.</span></span>



## <a name="related-articles"></a><span data-ttu-id="e0764-119">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e0764-119">Related articles</span></span>

- [<span data-ttu-id="e0764-120">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="e0764-120">Date and time controls</span></span>](date-and-time.md)
- [<span data-ttu-id="e0764-121">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="e0764-121">Calendar date picker</span></span>](calendar-date-picker.md)
- [<span data-ttu-id="e0764-122">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="e0764-122">Calendar view</span></span>](calendar-view.md)
- [<span data-ttu-id="e0764-123">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="e0764-123">Time picker</span></span>](time-picker.md)
