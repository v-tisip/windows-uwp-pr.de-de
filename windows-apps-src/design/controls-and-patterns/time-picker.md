---
Description: The time picker gives you a standardized way to let users pick a time value using touch, mouse, or keyboard input.
title: Uhrzeitauswahl
ms.assetid: 5124ecda-09e6-449e-9d4a-d969dca46aa3
label: Time picker
template: detail.hbs
ms.date: 05/08/2017
ms.topic: article
keywords: windows10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: joyate
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 5187f3fe6f8ca14725f56b64f212e11f99dfc911
ms.sourcegitcommit: a60ab85e9f2f9690e0141050ec3aa51f18ec61ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "9037002"
---
# <a name="time-picker"></a><span data-ttu-id="77659-103">Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="77659-103">Time picker</span></span>
 

<span data-ttu-id="77659-104">Mit der Zeitauswahl verfügen Sie über eine standardmäßige Methode, mit der die Benutzer einen Zeitwert per Touch-, Maus- oder Tastatureingabe auswählen können.</span><span class="sxs-lookup"><span data-stu-id="77659-104">The time picker gives you a standardized way to let users pick a time value using touch, mouse, or keyboard input.</span></span> 

> <span data-ttu-id="77659-105">**Wichtige APIs**: [TimePicker-Klasse](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx), [Time-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.time.aspx)</span><span class="sxs-lookup"><span data-stu-id="77659-105">**Important APIs**: [TimePicker class](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.aspx), [Time property](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.timepicker.time.aspx)</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="77659-106">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="77659-106">Is this the right control?</span></span>
<span data-ttu-id="77659-107">Verwenden Sie die Zeitauswahl, um Benutzern die Auswahl eines einzelnen Zeitwerts zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="77659-107">Use a time picker to let a user pick a single time value.</span></span>

<span data-ttu-id="77659-108">Weitere Informationen zur Auswahl des passenden Steuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).</span><span class="sxs-lookup"><span data-stu-id="77659-108">For more info about choosing the right control, see the [Date and time controls](date-and-time.md) article.</span></span>

## <a name="examples"></a><span data-ttu-id="77659-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="77659-109">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="77659-110">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="77659-110">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="77659-111">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/TimePicker">die App zu öffnen und TimePicker in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="77659-111">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/TimePicker">open the app and see the TimePicker in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="77659-112">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="77659-112">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Xaml-Controls-Gallery"><span data-ttu-id="77659-113">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="77659-113">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="77659-114">Der Einstiegspunkt zeigt die ausgewählte Uhrzeit an, und wenn der Benutzer den Einstiegspunkt auswählt, wird eine Auswahloberfläche von der Bildschirmmitte aus vertikal erweitert, damit eine Auswahl getroffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="77659-114">The entry point displays the chosen time, and when the user selects the entry point, a picker surface expands vertically from the middle for the user to make a selection.</span></span> <span data-ttu-id="77659-115">Die Zeitauswahl überlagert andere Elemente der Benutzeroberfläche. Die anderen Elemente der Benutzeroberfläche werden dadurch jedoch nicht „verschoben“.</span><span class="sxs-lookup"><span data-stu-id="77659-115">The time picker overlays other UI; it doesn't push other UI out of the way.</span></span>

![Beispiel für die Erweiterung der Zeitauswahl](images/controls_timepicker_expand.png)

## <a name="create-a-time-picker"></a><span data-ttu-id="77659-117">Erstellen einer Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="77659-117">Create a time picker</span></span>

<span data-ttu-id="77659-118">Dieses Beispiel zeigt, wie Sie ein einfaches Zeitauswahl-Steuerelement mit einer Kopfzeile erstellen.</span><span class="sxs-lookup"><span data-stu-id="77659-118">This example shows how to create a simple time picker with a header.</span></span>

```xaml
<TimePicker x:Name=arrivalTimePicker Header="Arrival time"/>
```

```csharp
TimePicker arrivalTimePicker = new TimePicker();
arrivalTimePicker.Header = "Arrival time";
```

<span data-ttu-id="77659-119">Die fertige Zeitauswahl sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="77659-119">The resulting time picker looks like this:</span></span>

![Beispiel für Zeitauswahl](images/time-picker-closed.png)

> [!NOTE]
> <span data-ttu-id="77659-121">Wichtige Informationen zu Uhrzeit- und Datumswerten finden Sie unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values) im Artikel *Steuerelemente für Datum und Uhrzeit*.</span><span class="sxs-lookup"><span data-stu-id="77659-121">For important info about date and time values, see [DateTime and Calendar values](date-and-time.md#datetime-and-calendar-values) in the *Date and time controls* article.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="77659-122">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="77659-122">Get the sample code</span></span>

- <span data-ttu-id="77659-123">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Xaml-Controls-Gallery) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="77659-123">[XAML Controls Gallery sample](https://github.com/Microsoft/Xaml-Controls-Gallery) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="77659-124">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="77659-124">Related topics</span></span>

- [<span data-ttu-id="77659-125">Steuerelemente für Datum und Uhrzeit</span><span class="sxs-lookup"><span data-stu-id="77659-125">Date and time controls</span></span>](date-and-time.md)
- [<span data-ttu-id="77659-126">Kalenderdatumsauswahl</span><span class="sxs-lookup"><span data-stu-id="77659-126">Calendar date picker</span></span>](calendar-date-picker.md)
- [<span data-ttu-id="77659-127">Kalenderansicht</span><span class="sxs-lookup"><span data-stu-id="77659-127">Calendar view</span></span>](calendar-view.md)
- [<span data-ttu-id="77659-128">Datumsauswahl</span><span class="sxs-lookup"><span data-stu-id="77659-128">Date picker</span></span>](date-picker.md)
