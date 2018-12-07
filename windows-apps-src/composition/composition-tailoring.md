---
title: Anpassen der Komposition
description: Verwenden Sie die Composition-APIs zum Anpassen der Benutzeroberfläche, Leistung optimieren und benutzereinstellungen und Geräteeigenschaften anzupassen.
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e6252ce3d2e213602250f6c24f8867767accecbe
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8798013"
---
# <a name="tailoring-effects--experiences-using-windows-ui"></a>Anpassen von Effekten und Funktionen, die über Windows-Benutzeroberfläche

Windows-Benutzeroberfläche bietet viele ansprechender Effekte, Animationen und bedeutet, dass zur Differenzierung. Erfüllen die Erwartungen der Benutzer für die Leistung und anpassbarkeit bietet ist jedoch weiterhin erforderlich Teil erfolgreiche Anwendungen erstellen. Die universelle Windows-Plattform unterstützt eine große, diverse Familie von Geräten, die verschiedenen Features und Funktionen. Um eine inklusive Umgebung für alle Benutzer bereitstellen, müssen Sie sicherzustellen, dass Ihre Anwendung Skalierung auf allen Geräten und Voreinstellungen des Benutzers zu respektieren. Anpassen der Benutzeroberfläche kann eine effiziente Möglichkeit zum Nutzen Funktionen des Geräts und sicherzustellen, dass ein angenehmeres und inklusive Umgebung bereitstellen.

Anpassen der Benutzeroberfläche ist eine allgemeine Kategorie umfassenden Arbeit für eine hohe Leistung schöne UI in Bezug auf den folgenden Bereichen:

- Die Wahrung und zur Anpassung an den benutzereinstellungen für Effekte
- Berücksichtigung von benutzereinstellungen für Animationen
- Optimierung der Benutzeroberfläche für die angegebene Hardwarefunktionen

Hier gehen wir wie Sie die Effekte und Animationen mit der visuellen Ebene in den Bereichen, die oben genannten anpassen können, aber es gibt viele andere Weise Ihrer Anwendung, um sicherzustellen, dass eine hervorragende benutzerumgebung End anpassen. Richtlinien-Dokumente stehen zum [Anpassen die Benutzeroberfläche](/design/layout/screen-sizes-and-breakpoints-for-responsive-design.md) für verschiedene Geräte und [Reaktionsfähigkeit der Benutzeroberfläche zu erstellen](/design/layout/responsive-design.md).

## <a name="user-effects-settings"></a>Effekte benutzereinstellungen

Benutzer können ihre Windows-Umgebung für eine Vielzahl von Gründen anpassen die Anwendungen zu respektieren und anpassen sollten. Um einen Bereich, die Benutzer steuern können ändert sich die Arten von Effekten den, die Benutzern angezeigt werden, wird ihre System verwendet.

### <a name="transparency-effects-settings"></a>Transparenz Effekte Einstellungen

Eine solche Effekt-Einstellung, die Benutzer anpassen können, ist Transparenzeffekten ein-/ausschalten aktivieren. Dies finden Sie in den Einstellungen unter Personalisierung > Farben, oder über die Einstellungs-app > erleichterte Bedienung > Anzeige.

![In den Einstellungen Transparenzfolienoption](images/tailoring-transparency-setting.png)

Wenn aktiviert, wird keine Auswirkungen, die Transparenz verwendet wie erwartet angezeigt. Dies gilt für Acryl, HostBackdropBrush oder alle benutzerdefinierten Effekt-Diagramm, das nicht vollständig undurchsichtig ist.

Wenn deaktiviert, wird Acryl-Material automatisch auf eine Volltonfarbe zurückgreifen, da XAMLs-acrylpinsel standardmäßig das dieses Ereignis überwacht hat. Hier sehen wir die Rechner-app entsprechend zurückgreifen auf eine Volltonfarbe Transparenzeffekten nicht aktiviert werden:

![Rechner mit Acryl](images/tailoring-acrylic.png)
![Rechner mit Acryl Transparenz Einstellungen reagieren](images/tailoring-acrylic-fallback.png)

Für jede benutzerdefinierte Effekte muss die Anwendung auf die [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) -Eigenschaft oder [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) Ereignis zu reagieren und wechseln Sie im Diagramm Effekt-Effekt Sie einen Effekt verwenden, der keine Transparenz festgelegt wurde. Ein Beispiel hierfür finden Sie unten:

```cs
public MainPage()
{
   var uisettings = new UISettings();
   bool advancedEffects = uisettings.AdvancedEffectsEnabled;
   uisettings.AdvancedEffectsEnabledChanged += Uisettings_AdvancedEffectsEnabledChanged;
}

private void Uisettings_AdvancedEffectsEnabledChanged(UISettings sender, object args)
{
    // TODO respond to sender.AdvancedEffectsEnabled
}
```

## <a name="animations-settings"></a>Einstellungen für Animationen

Anwendungen sollten auf ähnliche Weise überwachen und reagieren auf die [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) -Eigenschaft, um sicherzustellen, dass Animationen aktiviert bzw. deaktiviert auf Basis der Benutzer in den Einstellungen > erleichterte Bedienung > Anzeige.

![In den Einstellungen die Option Animationen](images/tailoring-animations-setting.png)

```cs
public MainPage()
{
   var uisettings = new UISettings();
   bool animationsEnabled = uisettings.AnimationsEnabled;
   // TODO respond to animations settings
}

```

## <a name="leveraging-the-capabilities-api"></a>Nutzung der API-Funktionen

Durch die Nutzung der [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, können Sie erkennen, welche Komposition verfügbar und Leistung auf bestimmten Hardware-Funktionen und passen Sie das Design, um sicherzustellen, dass Benutzer eine leistungsfähige und ansprechender Erfahrung auf jedem Gerät abrufen. Die APIs bieten eine Möglichkeit zum Überprüfen der Hardware-Systemfunktionen um ordnungsgemäßes Effekt über eine Vielzahl von Formfaktoren Skalierung zu implementieren. Dies erleichtert die Anwendung eine ansprechende erstellen und die nahtlose End-Benutzeroberfläche entsprechend anpassen.

Diese API stellt Methoden und ein Ereignis-Listener, der Effekt Skalierung Entscheidungen für die Benutzeroberfläche der Anwendung vornehmen verwendet werden kann. Das Feature erkennt, wie gut das System behandeln kann komplexe Komposition und Rendern Vorgänge aus und gibt die Informationen in einem-nutzen-Modell für Entwickler zu nutzen.

### <a name="using-composition-capabilities"></a>Verwendung der Composition-Funktionen

CompositionCapabilities-Funktion ist bereits für die Funktionen wie acrylmaterial, genutzt wird, in denen das Material wieder für eine weitere leistungsfähige Effekt je nach Szenario und Hardware fällt.

Die API kann auf vorhandenen Code in schnell und einfach hinzugefügt werden.

1. Erwerben Sie das Objekt Funktionen im Konstruktor der Anwendung.

    ```cs
    _capabilities = CompositionCapabilities.GetForCurrentView();
    ```

1. Registrieren Sie eine geänderte Funktionen Ereignislistener für Ihre app.

    ```cs
    _capabilities.Changed += HandleCapabilitiesChanged;
    ```

1. Hinzufügen von Inhalten zu Ereignis Callback-Methode zum Behandeln von verschiedenen Funktionen Ebenen. Dies kann oder möglicherweise nicht vergleichbar mit dem nächsten Schritt weiter unten.
1. Wenn Sie Effekte verwenden, überprüfen Sie zunächst das Objekt Funktionen. Erwägen Sie bedingte Überprüfungen oder zum Wechseln von Steuerelement-Anweisungen, je nachdem, wie Sie die Effekte anpassen möchten.

    ```cs
    if (_capabilities.AreEffectsSupported())
    {
        // Add incremental effects updates here

        if (_capabilities.AreEffectsFast())
        {
            // Add more advanced effects here where applicable
        }
    }
    ```

Vollständiger Beispielcode finden Sie auf das [Windows-UI-Github-Repository](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2015063/CompCapabilities).

## <a name="fast-vs-slow-effects"></a>Fast im Vergleich zu langsam Effekte

Anhand des Feedbacks der bereitgestellten [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) und [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) Methoden in der CompositionCapabilities-API, kann die Anwendung entscheiden teuer oder nicht unterstützte Effekte für andere Effekte ihrer Wahl ausgetauscht werden, die optimiert sind für das Gerät. Einige Effekte bekannt ist, dass viele Ressourcen, die als andere rechenintensive konsistent zu sein und sollten sparsam verwendet werden, und andere Effekte können mehr frei verwendet werden. Für alle Effekte sollte jedoch Vorsicht verwendet werden beim Verketten und als einige Szenarien oder Kombinationen Animieren der Leistungsmerkmale des Diagramms Effekt ändern können. Nachfolgend finden Sie einige Faustregel Leistungsmerkmale für einzelne Effekte:

- Effekte, die hohe Leistung auswirken sind wie folgt – Bildbearbeitungstools, Schatten Maske, BackDropBrush, HostBackDropBrush und Visual Layer. Diese werden nicht für low-End-Geräten [(Featureebene 9.1 9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx)empfohlen und sollte überlegt auf high-End-Geräten verwendet werden.
- Mit mittlerer Leistungseinbußen zu den Effekten zählen Farbe Matrix, die bestimmte Blend-Effekt BlendModes (Helligkeit, Farbe, Sättigung und Farbton), SpotLight, SceneLightingEffect und (je nach Szenario) BorderEffect. Diese Effekte mit bestimmten Szenarien auf low-End-Geräten funktionieren, aber achten sollte verwendet werden, wenn verketten und animieren. Empfehlen Sie einschränken der Verwendung auf zwei oder weniger und auf Übergänge nur animieren.
- Alle anderen Effekte wirken sich geringer Leistung und in allen angemessene Szenarien animieren und Verkettung arbeiten.

## <a name="related-articles"></a>Verwandte Artikel

- [UWP-Techniken für reaktionsfähiges Design](https://docs.microsoft.com/windows/uwp/design/layout/responsive-design)
- [UWP Gerät anpassen](https://docs.microsoft.com/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
