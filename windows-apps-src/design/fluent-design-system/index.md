---
description: Lernen Sie das Fluent Design und dessen Integration in Ihre Apps kennen.
title: Fluent Design System für UWP-Apps
author: mijacobs
keywords: Layout von UWP-Apps, universelle Windows-Plattform, App-Design, Schnittstelle, fluent design system
ms.author: mijacobs
ms.date: 3/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: high
ms.openlocfilehash: 5b57dc2ddae4c6e260df663097db5649866b96aa
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "1638788"
---
# <a name="the-fluent-design-system-for-uwp-apps"></a>Das Fluent Design System für UWP-Apps

## <a name="introduction"></a>Einführung

<img src="images/fluentdesign-app-header.jpg" alt=" " />

Die Benutzeroberfläche entwickelt sich weiter. Sie wird erweitert, um neue Dimensionen und Schnittstellen (2D, 3D, Tastatur, Maus, Blick, Stift, Touch etc.) abzudecken.  

Das Fluent Design System stellt eine Reihe von innovativen UWP-Funktionen in Kombination mit bewährten Verfahrensweisen für die Erstellung von Apps dar, die auf allen Arten von Windows-basierten Geräten hervorragend funktionieren.

Das Fluent Design System ist unser System zur Erstellung adaptiver, empathischer und schöner Benutzeroberflächen. 

**Adaptiv: Fluent-Erlebnisse fühlen sich auf jedem Gerät natürlich an.**

Fluent-Erlebnisse passen sich an die Umgebung an. Ein Fluent-Erlebnis fühlt sich auf einem Tablet, einem Desktop-PC und einer Xbox gut an. Es funktioniert sogar mit einem Mixed Reality-Headset hervorragend. Und wenn Sie mehr Hardware hinzufügen, wie z. B. einen zusätzlichen Monitor für Ihren PC, nutzt ein Fluent-Erlebnis diese Vorteile. 

**Empathisch: Fluent-Erlebnisse sind intuitiv und kraftvoll.**

Fluent-Erlebnisse passen sich dem Verhalten und der Absicht an – sie verstehen und antizipieren, was nötig ist. Sie vereinen Menschen und Ideen, egal ob sie sich auf gegenüberliegenden Seiten der Welt befinden oder direkt nebeneinander stehen. 

Empathie bedeutet, das Richtige zur richtigen Zeit zu tun. 

Fluent-Erlebnisse verwenden Steuerelement und Muster konsequent, sodass sie sich so verhalten, wie es der Benutzer erwartet hat. Fluent-Erlebnisse sind für Menschen mit einem breiten Spektrum an körperlichen Fähigkeiten zugänglich und umfassen Globalisierungsfunktionen für Menschen auf der ganzen Welt. 

**Wunderschön: Fluent-Erlebnisse sind einnehmend und immersiv.** 

Durch das Einbeziehen von Elementen der physischen Welt erschließt sich ein Fluent-Erlebniss etwas Grundsätzliches. Es nutzt Licht, Schatten, Bewegung, Tiefe und Textur, um Informationen intuitiv und instinktiv zu organisieren. 

Beim Fluent Design geht es nicht um auffällige Effekte. Es beinhaltet physikalische Effekte, die das Benutzererlebnis wirklich verbessern. Es emuliert Erlebnisse, die unser Gehirn effizient verarbeiten kann. 

## <a name="applying-fluent-design-to-your-app"></a>Umsetzung des Fluent Designs für Ihre App

Fluent Design-Features sind in UWP integriert. Einige dieser Funktionen – wie effektive Pixel und das universelle Eingabesystem – arbeiten automatisch. Sie müssen keinen zusätzlichen Code schreiben, um sie zu nutzen. Andere Funktionen, wie z. B. Acryl, sind optional. Sie nehmen sie in Ihre Anwendung auf, indem Sie Code schreiben. 

> Um mehr über die grundlegenden Funktionen zu erfahren, die automatisch in jeder UWP-Applikation enthalten sind, lesen Sie bitte den Artikel [Einführung in UWP-Apps](../basics/design-and-ui-intro.md). Wenn Sie völlig neu in der UWP-Entwicklung sind, sollten Sie sich zuerst unsere Seite [Erste Schritte mit UWP](https://developer.microsoft.com/windows/apps/getstarted) ansehen. 

Um mehr über die neuen Funktionen zu erfahren, mit denen Sie Fluent Design in Ihre App integrieren können, lesen Sie weiter.

## <a name="find-a-natural-fit"></a>Eine natürliche Form finden

Wie gestaltet man eine App auf einer Vielzahl von Geräten natürlich? Indem sie sich so anfühlt, als wäre sie für jedes einzelne Gerät entwickelt worden. Ein UI-Layout, das sich an verschiedene Bildschirmgrößen anpasst (ohne vergeudeten Platz oder Überladung) schafft ein natürliches Erlebnis – als ob es für dieses Gerät entwickelt wurde. 

*  **Design der richtigen Breakpoints**

    Anstatt das Design für jede einzelne Bildschirmgröße anzupassen, kann die Konzentration auf einige wenige aber wichtige Größen („Breakpoints”) Ihre Designs und Ihren Code stark vereinfachen und Ihre App gleichzeitig auf kleinen und großen Bildschirmen großartig darstellen.

    [Mehr über Bildschirmgrößen und Breakpoints](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)

*  **Erstellen eines dynamischen Layouts**

    Damit sich eine App natürlich anfühlt, muss sie den verfügbaren Anzeigeraum füllen, ohne überfüllt zu wirken. UWP stellt Panels bereit, die Inhalte in Rastern, Stapeln und Flüssen (Grid, Stack, Flow) anordnen und ineinander verschachteln können.

    [Mehr über die UWP-Layout-Panels](/windows/uwp/design/layout/layout-panels)

* **Design für ein Gerätespektrum**

    UWP-Apps können auf einer Vielzahl von Windows-basierten Geräten ausgeführt werden. Es ist hilfreich zu wissen, welche Geräte verfügbar sind, wofür sie gemacht sind und wie Benutzer mit ihnen interagieren.

    [Mehr über UWP-Geräte](/windows/uwp/design/devices/)

* **Optimierung für die passende Eingabe**

    UWP-Apps unterstützen automatisch gängige Maus-, Tastatur-, Stift- und Touch-Interaktionen. Sie müssen sich nicht extra darum kümmern. Aber Sie können Ihre Apps um einer optimierte Unterstützung für bestimmte Eingabemöglichkeiten (z. B. Stift und Surface Dial) erweitern.

    [Mehr über Eingaben und Interaktionen](/windows/uwp/design/input/input-primer)


## <a name="make-it-intuitive-and-powerful"></a>Intuitiv und leistungsstark

Ein Erlebnis fühlt sich intuitiv an, wenn es sich so verhält, wie der Benutzer es erwartet. Durch die Verwendung etablierter Steuerelemente und Muster und die Nutzung der Plattformunterstützung für die Zugänglichkeit und Globalisierung schaffen Sie eine reibungsloses Erlebnis, mit dem die Benutzer produktiver sind. 

* **Das passende Steuerelement für eine Aufgabe**

    Steuerelemente sind die Bausteine der Benutzeroberfläche. Mit dem richtigen Steuerelement können Sie eine Benutzeroberfläche erstellen, die sich so verhält, wie es die Benutzer erwarten.  UWP bietet mehr als 45 Steuerelemente – von einfachen Schaltflüchen bis hin zu leistungsstarken Daten-Steuerelementen. 

    [Mehr über UWP-Steuerelemente](/windows/uwp/design/controls-and-patterns/)

* **Gestalten Sie inklusiv** 

    Eine gut gestaltete App ist für Menschen mit Behinderungen zugänglich. Mit zusätzlichem Code können Sie Ihre Apps mit anderen Menschen auf der ganzen Welt teilen.

    [Mehr über Usability](/windows/uwp/design/usability/)


## <a name="be-engaging-and-immersive"></a>Gestalten Sie ansprechend und immersiv 

Gestalten Sie Ihre App ansprechend, indem Sie physische Elemente wie Licht und Bewegung integrieren. 

## <a name="use-light"></a>Verwendung von Licht

Licht kann unsere Aufmerksamkeit auf sich ziehen. Es schafft Atmosphäre und Raumgefühl und ist ein praktisches Werkzeug, um Informationen zu beleuchten.
        
Bringen Sie Licht in Ihre UWP-App:
        
* [Reveal-Highlight](../style/reveal.md) setzt Licht ein, um interaktive Elemente hervorzuheben. Licht beleuchtet das Element, mit dem der Benutzer interagieren kann und zeigt verborgene Grenzen auf. Reveal ist bei einigen Steuerelementen, wie z. B. der List-Ansicht und der Grid-Ansicht, automatisch aktiviert. Sie können es für andere Steuerelementen aktivieren, indem Sie unsere vordefinierten Reveal-Highlight-Stile verwenden. 

* [Reveal-Focus](../style/reveal-focus.md) verwendet Licht, um die Aufmerksamkeit auf das Element zu lenken, das aktuell den Eingabefokus hat.  

## <a name="create-a-sense-of-depth"></a>Schaffen Sie ein Gefühl von Tiefe

Wir leben in einer dreidimensionalen Welt. Durch die gezielte Integration von Tiefe in das UI verwandeln wir eine flache, 2D-Schnittstelle in etwas, das Informationen und Konzepte durch eine visuelle Hierarchie effizient präsentiert. Es erfindet neu, wie sich die Dinge in einer geschichteten, physikalischen Umgebung zueinander verhalten.

Bringen Sie Tiefe in Ihre UWP-App:

* [Acrylic](../style/acrylic.md) Ein transparentes Material, das dem Benutzer Ebenen von Inhalten anzeigt und eine Hierarchie von Oberflächenelementen aufbaut.

* [Parallax](../motion/parallax.md) Erzeugt die Illusion der Tiefe, indem es Gegenstände im Vordergrund schneller als Gegenstände im Hintergrund erscheinen lässt.

## <a name="incorporate-motion"></a>Integrieren von Bewegung

Stellen Sie sich Motion-Design wie einen Film vor. Nahtlose Übergänge halten Sie auf die Geschichte konzentriert und erwecken Erlebnisse zum Leben. Wir können dieses Gefühl in unsere Entwürfe einbringen und Menschen von einer Aufgabe zur nächsten führen.

Bringen Sie Bewegung in Ihre UWP-App:

* [Connected-Animations](../motion/connected-animation.md) helfen dem Benutzer, den Kontext zu behalten, indem sie einen nahtlosen Übergang zwischen den Szenen herstellen. 

## <a name="build-it-with-the-right-material"></a>Verwenden Sie das richtige Material

Die Dinge, die uns in der realen Welt umgeben, sind sinnlich und belebend. Sie biegen, strecken, prallen, zerspringen und gleiten. Diese materiellen Qualitäten übersetzen sich in digitale Umgebungen, die Menschen dazu bringen, unsere Entwürfe zu berühren und zu erreichen.

Bringen Sie Material in Ihre UWP-App: 
        
* [Acrylic](../style/acrylic.md) Ein transparentes Material, das dem Benutzer Ebenen von Inhalten anzeigt und eine Hierarchie von Oberflächenelementen aufbaut. 

## <a name="design-toolkits-and-code-samples"></a>Design-Toolkits und Codebeispiele

Sie möchten Ihre eigenen Apps mit Fluent Design erstellen? Unsere Toolkits für Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer und Sketch helfen Ihnen, Ihre Entwürfe zu beschleunigen. Mit unseren Beispielen können Sie schneller entwickeln.

* Schauen Sie sich unsere [Seite zu Design-Toolkits und Beispielen](/windows/uwp/design/downloads/) an.

<img src="images/fluentdesign_header.png" alt=" " />








