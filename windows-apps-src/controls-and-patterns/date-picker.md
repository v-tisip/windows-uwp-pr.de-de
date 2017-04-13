---
author: Jwmsft
Description: "Mit der Datumsauswahl verfügen Sie über eine standardisierte Methode, Benutzern die Möglichkeit zu bieten, einen lokalisierten Datumswert per Touch-, Maus- oder Tastatureingabe auszuwählen."
title: Datumsauswahl
ms.assetid: d4a01425-4dee-4de3-9a05-3e85c3fc03cb
isNew: True
label: Date picker
template: detail.hbs
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 114e91276ee4f080ead825b655fc05fcf460bacb
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="date-picker"></a>Datumsauswahl

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

Mit der Datumsauswahl verfügen Sie über eine standardisierte Methode, Benutzern die Möglichkeit zu bieten, einen lokalisierten Datumswert per Touch-, Maus- oder Tastatureingabe auszuwählen. 

<div class="important-apis" >
<b>Wichtige APIs</b><br/>
<ul>
<li>[**DatePicker-Klasse**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.aspx)</li>
<li>[**Date-Eigenschaft**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.datepicker.date.aspx) </li>

</ul>
</div>


## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?
Verwenden Sie eine Datumsauswahl, damit Benutzer ein bekanntes Datum wie etwa einen Geburtstag auswählen können, bei dem der Kalenderkontext unwichtig ist.

Weitere Informationen zur Auswahl des richtigen Datumssteuerelements finden Sie im Artikel über [Datums- und Uhrzeitsteuerelemente](date-and-time.md).

## <a name="examples"></a>Beispiele

Der Einstiegspunkt zeigt das ausgewählte Datum an, und wenn der Benutzer den Einstiegspunkt auswählt, wird eine Auswahloberfläche von der Bildschirmmitte aus vertikal erweitert, damit eine Auswahl getroffen werden kann. Die Datumsauswahl überlagert andere Elemente der Benutzeroberfläche; die anderen Elemente der Benutzeroberfläche werden jedoch nicht „beiseitegeschoben“.

![Beispiel für die Erweiterung der Datumsauswahl](images/controls_datepicker_expand.png)

## <a name="create-a-date-picker"></a>Erstellen einer Datumsauswahl

Dieses Beispiel zeigt, wie Sie eine einfache Datumsauswahl mit einer Kopfzeile erstellen.

```xaml
<DatePicker x:Name=birthDatePicker Header="Date of birth"/>
```

```csharp
DatePicker birthDatePicker = new DatePicker();
birthDatePicker.Header = "Date of birth";
```

Die fertige Datumsauswahl sieht wie folgt aus:

![Beispiel für eine Datumsauswahl](images/date-picker-closed.png)

> **Hinweis**&nbsp;&nbsp;Wichtige Informationen zu Datumswerten finden Sie im Artikel zu Datums- und Uhrzeitsteuerelementen unter [DateTime- und Calendar-Werte](date-and-time.md#datetime-and-calendar-values).



## <a name="related-articles"></a>Verwandte Artikel

- [Datums- und Uhrzeitsteuerelemente](date-and-time.md)
- [Kalenderdatumsauswahl](calendar-date-picker.md)
- [Kalenderansicht](calendar-view.md)
- [Uhrzeitauswahl](time-picker.md)
