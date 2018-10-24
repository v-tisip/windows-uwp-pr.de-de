---
author: daneuber
title: Anpassen der Komposition
description: Verwenden Sie die Composition-APIs zum Anpassen der Benutzeroberfläche, Leistung optimieren und benutzereinstellungen und Geräteeigenschaften anzupassen.
ms.author: jimwalk
ms.date: 07/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 66384c4df3195ae0fff35ae5dd7e1b1983204068
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5440156"
---
# <a name="tailoring-effects--experiences-using-windows-ui"></a><span data-ttu-id="50108-104">Anpassung Effekte und mithilfe der Windows-UI-Erlebnisse</span><span class="sxs-lookup"><span data-stu-id="50108-104">Tailoring effects & experiences using Windows UI</span></span>

<span data-ttu-id="50108-105">Windows-Benutzeroberfläche bietet viele ansprechender Effekte, Animationen und bedeutet, dass zur Differenzierung.</span><span class="sxs-lookup"><span data-stu-id="50108-105">Windows UI provides many beautiful effects, animations, and means for differentiation.</span></span> <span data-ttu-id="50108-106">Erfüllen die Erwartungen der Benutzer für die Leistung und anpassbarkeit bietet ist jedoch weiterhin ein notwendiger Bestandteil erfolgreiche Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="50108-106">However, meeting user expectations for performance and customizability is still a necessary part of creating successful applications.</span></span> <span data-ttu-id="50108-107">Die universelle Windows-Plattform unterstützt eine große, diverse Familie von Geräten, die verschiedenen Features und Funktionen haben.</span><span class="sxs-lookup"><span data-stu-id="50108-107">The Universal Windows Platform supports a large, diverse family of devices, which have different features and capabilities.</span></span> <span data-ttu-id="50108-108">Um eine inklusive Umgebung für alle Ihre Benutzer bereitzustellen, müssen Sie sicherzustellen, dass Ihre Anwendungen Skalieren auf allen Geräten und Voreinstellungen des Benutzers zu respektieren.</span><span class="sxs-lookup"><span data-stu-id="50108-108">In order to provide an inclusive experience for all your users, you need to ensure your applications scale across devices and respect user preferences.</span></span> <span data-ttu-id="50108-109">Benutzeroberfläche anpassen kann eine effiziente Möglichkeit zum Nutzen Funktionen des Geräts und sicherzustellen, dass ein angenehmeres und inklusive Umgebung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="50108-109">UI tailoring can provide an efficient way to leverage a device’s capabilities and ensure a pleasant and inclusive user experience.</span></span>

<span data-ttu-id="50108-110">Anpassen der Benutzeroberfläche ist eine allgemeine Kategorie umfasst Arbeit für eine hohe Leistung schöne UI in Bezug auf den folgenden Bereichen:</span><span class="sxs-lookup"><span data-stu-id="50108-110">UI tailoring is a broad category encompassing work for performant, beautiful UI with respect to the following areas:</span></span>

- <span data-ttu-id="50108-111">Gleichzeitiger Wahrung der und zur Anpassung an den benutzereinstellungen für Effekte</span><span class="sxs-lookup"><span data-stu-id="50108-111">Respecting and adapting to user settings for effects</span></span>
- <span data-ttu-id="50108-112">Mit benutzereinstellungen für Animationen</span><span class="sxs-lookup"><span data-stu-id="50108-112">Accommodating user settings for animations</span></span>
- <span data-ttu-id="50108-113">Optimieren der Benutzeroberfläche für die angegebene Hardwarefunktionen</span><span class="sxs-lookup"><span data-stu-id="50108-113">Optimizing UI for the given hardware capabilities</span></span>

<span data-ttu-id="50108-114">Hier werden wie bei der Gestaltung Ihrer Effekte und Animationen mit der visuellen Ebene in den Bereichen oben behandelt, aber es gibt viele andere Weise bei der Gestaltung Ihrer Anwendung, um eine hervorragende endbenutzererfahrung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="50108-114">Here, we'll cover how to tailor your effects and animations with the Visual Layer in the areas above, but there are many other means to tailor your application to ensure a great end user experience.</span></span> <span data-ttu-id="50108-115">Anleitung Dokumente stehen zum [Anpassen die Benutzeroberfläche](/design/layout/screen-sizes-and-breakpoints-for-responsive-design.md) für verschiedene Geräte und [reaktionsfähige Benutzeroberfläche zu erstellen](/design/layout/responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="50108-115">Guidance docs are available on how to [tailor your UI](/design/layout/screen-sizes-and-breakpoints-for-responsive-design.md) for various devices and [create responsive UI](/design/layout/responsive-design.md).</span></span>

## <a name="user-effects-settings"></a><span data-ttu-id="50108-116">Effekte benutzereinstellungen</span><span class="sxs-lookup"><span data-stu-id="50108-116">User effects settings</span></span>

<span data-ttu-id="50108-117">Benutzer können die Windows-Erfahrung für den unterschiedlichsten Gründen, anpassen, die Anwendungen sollten respektieren und Anpassung an.</span><span class="sxs-lookup"><span data-stu-id="50108-117">Users may customize their Windows experience for a variety of reasons, which applications should respect and adapt to.</span></span> <span data-ttu-id="50108-118">Um einen Bereich, die Endbenutzer steuern können ändert sich die Arten von Effekten den, die Benutzern angezeigt werden, wird ihre System verwendet.</span><span class="sxs-lookup"><span data-stu-id="50108-118">One area end users can control is changing the types of effects they see used throughout their system.</span></span>

### <a name="transparency-effects-settings"></a><span data-ttu-id="50108-119">Transparenz Effekte Einstellungen</span><span class="sxs-lookup"><span data-stu-id="50108-119">Transparency effects settings</span></span>

<span data-ttu-id="50108-120">Eine solche Effekt-Einstellung, die Benutzer anpassen können ist Transparenzeffekten ein-/ausschalten aktivieren.</span><span class="sxs-lookup"><span data-stu-id="50108-120">One such effect setting users can customize is turning transparency effects on/off.</span></span> <span data-ttu-id="50108-121">Dies finden Sie in den Einstellungen unter Personalisierung > Farben, oder über die Einstellungs-app > erleichterte Bedienung > Anzeige.</span><span class="sxs-lookup"><span data-stu-id="50108-121">This can be found in the Settings app under Personalization > Colors, or through Settings app > Ease of Access > Display.</span></span>

![Transparenzfolienoption unter "Einstellungen"](images/tailoring-transparency-setting.png)

<span data-ttu-id="50108-123">Wenn aktiviert, wird keine Auswirkung, die Transparenz verwendet wie erwartet angezeigt.</span><span class="sxs-lookup"><span data-stu-id="50108-123">When turned on, any effect that uses transparency will appear as expected.</span></span> <span data-ttu-id="50108-124">Dies gilt für Acryl, HostBackdropBrush oder alle benutzerdefinierten effektgraphen entnommen, die nicht vollständig undurchsichtig ist.</span><span class="sxs-lookup"><span data-stu-id="50108-124">This applies to Acrylic, HostBackdropBrush, or any custom effect graph that is not fully opaque.</span></span>

<span data-ttu-id="50108-125">Wenn diese Option deaktiviert, wird Acryl-Material automatisch mit einer Volltonfarbe anzuzeigen zurückgreifen, da des XAML-acrylpinsel standardmäßig das dieses Ereignis überwacht hat.</span><span class="sxs-lookup"><span data-stu-id="50108-125">When turned off, acrylic material will automatically fall back to a solid color because XAML's acrylic brush has listened to this event by default.</span></span> <span data-ttu-id="50108-126">Hier sehen wir die Rechner-app entsprechend zurückgreifen auf eine Volltonfarbe Transparenzeffekten nicht aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="50108-126">Here, we see the calculator app appropriately falling back to a solid color when transparency effects are not enabled:</span></span>

![<span data-ttu-id="50108-127">Rechner mit Acryl](images/tailoring-acrylic.png)
![Rechner mit Acryl reagieren auf Transparenz Einstellungen</span><span class="sxs-lookup"><span data-stu-id="50108-127">Calculator with Acrylic](images/tailoring-acrylic.png)
![Calculator with Acrylic Responding to Transparency Settings</span></span>](images/tailoring-acrylic-fallback.png)

<span data-ttu-id="50108-128">Für jede benutzerdefinierte Effekte muss die Anwendung auf die [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) Eigenschaft oder [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) Ereignis zu reagieren und wechseln Sie den Effekt-Effekt Graph für einen Effekt verwenden, der keine Transparenz festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="50108-128">However, for any custom effects the application needs to respond to the [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) property or [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) event and switch out the effect/effect graph to use an effect that has no transparency.</span></span> <span data-ttu-id="50108-129">Ein Beispiel hierfür finden Sie unten:</span><span class="sxs-lookup"><span data-stu-id="50108-129">An example of this is below:</span></span>

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

## <a name="animations-settings"></a><span data-ttu-id="50108-130">Animationen Einstellungen</span><span class="sxs-lookup"><span data-stu-id="50108-130">Animations settings</span></span>

<span data-ttu-id="50108-131">Anwendungen sollten auf ähnliche Weise überwachen und reagieren auf die [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) -Eigenschaft, um sicherzustellen, dass Animationen aktiviert bzw. deaktiviert basierend auf benutzereinstellungen unter "Einstellungen" > erleichterte Bedienung > Anzeige.</span><span class="sxs-lookup"><span data-stu-id="50108-131">Similarly, applications should listen and respond to the [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) property to ensure animations are turned on or off based on user settings in Settings > Ease of Access > Display.</span></span>

![Animationen Option unter "Einstellungen"](images/tailoring-animations-setting.png)

```cs
public MainPage()
{
   var uisettings = new UISettings();
   bool animationsEnabled = uisettings.AnimationsEnabled;
   // TODO respond to animations settings
}

```

## <a name="leveraging-the-capabilities-api"></a><span data-ttu-id="50108-133">Nutzung der API-Funktionen</span><span class="sxs-lookup"><span data-stu-id="50108-133">Leveraging the capabilities API</span></span>

<span data-ttu-id="50108-134">Durch die Nutzung der [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, können Sie erkennen, bietet die Komposition verfügbar sind und Leistung auf die angegebene Hardware und passen Sie das Design, um sicherzustellen, dass Endbenutzer eine leistungsfähige und ansprechender Erfahrung auf jedem Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="50108-134">By leveraging the [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, you can detect which composition features are available and performant on given hardware and tailor the design to ensure end users get a performant and beautiful experience on any device.</span></span> <span data-ttu-id="50108-135">Die APIs bieten eine Möglichkeit zum Überprüfen der Hardware System Erstellungsfunktionen, um ein ordnungsgemäßes Effekt über eine Vielzahl von Formfaktoren Skalierung zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="50108-135">The APIs provide a means to check hardware system capabilities in order to implement graceful effect scaling across a variety of form factors.</span></span> <span data-ttu-id="50108-136">Dies erleichtert Ihnen die Anwendung, um ein schöner erstellen und die nahtlose endbenutzererfahrung entsprechend anpassen.</span><span class="sxs-lookup"><span data-stu-id="50108-136">This makes it easy to appropriately tailor the application to create a beautiful and seamless end user experience.</span></span>

<span data-ttu-id="50108-137">Diese API stellt Methoden und ein Klickereignis-Listener, der Effekt Skalierung Entscheidungen für die Anwendung UI vornehmen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="50108-137">This API provides methods and an event listener that can be used to make effect scaling decisions for the application UI.</span></span> <span data-ttu-id="50108-138">Das Feature erkennt, wie gut die System komplexe Komposition und rendering Vorgänge verarbeiten kann aus und gibt die Informationen in einem-nutzen-Modell für Entwickler zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="50108-138">The feature detects how well the system can handle complex composition and rendering operations and then returns the information in an easy-to-consume model for developers to utilize.</span></span>

### <a name="using-composition-capabilities"></a><span data-ttu-id="50108-139">Verwendung der Composition-Funktionen</span><span class="sxs-lookup"><span data-stu-id="50108-139">Using composition capabilities</span></span>

<span data-ttu-id="50108-140">Die CompositionCapabilities-Funktionalität wird bereits für Funktionen wie acrylmaterial, genutzt wird, in denen das Material Fallback für eine weitere leistungsfähige Effekt je nach Szenario und Hardware erfolgt.</span><span class="sxs-lookup"><span data-stu-id="50108-140">The CompositionCapabilities functionality is already being leveraged for features like Acrylic material, where the material falls back to a more performant effect depending on the scenario and hardware.</span></span>

<span data-ttu-id="50108-141">Die API kann auf vorhandenen Code in einigen einfachen Schritten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="50108-141">The API can be added to existing code in a few easy steps.</span></span>

1. <span data-ttu-id="50108-142">Das Objekt Funktionen in Ihrer Anwendung Konstruktor zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="50108-142">Acquire the capabilities object in your application’s constructor.</span></span>

    ```cs
    _capabilities = CompositionCapabilities.GetForCurrentView();
    ```

1. <span data-ttu-id="50108-143">Registrieren Sie eine geänderte Funktionen Ereignislistener für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="50108-143">Register a capabilities changed event listener for your app.</span></span>

    ```cs
    _capabilities.Changed += HandleCapabilitiesChanged;
    ```

1. <span data-ttu-id="50108-144">Hinzufügen von Inhalten zu Ereignis Callback-Methode zum Behandeln von verschiedenen Funktionen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="50108-144">Add content to the event callback method to handle various capabilities levels.</span></span> <span data-ttu-id="50108-145">Dies kann oder möglicherweise nicht vergleichbar mit dem nächsten Schritt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="50108-145">This may or may not be similar to the next step below.</span></span>
1. <span data-ttu-id="50108-146">Wenn Sie Effekte verwenden, überprüfen Sie zunächst das Objekt Funktionen.</span><span class="sxs-lookup"><span data-stu-id="50108-146">When using effects, check the capabilities object first.</span></span> <span data-ttu-id="50108-147">Wechseln Sie Steuerelement eine Anweisung, je nachdem, wie Sie die Effekte anpassen möchten, oder bedingte Überprüfungen in Betracht.</span><span class="sxs-lookup"><span data-stu-id="50108-147">Consider using conditional checks or switch control statements, depending on how you want to tailor the effects.</span></span>

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

<span data-ttu-id="50108-148">Vollständiger Beispielcode finden Sie auf das [Windows-UI-Github-Repository](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2015063/CompCapabilities).</span><span class="sxs-lookup"><span data-stu-id="50108-148">Full example code can be found on the [Windows UI Github repo](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2015063/CompCapabilities).</span></span>

## <a name="fast-vs-slow-effects"></a><span data-ttu-id="50108-149">Fast im Vergleich zu langsam Effekte</span><span class="sxs-lookup"><span data-stu-id="50108-149">Fast vs. slow effects</span></span>

<span data-ttu-id="50108-150">Anhand des Feedbacks der bereitgestellten Methoden [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) und [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) in der CompositionCapabilties-API, kann die Anwendung entscheiden teuer oder nicht unterstützte Effekte für andere Effekte ihrer Wahl ausgetauscht, die optimiert sind für das Gerät.</span><span class="sxs-lookup"><span data-stu-id="50108-150">Based on feedback from the provided [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) and [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) methods in the CompositionCapabilties API, the application can decide to swap expensive or unsupported effects for other effects of their choice that are optimized for the device.</span></span> <span data-ttu-id="50108-151">Einige Effekte bekannt ist, dass viele Ressourcen, die als andere rechenintensive konsistent sein und sollten sparsam verwendet werden, und andere Effekte können mehr frei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="50108-151">Some effects are known to consistently be more resource intensive than others and should be used sparingly, and other effects can be used more freely.</span></span> <span data-ttu-id="50108-152">Für alle Effekte sollte jedoch Vorsicht verwendet werden beim Verketten und als einige Szenarien oder Kombinationen Animieren der Leistungsmerkmale effektgraphen entnommen ändern können.</span><span class="sxs-lookup"><span data-stu-id="50108-152">For all effects, however, care should be used when chaining and animating as some scenarios or combinations may change the performance characteristics of the effect graph.</span></span> <span data-ttu-id="50108-153">Nachfolgend finden Sie einige Faustregel Leistungsmerkmale für einzelne Effekte:</span><span class="sxs-lookup"><span data-stu-id="50108-153">Below are some rule of thumb performance characteristics for individual effects:</span></span>

- <span data-ttu-id="50108-154">Effekte, die bekanntermaßen mit hoher Leistung auswirken sind wie folgt – Bildbearbeitungstools, Schatten Maske, BackDropBrush, HostBackDropBrush und Visual Layer.</span><span class="sxs-lookup"><span data-stu-id="50108-154">Effects that are known to have high performance impact are as follows – Gaussian Blur, Shadow Mask, BackDropBrush, HostBackDropBrush, and Layer Visual.</span></span> <span data-ttu-id="50108-155">Diese werden nicht für low-End-Geräten [(Featureebene 9.1-9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx)empfohlen und sollte überlegt auf high-End-Geräten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="50108-155">These are not recommended for low end devices [(feature level 9.1-9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx), and should be used judiciously on high end devices.</span></span>
- <span data-ttu-id="50108-156">Mit mittlerer Leistungseinbußen zu den Effekten zählen Farbe Matrix, die bestimmte Blend-Effekt BlendModes (Helligkeit, Farbe, Sättigung und Farbton), SpotLight, SceneLightingEffect und (je nach Szenario) BorderEffect.</span><span class="sxs-lookup"><span data-stu-id="50108-156">Effects with medium performance impact include Color Matrix, certain Blend Effect BlendModes (Luminosity, Color, Saturation, and Hue), SpotLight, SceneLightingEffect, and (depending on scenario) BorderEffect.</span></span> <span data-ttu-id="50108-157">Diese Effekte mit bestimmten Szenarien auf low-End-Geräten funktionieren, aber Vorsicht sollte verwendet werden, wenn das Verketten und animieren.</span><span class="sxs-lookup"><span data-stu-id="50108-157">These effects may work with certain scenarios on low end devices, but care should be used when chaining and animating.</span></span> <span data-ttu-id="50108-158">Empfehlen Sie einschränken der Verwendung auf zwei oder weniger und auf Übergänge nur animieren.</span><span class="sxs-lookup"><span data-stu-id="50108-158">Recommend restricting use to two or less and animating on transitions only.</span></span>
- <span data-ttu-id="50108-159">Andere Effekte wirken sich die niedrige Leistung und in allen angemessene Szenarien beim animieren und Verkettung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="50108-159">All other effects have low performance impact and work in all reasonable scenarios when animating and chaining.</span></span>

## <a name="related-articles"></a><span data-ttu-id="50108-160">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="50108-160">Related articles</span></span>

- [<span data-ttu-id="50108-161">Reaktionsfähige Designtechniken UWP</span><span class="sxs-lookup"><span data-stu-id="50108-161">UWP Responsive Design Techniques</span></span>](https://docs.microsoft.com/windows/uwp/design/layout/responsive-design)
- [<span data-ttu-id="50108-162">UWP Gerät anpassen</span><span class="sxs-lookup"><span data-stu-id="50108-162">UWP Device Tailoring</span></span>](https://docs.microsoft.com/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
