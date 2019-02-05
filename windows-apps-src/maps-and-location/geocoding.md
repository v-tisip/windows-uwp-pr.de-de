---
title: Durchführen der Geocodierung und umgekehrten Geocodierung
description: Dieser Anleitung erfahren Sie, wie Sie konvertieren Adressen in geografische Standorte (geocodierung) und geografische Standorte in Adressen (umgekehrte geocodierung) durch Aufrufen der Methoden der MapLocationFinder-Klasse im Windows.Services.Maps-Namespace.
ms.assetid: B912BE80-3E1D-43BB-918F-7A43327597D2
ms.date: 07/02/2018
ms.topic: article
keywords: Windows10, UWP, Geocodierung, Karte, Ort, Standort
ms.localizationpriority: medium
ms.openlocfilehash: a30ca89242b15866019fffc6972bdae7086f3f7e
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9046443"
---
# <a name="perform-geocoding-and-reverse-geocoding"></a>Durchführen von Geocodierung und umgekehrter Geocodierung

In dieser Anleitung erfahren Sie, wie Sie konvertieren Adressen in geografische Standorte (geocodierung) und geografische Standorte in Adressen (umgekehrte geocodierung) durch Aufrufen der Methoden der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse in der [**Windows.Services.Maps **](https://msdn.microsoft.com/library/windows/apps/dn636979)Namespace.

> [!TIP]
> Um mehr über die Verwendung von Karten in Ihrer app zu erfahren, laden Sie das [MapControl](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MapControl) -Beispiel aus dem [Windows-universal-Samples-Repository](hhttps://github.com/Microsoft/Windows-universal-samples) auf GitHub.

Die Klassen geocodierung und umgekehrte geocodierung beteiligt sind wie folgt aufgebaut.

-   [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse enthält Methoden für die Verarbeitung von geocodierung ([**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925)) und umgekehrten geocodierung ([**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)).
-   Diese Methoden geben eine [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) -Instanz zurück.
-   Die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) enthält eine Auflistung der [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) -Objekte. 
-   [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte enthalten eine [**Adresse**](https://msdn.microsoft.com/library/windows/apps/dn636929) -Eigenschaft, die ein [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) -Objekt, das eine Straße darstellen verfügbar macht, sowohl eine [**Punkt**](https://docs.microsoft.com/uwp/api/windows.services.maps.maplocation.point) -Eigenschaft, die ein [**Geopoint**](https://docs.microsoft.com/uwp/api/windows.devices.geolocation.geopoint) -Objekt zurück, einen geografischen Standort verfügbar macht.

> [!IMPORTANT]
> Sie müssen einen Kartenauthentifizierungsschlüssel angeben, bevor Sie Kartendienste verwenden können. Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](authentication-key.md).

## <a name="get-a-location-geocode"></a>Abrufen eines Standorts (Geocode)

In diesem Abschnitt zeigt, wie eine Adresse oder einen Ortsnamen in einen geografischen Standort (geocodierung) konvertiert.

1.  Rufen Sie eine der Überladungen der [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) -Methode der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550) -Klasse mit einem Ortsnamen oder Straße.
2.  Die [**FindLocationsAsync**](https://msdn.microsoft.com/library/windows/apps/dn636925) -Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) -Objekt zurück.
3.  Verwenden Sie die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) , um eine Sammlung [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) -Objekte verfügbar zu machen. Da das System mehreren Standorten finden kann, die der Eingabe entsprechen, möglicherweise mehrere [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte vor.

```csharp
using Windows.Services.Maps;
using Windows.Devices.Geolocation;
...
private async void geocodeButton_Click(object sender, RoutedEventArgs e)
{
   // The address or business to geocode.
   string addressToGeocode = "Microsoft";

   // The nearby location to use as a query hint.
   BasicGeoposition queryHint = new BasicGeoposition();
   queryHint.Latitude = 47.643;
   queryHint.Longitude = -122.131;
   Geopoint hintPoint = new Geopoint(queryHint);

   // Geocode the specified address, using the specified reference point
   // as a query hint. Return no more than 3 results.
   MapLocationFinderResult result =
         await MapLocationFinder.FindLocationsAsync(
                           addressToGeocode,
                           hintPoint,
                           3);

   // If the query returns results, display the coordinates
   // of the first result.
   if (result.Status == MapLocationFinderStatus.Success)
   {
      tbOutputText.Text = "result = (" +
            result.Locations[0].Point.Position.Latitude.ToString() + "," +
            result.Locations[0].Point.Position.Longitude.ToString() + ")";
   }
}
```

Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:

``` syntax
result = (47.6406099647284,-122.129339994863)
```

## <a name="get-an-address-reverse-geocode"></a>Abrufen einer Adresse (umgekehrte Geocodierung)

In diesem Abschnitt zeigt, wie konvertieren einen geografischen Standort in eine Adresse (umgekehrte geocodierung).

1.  Rufen Sie die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode der [**MapLocationFinder**](https://msdn.microsoft.com/library/windows/apps/dn627550)-Klasse auf.
2.  Die [**FindLocationsAtAsync**](https://msdn.microsoft.com/library/windows/apps/dn636928)-Methode gibt ein [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551)-Objekt zurück, das eine Sammlung übereinstimmender [**MapLocation**](https://msdn.microsoft.com/library/windows/apps/dn627549)-Objekte enthält.
3.  Verwenden Sie die [**Speicherorte**](https://msdn.microsoft.com/library/windows/apps/dn627552) -Eigenschaft der [**MapLocationFinderResult**](https://msdn.microsoft.com/library/windows/apps/dn627551) , um eine Sammlung [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) -Objekte verfügbar zu machen. Da das System mehreren Standorten finden kann, die der Eingabe entsprechen, möglicherweise mehrere [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) Objekte vor.
4.  Greifen Sie über die [**Adresse**](https://msdn.microsoft.com/library/windows/apps/dn636929) -Eigenschaft jedes [**Kartenregion**](https://msdn.microsoft.com/library/windows/apps/dn627549) [**MapAddress**](https://msdn.microsoft.com/library/windows/apps/dn627533) Objekte auf.

```csharp
using Windows.Services.Maps;
using Windows.Devices.Geolocation;
...
private async void reverseGeocodeButton_Click(object sender, RoutedEventArgs e)
{
   // The location to reverse geocode.
   BasicGeoposition location = new BasicGeoposition();
   location.Latitude = 47.643;
   location.Longitude = -122.131;
   Geopoint pointToReverseGeocode = new Geopoint(location);

   // Reverse geocode the specified geographic location.
   MapLocationFinderResult result =
         await MapLocationFinder.FindLocationsAtAsync(pointToReverseGeocode);

   // If the query returns results, display the name of the town
   // contained in the address of the first result.
   if (result.Status == MapLocationFinderStatus.Success)
   {
      tbOutputText.Text = "town = " +
            result.Locations[0].Address.Town;
   }
}
```

Dieser Code zeigt die folgenden Ergebnisse im `tbOutputText`-Textfeld an:

``` syntax
town = Redmond
```

## <a name="related-topics"></a>Verwandte Themen

* [Beispiel für UWP-Karte](https://go.microsoft.com/fwlink/p/?LinkId=619977)
* [Beispiel für eine UWP-App mit Verkehrsinformationen](https://go.microsoft.com/fwlink/p/?LinkId=619982)
* [Entwurfsrichtlinien für Karten](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [Video: Nutzen von Karten und Position über Telefon, Tablet und PC in Ihren Windows-Apps](https://channel9.msdn.com/Events/Build/2015/2-757)
* [Bing Maps Developer Center](https://www.bingmapsportal.com/)
* [**MapLocationFinder** Klasse](https://msdn.microsoft.com/library/windows/apps/dn627550)
* [**FindLocationsAsync** -Methode](https://msdn.microsoft.com/library/windows/apps/dn636925)
* [**FindLocationsAtAsync** -Methode](https://msdn.microsoft.com/library/windows/apps/dn636928)
