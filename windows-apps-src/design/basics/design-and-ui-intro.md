---
author: serenaz
Description: An overview of the universal design features that are included in every UWP app to help you build apps that scale beautifully across a range of devices.
title: Einführung in das UWP-App-Design (Universelle Windows-Plattform) (Windows-Apps)
ms.assetid: 50A5605E-3A91-41DB-800A-9180717C1E86
ms.author: sezhen
ms.date: 12/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: d0527866777c7b5dbbc10697bb313d664f4555fa
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817278"
---
#  <a name="introduction-to-uwp-app-design"></a>Einführung in das UWP-App-Design

Der universelle Windows-Plattform (UWP)-Designleitfaden ist eine Ressource, um ansprechende, optimierte Apps zu entwerfen und erstellen.

Es ist keine Liste von Vorschriften, sondern ein lebendiges Dokument, das entwickelt wurde, um sich entsprechend unseres [Fluent Design-Systems](../fluent-design-system/index.md) sowie der Bedürfnisse unserer App-Entwicklungs-Community zu entwickeln.

Diese Einführung bietet einen Überblick über die universellen Designfunktionen, die in jeder UWP-Apps enthalten sind. Es hilft Ihnen, Benutzeroberflächen (UIs) zu erstellen, die sich über eine Vielzahl von Geräten wunderbar skalieren lassen.

## <a name="video-summary"></a>Video-Zusammenfassung

> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/Designing-Universal-Windows-Platform-apps/player]

## <a name="effective-pixels-and-scaling"></a>Effektive Pixel und Skalierung

UWP-Apps passen automatisch die Größe von Steuerelementen, Schriftarten und anderer UI-Elemente an, damit sie auf [allen Geräten mit UWP-App-Unterstützung](../devices/index.md) lesbar sind und die Interaktion erleichtern.

Wenn Ihre App auf einem Gerät ausgeführt wird, verwendet das System einen Algorithmus, um die Art der Anzeige der UI-Elemente auf dem Bildschirm zu normalisieren. Dieser Skalierungsalgorithmus berücksichtigt den Abstand zum Bildschirm und die Bildschirmdichte (Pixel pro Zoll), um die wahrgenommene Größe (anstelle der physischen Größe) zu optimieren. Mit dem Skalierungsalgorithmus wird sichergestellt, dass der Schriftgrad 24 Pixel auf einem 3 Meter entfernten Surface Hub genauso für den Benutzer lesbar ist wie der Schriftgrad 24 Pixel auf einem 5-Zoll-Smartphone, das nur einige Zentimeter entfernt ist.

![Sichtabstände für verschiedene Geräte](images/1910808-hig-uap-toolkit-03.png)

Aufgrund der Funktionsweise des Skalierungssystems beim Entwerfen Ihrer UWP-App, verwenden Sie effektive Pixeln, und nicht die tatsächlichen physischen Pixel. Effektive Pixel (epx) sind eine virtuelle Maßeinheit und werden verwendet, um Layoutabmessungen und -abstände unabhängig von der Pixeldichte auszudrücken. (In unseren Richtlinien werden epx, ep und px austauschbar verwendet.)

Sie können die Pixeldichte und die tatsächliche Bildschirmauflösung beim Entwerfen ignorieren. Entwerfen Sie stattdessen für die effektive Auflösung (die Auflösung in effektiven Pixeln) für eine Größenklasse (Details finden Sie im Artikel [Bildschirmgrößen und Haltepunkte](../layout/screen-sizes-and-breakpoints-for-responsive-design.md)).

> [!TIP]
> Legen Sie beim Erstellen von Bildschirmmodellen in Bildbearbeitungsprogrammen die DPI auf 72 und die Bildgröße auf effektive Auflösung für die Zielgrößenklasse fest. Eine Liste der Größenklassen und effektiven Auflösungen finden Sie unter dem [Artikel Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).


## <a name="layout"></a>Layout

### <a name="margins-spacing-and-positioning"></a>Ränder, Abstände und Positionierung 
![Raster](images/4epx.png)

Wenn das System die Benutzeroberfläche skaliert, erfolgt dies durch die Multiplikation mit vier.

Daher sollten die Größen, Ränder und Positionen der **UI-Elemente immer ein Vielfaches von 4 epx betragen**. Das Ergebnis ist ein optimales Rendering durch Ausrichtung auf ganze Pixel. Es sorgt auch dafür, dass UI-Elemente scharfe und deutliche Kanten haben. 

Beachten Sie, dass Text diese Anforderung nicht hat. Der Text kann eine beliebige Größe und Position haben. Hinweise zum Ausrichten von Text an anderen UI-Elementen finden Sie im [UWP-Typografieleitfaden](../style/typography.md).

![Skalierung auf dem Raster](images/epx-4pixelgood.png)

### <a name="layout-patterns"></a>Layoutmuster

![Ein gemeinsames Layoutmuster](images/page-components.png)

Die Benutzeroberfläche besteht aus drei Arten von Elementen: 
1. Mithilfe von **Navigationselementen** können Benutzer die Inhalte auswählen, die sie anzeigen möchten. Weitere Infos unter [Navigationsgrundlagen](navigation-basics.md).
2. **Befehlselemente** initiieren Aktionen wie etwa das Bearbeiten, Speichern oder Freigeben von Inhalten. Weitere Infos unter [Befehlsgrundlagen](commanding-basics.md).
3. Die **Inhaltselemente** zeigen die Inhalte der App an. Weitere Infos unter [Inhaltsgrundlagen](content-basics.md).

### <a name="adaptive-behavior"></a>Adaptives Verhalten
![Adaptives Verhalten für Smartphones und Desktops](../controls-and-patterns/images/patterns_masterdetail.png)

Zwar ist die Benutzeroberfläche Ihrer App auf allen Windows-basierten Geräten lesbar und verwendbar, doch Sie sollten sie für bestimmte Geräte und Bildschirmgrößen anpassen. Weitere Informationen finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) und [Reaktionsfähige Designtechniken](../layout/responsive-design.md).

## <a name="type"></a>Schriftart

Standardmäßig verwenden UWP-Anwendungen die **Segoe UI**-Schriftart. Die UWP-Typhierarchie umfassen sieben Typografie-Klassen, die den effizientesten Ansatz für alle Displaygrößen anstreben. 

![Typhierarchie](images/type-ramp.png)

Einzelheiten zur Typhierarchie finden Sie im [UWP-Typografieleitfaden](../style/typography.md). Um zu erfahren, wie Sie die verschiedenen Ebenen der UWP-Typhierarchie in Ihrer App verwenden können, lesen Sie die den Abschnitt [Designressourcen](../controls-and-patterns/xaml-theme-resources.md#the-xaml-type-ramp).

## <a name="color"></a>Farben

Farben bietet eine intuitive Möglichkeit, Informationen an die Benutzer zu kommunizieren. Sie können verwendet werden, um Interaktivität zu signalisieren, Feedback zu Benutzeraktionen zu geben, Zustandsinformationen zu übermitteln und Ihrer Benutzeroberfläche ein Gefühl der visuellen Kontinuität zu geben. 

Windows 10 bietet eine gemeinsame, universelle Farbpalette von 48 Farben, die auf die Shell und UWP-Apps angewendet wird. 

![Universelle Windows-Farbpalette](images/colors.png)

Das System wendet automatisch Farben auf Ihre UWP-Apps mit der Systemakzentfarbe an. Wenn Benutzer eine Akzentfarbe aus der Farbpalette in ihren Einstellungen auswählen, wird die Farbe als Teil ihres Systemdesigns angezeigt. Abhängig von den Benutzereinstellungen kann die Systemakzentfarbe auch auf das Startmenü, Kacheln, Taskleiste und Titelleisten angewendet werden. 

![Akzentfarbe in den Einstellungen wählen](images/selectcolor.png)

Innerhalb Ihrer UWP-App spiegeln Hyperlinks und ausgewählte Zustände innerhalb gemeinsamer Steuerelemente die Akzentfarbe des Systems wider.

![Systemakzentfarbe auf den Steuerelementen](images/accentcolor.png)

UWP-Apps können die Systemakzentfarbe bei der Anzeige in Steuerelementen überschreiben, indem sie eine [einfache Formatierung](../controls-and-patterns/xaml-styles.md#lightweight-styling) verwenden oder [benutzerdefinierte Steuerelemente](../controls-and-patterns/control-templates.md) erstellen.

Weitere Informationen zur Verwendung von Farben in Ihrer UWP-App finden Sie im Artikel [Farbe](../style/color.md).

### <a name="themes"></a>Designs

Der Benutzer kann zwischen einem hellen, dunklen oder kontrastreichen Design wählen. Sie können das Aussehen Ihrer App je nach Design des Benutzers ändern oder dieses ignorieren.

Das helle Design eignet sich am besten für Produktivitätsaufgaben und das Lesen.

Das dunkle Design ermöglicht mehr sichtbare Kontraste in medienzentrierten Anwendungen und Szenarien, die eine Fülle von Videos oder Bildern enthalten. In diesen Szenarien ist die Hauptaufgabe eher das Beobachten von Filmen als das Lesen bei schlechten Lichtverhältnissen.

![Rechner im hellen und dunklen Design](images/light-dark.png)

Designs mit hohem Kontrast verwenden eine kleine Palette von Farbkombinationen mit hohem Farbkontrast, durch die die Benutzeroberfläche leichter zu erkennen ist.
![Rechner im hellen Design und im Design „Hoher Kontrast (Schwarz)”](../accessibility/images/high-contrast-calculators.png)


Weitere Informationen zur Verwendung von Design und der UWP-Farbhistorie in Ihrer App finden Sie unter [Design-Ressourcen](../controls-and-patterns/xaml-theme-resources.md).

## <a name="icons"></a>Symbole
![Symbole](images/icons.png)

Symbole sind eine Art Bildsprache, die sich in unseren Alltag eingeprägt hat. Sie lassen uns Konzepte und Handlungen visuell überzeugend ausdrücken, sparen Platz auf dem Bildschirm und dienen der Navigation in unserem digitalen Leben. 

Alle UWP-App haben Zugriff auf die Symbole der Schriftart [Segoe MDL2](../style/segoe-ui-symbol-font.md). Diese Symbole beruhen auf etablierten Formen, die jedem bekannt und leicht zu identifizieren sind, aber sie wurden auch modernisiert, damit sie sich anfühlen, als wären sie von einer Hand gezeichnet worden.

Wenn Sie Ihre eigenen Symbole erstellen möchten, finden Sie weitere Infos unter [Symbole für UWP-Apps](../style/icons.md).

## <a name="tiles"></a>Kacheln
![Kacheln im Startmenü](images/tiles.png)

Kacheln werden im Startmenü angezeigt und geben einen Einblick in das Geschehen in Ihrer App. Ihr Mehrwert basiert auf dem zugrunde liegenden Inhalt und ihrem Design. 

UWP-App haben vier Kachelgrößen (klein, mittel, breit und groß), die mit dem Symbol und der Identität der App angepasst werden können. Hinweise zur Gestaltung von Kacheln für Ihre UWP-Apps finden Sie unter [Richtlinien für Kachel- und Symbolelemente](../shell/tiles-and-notifications/app-assets.md).

## <a name="controls"></a>Steuerelemente
![Schaltflächen-Steuerelement](images/1910808-hig-uap-toolkit-01.png)

UWP bietet einen Satz von universellen Steuerelementen, die garantiert gut auf allen Windows-Geräten funktionieren. Diese Steuerelemente reichen von einfachen Steuerelementen wie Schaltflächen und Textelementen bis hin zu ausgeklügelten Steuerelementen, die Listen aus einem Datensatz und einer Vorlage erzeugen können.

UWP-Steuerelemente wählen automatisch das Systemdesign und die Akzentfarbe aus, arbeiten mit allen Eingabetypen und skalieren auf allen Geräten. Und sie sind außerdem sehr anpassbar. Sie können die Vordergrundfarbe eines Steuerelements ändern oder sein Aussehen komplett anpassen. 

Eine vollständige Liste der UWP-Steuerelemente und der -Muster, die Sie aus ihnen erstellen können, finden Sie im Abschnitt [Steuerelemente und Muster](../controls-and-patterns/index.md).

## <a name="input"></a>Eingabe
![Eingabe](../input/images/input-interactions/icons-inputdevices03.png)

UWP-Apps basieren auf intelligenten Interaktionen. Dies bedeutet, dass Sie um eine Klick-Interaktion herum entwerfen können, ohne zu wissen oder festzulegen, ob der Klick von einem echten Mausklick oder einem Fingertipp stammt. Sie können Ihre Apps aber auch für bestimmte [Eingabemodi und Geräte gestalten](../input/input-primer.md).

## <a name="accessibility"></a>Bedienungshilfen
![Benutzer des inklusiven Designs](images/inclusive.png)

Letztendlich geht es bei der Barrierefreiheit darum, das Erlebnis Ihrer App allen Nutzern zugänglich zu machen. Es ist für alle relevant, nicht nur für Menschen mit Einschränkungen. Jeder kann von einer wirklich umfassenden Benutzererfahrung profitieren. In [Benutzerfreundlichkeit von UWP-Apps](../usability/index.md) erfahren Sie, wie Sie Ihre App für jedermann benutzerfreundlich gestalten können. Vielleicht möchten Sie auch [Barrierefreiheitsfunktionen](../accessibility/accessibility-overview.md) für Benutzer mit eingeschränkter Seh-, Hör- und Bewegungsfreiheit in Betracht ziehen. 

Wenn die Barrierefreiheit von Anfang an in Ihr Design integriert ist, sollte die [Umsetzung der Barrierefeiheit](../accessibility/accessibility-in-the-store.md) Ihrer App nur sehr wenig Zeit und Mühe in Anspruch nehmen.

## <a name="tools-and-design-toolkits"></a>Tools und Design-Toolkits
Da Sie nun über die grundlegenden Designfunktionen Bescheid wissen, sollten Sie die ersten Schritte beim Design Ihrer UWP-App unternehmen.

Wir bieten eine Vielzahl von Werkzeugen zur Unterstützung Ihres Designprozesses:

* Weitere Informationen für XD, Illustrator, Photoshop, Framer und Sketch-Toolkits sowie zusätzliche Entwicklungstools und Downloads für Schriftarten finden Sie auf der [Design-Toolkits-Seite](../downloads/index.md). 

* Um Ihren Computer so einzurichten, dass er das Codieren von UWP-Apps ermöglicht, lesen Sie den Artikel [Erste Schritte &gt;Vorbereiten](../../get-started/get-set-up.md). 

* Für Anregungen zur Implementierung von Benutzeroberflächen für UWP werfen Sie einen Blick auf unsere umfassenden [UWP-Beispiel-Apps](https://developer.microsoft.com/windows/samples).

## <a name="next-fluent-design-system"></a>Nächstes Thema: Fluent Design-System
Wenn Sie weitere Informationen zu der Prinzipien hinter Fluent Design (das Design-System von Microsoft) und weitere Features für Ihre UWP-App kennenlernen möchten, fahren Sie mit dem Artikel [Fluent Design-System](../fluent-design-system/index.md) fort.