---
author: mijacobs
description: "„Einblendungen” ist ein neues Interaktionsmodell, mit dem sich ein stärkerer Fokus und mehr Spaß in Ihre Anwendung bringen lassen."
title: Einblendungen
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: kisai
design-contact: conrwi
dev-contact: jevansa
doc-status: Published
ms.openlocfilehash: d50e3f47faad5fff0ef461a4b5312127a0b9ec9c
ms.sourcegitcommit: 0d5b3daddb3ae74f91178c58e35cbab33854cb7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="reveal"></a>Einblendungen

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Einblendungen sind neue Lichteffekte, welche die interaktiven Elemente in Ihrer App mit Tiefe und Fokus versehen kann.

> **Wichtige APIs**: [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush), [RevealBackgroundBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbackgroundbrush), [RevealBorderBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealborderbrush), [RevealBrushHelper-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrushhelper), [VisualState-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.VisualState)

Zu diesem Zweck werden mithilfe des Einblendeverhaltens Teile von Elementen um Favoriteninhalt (oder zentralen Inhalt) herum eingeblendet, wenn die Maus oder das Fokusrechteck über die gewünschten Bereiche bewegt wird.

![Einblendeanzeige](images/Nav_Reveal_Animation.gif)

Da durch Einblendungen die ausgeblendeten Rahmen um Objekte herum angezeigt werden, entwickeln Benutzer ein besseres Verständnis von dem Raum, mit dem diese Objekte interagieren. Darüber hinaus erfahren sie dadurch, welche Aktionen verfügbar sind. Dies ist besonders wichtig in Listensteuerelementen und Steuerelementen mit Backplates.

## <a name="reveal-and-the-fluent-design-system"></a>Einblendungen und das Fluent Design-System

 Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten. „Einblendungen” ist eine Komponente des Fluent Design-Systems, die Lichteffekte in Ihrer App ermöglicht. 

## <a name="what-is-reveal"></a>Was sind Einblendungen?

Es gibt zwei visuelle Hauptkomponenten für Einblendungen: das Verhalten **Einblenden durch Daraufzeigen** und das Verhalten **Rahmen einblenden**.

![Ebenen einblenden](images/RevealLayers.png)

Das Verhalten „Einblenden durch Daraufzeigen” ist direkt mit dem Inhalt verbunden, auf den gezeigt wird (mit Zeiger- oder Fokuseingaben). Dabei wird ein leichter Lichthof um das Element herum eingeblendet, auf das gezeigt oder das fokussiert wird, sodass Sie wissen, dass Sie damit interagieren können.

Das Verhalten „Rahmen einblenden” wird auf das fokussierte Element und andere Elemente in dessen Nähe angewendet. Dadurch erfahren Sie, dass diese Objekte in der Nähe ähnliche Aktionen wie das aktuell fokussierte Objekt durchführen können.

Die Aufschlüsselung der Anleitung für Einblendungen sieht folgendermaßen aus:

- Das Verhalten „Rahmen einblenden” befindet sich über dem gesamten Inhalt, jedoch an den angegebenen Rändern.
- Text und Inhalt werden direkt unter dem Verhalten „Rahmen einblenden” angezeigt.
- Das Verhalten „Einblenden durch Daraufzeigen” befindet sich unterhalb von Inhalt und Text.
- Die Backplate (die das Verhalten „Rahmen einblenden” aktiviert)
- Der Hintergrund (Hintergrund des Steuerelements)

<!--
<div class=”microsoft-internal-note”>
To create your own Reveal lighting effect for static comps or prototype purposes, see the full [uni design guidance](http://uni/DesignDepot.FrontEnd/#/ProductNav/3020/1/dv/?t=Resources%7CToolkit%7CReveal&f=Neon) for this effect in illustrator.
</div>
-->

## <a name="how-to-use-it"></a>Verwendung

Durch Einblendungen wird Geometrie um den Cursor herum angezeigt, wenn diese benötigt wird, und sie wird nahtlos ausgeblendet, wenn der Cursor weiterbewegt wird.

Einblendungen lassen sich am besten verwenden, wenn sie für den Hauptinhalt Ihrer App (Favoriteninhalt) aktiviert sind, der Grenzen und Backplates aufweist. Einblendungen sollten darüber hinaus für Auflistungs- oder listenähnliche Steuerelemente verwendet werden.

## <a name="controls-that-automatically-use-reveal"></a>Steuerelemente, die Einblendungen automatisch verwenden

- [**ListView**](../controls-and-patterns/lists.md)
- [**TreeView**](../controls-and-patterns/tree-view.md)
- [**NavigationView**](../controls-and-patterns/navigationview.md)
- [**AutosuggestBox**](../controls-and-patterns/auto-suggest-box.md)

## <a name="enabling-reveal-on-other-common-controls"></a>Aktivieren von Einblendungen für andere allgemeine Steuerelemente

Für Szenarien, in denen Einblendungen angewendet werden sollten (diese Steuerelemente sind Hauptinhalt und/oder werden in einer Liste oder Auflistungsausrichtung verwendet), haben wir optionale Ressourcenformate bereitgestellt, mithilfe derer Sie Einblendungen für solche Situationen aktivieren können.

Diese Steuerelemente verfügen nicht standardmäßig über Einblendungen, da sie kleinere Steuerelemente sind, die in der Regel als Hilfssteuerelemente für die zentralen Punkte Ihrer Anwendung dienen. Alle Apps sind jedoch verschieden, und wenn diese Steuerelemente in Ihrer App am meisten verwendet werden, stehen Ihnen einige Formate als Hilfe zur Verfügung:

| Name des Steuerelements   | Ressourcenname |
|----------|:-------------:|
| Button |  ButtonRevealStyle |
| ToggleButton | ToggleButtonRevealStyle |
| RepeatButton | RepeatButtonRevealStyle |
| AppBarButton | AppBarButtonRevealStyle |
| SemanticZoom | SemanticZoomRevealStyle |
| ComboBoxItem | ComboxBoxItemRevealStyle |

Um diese Formate anzuwenden, aktualisieren Sie einfach folgendermaßen die Eigenschaft „Style”:

```XAML
<Button Content="Button Content" Style="{StaticResource ButtonRevealStyle}"/>
```

> [!NOTE]
> In Version 16190 des SDK werden diese Formate nicht automatisch zur Verfügung gestellt. Um sie zu verwenden, müssen Sie diese Formate manuell aus generic.xaml in Ihre App kopieren. Generic.xaml finden Sie normalerweise unter C:\Programme (x86)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\10.0.16190.0\Generic. Dieses Problem wird in einem späteren Build behoben. 

## <a name="enabling-reveal-on-custom-controls"></a>Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente

Rufen Sie zum Aktivieren von Einblendungen für benutzerdefinierte Steuerelemente oder Steuerelemente mit neuen Vorlagen das Format für dieses Steuerelement in den visuellen Zuständen der Vorlage für dieses Steuerelement auf, und legen Sie Einblendungen im Stammraster fest:

```xaml
<VisualState x:Name="PointerOver">
  <VisualState.Setters>
    <Setter Target="RootGrid.(RevealBrushHelper.State)" Value="PointerOver" />
    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPointerOver}"/>
    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushPointerOver}"/>
    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPointerOver}"/>
  </VisualState.Setters>
</VisualState>
```

Um den Pull-Effekt bei Einblendungen zu erhalten, müssen Sie denselben RevealBrushHelper zu PressedState hinzufügen:

```xaml
<VisualState x:Name="Pressed">
  <VisualState.Setters>
    <Setter Target="RootGrid.(RevealBrushHelper.State)" Value="Pressed" />
    <Setter Target="RootGrid.Background" Value="{ThemeResource ButtonRevealBackgroundPressed}"/>
    <Setter Target="ContentPresenter.BorderBrush" Value="{ThemeResource ButtonRevealBorderBrushPressed}"/>
    <Setter Target="ContentPresenter.Foreground" Value="{ThemeResource ButtonForegroundPressed}"/>
  </VisualState.Setters>
</VisualState>
```


Wenn Sie unsere Systemressource „Einblendungen” verwenden, kümmern wir uns für Sie um alle Designänderungen.

## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen
- Verwenden Sie Einblendungen für Elemente, auf denen Benutzer Aktionen durchführen können – Einblendungen sollten nicht für statischen Inhalt verwendet werden.
- Verwenden Sie Einblendungen in Listen oder Datensammlungen.
- Wenden Sie Einblendungen auf klar eingebundene Inhalte mit Backplates an.
- Verwenden Sie keine Einblendungen auf statischen Hintergründen, Text oder Bildern, mit denen keine Interaktionen möglich sind.
- Wenden Sie Einblendungen nicht auf nicht irrelevanten, schwebenden Inhalt an.
- Verwenden Sie Einblendungen nicht für einmalige, isolierte Situationen, wie Dialoge oder Benachrichtigungen zum Inhalt.
- Verwenden Sie Einblendungen nicht bei sicherheitsbezogenen Entscheidungen, da es die Aufmerksamkeit von der Nachricht, die Sie an die Benutzer übermitteln möchten, weglenken kann.

## <a name="related-articles"></a>Verwandte Artikel

- [RevealBrush-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.revealbrush)
- [**Acryl**](acrylic.md)
- [**Kompositionseffekte**](https://msdn.microsoft.com/windows/uwp/graphics/composition-effects)
