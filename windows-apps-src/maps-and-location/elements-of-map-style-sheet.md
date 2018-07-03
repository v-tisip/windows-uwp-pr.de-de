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
ms.openlocfilehash: 8fb80bc28900ee695ecf3b9e62b5dafc8f1a8cb3
ms.sourcegitcommit: f91aa1e402f1bc093b48a03fbae583318fc7e05d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "1917773"
---
# <a name="map-style-sheet-reference"></a>Karten-Stylesheet-Referenz

Sie können Karten-Stylesheets in der JavaScript Object Notation (JSON) erstellen.

Beispielsweise würden Sie den folgende JSON-Code verwenden, damit Wasserflächen in Rot, Wasserbeschriftungen in Grün und Landflächen in Blau dargestellt werden:

```json
    {"version":"1.*",
        "settings":{"landColor":"#0000FF"},
        "elements":{"water":{"fillColor":"#FF0000", "labelColor":"#00FF00"}}
    }
```
Sie können mit JSON auch alle Beschriftungen und Punkte auf einer Karte entfernen.

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

In diesem Thema werden die JSON-Einträge und [-Eigenschaften](#properties) behandelt, mit denen Sie das Aussehen und Verhalten von Karten anpassen können.

<a id="entries" />

## <a name="entries"></a>Einträge
In der folgenden Tabelle wird das Zeichen „>” verwendet, um Ebenen in der Eintragshierarchie darzustellen.   

| Name                         | Eigenschaftsgruppe            | Beschreibung    |
|------------------------------|---------------------------|----------------|
| version                      | [Version](#version)       | Die Stylesheet-Version, die Sie verwenden möchten |
| settings                     | [Einstellungen](#settings)     | Die Einstellungen, die für das gesamte Stylesheet gelten |
| mapElement                   | [MapElement](#mapelement) | Der übergeordnete Eintrag für alle Karteneinträge |
| > baseMapElement             | [MapElement](#mapelement) | Der übergeordnete Eintrag für alle Einträge mit Ausnahme von Benutzereinträgen |
| >> area                      | [MapElement](#mapelement) | Flächen der Landnutzung (nicht zu verwechseln mit dem Struktureintrag) |
| >>> airport                  | [MapElement](#mapelement) | Flächen, die einen Flughafen umgeben |
| >>> areaOfInterest           | [MapElement](#mapelement) | Bereiche, in denen es viele Unternehmen oder Sehenswürdigkeiten gibt |
| >>> cemetery                 | [MapElement](#mapelement) | Flächen mit Friedhöfen |
| >>> continent                | [MapElement](#mapelement) | Flächen ganzer Kontinente |
| >>> education                | [MapElement](#mapelement) |  |
| >>> indigenousPeoplesReserve | [MapElement](#mapelement) |  |
| >>> industrial               | [MapElement](#mapelement) | Landflächen, die für industrielle Zwecke genutzt werden |
| >>> island                   | [MapElement](#mapelement) | Beschriftungen auf Inselflächen |
| >>> medical                  | [MapElement](#mapelement) | Landflächen, die für medizinische Zwecke genutzt werden (z.B. ein Krankenhauskomplex) |
| >>> military                 | [MapElement](#mapelement) | Flächen von Militärbasen |
| >>> nautical                 | [MapElement](#mapelement) | Landflächen, die für nautische Zwecke genutzt werden |
| >>> neighborhood             | [MapElement](#mapelement) | Beschriftungen auf Flächen, die als Stadtteile definiert sind |
| >>> runway                   | [MapElement](#mapelement) | Landflächen, auf der sich eine Landebahn befindet |
| >>> sand                     | [MapElement](#mapelement) | Sandige Flächen wie Strände |
| >>> shoppingCenter           | [MapElement](#mapelement) | Flächen, die Einkaufspassagen oder Einkaufszentren zugeordnet sind |
| >>> stadium                  | [MapElement](#mapelement) | Fläche eines Stadiums |
| >>> underground              | [MapElement](#mapelement) | Unterirdische Bereiche (z.B. Fläche einer U-Bahn-Station) |
| >>> vegetation               | [MapElement](#mapelement) | Wälder, Grünflächen usw. |
| >>>> forest                  | [MapElement](#mapelement) | Flächen mit Waldbestand |
| >>>> golfCourse              | [MapElement](#mapelement) |  |
| >>>> park                    | [MapElement](#mapelement) | Parkflächen |
| >>>> playingField            | [MapElement](#mapelement) | Als Spielfelder genutzte Flächen, wie Baseballfelder oder Tennisplätze |
| >>>> reserve                 | [MapElement](#mapelement) | Flächen von Naturschutzgebieten |
| >> point                     | [PointStyle](#pointstyle) | Alle Punktfeatures, die mit einem Symbol dargestellt werden |
| >>> address                  | [PointStyle](#pointstyle) | Zahlen in Adressen |
| >>> naturalPoint             | [PointStyle](#pointstyle) |  |
| >>>> peak                    | [PointStyle](#pointstyle) | Symbole, die Berggipfel darstellen |
| >>>>> volcanicPeak           | [PointStyle](#pointstyle) | Symbole, die Vulkangipfel darstellen |
| >>>> waterPoint              | [PointStyle](#pointstyle) | Symbole, die Standorte von Wasseranlagen darstellen, wie Wasserfälle |
| >>> pointOfInterest          | [PointStyle](#pointstyle) | Restaurants, Krankenhäuser, Schulen, Yachthäfen, Skigebiete usw. |
| >>>> business                | [PointStyle](#pointstyle) | Restaurants, Krankenhäuser, Schulen usw. |
| >>>>> foodPoint              | [PointStyle](#pointstyle) | Restaurants, Cafés usw. |
| >>> populatedPlace           | [PointStyle](#pointstyle) | Symbole, die die Größe eines bewohnten Ortes darstellen (z.B. eine Stadt oder eine Ortschaft) |
| >>>> capital                 | [PointStyle](#pointstyle) | Symbole, die die Hauptstadt eines bewohnten Gebiets darstellen |
| >>>>> adminDistrictCapital   | [PointStyle](#pointstyle) | Symbole, die die Hauptstadt von Bundesländern/Provinzen darstellen |
| >>>>> countryRegionCapital   | [PointStyle](#pointstyle) | Symbole, die die Hauptstadt von Ländern oder Regionen darstellen |
| >>> roadShield               | [PointStyle](#pointstyle) | Zeichen, die die Bezeichnung einer Straße darstellen (zum Beispiel: I-5). Verwenden Sie nur Palettenwerte, wenn Sie die **ImageFamily**-Eigenschaft des Einstellungseintrags auf einen Wert von *Palette* festlegen. |
| >>> roadExit                 | [PointStyle](#pointstyle) | Symbole, die Ausfahrten, in der Regel aus einer Autobahn mit Zugangsüberwachungssystem, darstellen |
| >>> transit                  | [PointStyle](#pointstyle) | Symbole, die Bushaltestellen, Zughaltestellen, Flughäfen usw. darstellen |
| >> political                 | [BorderedMapElement](#borderedmapelement) | Politische Gebiete, wie Länder, Regionen und Staaten |
| >>> countryRegion            | [BorderedMapElement](#borderedmapelement) |  |
| >>> adminDistrict            | [BorderedMapElement](#borderedmapelement) | Admin1, Staaten, Provinzen usw. |
| >>> district                 | [BorderedMapElement](#borderedmapelement) | Admin2 Landkreise usw. |
| >> structure                 | [MapElement](#mapelement) | Häuser und andere gebäudeähnliche Bauten |
| >>> building                 | [MapElement](#mapelement) |  |
| >>>> educationBuilding       | [MapElement](#mapelement) |  |
| >>>> medicalBuilding         | [MapElement](#mapelement) |  |
| >>>> transitBuilding         | [MapElement](#mapelement) |  |
| >> transportation            | [MapElement](#mapelement) | Linien, die Teil des Transportnetzwerks sind (z.B. Straßen, Züge und Fähren) |
| >>> road                     | [MapElement](#mapelement) | Linien, die alle Straßen darstellen |
| >>>> controlledAccessHighway | [MapElement](#mapelement) |  |
| >>>>> highSpeedRamp          | [MapElement](#mapelement) | Linien, die Auffahrten darstellen. Diese Auffahrten erscheinen normalerweise zusammen mit Autobahnen mit Zugangsüberwachungssystem. |
| >>>> highway                 | [MapElement](#mapelement) |  |
| >>>> majorRoad               | [MapElement](#mapelement) |  |
| >>>> arterialRoad            | [MapElement](#mapelement) |  |
| >>>> street                  | [MapElement](#mapelement) |  |
| >>>>> ramp                   | [MapElement](#mapelement) | Linien, die Ein- und Ausfahrten einer Autobahn darstellen |
| >>>>> unpavedStreet          | [MapElement](#mapelement) |  |
| >>>> tollRoad                | [MapElement](#mapelement) | Mautstraßen |
| >>> railway                  | [MapElement](#mapelement) | Eisenbahnlinien |
| >>> trail                    | [MapElement](#mapelement) | Spazierwege durch Parks oder Wanderwege |
| >>> waterRoute               | [MapElement](#mapelement) | Fährlinien |
| >> water                     | [MapElement](#mapelement) | Alle Elemente, die wie Wasser aussehen. Dazu zählen Ozeane und Flüsse. |
| >>> river                    | [MapElement](#mapelement) | Flüsse, Ströme oder andere Wasserstraßen.  Beachten Sie, dass es sich herbei um Linien oder Polygone handeln kann, die zu stehenden Gewässern verbinden können. |
| > routeMapElement            | [MapElement](#mapelement) | Alle Streckenführungen fallen unter diesen Eintrag. |
| >> routeLine                 | [MapElement](#mapelement) | Das Format für alle Streckenführungen |
| >>> drivingRoute             | [MapElement](#mapelement) |  |
| >>> scenicRoute              | [MapElement](#mapelement) |  |
| >>> walkingRoute             | [MapElement](#mapelement) |  |
| > userMapElement             | [MapElement](#mapelement) | Alle Benutzereinträge fallen unter diesen Eintrag. |
| >> userBillboard             | [MapElement](#mapelement) | Das Format für Standard-[MapBillboard](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapbillboard)-Instanzen |
| >> userLine                  | [MapElement](#mapelement) | Das Format für Standard-[MapPolyline](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mappolyline)-Instanzen |
| >> userModel3D               | [MapElement3D](#mapelement3d) | Das Format für Standard-[MapModel3D](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapmodel3d)-Instanzen.  Dies gilt in erster Linie zur Einstellung von renderAsSurface. |
| >> userPoint                 | [PointStyle](#pointstyle) | Das Format für Standard-[MapIcon](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapicon)-Instanzen |


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

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                                                                                                                 |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| atmosphereVisible            | Bool    | Ein Flag, das angibt, ob die Atmosphäre im 3D-Steuerelement angezeigt wird                                                                                                                                                     |
| buildingTexturesVisible      | Bool    | Ein Flag, das angibt, ob Texturen auf symbolischen 3D-Gebäuden, die über Texturen verfügen, angezeigt werden sollen oder nicht                                                                                                                          |
| fogColor                     | Farbe   | Der ARGB-Farbwert des Distanznebels, der im 3D-Steuerelement angezeigt wird                                                                                                                                                    |
| glowColor                    | Farbe   | Der ARGB-Farbwert, der für glänzende Beschriftungen und Symbole angewendet werden kann                                                                                                                                                     |
| imageFamily                  | Zeichenfolge  | Der Name der Bildzusammenstellung, die für dieses Format verwendet werden soll. Legen Sie diesen Wert auf *Default* für Zeichen fest, die feste Farben verwenden, die auf den Zeichen in der realen Welt basieren. Legen Sie diesen Wert auf *Palette* für Zeichen fest, die über die Palette konfigurierbare Farben verwenden. |
| landColor                    | Farbe   | Der ARGB-Farbwert von Landflächen, bevor etwas darauf gezeichnet wird                                                                                                                                                     |
| logosVisible                 | Bool    | Ein Flag, das angibt, ob Elemente mit einer **Organization**-Eigenschaft die entsprechenden Logos zeichnen oder ein allgemeines Symbol verwenden sollen                                                                                         |
| officialColorVisible         | Bool    | Ein Flag, das angibt, ob Elemente, die über eine offizielle Farbeigenschaft verfügen (wie Transitlinien in China), in dieser Farbe gezeichnet werden sollen. Deaktivieren Sie diesen Wert beispielsweise für Schwarz-Weiß-Karten.                               |
| rasterRegionsVisible         | Bool    | Ein Flag, das angibt, ob Rasterregionen gezeichnet werden sollen, wenn Rendern per Vektoren verwendet wird (z.B. Japan und Korea)                                                                                                |
| shadedReliefVisible          | Bool    | Ein Flag, das angibt, ob Schattierungen für Erhöhungen auf der Karte gezeichnet werden sollen                                                                                                                                                  |
| shadedReliefDarkColor        | Farbe   | Die Farbe der dunklen Seite des schattierten Reliefs.  Der Alphakanal stellt den maximalen Alphawert dar.                                                                                                                            |
| shadedReliefLightColor       | Farbe   | Die Farbe der hellen Seite des schattierten Reliefs.  Der Alphakanal stellt den maximalen Alphawert dar.                                                                                                                           |
| spaceColor                   | Farbe   | Der ARGB-Farbwert für den Bereich um die Karte herum                                                                                                                                                                               |
| useDefaultImageColors        | Bool    | Ein Flag, das angibt, ob die ursprünglichen Farben in SVG verwendet werden sollen, anstatt den Paletteneintrag nach Farben in einem Bild zu durchsuchen                                                                                |

<a id="mapelement" />

### <a name="mapelement-properties"></a>MapElement-Eigenschaften

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                       |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| backgroundScale              | Gleitkomma   | Betrag, um den das Hintergrundelement eines Symbols skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| fillColor                    | Farbe   | Die Farbe, die für das Füllen von Polygonen, den Hintergrund von Punktsymbolen und für die Mitte von geteilten Linien verwendet wird       |
| fontFamily                   | String  |                                                                                                                                   |
| iconColor                    | Farbe   | Die Farbe der Glyphe, die in der Mitte eines Punktsymbols angezeigt wird                                                                       |
| iconScale                    | Gleitkomma   | Betrag, um den die Glyphe eines Symbols skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.              |
| labelColor                   | Farbe   |                                                                                                                                   |
| labelOutlineColor            | Farbe   |                                                                                                                                   |
| labelScale                   | Gleitkomma   | Der Wert, um den die Standardgröße von Beschriftungen skaliert wird. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.                  |
| labelVisible                 | Bool    |                                                                                                                                   |
| overwriteColor               | Bool    | Führt das Überschreiben von **StrokeColor** mit dem Alphawert von **FillColor** aus, anstatt eine Mischung der beiden Farben zu verwenden                               |
| scale                        | Gleitkomma   | Der Wert, um den die gesamte Größe des Punkts skaliert wird. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.                |
| strokeColor                  | Farbe   | Die Farbe, die für die Kontur von Polygonen, die Kontur von Punktsymbolen und die Farbe von Linien verwendet werden soll                         |
| strokeWidthScale             | Gleitkomma   | Der Wert, um den die Strichstärke von Linien skaliert wird Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.                  |
| visible                      | Bool    |                                                                                                                                   |

<a id="borderedmap" />

### <a name="borderedmapelement"></a>BorderedMapElement

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                           |
|------------------------------|---------|-----------------------------------------------------------------------|
| borderOutlineColor           | Farbe   | Die sekundäre oder Umrandungslinienfarbe des Rahmens eines gefüllten Polygons |
| borderStrokeColor            | Farbe   | Die primäre Farbe des Rahmens eines gefüllten Polygons             |
| borderVisible                | Bool    |                                                                       |
| borderWidthScale             | Gleitkomma   |                                                                       |

<a id="pointstyle" />

### <a name="pointstyle-properties"></a>PointStyle-Eigenschaften

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                      |
|------------------------------|---------|----------------------------------------------------------------------------------------------------------------------------------|
| stemAnchorRadiusScale        | Gleitkomma   | Betrag, um den der Ankerpunkt eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| stemColor                    | Farbe   | Die Farbe des Schafts unten an einem Symbol im 3D-Modus                                                           |
| stemHeightScale              | Gleitkomma   | Betrag, um den die Länge eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Länge. |
| stemWidthScale               | Gleitkomma   | Betrag, um den die Breite eines Symbolschafts skaliert werden soll.  Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Länge.  |
| stemOutlineColor             | Farbe   | Die Farbe der Kontur um den Schaft unten an einem Symbol im 3D-Modus                                        |

<a id="mapelement3d" />

### <a name="mapelement3d"></a>MapElement3D

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                      |
|------------------------------|---------|----------------------------------------------------------------------------------------------------------------------------------|
| renderAsSurface              | Bool    | Ein Flag, das angibt, dass ein 3D-Modell wie ein Gebäude gerendert werden soll – ohne Tiefenausblendung gegen den Boden               |
