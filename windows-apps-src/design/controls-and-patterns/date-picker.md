---
author: muhsinking
Description: The date picker gives you a standardized way to let users pick a localized date value using touch, mouse, or keyboard input.
title: Datumsauswahl
ms.assetid: d4a01425-4dee-4de3-9a05-3e85c3fc03cb
isNew: true
label: Date picker
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: windows 10, uwp
pm-contact: kisai
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1f258ff63d2cf9badfc1066f46c97ecc14b90f5f
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7440461"
---
# <a name="date-picker"></a><span data-ttu-id="f8262-103">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="f8262-103">Date picker</span></span>

 

<span data-ttu-id="f8262-104">Mit der Datumsauswahl verfügen Sie über eine standardisierte Methode, Benutzern die Möglichkeit zu bieten, einen lokalisierten Datumswert per Touch-, Maus- oder Tastatureingabe auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f8262-104">The date picker gives you a standardized way to let users pick a localized date value using touch, mouse, or keyboard input.</span></span> 

> <span data-ttu-id="f8262-105">**Wichtige APIs:** [Klasse „DatePicker“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx), [Eigenschaft „Date“](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.date.aspx)</span><span class="sxs-lookup"><span data-stu-id="f8262-105">**Important APIs**: [DatePicker class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx), [Date property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.date.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="f8262-106">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="f8262-106">Is this the right control?</span></span>
<span data-ttu-id="f8262-107">Verwenden Sie eine Datumsauswahl, damit Benutzer ein bekanntes Datum wie etwa einen Geburtstag auswählen können, bei dem der Kalenderkontext unwichtig ist.</span><span class="sxs-lookup"><span data-stu-id="f8262-107">Use a date picker to let a user pick a known date, such as a date of birth, where the context of the calendar is not important.</span></span>

<span data-ttu-id="f8262-108">Weitere Informationen zur Auswahl des richtigen Datumssteuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).</span><span class="sxs-lookup"><span data-stu-id="f8262-108">For more info about choosing the right date control, see the [Date and time controls](date-and-time.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="f8262-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f8262-109">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="f8262-110">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="f8262-110">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="f8262-111">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/DatePicker">die App zu öffnen und DatePicker in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="f8262-111">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/DatePicker">open the app and see the DatePicker in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="f8262-112">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="f8262-112">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="f8262-113">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="f8262-113">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="f8262-114">Der Einstiegspunkt zeigt das ausgewählte Datum an, und wenn der Benutzer den Einstiegspunkt auswählt, wird eine Auswahloberfläche von der Bildschirmmitte aus vertikal erweitert, damit eine Auswahl getroffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f8262-114">The entry point displays the chosen date, and when the user selects the entry point, a picker surface expands vertically from the middle for the user to make a selection.</span></span> <span data-ttu-id="f8262-115">Die Datumsauswahl überlagert andere Elemente der Benutzeroberfläche; die anderen Elemente der Benutzeroberfläche werden jedoch nicht „beiseitegeschoben“.</span><span class="sxs-lookup"><span data-stu-id="f8262-115">The date picker overlays other UI; it doesn't push other UI out of the way.</span></span>

![Beispiel für die Erweiterung der Datumsauswahl](images/controls_datepicker_expand.png)

## <a name="create-a-date-picker"></a><span data-ttu-id="f8262-117">Erstellen einer Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="f8262-117">Create a date picker</span></span>

<span data-ttu-id="f8262-118">Dieses Beispiel zeigt, wie Sie eine einfache Datumsauswahl mit einer Kopfzeile erstellen.</span><span class="sxs-lookup"><span data-stu-id="f8262-118">This example shows how to create a simple date picker with a header.</span></span>

```xaml
<DatePicker x:Name=birthDatePicker Header="Date of birth"/>
```

```csharp
DatePicker birthDatePicker = new DatePicker();
birthDatePicker.Header = "Date of birth";
```

<span data-ttu-id="f8262-119">Die fertige Datumsauswahl sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="f8262-119">The resulting date picker looks like this:</span></span>

![Beispiel für eine Datumsauswahl](images/date-picker-closed.png)

> <span data-ttu-id="f8262-121">**Hinweis**&nbsp;&nbsp;Wichtige Informationen zu Datumswerten finden Sie im Artikel zu Datums- und Uhrzeitsteuerelementen unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values).</span><span class="sxs-lookup"><span data-stu-id="f8262-121">**Note**&nbsp;&nbsp;For important info about date values, see [DateTime and Calendar values](date-and-time.md#datetime-and-calendar-values) in the Date and time controls article.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="f8262-122">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="f8262-122">Get the sample code</span></span>

- <span data-ttu-id="f8262-123">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f8262-123">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="f8262-124">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f8262-124">Related articles</span></span>

- [<span data-ttu-id="f8262-125">Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="f8262-125">Date and time controls</span></span>](date-and-time.md)
- [<span data-ttu-id="f8262-126">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="f8262-126">Calendar date picker</span></span>](calendar-date-picker.md)
- [<span data-ttu-id="f8262-127">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="f8262-127">Calendar view</span></span>](calendar-view.md)
- [<span data-ttu-id="f8262-128">Uhrzeitauswahl</span><span class="sxs-lookup"><span data-stu-id="f8262-128">Time picker</span></span>](time-picker.md)
