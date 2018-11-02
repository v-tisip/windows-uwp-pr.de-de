---
description: Lernen Sie das Fluent Design und dessen Integration in Ihre Apps kennen.
title: Fluent Design System für Windows
author: mijacobs
keywords: Layout von UWP-Apps, universelle Windows-Plattform, App-Design, Schnittstelle, fluent design system
ms.author: mijacobs
ms.date: 3/7/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 2ab8e8c18a0b1db0991bf470f194f8774f2357b4
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5943090"
---
# <a name="the-fluent-design-system-for-windows-app-creators"></a>Das Fluent Design System für Windows-app creators

![Fluent Design-header](images/fluentdesign-app-header.jpg)

## <a name="introduction"></a>Einführung

Das Fluent Design System ist unser System zur Erstellung adaptiver, empathischer und schöner Benutzeroberflächen.

## <a name="principles"></a>Prinzipien

**Adaptiv: Fluent-Erlebnisse fühlen sich auf jedem Gerät natürlich an.**

Fluent-Erlebnisse passen sich an die Umgebung an. Ein Fluent-Erlebnis fühlt sich auf einem Tablet, desktop-PCs und einer Xbox – es funktioniert sogar hervorragend auf einem Mixed Reality-Kopfhörer. Und wenn Sie mehr Hardware hinzufügen, wie z. B. einen zusätzlichen Monitor für Ihren PC, nutzt ein Fluent-Erlebnis diese Vorteile.

**Empathisch: Fluent-Erlebnisse sind intuitiv und kraftvoll.**

Fluent-Erlebnisse passen sich dem Verhalten und der Absicht an – sie verstehen und antizipieren, was nötig ist. Sie vereinen Menschen und Ideen, egal ob sie sich auf gegenüberliegenden Seiten der Welt befinden oder direkt nebeneinander stehen.

**Wunderschön: Fluent-Erlebnisse sind einnehmend und immersiv.**

Durch das Einbeziehen von Elementen der physischen Welt erschließt sich ein Fluent-Erlebniss etwas Grundsätzliches. Es nutzt Licht, Schatten, Bewegung, Tiefe und Textur, um Informationen intuitiv und instinktiv zu organisieren.


## <a name="applying-fluent-design-to-your-app-with-uwp"></a>Umsetzung des Fluent Designs für Ihre app mit UWP

![Fluent Design-logo](images/fluentdesign_header.png)

Unseren Designrichtlinien erläutert, wie Sie Fluent-Entwurfsprinzipien auf apps anwenden. Welche Art von apps? Obwohl viele unserer Richtlinien auf jeder Plattform angewendet werden können, haben wir Windows-Plattform (die Universal) zur Unterstützung der Fluent Design erstellt.

Fluent Design-Features sind in UWP integriert. Einige dieser Funktionen – wie effektive Pixel und das universelle Eingabesystem – arbeiten automatisch. Sie müssen keinen zusätzlichen Code schreiben, um sie zu nutzen. Andere Funktionen, wie z. B. Acryl, sind optional. Sie nehmen sie in Ihre Anwendung auf, indem Sie Code schreiben.

> Wir bringen UWP-Steuerelemente auf den Desktop, damit Sie das Aussehen, Verhalten und die Funktionalität Ihrer vorhandenen WPF- oder Windows-Anwendungen mit Fluent Design-Features verbessern können. Weitere Informationen hierzu finden Sie in der [Host-UWP-Steuerelemente in WPF- oder Windows Forms-Anwendung](/windows/uwp/xaml-platform/xaml-host-controls).

<!-- To apply Fluent Design to your app, follow our guidelines and use UWP (Universal Windows Platform) you can use UWP UI features combined with best practices for creating apps that perform beautifully on all types of Windows-powered devices. -->

Zusätzlich zu designanleitungen zeigen unserer Fluent Design-Artikel auch Ihnen, wie Sie Code schreiben, der Ihre Entwürfe passieren erheblich vereinfacht. UWP verwendet XAML, eine Markup-basierte Programmiersprache, die einfacher für Benutzeroberflächen erstellen kann. Beispiel:

```xaml
<Grid BorderBrush="Blue" BorderThickness="4">
    <TextBox Text="Design with XAML" Margin="20" Padding="24,16"/>
</Grid>
```

![](images/xaml-example.png)


> Wenn Sie die Entwicklung für UWP sind, sehen Sie sich unsere [Erste Schritte mit UWP-Seite](https://developer.microsoft.com/windows/apps/getstarted).

## <a name="find-a-natural-fit"></a>Eine natürliche Form finden

Wie gestaltet man eine App auf einer Vielzahl von Geräten natürlich? Indem sie sich so anfühlt, als wäre sie für jedes einzelne Gerät entwickelt worden. Ein UI-Layout, das sich an verschiedene Bildschirmgrößen anpasst (ohne vergeudeten Platz oder Überladung) schafft ein natürliches Erlebnis – als ob es für dieses Gerät entwickelt wurde.

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-size-classes.jpg)
    :::column-end:::
    :::column span="2":::
        **Design for the right breakpoints**

        Instead of designing for every individual screen size, focusing on a few key widths (also called "breakpoints") can greatly simplify your designs and code while still making your app look great on small to large screens.

        [Learn about screen sizes and breakpoints](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/rspd-resize.gif)
    :::column-end:::
    :::column span="2":::
        **Create a responsive layout**

        For an app to feel natural, it should adapt its layout to different screen sizes and devices. You can use automatic sizing, layout panels, visual states, and even separate UI definitions in XAML to create a responsive UI.

        [Learn about responsive design](/windows/uwp/design/layout/responsive-design)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/devices.jpg)
    :::column-end:::
    :::column span="2":::
        **Design for a spectrum of devices**

        UWP apps can run on a wide variety of Windows-powered devices. It's helpful to understand which devices are available, what they're made for, and how users interact with them.

        [Learn about UWP devices](/windows/uwp/design/devices/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/keyboard-shortcuts.jpg)
    :::column-end:::
    :::column span="2":::
        **Optimize for the right input**

        UWP apps automatically support common mouse, keyboard, pen, and touch interactions&mdash;there's nothing extra you have to do. But you can enhance your app with optimized support for specific inputs, like pen and the Surface Dial.

        [Learn about inputs and interactions](/windows/uwp/design/input/input-primer)
:::row-end:::

## <a name="make-it-intuitive"></a>Stellen sie intuitiv

Ein Erlebnis fühlt sich intuitiv, wenn es sich um die Art und Weise verhält, wie der Benutzer es erwartet. Durch die Verwendung etablierter Steuerelemente und Muster und die Nutzung der Plattformunterstützung für die Zugänglichkeit und Globalisierung schaffen Sie eine reibungsloses Erlebnis, mit dem die Benutzer produktiver sind.

Empathie bedeutet, das Richtige zur richtigen Zeit zu tun.

Fluent-Erlebnisse verwenden Steuerelement und Muster konsequent, sodass sie sich so verhalten, wie es der Benutzer erwartet hat. Fluent-Erlebnisse sind für Menschen mit einem breiten Spektrum an körperlichen Fähigkeiten zugänglich und umfassen Globalisierungsfunktionen für Menschen auf der ganzen Welt.

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-navview.png)
    :::column-end:::
    :::column span="2":::
        **Provide the right navigation**

        Create an effortless experience by using the right app structure and navigation components.

        [Learn about navigation](/windows/uwp/design/basics/navigation-basics/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-commanding.png)
    :::column-end:::
    :::column span="2":::
        **Be interactive**

        Buttons, command bars, keyboard shortcuts, and context menus enable users to interact with your app; they're the tools that change a static experience into something dynamic.

        [Learn about commanding](/windows/uwp/design/basics/commanding-basics/)
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-controls-2.jpg)
    :::column-end:::
    :::column span="2":::
        **Use the right control for the job**

        Controls are the building blocks of the user interface; using the right control helps you create a user interface that behaves the way users expect it to.  UWP provides more than 45 controls,ranging from simple buttons to powerful data controls.

        [Learn about UWP controls](/windows/uwp/design/controls-and-patterns/)
:::row-end:::

:::row:::
    :::column:::
        ![inclusive image](images/thumbnail-inclusive.png)
    :::column-end:::
    :::column span="2":::
        **Be inclusive**
        A well-design app is accessible to people with disabilities. With some extra coding, you can share your app with people around the world.

        [Learn about Usability](/windows/uwp/design/usability/)
:::row-end:::

## <a name="be-engaging-and-immersive"></a>Gestalten Sie ansprechend und immersiv

Beim Fluent Design geht es nicht um auffällige Effekte. Es beinhaltet physikalische Effekte, die das Benutzererlebnis wirklich verbessern. Es emuliert Erlebnisse, die unser Gehirn effizient verarbeiten kann.

## <a name="use-light"></a>Verwendung von Licht

Licht kann unsere Aufmerksamkeit auf sich ziehen. Es schafft Atmosphäre und Raumgefühl und ist ein praktisches Werkzeug, um Informationen zu beleuchten.

Bringen Sie Licht in Ihre UWP-App:

:::row:::
    :::column:::
        ![fpo image](../style/images/Nav_Reveal_Animation.gif)
    :::column-end:::
    :::column span="2":::
        **Reveal highlight**

        [Reveal highlight](../style/reveal.md) uses light to make interactive elements stand out. Light illuminates the elements the user can interact with, revealing hidden borders. Reveal is automatically enabled on some controls, such as list view and grid view. You can enable it on other controls by applying our predefined Reveal highlight styles.
:::row-end:::

:::row:::
    :::column:::
        ![fpo image](../style/images/traveling-focus-fullscreen-light-rf.gif)
    :::column-end:::
    :::column span="2":::
        **Reveal focus**

        [Reveal focus](../style/reveal-focus.md) uses light to call attention to the element that currently has input focus.
:::row-end:::

## <a name="create-a-sense-of-depth"></a>Schaffen Sie ein Gefühl von Tiefe

Wir leben in einer dreidimensionalen Welt. Durch die gezielte Integration von Tiefe in das UI verwandeln wir eine flache, 2D-Schnittstelle in etwas, das Informationen und Konzepte durch eine visuelle Hierarchie effizient präsentiert. Es erfindet neu, wie sich die Dinge in einer geschichteten, physikalischen Umgebung zueinander verhalten.

Bringen Sie Tiefe in Ihre UWP-App:

:::row:::
    :::column:::
        ![fpo image](../motion/images/_parallax_v2.gif)
    :::column-end:::
    :::column span="2":::
        **Parallax**

        [Parallax](../motion/parallax.md) creates the illusion of depth by making items in the foreground appear to move more quickly than items in the background.
:::row-end:::

## <a name="incorporate-motion"></a>Integrieren von Bewegung

Stellen Sie sich Motion-Design wie einen Film vor. Nahtlose Übergänge halten Sie auf die Geschichte konzentriert und erwecken Erlebnisse zum Leben. Wir können dieses Gefühl in unsere Entwürfe einbringen und Menschen von einer Aufgabe zur nächsten führen.

Bringen Sie Bewegung in Ihre UWP-App:

:::row:::
    :::column:::
        ![continuity gif](images/continuityXbox.gif)
    :::column-end:::
    :::column span="2":::
        **Connected animations**

        [Connected animations](../motion/connected-animation.md) help the user maintain context by creating a seamless transition between scenes.
:::row-end:::

## <a name="build-it-with-the-right-material"></a>Verwenden Sie das richtige Material

Die Dinge, die uns in der realen Welt umgeben, sind sinnlich und belebend. Sie biegen, strecken, prallen, zerspringen und gleiten. Diese materiellen Qualitäten übersetzen sich in digitale Umgebungen, die Menschen dazu bringen, unsere Entwürfe zu berühren und zu erreichen.

Bringen Sie Material in Ihre UWP-App:

:::row:::
    :::column:::
        ![fpo image](../style/images/acrylic_lighttheme_base.png)
    :::column-end:::
    :::column span="2":::
        **Acrylic**

        [Acrylic](../style/acrylic.md) is a translucent material that lets the user see layers of content, establishing a hierarchy of UI elements.
:::row-end:::

## <a name="design-toolkits-and-code-samples"></a>Design-Toolkits und Codebeispiele

Sie möchten Ihre eigenen Apps mit Fluent Design erstellen? Unsere Toolkits für Adobe XD, Adobe Illustrator, Adobe Photoshop, Framer und Sketch helfen Ihnen, Ihre Entwürfe zu beschleunigen. Mit unseren Beispielen können Sie schneller entwickeln.

:::row:::
    :::column:::
        ![fpo image](images/thumbnail-toolkits.jpg)
    :::column-end:::
    :::column span="2":::
        **Design toolkits and samples page**

        Check out our [Design toolkits and samples page](/windows/uwp/design/downloads/)
:::row-end:::









