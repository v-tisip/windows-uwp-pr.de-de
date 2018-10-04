---
author: normesta
description: Die Einträge und Eigenschaften eines Karten-Stylesheets
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: Karten-Stylesheet-Referenz
ms.author: normesta
ms.date: 03/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Karten, Karten-Stylesheet
ms.localizationpriority: medium
ms.openlocfilehash: f0a657ada755b77abe8ffef6a38bfa1f9ece8fcd
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4353397"
---
# <a name="map-style-sheet-reference"></a>Karten-Stylesheet-Referenz

Microsoft-Mapping-Technologien verwenden _Karten-Stylesheets_ , um die Darstellung der Karten zu definieren.  Eine Karte dem Stylesheet wird mithilfe von JavaScript Object Notation (JSON) definiert und in verschiedenen u. a. in einer Windows Store-Anwendung [MapControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol) über die [MapStyleSheet.ParseFromJson](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapstylesheet.parsefromjson#Windows_UI_Xaml_Controls_Maps_MapStyleSheet_ParseFromJson_System_String_) -Methode verwendet werden kann.

Stylesheets können interaktiv mithilfe der [Karte Formatvorlagen-Editor](https://www.microsoft.com/p/map-style-sheet-editor/9nbhtcjt72ft) -Anwendung erstellt werden.

Die folgende JSON kann verwendet werden, um Wasser wasserflächen in Rot, wasserbeschriftungen in Grün und landflächen in Blau:

```json
    {"version":"1.*",
        "settings":{"landColor":"#0000FF"},
        "elements":{"water":{"fillColor":"#FF0000","labelColor":"#00FF00"}}
    }
```

Diese JSON kann verwendet werden, um alle Beschriftungen und Punkte auf einer Karte entfernen.

```json

    {"version":"1.*", "elements":{"mapElement":{"labelVisible":false},"point":{"visible":false}}}
```

In einigen Fällen wird der Wert einer Eigenschaft transformiert, um das endgültige Ergebnis zu erzielen.  Beispielsweise hat die Pflanzen-FillColor je nach Typ der Entität geringfügig andere Töne.  Dieses Verhalten kann deaktiviert werden. So wird der exakte bereitgestellte Wert mithilfe der IgnoreTransform-Eigenschaft verwenden.

```json
    {"version":"1.*",
        "settings":{"shadedReliefVisible":false},
        "elements":{"vegetation":{"fillColor":{"value":"#999999","ignoreTransform":true}}}
    }
```

In diesem Thema werden die JSON-Einträge und [-Eigenschaften](#properties) behandelt, mit denen Sie das Aussehen und Verhalten von Karten anpassen können.  Diese Eigenschaften können auch auf Elemente der Karte über die Eigenschaft [MapStyleSheetEntry](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelement.mapstylesheetentry) angewendet werden.

<a id="entries" />

## <a name="entries"></a>Einträge
In der folgenden Tabelle wird das Zeichen „>” verwendet, um Ebenen in der Eintragshierarchie darzustellen.  Es zeigt auch, welche Versionen von Windows jeder Eintrag unterstützen und die ignorieren.

| Version | Name des Windows-Version |
|---------|----------------------|
|  1703   | Creators Update      |
|  1709   | Fall Creators Update |
|  1803   | Update April 2018    |
|  1809   | Oktober 2018-Update  |

| Name                         | Eigenschaftsgruppe            | 1703 | 1709 | 1803 | 1809 | Beschreibung    |
|------------------------------|---------------------------|------|------|------|------|----------------|
| version                      | [Version](#version)       |  ✔   |  ✔   |  ✔   |  ✔   | Die Stylesheet-Version, die Sie verwenden möchten |
| settings                     | [Einstellungen](#settings)     |  ✔   |  ✔   |  ✔   |  ✔   | Die Einstellungen, die für das gesamte Stylesheet gelten |
| mapElement                   | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Der übergeordnete Eintrag für alle Karteneinträge |
| > baseMapElement             | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Der übergeordnete Eintrag für alle Einträge mit Ausnahme von Benutzereinträgen |
| >> area                      | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Beschreiben Flächen Bereiche verwenden.  Diese sollten nicht zu verwechseln mit den physischen Gebäuden die unter dem Struktureintrag sind. |
| >>> airport                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Flächen, die Flughafen. |
| >>> areaOfInterest           | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Bereiche, in denen es viele Unternehmen oder Sehenswürdigkeiten gibt |
| >>> cemetery                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die FRIEDHÖFEN umfassen. |
| >>> continent                | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Continent Bereich Beschriftungen. |
| >>> education                | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die Schulen und andere Bildungseinrichtungen Funktionen umfassen. |
| >>> indigenousPeoplesReserve | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die einheimische Personen umfassen reserviert. |
| >>> industrial               | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Bereiche, die für gewerbliche Zwecke verwendet werden. |
| >>> island                   | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Insel Bereich Beschriftungen. |
| >>> medical                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die für medizinische Zwecke verwendet werden (z. B.: ein Krankenhaus-Geländes). |
| >>> military                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die umfassen militärbasen oder military verwendet haben. |
| >>> nautical                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die für nautische verwandte Zwecke verwendet werden. |
| >>> neighborhood             | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Nachbarschaft Bereich Beschriftungen. |
| >>> runway                   | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die als ein Flugzeug Landebahn verwendet wird. |
| >>> sand                     | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Sandige Flächen wie Strände |
| >>> shoppingCenter           | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Flächen, die Einkaufspassagen oder Einkaufszentren zugeordnet sind |
| >>> stadium                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die Stadionverbote umfassen. |
| >>> underground              | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Unterirdische Bereiche (z.B. Fläche einer U-Bahn-Station) |
| >>> vegetation               | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Wälder, Grünflächen usw. |
| >>>> forest                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Flächen mit Waldbestand |
| >>>> golfCourse              | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die Golfplätze umfassen. |
| >>>> park                    | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die Parks umfassen. |
| >>>> playingField            | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Als Spielfelder genutzte Flächen, wie Baseballfelder oder Tennisplätze |
| >>>> reserve                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Bereiche, die Art umfassen reserviert. |
| >> point                     | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Alle Point-Features, die mit einem Symbol irgendeiner gezeichnet werden. |
| >>> address                  | [PointStyle](#pointstyle) |      |      |  ✔   |  ✔   | Beheben Sie Zahlen Beschriftungen. |
| >>> naturalPoint             | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die natürliche Features darstellen. |
| >>>> peak                    | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Berggipfel darstellen |
| >>>>> volcanicPeak           | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Vulkangipfel darstellen |
| >>>> waterPoint              | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Standorte von Wasseranlagen darstellen, wie Wasserfälle |
| >>> pointOfInterest          | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die jedem Standort und interessante darstellen. |
| >>>> business                | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die alle Unternehmen Locaiton darstellen. |
| >>>>> AttractionPoint        | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Touristenattraktionen wie Museen, zoologischen Gärten usw. darstellen. |
| >>>>> CommunityPoint         | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Positionen der allgemeine Verwendung in der Community darstellen. |
| >>>>> EducationPoint         | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Schulen und anderen Education darstellen, im Zusammenhang mit Standorten. |
| >>>>> EntertainmentPoint     | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Unterhaltung Orten wie Theater, Kinos usw. darstellen. |
| >>>>> EssentialServicePoint  | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die wichtige Dienste wie Parkplätze, Bänke verfügen, Gaspedal usw. darstellen. |
| >>>>> foodPoint              | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Restaurants, Cafés usw. darstellen. |
| >>>>> LodgingPoint           | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Hotels und andere Unternehmen Stellung darstellen. |
| >>>>> RealEstatePoint        | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Unternehmen Immobilien darstellen. |
| >>>>> ShoppingPoint          | [PointStyle](#pointstyle) |      |  ✔   |  ✔   |  ✔   | Symbole, die Hotels und andere Unternehmen Stellung darstellen. |
| >>> populatedPlace           | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die die Größe eines bewohnten Ortes darstellen (z.B. eine Stadt oder eine Ortschaft) |
| >>>> capital                 | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die die Hauptstadt eines bewohnten Gebiets darstellen |
| >>>>> adminDistrictCapital   | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die die Hauptstadt von Bundesländern/Provinzen darstellen |
| >>>>> countryRegionCapital   | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die die Hauptstadt von Ländern oder Regionen darstellen |
| >>> roadShield               | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Zeichen, die die Bezeichnung einer Straße darstellen (zum Beispiel: I-5). Verwenden Sie nur Palettenwerte, wenn Sie die **ImageFamily**-Eigenschaft des Einstellungseintrags auf einen Wert von *Palette* festlegen. |
| >>> roadExit                 | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Ausfahrten, in der Regel aus einer Autobahn mit Zugangsüberwachungssystem, darstellen |
| >>> transit                  | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Symbole, die Bushaltestellen, Zughaltestellen, Flughäfen usw. darstellen |
| >> political                 | [BorderedMapElement](#borderedmapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Politische Gebiete, wie Länder, Regionen und Staaten |
| >>> countryRegion            | [BorderedMapElement](#borderedmapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Land Region Rahmen und Beschriftungen. |
| >>> adminDistrict            | [BorderedMapElement](#borderedmapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Admin1, Staaten, Provinzen usw., Ränder und bezeichnet wird. |
| >>> district                 | [BorderedMapElement](#borderedmapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Admin2, Landkreise usw., Ränder und bezeichnet wird. |
| >> structure                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Häuser und andere gebäudeähnliche Bauten |
| >>> building                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Gebäude. |
| >>>> educationBuilding       | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Gebäude für Bildungseinrichtungen verwendet. |
| >>>> medicalBuilding         | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Gebäude für medizinische Zwecke wie z. B. Krankenhäuser verwendet. |
| >>>> transitBuilding         | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Gebäude für Öffentliche Verkehrsmittel wie Flughäfen verwendet. |
| >> transportation            | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Teil des Transportnetzwerks sind (z.B. Straßen, Züge und Fähren) |
| >>> road                     | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die alle Straßen darstellen |
| >>>> controlledAccessHighway | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die große, kontrollierte Zugriff Autobahnen darstellen. |
| >>>>> highSpeedRamp          | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die mit hoher Geschwindigkeit auffahrten darstellen, die in der Regel Verbindung kontrollierten Zugriff Autobahnen. |
| >>>> highway                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Autobahnen darstellen. |
| >>>> majorRoad               | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die wichtige Straßen darstellen. |
| >>>> arterialRoad            | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Arterieller Straßen darstellen. |
| >>>> street                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Straßen darstellen. |
| >>>>> ramp                   | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die auffahrten darstellen, die in der Regel mit Autobahnen verbinden. |
| >>>>> unpavedStreet          | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die unpaved Straßen darstellen. |
| >>>> tollRoad                | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Straßen, die Kosten Geld darstellen zu verwenden. |
| >>> railway                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Eisenbahnlinien |
| >>> trail                    | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Spazierwege durch Parks oder Wanderwege |
| >>> Gehweg eingetragen                  | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Mit erhöhten Rechten Gehweg eingetragen. |
| >>> waterRoute               | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Fährlinien |
| >> water                     | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Alle Elemente, die wie Wasser aussehen. Dazu zählen Ozeane und Flüsse. |
| >>> river                    | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Flüsse, Ströme oder andere Wasserstraßen.  Beachten Sie, dass es sich herbei um Linien oder Polygone handeln kann, die zu stehenden Gewässern verbinden können. |
| > routeMapElement            | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Alle zugehörigen Routingeinträgen. |
| >> routeLine                 | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Weiterleiten Zeile im Zusammenhang mit Einträgen. |
| >>> drivingRoute             | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die steuernde Routen darstellen. |
| >>> scenicRoute              | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Linien, die malerische steuernde Routen darstellen. |
| >>> walkingRoute             | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Linien, die Routen walking darstellen. |
| > userMapElement             | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Alle Benutzereinträge. |
| >> userBillboard             | [MapElement](#mapelement) |      |  ✔   |  ✔   |  ✔   | Das Format für Standard-[MapBillboard](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)-Instanzen |
| >> userLine                  | [MapElement](#mapelement) |  ✔   |  ✔   |  ✔   |  ✔   | Das Format für Standard-[MapPolyline](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mappolyline)-Instanzen |
| >> userModel3D               | [MapElement3D](#mapelement3d) |      |  ✔   |  ✔   |  ✔   | Das Format für Standard-[MapModel3D](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapmodel3d)-Instanzen.  Dies gilt in erster Linie zur Einstellung von renderAsSurface. |
| >> userPoint                 | [PointStyle](#pointstyle) |  ✔   |  ✔   |  ✔   |  ✔   | Das Format für Standard-[MapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapicon)-Instanzen |

<a id="properties" />

## <a name="properties"></a>Eigenschaften

In diesem Abschnitt werden die Eigenschaften beschrieben, die Sie für die Einträge verwenden können.

<a id="version" />

### <a name="version-properties"></a>Versionseigenschaften

| Eigenschaft                     | Typ    | Beschreibung                                                                                                           |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------|
| version                      | Zeichenfolge  | Version des zu verwendenden Stylesheets. Wird für die Anwendbarkeit verwendet. „1.0” als Standard, „1. *” für zusätzliche geringfügige Featureupdates |

<a id="settings" />

### <a name="settings-properties"></a>Einstellungseigenschaften

| Eigenschaft                     | Typ    | 1703 | 1709 | 1803 | 1809 | Beschreibung |
|------------------------------|---------|------|------|------|------|-------------|
| atmosphereVisible            | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob die Atmosphäre im 3D-Steuerelement angezeigt wird |
| buildingTexturesVisible      | Bool    |      |      |  ✔   |  ✔   | Ein Flag, das angibt, ob Texturen auf symbolischen 3D-Gebäuden, die über Texturen verfügen, angezeigt werden sollen oder nicht |
| fogColor                     | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Der ARGB-Farbwert des Distanznebels, der im 3D-Steuerelement angezeigt wird |
| glowColor                    | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Der ARGB-Farbwert, der für glänzende Beschriftungen und Symbole angewendet werden kann |
| imageFamily                  | Zeichenfolge  |  ✔   |  ✔   |  ✔   |  ✔   | Der Name der Bildzusammenstellung, die für dieses Format verwendet werden soll. Legen Sie diesen Wert auf *Default* für Zeichen fest, die feste Farben verwenden, die auf den Zeichen in der realen Welt basieren. Legen Sie diesen Wert auf *Palette* für Zeichen fest, die über die Palette konfigurierbare Farben verwenden. |
| landColor                    | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Der ARGB-Farbwert von Landflächen, bevor etwas darauf gezeichnet wird |
| logosVisible                 | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob Elemente mit einer **Organization**-Eigenschaft die entsprechenden Logos zeichnen oder ein allgemeines Symbol verwenden sollen |
| officialColorVisible         | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob Elemente, die über eine offizielle Farbeigenschaft verfügen (wie Transitlinien in China), in dieser Farbe gezeichnet werden sollen. Deaktivieren Sie diesen Wert beispielsweise für Schwarz-Weiß-Karten. |
| rasterRegionsVisible         | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob rasterregionen gezeichnet, in denen sie eine bessere Darstellung als Vektoren (Japan und Korea) verfügen. |
| shadedReliefVisible          | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob Schattierungen für Erhöhungen auf der Karte gezeichnet werden sollen |
| shadedReliefDarkColor        | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe der dunklen Seite des schattierten Reliefs.  Der Alphakanal stellt den maximalen Alphawert. |
| shadedReliefLightColor       | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe der hellen Seite des schattierten Reliefs.  Der Alphakanal stellt den maximalen Alphawert. |
| shadowColor                  | Farbe   |      |      |      |  ✔️   | Die Farbe des Schattens hinter Symbole, die Schatten verwenden. |
| spaceColor                   | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Der ARGB-Farbwert für den Bereich um die Karte herum |
| useDefaultImageColors        | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Ein Flag, das angibt, ob die ursprünglichen Farben in SVG suchen Sie den Paletteneintrag nach Farben in einem Bild, anstatt verwendet werden soll. |

<a id="mapelement" />

### <a name="mapelement-properties"></a>MapElement-Eigenschaften

| Eigenschaft                     | Typ    | 1703 | 1709 | 1803 | 1809 | Beschreibung |
|------------------------------|---------|------|------|------|------|-------------|
| backgroundScale              | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Betrag, um den das Hintergrundelement eines Symbols skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| fillColor                    | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe, die für das Füllen von Polygonen, den Hintergrund von Punktsymbolen und für die Mitte von geteilten Linien verwendet wird |
| fontFamily                   | String  |  ✔   |  ✔   |  ✔   |  ✔   |  |
| iconColor                    | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe der Glyphe, die in der Mitte eines Punktsymbols angezeigt wird |
| iconScale                    | Gleitkomma   |      |  ✔   |  ✔   |  ✔   | Betrag, um den die Glyphe eines Symbols skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| labelColor                   | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   |  |
| labelOutlineColor            | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   |  |
| labelScale                   | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Der Wert, um den die Standardgröße von Beschriftungen skaliert wird. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| labelVisible                 | Bool    |  ✔   |  ✔   |  ✔   |  ✔   |  |
| overwriteColor               | Bool    |  ✔   |  ✔   |  ✔   |  ✔   | Führt das Überschreiben von **StrokeColor** mit dem Alphawert von **FillColor** aus, anstatt eine Mischung der beiden Farben zu verwenden |
| scale                        | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Der Wert, um den die gesamte Größe des Punkts skaliert wird. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| strokeColor                  | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe, die für die Kontur von Polygonen, die Kontur von Punktsymbolen und die Farbe von Linien verwendet werden soll |
| strokeWidthScale             | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Der Wert, um den die Strichstärke von Linien skaliert wird Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| visible                      | Bool    |  ✔   |  ✔   |  ✔   |  ✔   |  |

<a id="borderedmap" />

### <a name="borderedmapelement"></a>BorderedMapElement

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | 1703 | 1709 | 1803 | 1809 | Beschreibung |
|------------------------------|---------|------|------|------|------|-------------|
| borderOutlineColor           | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die sekundäre oder Umrandungslinienfarbe des Rahmens eines gefüllten Polygons |
| borderStrokeColor            | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die primäre Farbe des Rahmens eines gefüllten Polygons |
| borderVisible                | Bool    |  ✔   |  ✔   |  ✔   |  ✔   |  |
| borderWidthScale             | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Der Betrag, den die Strichstärke von Rahmen skaliert werden. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |

<a id="pointstyle" />

### <a name="pointstyle-properties"></a>PointStyle-Eigenschaften

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | 1703 | 1709 | 1803 | 1809 | Beschreibung |
|------------------------------|---------|------|------|------|------|-------------|
| Shape-Hintergrund             | Gleitkomma   |      |      |      |  ✔️   | Form, der als Hintergrund des Symbols – ersetzt eine beliebige Form, die vorhanden ist. |
| stemAnchorRadiusScale        | Gleitkomma   |      |      |  ✔   |  ✔   | Betrag, um den der Ankerpunkt eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| stemColor                    | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe des Schafts unten an einem Symbol im 3D-Modus |
| stemHeightScale              | Gleitkomma   |      |      |  ✔   |  ✔   | Betrag, um den die Länge eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Länge. |
| stemOutlineColor             | Farbe   |  ✔   |  ✔   |  ✔   |  ✔   | Die Farbe der Kontur um den Schaft unten an einem Symbol im 3D-Modus |
| stemWidthScale               | Gleitkomma   |  ✔   |  ✔   |  ✔   |  ✔   | Betrag, um den die Breite eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Länge. |

<a id="mapelement3d" />

### <a name="mapelement3d"></a>MapElement3D

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | 1703 | 1709 | 1803 | 1809 | Beschreibung |
|------------------------------|---------|------|------|------|------|------------|
| renderAsSurface              | Bool    |      |      |  ✔   |  ✔   | Ein Flag, das angibt, dass ein 3D-Modell wie ein Gebäude gerendert werden soll – ohne Tiefenausblendung gegen den Boden |
