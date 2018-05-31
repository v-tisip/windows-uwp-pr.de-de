---
author: stevewhims
Description: Design your app to support the layouts and fonts of multiple languages, including RTL (right-to-left) flow direction.
title: Layout und Schriften anpassen und RTL unterstützen
ms.assetid: F2522B07-017D-40F1-B3C8-C4D0DFD03AC3
label: Adjust layout and fonts, and support RTL
template: detail.hbs
ms.author: stwhi
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Lokalisierbarkeit, Lokalisierung, rtl, ltr
ms.localizationpriority: medium
ms.openlocfilehash: cf3a2d781dc916fbda9a9d6386dee4e2e6144873
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1673977"
---
# <a name="adjust-layout-and-fonts-and-support-rtl"></a>Layout und Schriften anpassen und RTL unterstützen

Entwerfen Sie Ihre App so, dass die Layouts und Schriften mehrerer Sprachen unterstützen – beispielsweise auch den Textfluss von rechts nach links (right-to-left, RTL). Die Textflussrichtung ist die Richtung, in der ein Text geschrieben und angezeigt wird, und die UI-Elemente auf der Seite werden entsprechend gelesen.

## <a name="layout-guidelines"></a>Layoutrichtlinien

Sprachen wie Deutsch und Finnisch benötigen in der Regel mehr Zeichen als Englisch. Fernöstliche Schriften benötigen normalerweise mehr Höhe. Und bei Sprachen wie Arabisch und Hebräisch muss die Leserichtung in Textfeldern und des App-Elementen von rechts nach links (RTL) verlaufen.

Aufgrund der variablen Länge des übersetzten Texts sollten Sie dynamische UI-Layoutmechanismen anstelle von absoluten Positionierungen, festen Breiten oder festen Höhen verwenden. Durch die Pseudolokalisierung für die App werden problematische Fälle aufgedeckt, in denen UI-Elemente nicht richtig an den Inhalt angepasst sind.

Verwenden Sie für RTL-Sprachen die Eigenschaft [**FrameworkElement.FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection), und legen Sie symmetrische Abstände und Ränder fest. Layoutpanels wie [**Grid**](/uwp/api/Windows.UI.Xaml.Controls.Grid?branch=live) skalieren und spiegeln sich automatisch gemäß dem von Ihnen festgelegten Wert für **FlowDirection**.

Es folgt ein Beispiel für die Bereitstellung einer FlowDirection-Eigenschaft in Ihrer App als Ressource, die von Lokalisierern entsprechend festgelegt werden kann.

Fügen Sie zunächst in der Ressourcendatei Ihrer App (.resw) eine Eigenschaften-ID mit dem Namen „MainPage.FlowDirection” hinzu (anstelle von „MainPage” können Sie einen beliebigen Namen verwenden).

Verwenden Sie dann **x:Uid**, um Ihr hauptsächliches **Page**-Element mit dieser Eigenschaftskennung zu verknüpfen.

```xaml
<Page x:Uid="MainPage">
```

Weitere Informationen zu Zeichenfolgenressourcen-Bezeichner und Ressourcendateien (.resw) finden Sie unter Lokalisieren der Zeichenfolge im Paketmanifest der Benutzeroberfläche und der App.
Weitere Informationen zu Ressourcendateien (.resw), Eigenschaften-IDs und **x:Uid** finden Sie unter [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest](../../app-resources/localize-strings-ui-manifest.md).

Vermeiden Sie, absolute Layoutwerte für ein beliebiges Benutzeroberflächenelement basierend auf der Sprache festzulegen. Wenn das jedoch absolut unvermeidbar ist, können Sie eine Eigenschaftskennung der Form „TitleText.Width” erstellen.

```xaml
<TextBlock x:Uid="TitleText">
```

## <a name="fonts"></a>Schriften

Verwenden Sie die [**LanguageFont**](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)-Schriftzuordnungsklasse für den programmgesteuerten Zugriff auf die empfohlene Familie und Breite und den empfohlenen Grad und Schnitt der Schriftart für eine spezielle Sprache. Die **LanguageFont**-Klasse ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriften für den Textkörper, die vom Benutzer bearbeitet werden können.

## <a name="mirroring-images"></a>Spiegeln von Bildern

Wenn Ihre App Bilder enthält, die für die Leserichtung rechts nach links (RTL) gespiegelt werden müssen (Umkehrung des Bilds), können Sie die **FlowDirection**-Eigenschaft verwenden.

```xaml
<!-- en-US\localized.xaml -->
<Image ... FlowDirection="LeftToRight" />

<!-- ar-SA\localized.xaml -->
<Image ... FlowDirection="RightToLeft" />
```

Wenn die App ein anderes Bild benötigt, damit dieses richtig umgedreht werden kann, können Sie das Ressourcenverwaltungssystem mit dem `LayoutDirection`-Qualifizierer verwenden (s. LayoutDirection-Abschnitt in [Ressourcen an Sprache, Skalierung und andere Qualifikationsmerkmale anpassen](../../app-resources/tailor-resources-lang-scale-contrast.md#layoutdirection)). Das System wählt ein Bild mit dem Namen `file.layoutdir-rtl.png` aus, wenn die App-Laufzeitsprache (s. [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md))auf eine RTL-Sprache festgelegt wird. Diese Vorgehensweise ist möglicherweise nötig, wenn nicht alle Teile des Bilds umgedreht werden.

## <a name="best-practices-for-handling-right-to-left-rtl-languages"></a>Bewährte Methoden für die Behandlung von Sprachen, die von rechts nach links gelesen werden (RTL-Sprachen)

Wenn Ihre App für Sprachen lokalisiert wurde, die von rechts nach links gelesen werden (RTL-Sprachen), können Sie APIs verwenden, um die standardmäßige Textrichtung für das Root-Layout-Panel Ihrer Seite festzulegen So wird erreicht, dass alle Steuerelemente, die in Root-Panel enthalten sind, richtig auf die standardmäßige Textrichtung reagieren. Wenn mehr als eine Sprache unterstützt wird, verwenden Sie `LayoutDirection` für die bevorzugte App-Laufzeitsprache, um die Eigenschaft [**FlowDirection**](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection) festzulegen (s. Codebeispiel unten). Die meisten Steuerelemente in Windows verwenden **FlowDirection** bereits. Wenn Sie benutzerdefinierte Steuerelemente implementieren, sollte **FlowDirection** verwendet werden, um entsprechende Layoutänderungen für RTL- und LTR-Sprachen vorzunehmen.

```csharp    
this.languageTag = Windows.Globalization.ApplicationLanguages.Languages[0];

// For bidirectional languages, determine flow direction for the root layout panel, and all contained UI.

var flowDirectionSetting = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues["LayoutDirection"];
if (flowDirectionSetting == "LTR")
{
    this.layoutRoot.FlowDirection = Windows.UI.Xaml.FlowDirection.LeftToRight;
}
else
{
    this.layoutRoot.FlowDirection = Windows.UI.Xaml.FlowDirection.RightToLeft;
}
```

```cpp
this->languageTag = Windows::Globalization::ApplicationLanguages::Languages->GetAt(0);

// For bidirectional languages, determine flow direction for the root layout panel, and all contained UI.

auto flowDirectionSetting = Windows::ApplicationModel::Resources::Core::ResourceContext::GetForCurrentView()->QualifierValues->Lookup("LayoutDirection");
if (flowDirectionSetting == "LTR")
{
    this->layoutRoot->FlowDirection = Windows::UI::Xaml::FlowDirection::LeftToRight;
}
else
{
    this->layoutRoot->FlowDirection = Windows::UI::Xaml::FlowDirection::RightToLeft;
}
```

### <a name="rtl-faq"></a>Häufig gestellte Fragen zu RTL 

**F:** Wird **FlowDirection** automatisch basierend auf der aktuellen Sprachauswahl festgelegt? Wenn ich beispielsweise Englisch auswähle, wird dann die Links-nach-rechts-Leserichtung angezeigt, und für Arabisch die Rechts-nach-links-Leserichtung?

> **A:** **FlowDirection** ist nicht mit einer Berücksichtigung der Sprache verbunden. Sie legen **FlowDirection** entsprechend für die Sprache fest, die gerade angezeigt wird. Siehe obigen Beispielcode.

**F:** Ich kenne mich mit Lokalisierung nicht aus. Enthalten die Ressourcen bereits die Textflussrichtung? Ist es möglich, die Flussrichtung für die aktuelle Sprache zu bestimmen?

> **A:** Wenn Sie sich an die derzeitigen bewährten Methoden halten, enthalten die Ressourcen die Flussrichtung nicht direkt. Sie müssen die Flussrichtung für die aktuelle Sprache bestimmen. Dazu gibt es zwei Möglichkeiten.
> 
> Die bevorzugte Methode ist die Verwendung von **LayoutDirection** für die bevorzugte Sprache, um die Eigenschaft **FlowDirection** für den RootFrame festzulegen. Alle Steuerelemente in RootFrame erben „FlowDirection“ vom RootFrame-Element.
> 
> Eine andere Möglichkeit ist das Festlegen von FlowDirection in der RESW-Datei für die RTL-Sprachen, für die Sie die Lokalisierung durchführen. Sie können beispielsweise eine arabische RESW-Datei und eine hebräische RESW-Datei verwenden. In diesen Dateien können Sie „x:UID“ zum Festlegen von FlowDirection verwenden. Diese Methode ist aber fehleranfälliger als die programmgesteuerte Methode.

## <a name="important-apis"></a>Wichtige APIs

* [FrameworkElement.FlowDirection](/uwp/api/Windows.UI.Xaml.FrameworkElement.FlowDirection)
* [LanguageFont](/uwp/api/Windows.Globalization.Fonts.LanguageFont?branch=live)

## <a name="related-topics"></a>Verwandte Themen

* [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im Paketmanifest der App](../../app-resources/localize-strings-ui-manifest.md)
* [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften](../../app-resources/tailor-resources-lang-scale-contrast.md)
* [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md)