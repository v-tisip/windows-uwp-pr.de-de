---
author: normesta
description: "Die Einträge und Eigenschaften eines Karten-Stylesheets"
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: Karten-Stylesheet-Referenz
ms.author: normesta
ms.date: 03/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Karten, Karten-Stylesheet
ms.openlocfilehash: 9e2605917027d7be96ac86421e83082aa5f368f9
ms.sourcegitcommit: 23cda44f10059bcaef38ae73fd1d7c8b8330c95e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2017
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

<span id="entries" />
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
| >>> cemetery                 | [MapElement](#mapelement) | Flächen mit Friedhöfen |
| >>> continent                | [MapElement](#mapelement) | Flächen ganzer Kontinente |
| >>> education                | [MapElement](#mapelement) |  |
| >>> indigenousPeoplesReserve | [MapElement](#mapelement) |  |
| >>> island                   | [MapElement](#mapelement) | Beschriftungen auf Inselflächen |
| >>> medical                  | [MapElement](#mapelement) | Landflächen, die für medizinische Zwecke genutzt werden (z.B. ein Krankenhauskomplex) |
| >>> military                 | [MapElement](#mapelement) | Flächen von Militärbasen |
| >>> nautical                 | [MapElement](#mapelement) | Landflächen, die für nautische Zwecke genutzt werden |
| >>> neighborhood             | [MapElement](#mapelement) | Beschriftungen auf Flächen, die als Stadtteile definiert sind |
| >>> runway                   | [MapElement](#mapelement) | Landflächen, auf der sich eine Landebahn befindet |
| >>> sand                     | [MapElement](#mapelement) | Sandige Flächen wie Strände |
| >>> shoppingCenter           | [MapElement](#mapelement) | Flächen, die Einkaufspassagen oder Einkaufszentren zugeordnet sind |
| >>> stadium                  | [MapElement](#mapelement) | Fläche eines Stadiums |
| >>> vegetation               | [MapElement](#mapelement) | Wälder, Grünflächen usw. |
| >>>> forest                  | [MapElement](#mapelement) | Flächen mit Waldbestand |
| >>>> golfCourse              | [MapElement](#mapelement) |  |
| >>>> park                    | [MapElement](#mapelement) | Parkflächen |
| >>>> playingField            | [MapElement](#mapelement) | Als Spielfelder genutzte Flächen, wie Baseballfelder oder Tennisplätze |
| >>>> reserve                 | [MapElement](#mapelement) | Flächen von Naturschutzgebieten |
| >> point                     | [PointStyle](#pointstyle) | Alle Punktfeatures, die mit einem Symbol dargestellt werden |
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
| >> transportation            | [TwoToneLineStyle](#twotonelinestyle) | Linien, die Teil des Transportnetzwerks sind (z.B. Straßen, Züge und Fähren) |
| >>> road                     | [TwoToneLineStyle](#twotonelinestyle) | Linien, die alle Straßen darstellen |
| >>>> controlledAccessHighway | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>>> highSpeedRamp          | [TwoToneLineStyle](#twotonelinestyle) | Linien, die Auffahrten darstellen. Diese Auffahrten erscheinen normalerweise zusammen mit Autobahnen mit Zugangsüberwachungssystem. |
| >>>> highway                 | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>> majorRoad               | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>> arterialRoad            | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>> street                  | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>>> ramp                   | [TwoToneLineStyle](#twotonelinestyle) | Linien, die Ein- und Ausfahrten einer Autobahn darstellen |
| >>>>> unpavedStreet          | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>>> tollRoad                | [TwoToneLineStyle](#twotonelinestyle) | Mautstraßen |
| >>> railway                  | [TwoToneLineStyle](#twotonelinestyle) | Eisenbahnlinien |
| >>> trail                    | [TwoToneLineStyle](#twotonelinestyle) | Spazierwege durch Parks oder Wanderwege |
| >>> waterRoute               | [TwoToneLineStyle](#twotonelinestyle) | Fährlinien |
| >> water                     | [MapElement](#mapelement) | Alle Elemente, die wie Wasser aussehen. Dazu zählen Ozeane und Flüsse. |
| >>> river                    | [MapElement](#mapelement) | Flüsse, Ströme oder andere Wasserstraßen.  Beachten Sie, dass es sich herbei um Linien oder Polygone handeln kann, die zu stehenden Gewässern verbinden können. |
| > routeMapElement            | [MapElement](#mapelement) | Alle Streckenführungen fallen unter diesen Eintrag. |
| >> routeLine                 | [TwoToneLineStyle](#twotonelinestyle) | Das Format für alle Streckenführungen |
| >>> walkingRoute             | [TwoToneLineStyle](#twotonelinestyle) |  |
| >>> drivingRoute             | [TwoToneLineStyle](#twotonelinestyle) |  |
| > userMapElement             | [MapElement](#mapelement) | Alle Benutzereinträge fallen unter diesen Eintrag. |
| >> userPoint                 | [PointStyle](#pointstyle) | Das Format für Standard-Benutzerpunkte |
| >> userLine                  | [MapElement](#mapelement) | Das Format für Standard-Benutzerlinien. |

<span id="properties" />
## <a name="properties"></a>Eigenschaften

In diesem Abschnitt werden die Eigenschaften beschrieben, die Sie für die Einträge verwenden können.

<span id="version" />
### <a name="version-properties"></a>Versionseigenschaften

| Eigenschaft                     | Typ    | Beschreibung                                                                                                           |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------|
| version                      | Zeichenfolge  | Version des zu verwendenden Stylesheets. Wird für die Anwendbarkeit verwendet. „1.0” als Standard, „1. *” für zusätzliche geringfügige Featureupdates |

<span id="settings" />
### <a name="settings-properties"></a>Einstellungseigenschaften

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                                                                                                                 |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| atmosphereVisible            | Bool    | Ein Flag, das angibt, ob die Atmosphäre im 3D-Steuerelement angezeigt wird                                                                                                                                                     |
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

<span id="mapelement" />
### <a name="mapelement-properties"></a>MapElement-Eigenschaften

| Eigenschaft                     | Typ    | Beschreibung                                                                                                                 |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------|
| fillColor                    | Farbe   | Die Farbe, die für das Füllen von Polygonen, den Hintergrund von Punktsymbolen und für die Mitte von geteilten Linien verwendet wird |
| fontFamily                   | Zeichenfolge  |                                                                                                                             |
| labelColor                   | Farbe   |                                                                                                                             |
| labelOutlineColor            | Farbe   |                                                                                                                             |
| labelScale                   | Gleitkomma   | Der Wert, um den die Standardgröße von Beschriftungen skaliert wird. Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.            |
| labelVisible                 | Bool    |                                                                                                                             |
| strokeColor                  | Farbe   | Die Farbe, die für die Kontur von Polygonen, die Kontur von Punktsymbolen und die Farbe von Linien verwendet werden soll                   |
| strokeWidthScale             | Gleitkomma   | Der Wert, um den die Strichstärke von Linien skaliert wird Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe.            |
| visible                      | Bool    |                                                                                                                             |

<span id="borderedmap" />
### <a name="borderedmapelement"></a>BorderedMapElement

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                           |
|------------------------------|---------|-----------------------------------------------------------------------|
| borderOutlineColor           | Farbe   | Die sekundäre oder Umrandungslinienfarbe des Rahmens eines gefüllten Polygons |
| borderStrokeColor            | Farbe   | Die primäre Farbe des Rahmens eines gefüllten Polygons             |
| borderVisible                | Bool    |                                                                       |
| borderWidthScale             | Gleitkomma   |                                                                       |

<span id="pointstyle" />
### <a name="pointstyle-properties"></a>PointStyle-Eigenschaften

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                                                                        |
|------------------------------|---------|--------------------------------------------------------------------------------------------------------------------|
| iconColor                    | Farbe   | Die Farbe der Glyphe, die in der Mitte eines Punktsymbols angezeigt wird                                                        |
| scale                        | Gleitkomma   | Der Wert, um den die gesamte Größe des Punkts skaliert wird Verwenden Sie z.B. *1* für die Standardgröße und *2* für die doppelte Größe. |
| stemColor                    | Farbe   | Die Farbe des Schafts unten an einem Symbol im 3D-Modus                                             |
| stemOutlineColor             | Farbe   | Die Farbe der Kontur um den Schaft unten an einem Symbol im 3D-Modus                          |

<span id="twotonelinestyle" />
### <a name="twotonelinestyle-properties"></a>TwoToneLineStyle-Eigenschaften

Diese Eigenschaftengruppe erbt von der [MapElement](#mapelement)-Eigenschaftengruppe.

| Eigenschaft                     | Typ    | Beschreibung                                                                                          |
|------------------------------|---------|------------------------------------------------------------------------------------------------------|
| overwriteColor               | Bool    |  Führt das Überschreiben von **StrokeColor** mit dem Alphawert von **FillColor** aus, anstatt eine Mischung der beiden Farben zu verwenden |
