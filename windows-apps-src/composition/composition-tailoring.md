---
title: Komposition anpassen
description: Verwenden Sie die Composition-APIs zum Anpassen der Benutzeroberfläche für Leistung optimieren und benutzereinstellungen und Geräteeigenschaften anzupassen.
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: bcc9a6d89a143d8fd03d73dbd83b832ed9513ee2
ms.sourcegitcommit: b975c8fc8cf0770dd73d8749733ae5636f2ee296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9058711"
---
# <a name="tailoring-effects--experiences-using-windows-ui"></a>Kollatierungsanpassung Effekte & spielumgebungen mit Windows-Benutzeroberfläche

Windows-Benutzeroberfläche bietet viele ansprechender Effekte, Animationen und bedeutet, dass zur Differenzierung. Benutzer für die Leistung und anpassbarkeit bietet erfüllen ist jedoch weiterhin ein notwendiger Bestandteil erfolgreiche Anwendungen erstellen. Die universelle Windows-Plattform unterstützt eine große, diverse Familie von Geräten, die verschiedenen Features und Funktionen. Um eine inklusive Umgebung für alle Ihre Benutzer bereitzustellen, müssen Sie sicherzustellen, dass Ihre Anwendung Skalieren auf allen Geräten und Voreinstellungen des Benutzers zu respektieren. Anpassen der Benutzeroberfläche kann eine effiziente Möglichkeit zum Nutzen Funktionen des Geräts und sicherzustellen, dass ein angenehmeres und inklusive Umgebung bereitstellen.

Anpassen der Benutzeroberfläche ist eine allgemeine Kategorie umfassenden Arbeit für eine hohe Leistung schöne UI in Bezug auf den folgenden Bereichen:

- Die Wahrung und zur Anpassung an den benutzereinstellungen für Effekte
- Mit benutzereinstellungen für Animationen
- Optimierung der Benutzeroberfläche für die angegebene Hardwarefunktionen

Hier werden wie bei der Gestaltung Ihrer Effekte und Animationen mit der visuellen Ebene in den Bereichen oben behandelt, aber es gibt viele andere Weise bei der Gestaltung Ihrer Anwendung, um sicherzustellen, dass eine hervorragende benutzerumgebung Ende. Richtlinien-Dokumente stehen zum [Anpassen die Benutzeroberfläche](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) für verschiedene Geräte und [Reaktionsfähigkeit der Benutzeroberfläche zu erstellen](/windows/uwp/design/layout/responsive-design).

## <a name="user-effects-settings"></a>Effekte benutzereinstellungen

Benutzer können die Windows-Erfahrung für den unterschiedlichsten Gründen, anpassen, die Anwendungen sollten respektieren und Anpassung an. Um einen Bereich, die Endbenutzer steuern können ändert sich die Arten von Effekten den, die Benutzern angezeigt werden, wird ihre System verwendet.

### <a name="transparency-effects-settings"></a>Transparenz Effekte Einstellungen

Eine solche Effekt-Einstellung, die Benutzer anpassen können, ist Transparenzeffekten ein-/ausschalten aktivieren. Dies kann in den Einstellungen unter Personalisierung > Farben oder über Einstellungen app > erleichterte Bedienung > Anzeige gefunden werden.

![Option "Transparenz" unter "Einstellungen"](images/tailoring-transparency-setting.png)

Wenn aktiviert, wird keine Auswirkungen, die Transparenz verwendet wie erwartet angezeigt. Dies gilt für Acryl, HostBackdropBrush oder alle benutzerdefinierten Effekt-Diagramm, das nicht vollständig deckend ist.

Wenn deaktiviert, wird Acryl-Material automatisch mit einer Volltonfarbe anzuzeigen zurückgreifen, da des XAML-acrylpinsel standardmäßig das dieses Ereignis überwacht hat. Hier sehen wir die Rechner-app entsprechend zurückgreifen auf eine Volltonfarbe Transparenzeffekten nicht aktiviert werden:

![Rechner mit Acryl](images/tailoring-acrylic.png)
![Rechner mit Acryl, die Reaktion auf Transparenz-Einstellungen](images/tailoring-acrylic-fallback.png)

Jedoch muss die Anwendung für jede benutzerdefinierte Effekte auf die [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) -Eigenschaft oder [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) -Ereignis zu reagieren und wechseln Sie den Effekt/effektgraphen entnommen Sie einen Effekt verwenden, der keine Transparenz festgelegt wurde. Ein Beispiel hierfür finden Sie unten:

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

## <a name="animations-settings"></a>Animationen Einstellungen

Anwendungen sollten auf ähnliche Weise überwachen und reagieren auf die [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) -Eigenschaft, um sicherzustellen, dass Animationen auf oder basierend auf benutzereinstellungen in Einstellungen > erleichterte Bedienung > Anzeige deaktiviert sind.

![Animationen Option unter "Einstellungen"](images/tailoring-animations-setting.png)

```cs
public MainPage()
{
   var uisettings = new UISettings();
   bool animationsEnabled = uisettings.AnimationsEnabled;
   // TODO respond to animations settings
}

```

## <a name="leveraging-the-capabilities-api"></a>Nutzung der API-Funktionen

Durch die Nutzung der [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, können Sie erkennen, welche Komposition verfügbar sind und Leistung auf die angegebene Hardware-Funktionen und passen Sie das Design, um sicherzustellen, dass Endbenutzer eine leistungsfähige und ansprechender Erfahrung auf jedem Gerät abrufen. Die APIs bieten eine Möglichkeit zum Überprüfen der Hardware-Systemfunktionen um ordnungsgemäßes Effekt über eine Vielzahl von verschiedenen Formfaktoren Skalierung zu implementieren. Dies erleichtert Ihnen die Anwendung, um ein schöner erstellen und die nahtlose endbenutzererfahrung entsprechend anpassen.

Diese API stellt Methoden und ein Ereignis-Listener, der durchgeführt werden kann, Effekt Skalierung Entscheidungen für die Benutzeroberfläche der Anwendung. Das Feature erkennt, wie gut das System komplexen Komposition und Rendern Vorgänge verarbeiten kann und dann die Informationen in einem-nutzen-Modell für Entwickler nutzen.

### <a name="using-composition-capabilities"></a>Komposition Funktionen verwenden

Die CompositionCapabilities-Funktionalität wird bereits für Funktionen wie acrylmaterial, genutzt wird, in denen das Material wieder für eine weitere leistungsfähige Effekt je nach Szenario und Hardware fällt.

Die API kann auf vorhandenen Code in einigen einfachen Schritten hinzugefügt werden.

1. Erwerben Sie das Objekt Funktionen in Ihrer Anwendung-Konstruktor.

    ```cs
    _capabilities = CompositionCapabilities.GetForCurrentView();
    ```

1. Registrieren Sie eine geänderte Funktionen Ereignislistener für Ihre app.

    ```cs
    _capabilities.Changed += HandleCapabilitiesChanged;
    ```

1. Hinzufügen von Inhalten zu Ereignis Rückrufmethode in verschiedenen Funktionen Ebenen zu behandeln. Dies kann nicht sein oder mit dem nächsten Schritt unten ähnlich.
1. Wenn Sie Effekte verwenden, überprüfen Sie zunächst das Objekt Funktionen. In Betracht, bedingte Überprüfungen oder zum Wechseln von Steuerelement-Anweisungen, je nachdem, wie Sie die Effekte anpassen möchten.

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

Anhand des Feedbacks der bereitgestellten [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) und [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) Methoden in der CompositionCapabilities-API, können die Anwendung teuer oder nicht unterstützte Effekte für andere Effekte ihrer Wahl ausgetauscht werden, die optimiert sind für das Gerät. Einige Effekte sind bekanntermaßen konsistent Weitere Ressourcen-intensiv als andere und sollten sparsam verwendet werden, und andere Effekte können mehr frei verwendet werden. Für alle Effekte sollte jedoch Vorsicht verwendet werden beim Verketten und als einige Szenarien oder Kombinationen Animieren der Leistungsmerkmale des Diagramms Effekt ändern können. Unten sind einige Faustregel Leistungsmerkmale für einzelne Effekte:

- Effekte, die bekanntermaßen mit hoher Leistung auswirken sind wie folgt – Bildbearbeitungstools, Schatten Maske, BackDropBrush, HostBackDropBrush und Visual Layer. Diese werden nicht für low-End-Geräten [(Featureebene 9.1-9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx)empfohlen und sollte überlegt auf high-End-Geräten verwendet werden.
- Effekte mit mittlerer Leistungseinbußen enthalten bestimmte Blend-Effekt BlendModes (Helligkeit, Farbe, Sättigung und Farbton), Farbe Matrix SpotLight SceneLightingEffect und (je nach Szenario) BorderEffect. Diese Effekte mit bestimmten Szenarien auf low-End-Geräten funktionieren, aber achten sollte verwendet werden, wenn verketten und animieren. Empfehlen Sie einschränken der Verwendung auf zwei oder weniger auf Übergänge nur animieren.
- Alle anderen Effekte geringe Leistung auswirken und in allen angemessene Szenarien beim animieren und Verkettung arbeiten.

## <a name="related-articles"></a>Verwandte Artikel

- [UWP-Techniken für reaktionsfähiges Design](https://docs.microsoft.com/windows/uwp/design/layout/responsive-design)
- [UWP Gerät anpassen](https://docs.microsoft.com/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
