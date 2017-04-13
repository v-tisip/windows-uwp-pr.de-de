---
author: DelfCo
Description: "Entwickeln Sie Ihre App so, dass die Layouts und Schriftarten mehrerer Sprachen unterstützt werden – also beispielsweise auch die Flussrichtung von rechts nach links (right-to-left, RTL)."
title: "Anpassen von Layout und Schriftarten und Unterstützen von „Von rechts nach links“"
ms.assetid: F2522B07-017D-40F1-B3C8-C4D0DFD03AC3
label: Adjust layout and fonts, and support RTL
template: detail.hbs
ms.author: bobdel
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 9c700928d2ec0da21b518528289034296637eeff
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="adjust-layout-and-fonts-and-support-rtl"></a>Anpassen von Layout und Schriftarten und Unterstützen von „Von rechts nach links“
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Entwickeln Sie Ihre App so, dass die Layouts und Schriftarten mehrerer Sprachen unterstützt werden –also beispielsweise auch die Flussrichtung von rechts nach links (right-to-left, RTL).

## <a name="layout-guidelines"></a>Layoutrichtlinien


Einige Sprachen, darunter Deutsch und Finnisch, benötigen für den Text mehr Raum als Englisch. Für die Schriftarten einiger Sprachen, z.B. Japanisch, wird eine größere Höhe benötigt. Und bei Sprachen wie Arabisch und Hebräisch muss die Leserichtung des Text- und des App-Layouts von rechts nach links verlaufen.

Verwenden Sie flexible Layoutmechanismen anstelle einer absoluten Positionierung oder fester Breiten und Höhen. Bestimmte UI-Elemente können abhängig von der Sprache geändert werden.

Geben Sie eine **Uid** für ein Element an:

```XML
<TextBlock x:Uid="Block1">
```

Stellen Sie sicher, dass die RESW-Datei der App eine Ressource für „Block1.Width“ besitzt, die Sie für jede zu lokalisierende Sprache festlegen können.

Verwenden Sie bei Windows Store-Apps mit C++, C\# oder Visual Basic die [**FlowDirection**](https://msdn.microsoft.com/library/windows/apps/br208716)-Eigenschaft mit symmetrischen Abständen und Rändern, um die Lokalisierung für andere Layoutrichtungen zu ermöglichen.

Bei XAML-Layoutsteuerelementen wie [**Grid**](https://msdn.microsoft.com/library/windows/apps/br242704) erfolgt das Skalieren und Kippen automatisch mit der [**FlowDirection**](https://msdn.microsoft.com/library/windows/apps/br208716)-Eigenschaft. Machen Sie Ihre eigene **FlowDirection**-Eigenschaft in Ihrer App als Ressource für Lokalisierer verfügbar.

Geben Sie eine **Uid** für die Hauptseite der App an:

```XML
<Page x:Uid="MainPage">
```

Stellen Sie sicher, dass die **ResW**-Datei der App eine Ressource für „MainPage.FlowDirection“ besitzt, die Sie für jede zu lokalisierende Sprache festlegen können.


## <a name="mirroring-images"></a>Spiegeln von Bildern

Wenn Ihre App Bilder enthält, die für die Leserichtung von rechts nach links gespiegelt werden müssen (Umkehrung desselben Bilds), können Sie die [**FlowDirection**](https://msdn.microsoft.com/library/windows/apps/br208716)-Eigenschaft anwenden:

```XML
<!-- en-US\localized.xaml -->
<Image ... FlowDirection="LeftToRight" />

<!-- ar-SA\localized.xaml -->
<Image ... FlowDirection="RightToLeft" />
```


Wenn die App ein anderes Bild benötigt, damit dieses richtig umgedreht werden kann, können Sie das Ressourcenverwaltungssystem mit dem [layoutdir](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324)-Qualifizierer verwenden. Das System wählt ein Bild mit dem Namen „file.layoutdir-rtl.png“ aus, wenn die [App-Sprache](manage-language-and-region.md) auf eine Rechts-nach-links-Sprache festgelegt wird. Diese Vorgehensweise ist möglicherweise nötig, wenn nicht alle Teile des Bilds umgedreht werden.

## <a name="fonts"></a>Schriftarten

Verwenden Sie die [**LanguageFont**](https://msdn.microsoft.com/library/windows/apps/br206864)-Schriftartenersetzungs-APIs für den programmgesteuerten Zugriff auf die empfohlene Familie und Breite und den empfohlenen Grad und Schnitt der Schriftart für eine spezielle Sprache. Das **LanguageFont**-Objekt ermöglicht den Zugriff auf die richtigen Schriftartinformationen für verschiedene Inhaltskategorien: UI-Kopfzeilen, Benachrichtigungen, Textkörper und Schriftarten für den Textkörper, die vom Benutzer bearbeitet werden können.

## <a name="best-practices-for-handling-right-to-left-rtl-languages"></a>Bewährte Methoden für die Behandlung von Sprachen, die von rechts nach links gelesen werden

Wenn Ihre App für Sprachen lokalisiert wurde, die von rechts nach links gelesen werden, können Sie APIs verwenden, um die standardmäßige Textrichtung für RootFrame festzulegen. So wird erreicht, dass alle Steuerelemente, die in RootFrame enthalten sind, richtig auf die standardmäßige Textrichtung reagieren.  Wenn mehr als eine Sprache unterstützt wird, verwenden Sie LayoutDirection für die oberste bevorzugte Sprache, um die FlowDirection-Eigenschaft festzulegen. Für die meisten Steuerelemente, die in Windows enthalten sind, wird FlowDirection bereits verwendet. Wenn Sie benutzerdefinierte Steuerelemente implementieren, sollte FlowDirection verwendet werden, um entsprechende Layoutänderungen für Sprachen mit Rechts-nach-links- und Links-nach-rechts-Leserichtung vorzunehmen.

C#
```csharp    
// For bidirectional languages, determine flow direction for RootFrame and all derived UI.

    string resourceFlowDirection = ResourceContext.GetForCurrentView().QualifierValues["LayoutDirection"];
    if (resourceFlowDirection == "LTR")
    {
       RootFrame.FlowDirection = FlowDirection.LeftToRight;
    }
    else
    {
       RootFrame.FlowDirection = FlowDirection.RightToLeft;
    }
```

C++:
```
    // Get preferred app language
    m_language = Windows::Globalization::ApplicationLanguages::Languages->GetAt(0);
     
    // Set flow direction accordingly
    m_flowDirection = ResourceManager::Current->DefaultContext->QualifierValues->Lookup("LayoutDirection") != "LTR" ? 
       FlowDirection::RightToLeft : FlowDirection::LeftToRight;
```


### <a name="rtl-faq"></a>Häufig gestellte Fragen zu Sprachen mit Rechts-nach-links-Leserichtung 

<dl>
  <dt> <p><b>F:</b> Wird <b>FlowDirection</b> automatisch basierend auf der aktuellen Sprachauswahl festgelegt? Wenn ich beispielsweise Englisch auswähle, wird dann die Links-nach-rechts-Leserichtung angezeigt, und für Arabisch die Rechts-nach-links-Leserichtung?</p></dt>

  <dd><p><b>A:</b> <b>FlowDirection</b> ist nicht mit einer Berücksichtigung der Sprache verbunden. Sie legen <b>FlowDirection</b> entsprechend für die Sprache fest, die gerade angezeigt wird. Siehe obigen Beispielcode.</p></dd> 

  <dt> <p><b>F:</b> Ich kenne mich mit der Lokalisierung nicht aus. Enthalten die Ressourcen bereits die Flussrichtung? Ist es möglich, die Flussrichtung für die aktuelle Sprache zu bestimmen?</p></dt>

  <dd> <p><b>A:</b> Wenn Sie sich an die derzeitigen bewährten Methoden halten, enthalten die Ressourcen die Flussrichtung nicht direkt. Sie müssen die Flussrichtung für die aktuelle Sprache bestimmen. Hierfür gibt es zwei Möglichkeiten: </p>
   <p>Die bevorzugte Methode ist die Verwendung von LayoutDirection für die oberste bevorzugte Sprache, um die FlowDirection-Eigenschaft für RootFrame festzulegen. Alle Steuerelemente in RootFrame erben „FlowDirection“ vom RootFrame-Element.</p>
   <p>Eine andere Möglichkeit ist das Festlegen von FlowDirection in der RESW-Datei für die Sprachen mit Rechts-nach-links-Leserichtung, für die Sie die Lokalisierung durchführen. Sie können beispielsweise eine arabische RESW-Datei und eine hebräische RESW-Datei verwenden. In diesen Dateien können Sie „x:UID“ zum Festlegen von FlowDirection verwenden. Diese Methode ist aber fehleranfälliger als die programmgesteuerte Methode.</p></dd>
</dl>


## <a name="related-topics"></a>Verwandte Themen
[FlowDirection](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.frameworkelement.flowdirection.aspx)
