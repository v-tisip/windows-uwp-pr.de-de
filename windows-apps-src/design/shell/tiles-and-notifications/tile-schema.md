---
author: andrewleader
Description: The following article describes all of the properties and elements within tile content.
title: Kachelinhaltsschema
ms.assetid: 7CBC3BD5-D9C3-4781-8BD0-1F28039E1FA8
label: Tile content schema
template: detail.hbs
ms.author: mijacobs
ms.date: 07/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Kachel, Kachelbenachrichtigung, Kachelinhalt, Schema, Kachelnutzlast
ms.localizationpriority: medium
ms.openlocfilehash: d2baa2e2d7b8d68505159eb480ea3be78750f507
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4317864"
---
# <a name="tile-content-schema"></a>Kachelinhaltsschema

 

Im Folgenden werden alle Eigenschaften und Elemente für die Kachelinhalte beschrieben.

Wenn Sie anstelle der [Notifications-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) lieber unformatiertes XML verwenden, finden Sie im [XML-Schema](../tiles-and-notifications/adaptive-tiles-schema.md) weitere Informationen.

[TileContent](#tilecontent)
* [TileVisual](#tilevisual)
  * [TileBinding](#tilebinding)
    * [TileBindingContentAdaptive](#TileBindingContentAdaptive)
    * [TileBindingContentIconic](#TileBindingContentIconic)
    * [TileBindingContentContact](#TileBindingContentContact)
    * [TileBindingContentPeople](#TileBindingContentPeople)
    * [TileBindingContentPhotos](#TileBindingContentPhotos)


## <a name="tilecontent"></a>TileContent
TileContent ist das Objekt der obersten Ebene, das die Inhalte einer Kachelbenachrichtigung beschreibt, einschließlich der visuellen Elemente.

| Eigenschaft | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| **Visual** | [ToastVisual](#tilevisual) | Wahr | Beschreibt den visuellen Teil der Kachelbenachrichtigung. |


## <a name="tilevisual"></a>TileVisual
Der Visual-Teil der Kacheln enthält die visuellen Spezifikationen für alle Kachelgrößen und weitere Eigenschaften zur Visualisierung.

| Eigenschaft | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| **TileSmall** | [TileBinding](#tilebinding) | Falsch | Geben Sie eine optionale Small-Bindung an, um die Inhalte für die Small-Kachelgröße anzugeben. |
| **TileMedium** | [TileBinding](#tilebinding) | Falsch | Geben Sie eine optionale Medium-Bindung an, um die Inhalte für die Medium-Kachelgröße anzugeben. |
| **TileWide** | [TileBinding](#tilebinding) | Falsch | Geben Sie eine optionale Wide-Bindung an, um die Inhalte für die Wide-Kachelgröße anzugeben. |
| **TileLarge** | [TileBinding](#tilebinding) | Falsch | Geben Sie eine optionale Large-Bindung an, um die Inhalte für die Large-Kachelgröße anzugeben. |
| **Branding** | [TileBranding](#tilebranding) | Falsch | Die Form, die von der Kachel zum Anzeigen des Brands der App verwendet werden sollte. Erbt standardmäßig das Branding der Standardkachel. |
| **DisplayName** | string | Falsch | Eine optionale Zeichenfolge zum Überschreiben des Anzeigenamens der Kachel beim Anzeigen dieser Benachrichtigung. |
| **Argumente** | Zeichenfolge | Falsch | Neues im Anniversary Update: Von der App definierte Daten, die über die Eigenschaft TileActivatedInfo von LaunchActivatedEventArgs an die App zurückgegeben werden, wenn der Benutzer die App über die Live-Kachel startet. Dadurch wissen Sie, welche Kachelbenachrichtigung der Benutzer beim Tippen auf die Live-Kachel gesehen hat. Bei Geräten ohne Anniversary Update wird dies einfach ignoriert. |
| **LockDetailedStatus1** | string | Falsch | Wenn Sie dies angeben, müssen Sie auch eine TileWide-Bindung bereitstellen. Dies ist die erste Zeile des Texts, der auf dem Sperrbildschirm angezeigt wird, wenn der Benutzer die Kachel der App als detaillierte Status-App ausgewählt hat. |
| **LockDetailedStatus2** | string | Falsch | Wenn Sie dies angeben, müssen Sie auch eine TileWide-Bindung bereitstellen. Dies ist die zweite Zeile des Texts, der auf dem Sperrbildschirm angezeigt wird, wenn der Benutzer die Kachel der App als detaillierten Status-App ausgewählt hat. |
| **LockDetailedStatus3** | string | Falsch | Wenn Sie dies angeben, müssen Sie auch eine TileWide-Bindung bereitstellen. Dies ist die dritte Zeile des Texts, der auf dem Sperrbildschirm angezeigt wird, wenn der Benutzer die Kachel der App als detaillierten Status-App ausgewählt hat. |
| **BaseUri** | Uri | Falsch | Eine grundlegende Standard-URL, die mit relativen URLs in Bildquellattributen kombiniert wird. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Popupbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |
| **Sprache**| Zeichenfolge | Falsch | Das Zielgebietsschema der visuellen Nutzlast bei Verwendung lokalisierter Ressourcen, angegeben als BCP-47-Sprachtags wie z.B. „en-US“ oder „fr-FR“. Dieses Gebietsschema wird von jedem in der Bindung oder dem Text angegebenen Gebietsschema überschrieben. Falls nicht angegeben, wird stattdessen das Gebietsschema des Systems verwendet. |


## <a name="tilebinding"></a>TileBinding
Das Binding-Objekt enthält die visuellen Inhalte für eine bestimmte Kachelgröße.

| Eigenschaft | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| **Inhalt** | [ITileBindingContent](#itilebindingcontent) | Falsch | Die visuellen Inhalte, die auf der Kachel angezeigt werden. [TileBindingContentAdaptive](#tilebindingcontentadaptive), [TileBindingContentIconic](#TileBindingContentIconic), [TileBindingContentContact](#TileBindingContentContact), [TileBindingContentPeople](#TileBindingContentPeople) oder [TileBindingContentPhotos](#TileBindingContentPhotos). |
| **Branding** | [TileBranding](#tilebranding) | Falsch | Die Form, die von der Kachel zum Anzeigen des Brands der App verwendet werden sollte. Erbt standardmäßig das Branding der Standardkachel. |
| **DisplayName** | string | Falsch | Eine optionale Zeichenfolge zum Überschreiben des Anzeigenamens der Kachel für diese Kachelgröße. |
| **Argumente** | Zeichenfolge | Falsch | Neues im Anniversary Update: Von der App definierte Daten, die über die Eigenschaft TileActivatedInfo von LaunchActivatedEventArgs an die App zurückgegeben werden, wenn der Benutzer die App über die Live-Kachel startet. Dadurch wissen Sie, welche Kachelbenachrichtigung der Benutzer beim Tippen auf die Live-Kachel gesehen hat. Bei Geräten ohne Anniversary Update wird dies einfach ignoriert. |
| **BaseUri** | Uri | Falsch | Eine grundlegende Standard-URL, die mit relativen URLs in Bildquellattributen kombiniert wird. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Popupbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |
| **Sprache**| Zeichenfolge | Falsch | Das Zielgebietsschema der visuellen Nutzlast bei Verwendung lokalisierter Ressourcen, angegeben als BCP-47-Sprachtags wie z.B. „en-US“ oder „fr-FR“. Dieses Gebietsschema wird von jedem in der Bindung oder dem Text angegebenen Gebietsschema überschrieben. Falls nicht angegeben, wird stattdessen das Gebietsschema des Systems verwendet. |


## <a name="itilebindingcontent"></a>ITileBindingContent
Markierungsschnittstelle für die Kachel-Bindungsinhalte. Dient zum Festlegen der visuellen Objekte der Kachel in adaptiven Vorlagen oder einer der speziellen Vorlagen.

| Implementierungen |
| --- |
| [TileBindingContentAdaptive](#TileBindingContentAdaptive) |
| [TileBindingContentIconic](#TileBindingContentIconic) |
| [TileBindingContentContact](#TileBindingContentContact) |
| [TileBindingContentPeople](#TileBindingContentPeople) |
| [TileBindingContentPhotos](#TileBindingContentPhotos) |


## <a name="tilebindingcontentadaptive"></a>TileBindingContentAdaptive
Für alle Größe unterstützt. Dies ist die empfohlene Methode zum Festlegen der Kachelinhalte. Vorlagen für adaptive Kacheln sind in Windows10 neu. Sie können eine Vielzahl von benutzerdefinierten Kacheln über Vorlagen für adaptive Kacheln erstellen.

| Eigenschaft | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| **Untergeordnete Elemente** | IList<[ITileBindingContentAdaptiveChild](#ITileBindingContentAdaptiveChild)> | Falsch | Die visuellen Inline-Elemente. Es können [AdaptiveText](#adaptivetext)-, [AdaptiveImage](#adaptiveimage)- und [AdaptiveGroup](#adaptivegroup)-Objekte hinzugefügt werden. Die untergeordneten Elemente werden als vertikales StackPanel angezeigt. |
| **BackgroundImage** | [TileBackgroundImage](#tilebackgroundimage) | Falsch | Ein optionales Hintergrundbild, das randlos hinter den Kachelinhalten angezeigt wird. |
| **PeekImage** | [TilePeekImage](#tilepeekimage) | Falsch | Ein optionales Vorschaubild, das von oben in die Kachel hineingleitet. |
| **TextStacking** | [TileTextStacking](#tiletextstacking) | Falsch | Steuert den gestapelten Text (vertikale Ausrichtung) der untergeordneten Inhalte als Ganzes. |


## <a name="adaptivetext"></a>AdaptiveText
Ein adaptives Textelement.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Text** | Zeichenfolge | Falsch | Der Text, der angezeigt werden soll. |
| **HintStyle** | [AdaptiveTextStyle](#adaptivetextstyle) | Falsch | Der Stil steuert den Schriftgrad, die Schriftbreite und die Deckkraft des Texts. |
| **HintWrap** | bool? | Falsch | Legen Sie diese Option auf „Wahr“ fest, um Textumbruch zu aktivieren. Der Standardwert ist „Falsch“. |
| **HintMaxLines** | int? | Falsch | Die maximale Anzahl der Zeilen, die das Textelement anzeigen darf. |
| **HintMinLines** | int? | Falsch | Die Mindestanzahl der Zeilen, die das Textelement anzeigen muss. |
| **HintAlign** | [AdaptiveTextAlign](#adaptivetextalign) | Falsch | Die horizontale Ausrichtung des Texts. |
| **Language** | Zeichenfolge | Falsch | Das Zielgebietsschema der XML-Nutzlast, angegeben als BCP-47-Sprachtags wie z.B. „ en-US“ oder „fr-FR“. Das hier angegebene Gebietsschema überschreibt jedes andere– etwa in der Bindung oder im visuellen Element– angegebene Gebietsschema. Wenn dieser Wert eine Literalzeichenfolge ist, wird für dieses Attribut standardmäßig die Sprache der Benutzeroberfläche des Benutzers verwendet. Wenn dieser Wert ein Zeichenfolgenverweis ist, wird für dieses Attribut standardmäßig das Gebietsschema verwendet, das beim Auflösen der Zeichenfolge von Windows-Runtime ausgewählt wurde. |


### <a name="adaptivetextstyle"></a>AdaptiveTextStyle
Textstil steuert Schriftgrad, Schriftbreite und Deckkraft. Dezente Deckkraft ist 60% undurchsichtig.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Stil wird durch den Renderer bestimmt. |
| **Untertitel für Hörgeschädigte** | Kleiner als Schriftgrad des Absatzes. |
| **CaptionSubtle** | Identisch mit „Untertitel für Hörgeschädigte“, aber mit dezenter Deckkraft. |
| **Textkörper** | Schriftgrad des Absatzes. |
| **bodySubtle** | Identisch mit „Textkörper“, aber mit dezenter Deckkraft. |
| **Basis** | Schriftgrad des Absatzes, fette Schriftbreite. Im Wesentlichen die fettgedruckte Version des Textkörpers. |
| **BaseSubtle** | Identisch mit „Basis“, aber mit dezenter Deckkraft. |
| **Untertitel** | H4-Schriftgrad. |
| **SubtitleSubtle** | Identisch mit „Untertitel“, aber mit dezenter Deckkraft. |
| **Titel** | H3-Schriftgrad. |
| **TitleSubtle** | Identisch mit „Titel“, aber mit dezenter Deckkraft. |
| **TitleNumeral** | Identisch mit „Titel“, aber ohne Abstand nach oben/unten. |
| **Unterüberschrift** | H2-Schriftgrad. |
| **SubheaderSubtle** | Identisch mit „Unterüberschrift“, aber mit dezenter Deckkraft. |
| **SubheaderNumeral** | Identisch mit „Unterüberschrift“, aber ohne Abstand nach oben/unten. |
| **Kopfzeile** | H1-Schriftgrad. |
| **HeaderSubtle** | Identisch mit „Kopfzeile“, aber mit dezenter Deckkraft. |
| **HeaderNumeral** | Identisch mit „Kopfzeile“, aber ohne Abstand nach oben/unten. |


### <a name="adaptivetextalign"></a>AdaptiveTextAlign
Steuert die horizontale Ausrichtung des Texts.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Ausrichtung wird automatisch vom Renderer bestimmt. |
| **Auto** | Ausrichtung durch die aktuelle Sprache und Kultur bestimmt. |
| **Links** | Den Text horizontal linksbündig ausrichten. |
| **Mitte** | Den Text horizontal zentrieren. |
| **Rechts** | Den Text horizontal rechtsbündig ausrichten. |


## <a name="adaptiveimage"></a>AdaptiveImage
Ein Inlinebild.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Quelle** | Zeichenfolge | Wahr | Die URL zum Bild. ms-appx, ms-appdata und http werden unterstützt. Im Fall Creators Update kann die Größe der Webbilder 3MB für normale Verbindungen und 1MB für getaktete Verbindungen betragen. Auf Geräten, die noch nicht das Fall Creators Update haben, dürfen Webbilder nicht größer als 200KB sein. |
| **HintCrop** | [AdaptiveImageCrop](#adaptiveimagecrop) | Falsch | Steuert den gewünschten Zuschnitt des Bilds. |
| **HintRemoveMargin** | bool? | Falsch | Bilder in Gruppen/Untergruppen verfügen standardmäßig über einen Rand von 8Pixel. Sie können diesen Rand entfernen, indem Sie diese Eigenschaft auf „Wahr“ festlegen. |
| **HintAlign** | [AdaptiveImageAlign](#adaptiveimagealign) | Falsch | Die horizontale Ausrichtung des Bilds. |
| **AlternateText** | Zeichenfolge | Falsch | Alternativtext, der das Bild beschreibt; wird für Bedienungshilfen verwendet. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Kachelbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |


### <a name="adaptiveimagecrop"></a>AdaptiveImageCrop
Gibt den gewünschten Zuschnitt des Bilds an.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Zuschneideverhalten wird vom Renderer bestimmt. |
| **Keine** | Bild wird nicht zugeschnitten. |
| **Kreis** | Bild wird kreisförmig zugeschnitten. |


### <a name="adaptiveimagealign"></a>AdaptiveImageAlign
Gibt die horizontale Ausrichtung für ein Bild an.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Ausrichtungsverhalten vom Renderer bestimmt. |
| **Strecken** | Bild wird gestreckt, um die verfügbare Breite (und möglicherweise auch die verfügbare Höhe, je nachdem, wo das Bild platziert wird) auszufüllen. |
| **Links** | Das Bild links ausrichten, wobei das Bild mit der systemeigenen Auflösung angezeigt wird. |
| **Mitte** | Das Bild zentrieren, wobei das Bild mit der systemeigenen Auflösung angezeigt wird. |
| **Rechts** | Das Bild rechts ausrichten, wobei das Bild mit der systemeigenen Auflösung angezeigt wird. |


## <a name="adaptivegroup"></a>AdaptiveGroup
Gruppen geben semantisch an, dass der Inhalt in der Gruppe entweder als Ganzes oder nicht angezeigt werden soll, wenn nicht genügend Platz vorhanden ist. Gruppen können auch mehrere Spalten erstellen.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Untergeordnete Elemente** | IList<[AdaptiveSubgroup](#adaptivesubgroup)> | Falsch | Untergruppen werden als vertikale Spalten angezeigt. Sie müssen Untergruppen verwenden, um Inhalt innerhalb einer AdaptiveGroup bereitzustellen. |


## <a name="adaptivesubgroup"></a>AdaptiveSubgroup
Untergruppen sind vertikale Spalten, die Text und Bilder enthalten können.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Untergeordnete Elemente** | IList<[IAdaptiveSubgroupChild](#iadaptivesubgroupchild)> | Falsch | [AdaptiveText](#adaptivetext) und [AdaptiveImage](#adaptiveimage) gültige untergeordnete Elemente von Untergruppen. |
| **HintWeight** | int? | Falsch | Steuern Sie die Breite dieser Untergruppenspalte, indem Sie die Breite im Verhältnis zu den anderen Untergruppen angeben. |
| **HintTextStacking** | [AdaptiveSubgroupTextStacking](#adaptivesubgrouptextstacking) | Falsch | Steuern Sie die vertikale Ausrichtung des Inhalts dieser Untergruppe. |


### <a name="iadaptivesubgroupchild"></a>IAdaptiveSubgroupChild
Markierungsschnittstelle für untergeordnete Untergruppenelemente.

| Implementierungen |
| --- |
| [AdaptiveText](#adaptivetext) |
| [AdaptiveImage](#adaptiveimage) |


### <a name="adaptivesubgrouptextstacking"></a>AdaptiveSubgroupTextStacking
TextStacking gibt die vertikale Ausrichtung des Inhalts an.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Renderer wählt automatisch die standardmäßige vertikale Ausrichtung aus. |
| **Oben** | Vertikal oben ausrichten. |
| **Mitte** | Vertikal zentrieren. |
| **Unten** | Vertikal unten ausrichten. |


## <a name="tilebackgroundimage"></a>TileBackgroundImage
Ein Hintergrundbild, das randlos auf der Kachel angezeigt wird.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Quelle** | Zeichenfolge | Wahr | Die URL zum Bild. ms-appx, ms-appdata und http(s) werden unterstützt. HTTP-Bilder müssen kleiner als 200KB sein. |
| **HintOverlay** | int? | Falsch | Ein schwarzes Overlay auf dem Hintergrundbild. Dieser Wert steuert die Deckkraft des schwarzen Overlays, wobei 0 kein Overlay und 100 vollständig schwarz ist. Die Standardeinstellung ist 20. |
| **HintCrop** | [TileBackgroundImageCrop](#tilebackgroundimagecrop) | Falsch | Neu in 1511: Geben Sie an, wie das Bild zugeschnitten werden soll. In Versionen vor 1511 wird dies ignoriert und das Hintergrundbild ohne Zuschneiden angezeigt. |
| **AlternateText** | Zeichenfolge | Falsch | Alternativtext, der das Bild beschreibt; wird für Bedienungshilfen verwendet. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Kachelbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |


### <a name="tilebackgroundimagecrop"></a>TileBackgroundImageCrop
Steuert das Zuschneiden des Hintergrundbilds.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Beim Zuschneiden wird das Standardverhalten des Renderers verwendet. |
| **Keine** | Bild wird nicht zugeschnitten, wird quadratisch angezeigt. |
| **Kreis** | Bild wird kreisförmig zugeschnitten. |


## <a name="tilepeekimage"></a>TilePeekImage
Ein Vorschaubild, das von oben in die Kachel hineingleitet.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Quelle** | Zeichenfolge | Wahr | Die URL zum Bild. ms-appx, ms-appdata und http(s) werden unterstützt. HTTP-Bilder müssen kleiner als 200KB sein. |
| **HintOverlay** | int? | Falsch | Neu ab 1511: Ein schwarzes Overlay auf dem Vorschaubild. Dieser Wert steuert die Deckkraft des schwarzen Overlays, wobei 0 kein Overlay und 100 vollständig schwarz ist. Die Standardeinstellung ist 20. In früheren Versionen wird dieser Wert ignoriert und das Peek-Bild wird mit 0 Overlay angezeigt. |
| **HintCrop** | [TilePeekImageCrop](#tilepeekimagecrop) | Falsch | Neu in 1511: Geben Sie an, wie das Bild zugeschnitten werden soll. In Versionen vor 1511 wird dies ignoriert und das Vorschaubild ohne Zuschneiden angezeigt. |
| **AlternateText** | Zeichenfolge | Falsch | Alternativtext, der das Bild beschreibt; wird für Bedienungshilfen verwendet. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Kachelbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |


### <a name="tilepeekimagecrop"></a>TilePeekImageCrop
Steuert das Zuschneiden des Vorschaubilds.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Beim Zuschneiden wird das Standardverhalten des Renderers verwendet. |
| **Keine** | Bild wird nicht zugeschnitten, wird quadratisch angezeigt. |
| **Kreis** | Bild wird kreisförmig zugeschnitten. |


### <a name="tiletextstacking"></a>TileTextStacking
Das Text-Stacking gibt die vertikale Ausrichtung des Inhalts an.

| Wert | Bedeutung |
|---|---|
| **Standardwert** | Standardwert. Renderer wählt automatisch die standardmäßige vertikale Ausrichtung aus. |
| **Oben** | Vertikal oben ausrichten. |
| **Mitte** | Vertikal zentrieren. |
| **Unten** | Vertikal unten ausrichten. |


## <a name="tilebindingcontenticonic"></a>TileBindingContentIconic
Für Small und Medium unterstützt. Ermöglicht eine Symbol-Kachelvorlage, bei der Sie ein Symbol und Badge nebeneinander auf der Kachel anzeigen lassen können, im klassischen Stil von Windows Phone. Die Zahl neben dem Symbol wird durch eine separate Badge-Benachrichtigung erreicht.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Icon** | [TileBasicImage](#tilebasicimage) | Wahr | Um sowohl Desktop- als auch Mobile-Small und -Medium-Kacheln zu unterstützen, stellen Sie mindestens ein Bild mit quadratischem Seitenverhältnis und einer Auflösung von 200x200 im PNG-Format mit Transparenz und keiner anderen Farbe als Weiß zur bereit. Weitere Informationen finden Sie unter [Spezielle Kachelvorlagen](../tiles-and-notifications/special-tile-templates-catalog.md). |


## <a name="tilebindingcontentcontact"></a>TileBindingContentContact
Nur Mobile. Für Small, Medium und Wide unterstützt.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Image** | [TileBasicImage](#tilebasicimage) | Wahr | Das anzuzeigende Bild. |
| **Text** | [TileBasicText](#tilebasictext) | Falsch | Eine Textzeile, die angezeigt wird. Nicht auf kleiner Kachel angezeigt. |


## <a name="tilebindingcontentpeople"></a>TileBindingContentPeople
In 1511 neu: Unterstützt von Medium, Wide und Large (Desktop und Mobile). Zuvor war dies nur für Mobile und nur Medium und Wide gültig.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Images** | IList<[TileBasicImage](#tilebasicimage)> | Wahr | Bilder, die sich im Kreis drehen. |


## <a name="tilebindingcontentphotos"></a>TileBindingContentPhotos
Animiert durch eine Diashow mit Fotos. Für alle Größe unterstützt.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Images** | IList<[TileBasicImage](#tilebasicimage)> | Wahr | Es können bis zu 12 Bilder zur Verfügung gestellt werden (Mobile zeigt nur bis zu 9 Bilder an), die für die Diashow verwendet werden. Das Hinzufügen von mehr als 12 löst eine Ausnahme aus. |


### <a name="tilebasicimage"></a>TileBasicImage
Ein Bild, das für verschiedenen spezielle Vorlagen verwendet wird.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Quelle** | Zeichenfolge | Wahr | Die URL zum Bild. ms-appx, ms-appdata und http(s) werden unterstützt. HTTP-Bilder müssen kleiner als 200KB sein. |
| **AlternateText** | Zeichenfolge | Falsch | Alternativtext, der das Bild beschreibt; wird für Bedienungshilfen verwendet. |
| **AddImageQuery** | bool? | Falsch | Legen Sie den Wert auf „Wahr“ fest, um an die in der Kachelbenachrichtigung angegebene Bild-URL eine Abfragezeichenfolge anzufügen. Verwenden Sie dieses Attribut, wenn Ihr Server Bilder hostet und Abfragezeichenfolgen verarbeiten kann, indem er entweder basierend auf den Abfragezeichenfolgen eine Bildvariante abruft oder die Abfragezeichenfolge ignoriert und das Bild wie angegeben ohne die Abfragezeichenfolge zurückgibt. Diese Abfragezeichenfolge gibt Skalierung, Kontrasteinstellung und Sprache an. So wird beispielsweise ein in der Benachrichtigung angegebener Wert „www.website.com/images/hello.png“ zu „www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us“ |


### <a name="tilebasictext"></a>TileBasicText
Ein einfaches Text-Element, das für verschiedene spezielle Vorlagen verwendet wird.

| Eigenschaft | Typ | Erforderlich |Beschreibung |
|---|---|---|---|
| **Text** | Zeichenfolge | Falsch | Der Text, der angezeigt werden soll. |
| **Sprache** | Zeichenfolge | Falsch | Das Zielgebietsschema der XML-Nutzlast, angegeben als BCP-47-Sprachtags wie z.B. „ en-US“ oder „fr-FR“. Das hier angegebene Gebietsschema überschreibt jedes andere– etwa in der Bindung oder im visuellen Element– angegebene Gebietsschema. Wenn dieser Wert eine Literalzeichenfolge ist, wird für dieses Attribut standardmäßig die Sprache der Benutzeroberfläche des Benutzers verwendet. Wenn dieser Wert ein Zeichenfolgenverweis ist, wird für dieses Attribut standardmäßig das Gebietsschema verwendet, das beim Auflösen der Zeichenfolge von Windows-Runtime ausgewählt wurde. |


## <a name="related-topics"></a>Verwandte Themen

* [Schnellstart: Senden einer lokalen Kachelbenachrichtigung](../tiles-and-notifications/sending-a-local-tile-notification.md)
* [Benachrichtigungsbibliothek auf GitHub](https://github.com/Microsoft/UWPCommunityToolkit/tree/dev/Notifications)