---
author: Jwmsft
Description: "Beim Master/Details-Muster werden eine Masterliste und die Details für das derzeit ausgewählte Element angezeigt. Dieses Muster wird häufig für E-Mails und Kontaktlisten/Adressbücher verwendet."
title: Master/Details
ms.assetid: 45C9FE8B-ECA6-44BF-8DDE-7D12ED34A7F7
label: Master/details
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 49a586aac0c846cdad02f8448532238bd3eb8551
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="masterdetails-pattern"></a>Master/Details-Muster

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

Das Master/Details-Muster verfügt über einen Masterbereich (in der Regel mit einer [Listenansicht](lists.md)) und einen Detailbereich für Inhalte. Wenn ein Element in der Masterliste ausgewählt wird, wird der Detailbereich aktualisiert. Dieses Muster wird häufig für E-Mails und Adressbücher verwendet.

> **Wichtige APIs**: [ListView-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView), [SplitView-Klasse](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.splitview)

![Beispiel für das Master/Detail-Muster](images/HIGSecOne_MasterDetail.png)

## <a name="is-this-the-right-pattern"></a>Ist dies das richtige Muster?

Master/Details-Muster eignet sich gut für Folgendes:

-   Erstellen einer E-Mail-App, eines Adressbuchs oder einer anderen App, die auf einem Listen-Details-Layout basiert
-   Suchen und Priorisieren einer großen Sammlung von Inhalten
-   Schnelles Hinzufügen und Entfernen von Elementen aus einer Liste und gleichzeitiges Wechseln zwischen Kontexten

## <a name="choose-the-right-style"></a>Auswählen des richtigen Formats

Beim Implementieren des Master/Details-Musters ist es ratsam, je nach Größe der verfügbaren Bildschirmfläche das gestapelte Format oder das Format mit paralleler Anordnung zu verwenden.

| Verfügbare Fensterbreite | Empfohlenes Format |
|------------------------|-------------------|
| 320Epx - 719Epx        | Gestapelt           |
| 720Epx oder breiter       | Nebeneinander      |

 
## <a name="stacked-style"></a>Gestapeltes Format

Im gestapelten Format ist jeweils nur ein Bereich sichtbar: die Master- oder der Detailbereich.

![Master/Details im Stapelmodus](images/patterns-md-stacked.png)

Der Benutzer beginnt im Masterbereich und führt einen Drilldown zum Detailbereich durch, indem er ein Element in der Masterliste auswählt. Für den Benutzer sieht es so aus, als ob sich die Masteransicht und die Detailansicht auf zwei getrennten Seiten befinden.

### <a name="create-a-stacked-masterdetails-pattern"></a>Erstellen eines gestapelten Master/Details-Musters

Eine Möglichkeit zur Erstellung des gestapelten Master/Details-Musters ist die Verwendung separater Seiten für den Masterbereich und den Detailbereich. Ordnen Sie die Listenansicht, in der die Masterliste bereitgestellt wird, auf einer Seite und das Inhaltselement für den Detailbereich auf einer separaten Seite an.

![Teile der Master/Details-Ansicht im gestapelten Format](images/patterns-md-stacked-parts.png)

Für den Masterbereich eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.

Verwenden Sie für den Detailbereich das am besten geeignete Inhaltselement. Wenn viele separate Felder vorhanden sind, erwägen Sie die Verwendung eines Rasterlayouts zum Anordnen der Elemente in einem Formular.

## <a name="side-by-side-style"></a>Format mit paralleler Anordnung

Im Format mit paralleler Anordnung sind Master- und Detailbereich gleichzeitig sichtbar.

![Das Master/Details-Muster](images/patterns-masterdetail-400x227.png)

Für die Liste im Masterbereich wird eine visuelle Auswahlmethode genutzt, um das derzeit ausgewählte Element anzugeben. Wenn in der Masterliste ein neues Element ausgewählt wird, wird der Detailbereich aktualisiert.

### <a name="create-a-side-by-side-masterdetails-pattern"></a>Erstellen eines parallelen Master/Details-Musters

Für den Masterbereich eignet sich ein [Listenansicht](lists.md)-Steuerelement gut für die Darstellung von Listen, die Bilder und Text enthalten können.

Verwenden Sie für den Detailbereich das am besten geeignete Inhaltselement. Sind mehrere separate Felder vorhanden, sollten Sie die Verwendung eines Rasterlayouts erwägen, um die Elemente als Formular anzuordnen.

## <a name="get-the-code-samples"></a>Beispielcode herunterladen

Beispielcode, der das Master/Detail-Muster veranschaulicht, finden Sie hier: 

- [Beispieldatenbank Kundenbestellung](https://github.com/Microsoft/Windows-appsample-customers-orders-database) 
- [Beispiele für Raster- und Listenansicht](http://go.microsoft.com/fwlink/p/?LinkId=619900)
- [RSS-Reader-Beispiel](https://github.com/Microsoft/Windows-appsample-rssreader)

## <a name="related-articles"></a>Verwandte Artikel

- [Listen](lists.md)
- [Suche](search.md)
- [App- und Befehlsleisten](app-bars.md)
- [Listenansichtsklasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.ListView)
