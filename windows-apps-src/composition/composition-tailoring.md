---
author: daneuber
title: Anpassen der Komposition
description: Verwenden Sie die Composition-APIs zum Anpassen der Benutzeroberfläche für Leistung optimieren und benutzereinstellungen und Geräteeigenschaften anzupassen.
ms.author: jimwalk
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2efea81f3520e6fb1a797394656587d2a29201aa
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5862799"
---
# <a name="tailoring-effects--experiences-using-windows-ui"></a><span data-ttu-id="bff0f-104">Anpassung Effekte und Erlebnisse mit Windows-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="bff0f-104">Tailoring effects & experiences using Windows UI</span></span>

<span data-ttu-id="bff0f-105">Windows-Benutzeroberfläche bietet viele ansprechender Effekte, Animationen und bedeutet, dass zur Differenzierung.</span><span class="sxs-lookup"><span data-stu-id="bff0f-105">Windows UI provides many beautiful effects, animations, and means for differentiation.</span></span> <span data-ttu-id="bff0f-106">Erfüllen die Erwartungen der Benutzer für die Leistung und anpassbarkeit bietet ist jedoch weiterhin ein notwendiger Bestandteil erfolgreiche Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-106">However, meeting user expectations for performance and customizability is still a necessary part of creating successful applications.</span></span> <span data-ttu-id="bff0f-107">Die universelle Windows-Plattform unterstützt eine große, diverse Familie von Geräten, die verschiedenen Features und Funktionen haben.</span><span class="sxs-lookup"><span data-stu-id="bff0f-107">The Universal Windows Platform supports a large, diverse family of devices, which have different features and capabilities.</span></span> <span data-ttu-id="bff0f-108">Um eine inklusive Umgebung für all Ihre Benutzer bereitstellen, müssen Sie Ihre Anwendung Skalierung auf allen Geräten gewährleisten und Voreinstellungen des Benutzers zu respektieren.</span><span class="sxs-lookup"><span data-stu-id="bff0f-108">In order to provide an inclusive experience for all your users, you need to ensure your applications scale across devices and respect user preferences.</span></span> <span data-ttu-id="bff0f-109">Anpassen der Benutzeroberfläche kann eine effiziente Möglichkeit zum Nutzen Funktionen des Geräts und sicherzustellen, dass ein angenehmeres und inklusive Umgebung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-109">UI tailoring can provide an efficient way to leverage a device’s capabilities and ensure a pleasant and inclusive user experience.</span></span>

<span data-ttu-id="bff0f-110">Anpassen der Benutzeroberfläche ist eine allgemeine Kategorie umfassenden Arbeit für eine hohe Leistung ansprechender Benutzeroberflächen in Bezug auf den folgenden Bereichen:</span><span class="sxs-lookup"><span data-stu-id="bff0f-110">UI tailoring is a broad category encompassing work for performant, beautiful UI with respect to the following areas:</span></span>

- <span data-ttu-id="bff0f-111">Die Wahrung und zur Anpassung an den benutzereinstellungen für Effekte</span><span class="sxs-lookup"><span data-stu-id="bff0f-111">Respecting and adapting to user settings for effects</span></span>
- <span data-ttu-id="bff0f-112">Berücksichtigung von benutzereinstellungen für Animationen</span><span class="sxs-lookup"><span data-stu-id="bff0f-112">Accommodating user settings for animations</span></span>
- <span data-ttu-id="bff0f-113">Optimieren der Benutzeroberfläche für die angegebene Hardwarefunktionen</span><span class="sxs-lookup"><span data-stu-id="bff0f-113">Optimizing UI for the given hardware capabilities</span></span>

<span data-ttu-id="bff0f-114">Hier gehen wir wie Sie die Effekte und Animationen mit der visuellen Ebene in den oben genannten Bereichen anpassen können, aber es gibt viele andere Weise Ihrer Anwendung, um sicherzustellen, dass eine hervorragende endbenutzererfahrung anpassen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-114">Here, we'll cover how to tailor your effects and animations with the Visual Layer in the areas above, but there are many other means to tailor your application to ensure a great end user experience.</span></span> <span data-ttu-id="bff0f-115">Anleitung Dokumente stehen zum [Anpassen die Benutzeroberfläche](/design/layout/screen-sizes-and-breakpoints-for-responsive-design.md) für verschiedene Geräte und [Reaktionsfähigkeit der Benutzeroberfläche zu erstellen](/design/layout/responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="bff0f-115">Guidance docs are available on how to [tailor your UI](/design/layout/screen-sizes-and-breakpoints-for-responsive-design.md) for various devices and [create responsive UI](/design/layout/responsive-design.md).</span></span>

## <a name="user-effects-settings"></a><span data-ttu-id="bff0f-116">Benutzereinstellungen Effekte</span><span class="sxs-lookup"><span data-stu-id="bff0f-116">User effects settings</span></span>

<span data-ttu-id="bff0f-117">Benutzer möglicherweise ihrer Windows-Erfahrung für den unterschiedlichsten Gründen, anpassen, die Anwendungen zu respektieren und auf angepasst werden sollten.</span><span class="sxs-lookup"><span data-stu-id="bff0f-117">Users may customize their Windows experience for a variety of reasons, which applications should respect and adapt to.</span></span> <span data-ttu-id="bff0f-118">Um einen Bereich, die Endbenutzer steuern können ändert sich die Arten von Effekten den, die Benutzern angezeigt werden, wird ihre System verwendet.</span><span class="sxs-lookup"><span data-stu-id="bff0f-118">One area end users can control is changing the types of effects they see used throughout their system.</span></span>

### <a name="transparency-effects-settings"></a><span data-ttu-id="bff0f-119">Transparenz Effekte Einstellungen</span><span class="sxs-lookup"><span data-stu-id="bff0f-119">Transparency effects settings</span></span>

<span data-ttu-id="bff0f-120">Eine solche Effekt-Einstellung, die Benutzer anpassen können ist Transparenzeffekten ein-/ausschalten aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bff0f-120">One such effect setting users can customize is turning transparency effects on/off.</span></span> <span data-ttu-id="bff0f-121">Dies finden Sie in den Einstellungen unter Personalisierung > Farben, oder über eine app Einstellungen > erleichterte Bedienung > Anzeige.</span><span class="sxs-lookup"><span data-stu-id="bff0f-121">This can be found in the Settings app under Personalization > Colors, or through Settings app > Ease of Access > Display.</span></span>

![Option "Transparenz" unter "Einstellungen"](images/tailoring-transparency-setting.png)

<span data-ttu-id="bff0f-123">Wenn aktiviert, wird keine Auswirkung, die Transparenz verwendet wie erwartet angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bff0f-123">When turned on, any effect that uses transparency will appear as expected.</span></span> <span data-ttu-id="bff0f-124">Dies gilt für Acryl, HostBackdropBrush oder alle benutzerdefinierten Effekt-Diagramm, das nicht vollständig deckend ist.</span><span class="sxs-lookup"><span data-stu-id="bff0f-124">This applies to Acrylic, HostBackdropBrush, or any custom effect graph that is not fully opaque.</span></span>

<span data-ttu-id="bff0f-125">Wenn deaktiviert, wird Acryl-Material automatisch auf eine Volltonfarbe zurückgreifen da des XAML-acrylpinsel standardmäßig das dieses Ereignis überwacht hat.</span><span class="sxs-lookup"><span data-stu-id="bff0f-125">When turned off, acrylic material will automatically fall back to a solid color because XAML's acrylic brush has listened to this event by default.</span></span> <span data-ttu-id="bff0f-126">Hier sehen wir die Rechner-app entsprechend zurückgreifen auf eine Volltonfarbe Transparenzeffekten nicht aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="bff0f-126">Here, we see the calculator app appropriately falling back to a solid color when transparency effects are not enabled:</span></span>

![<span data-ttu-id="bff0f-127">Rechner mit Acryl](images/tailoring-acrylic.png)
![Rechner mit Acryl Transparenz Einstellungen reagieren</span><span class="sxs-lookup"><span data-stu-id="bff0f-127">Calculator with Acrylic](images/tailoring-acrylic.png)
![Calculator with Acrylic Responding to Transparency Settings</span></span>](images/tailoring-acrylic-fallback.png)

<span data-ttu-id="bff0f-128">Allerdings muss die Anwendung für jede benutzerdefinierte Effekte auf die [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) Eigenschaft oder [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) Ereignis zu reagieren, und wechseln Sie den Effekt-Effekt Graph für einen Effekt verwenden, der keine Transparenz festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="bff0f-128">However, for any custom effects the application needs to respond to the [UISettings.AdvancedEffectsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) property or [AdvancedEffectsEnabledChanged](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.advancedeffectsenabledchanged) event and switch out the effect/effect graph to use an effect that has no transparency.</span></span> <span data-ttu-id="bff0f-129">Ein Beispiel hierfür finden Sie unten:</span><span class="sxs-lookup"><span data-stu-id="bff0f-129">An example of this is below:</span></span>

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

## <a name="animations-settings"></a><span data-ttu-id="bff0f-130">Animationen Einstellungen</span><span class="sxs-lookup"><span data-stu-id="bff0f-130">Animations settings</span></span>

<span data-ttu-id="bff0f-131">Anwendungen sollten auf ähnliche Weise überwachen und reagieren auf die [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) -Eigenschaft, um sicherzustellen, dass Animationen aktiviert bzw. deaktiviert basierend auf benutzereinstellungen unter "Einstellungen" > erleichterte Bedienung > Anzeige.</span><span class="sxs-lookup"><span data-stu-id="bff0f-131">Similarly, applications should listen and respond to the [UISettings.AnimationsEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.uisettings.animationsenabled) property to ensure animations are turned on or off based on user settings in Settings > Ease of Access > Display.</span></span>

![Animationen Option unter "Einstellungen"](images/tailoring-animations-setting.png)

```cs
public MainPage()
{
   var uisettings = new UISettings();
   bool animationsEnabled = uisettings.AnimationsEnabled;
   // TODO respond to animations settings
}

```

## <a name="leveraging-the-capabilities-api"></a><span data-ttu-id="bff0f-133">Nutzung der API-Funktionen</span><span class="sxs-lookup"><span data-stu-id="bff0f-133">Leveraging the capabilities API</span></span>

<span data-ttu-id="bff0f-134">Durch die Nutzung der [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, können Sie features der Komposition verfügbar sind und Leistung auf bestimmten Hardware erkennen und passen Sie das Design, um sicherzustellen, dass Endbenutzer eine leistungsfähige und ansprechender Erfahrung auf jedem Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-134">By leveraging the [CompositionCapabilities](/uwp/api/windows.ui.composition.compositioncapabilities) APIs, you can detect which composition features are available and performant on given hardware and tailor the design to ensure end users get a performant and beautiful experience on any device.</span></span> <span data-ttu-id="bff0f-135">Die APIs bieten eine Möglichkeit zum Überprüfen der Hardware System Erstellungsfunktionen, um ein ordnungsgemäßes Effekt über eine Vielzahl von verschiedenen Formfaktoren Skalierung zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="bff0f-135">The APIs provide a means to check hardware system capabilities in order to implement graceful effect scaling across a variety of form factors.</span></span> <span data-ttu-id="bff0f-136">Dies erleichtert die Anwendung ein schöner erstellen und die nahtlose endbenutzererfahrung entsprechend anpassen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-136">This makes it easy to appropriately tailor the application to create a beautiful and seamless end user experience.</span></span>

<span data-ttu-id="bff0f-137">Diese API stellt Methoden und ein Ereignis-Listener, der Effekt Skalierung Entscheidungen für die Benutzeroberfläche der Anwendung vornehmen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="bff0f-137">This API provides methods and an event listener that can be used to make effect scaling decisions for the application UI.</span></span> <span data-ttu-id="bff0f-138">Das Feature erkennt, wie gut das System behandeln kann komplexe Komposition und Rendern Vorgänge aus und gibt die Informationen in einem-nutzen-Modell für Entwickler zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-138">The feature detects how well the system can handle complex composition and rendering operations and then returns the information in an easy-to-consume model for developers to utilize.</span></span>

### <a name="using-composition-capabilities"></a><span data-ttu-id="bff0f-139">Verwendung der Composition-Funktionen</span><span class="sxs-lookup"><span data-stu-id="bff0f-139">Using composition capabilities</span></span>

<span data-ttu-id="bff0f-140">Die CompositionCapabilities-Funktionalität wird bereits für Funktionen wie acrylmaterial, genutzt wird, in denen das Material Fallback für eine weitere leistungsfähige Effekt je nach Szenario und Hardware erfolgt.</span><span class="sxs-lookup"><span data-stu-id="bff0f-140">The CompositionCapabilities functionality is already being leveraged for features like Acrylic material, where the material falls back to a more performant effect depending on the scenario and hardware.</span></span>

<span data-ttu-id="bff0f-141">Die API kann auf vorhandenen Code in einigen einfachen Schritten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bff0f-141">The API can be added to existing code in a few easy steps.</span></span>

1. <span data-ttu-id="bff0f-142">Das Objekt Funktionen in Ihrer Anwendung Konstruktor zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="bff0f-142">Acquire the capabilities object in your application’s constructor.</span></span>

    ```cs
    _capabilities = CompositionCapabilities.GetForCurrentView();
    ```

1. <span data-ttu-id="bff0f-143">Registrieren Sie eine geänderte Funktionen Ereignislistener für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="bff0f-143">Register a capabilities changed event listener for your app.</span></span>

    ```cs
    _capabilities.Changed += HandleCapabilitiesChanged;
    ```

1. <span data-ttu-id="bff0f-144">Hinzufügen von Inhalten zu dem Ereignis Callback-Methode zum Behandeln von verschiedenen Funktionen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-144">Add content to the event callback method to handle various capabilities levels.</span></span> <span data-ttu-id="bff0f-145">Dies kann oder möglicherweise nicht vergleichbar mit dem nachfolgenden Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="bff0f-145">This may or may not be similar to the next step below.</span></span>
1. <span data-ttu-id="bff0f-146">Wenn Sie Effekte verwenden, überprüfen Sie zunächst das Objekt Funktionen.</span><span class="sxs-lookup"><span data-stu-id="bff0f-146">When using effects, check the capabilities object first.</span></span> <span data-ttu-id="bff0f-147">Wechseln Sie Steuerelement-Anweisungen, je nachdem, wie Sie die Effekte anpassen möchten, oder bedingte Überprüfungen in Betracht.</span><span class="sxs-lookup"><span data-stu-id="bff0f-147">Consider using conditional checks or switch control statements, depending on how you want to tailor the effects.</span></span>

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

<span data-ttu-id="bff0f-148">Vollständiger Beispielcode finden Sie auf der [Windows-UI-Github-Repository](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2015063/CompCapabilities).</span><span class="sxs-lookup"><span data-stu-id="bff0f-148">Full example code can be found on the [Windows UI Github repo](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2015063/CompCapabilities).</span></span>

## <a name="fast-vs-slow-effects"></a><span data-ttu-id="bff0f-149">Fast im Vergleich zu langsam Effekte</span><span class="sxs-lookup"><span data-stu-id="bff0f-149">Fast vs. slow effects</span></span>

<span data-ttu-id="bff0f-150">Anhand des Feedbacks der bereitgestellten Methoden [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) und [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) in der CompositionCapabilties-API, kann die Anwendung entscheiden teuer oder nicht unterstützte Effekte für andere Effekte ihrer Wahl ausgetauscht, die optimiert sind für das Gerät.</span><span class="sxs-lookup"><span data-stu-id="bff0f-150">Based on feedback from the provided [AreEffectsSupported](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectssupported) and [AreEffectsFast](/uwp/api/windows.ui.composition.compositioncapabilities.areeffectsfast) methods in the CompositionCapabilties API, the application can decide to swap expensive or unsupported effects for other effects of their choice that are optimized for the device.</span></span> <span data-ttu-id="bff0f-151">Einige Effekte bekannt ist, dass viele Ressourcen, die als andere rechenintensive konsistent sein und sollten sparsam verwendet werden, und andere Effekte können mehr frei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bff0f-151">Some effects are known to consistently be more resource intensive than others and should be used sparingly, and other effects can be used more freely.</span></span> <span data-ttu-id="bff0f-152">Für alle Effekte sollte jedoch Vorsicht verwendet werden beim Verketten und als einige Szenarien oder Kombinationen Animieren der Leistungsmerkmale des Diagramms Effekt ändern können.</span><span class="sxs-lookup"><span data-stu-id="bff0f-152">For all effects, however, care should be used when chaining and animating as some scenarios or combinations may change the performance characteristics of the effect graph.</span></span> <span data-ttu-id="bff0f-153">Unten sind einige Faustregel Leistungsmerkmale für einzelne Effekte:</span><span class="sxs-lookup"><span data-stu-id="bff0f-153">Below are some rule of thumb performance characteristics for individual effects:</span></span>

- <span data-ttu-id="bff0f-154">Effekte, die bekanntermaßen mit hoher Leistung auswirken sind wie folgt – Bildbearbeitungstools, Schatten Maske, BackDropBrush, HostBackDropBrush und Visual Layer.</span><span class="sxs-lookup"><span data-stu-id="bff0f-154">Effects that are known to have high performance impact are as follows – Gaussian Blur, Shadow Mask, BackDropBrush, HostBackDropBrush, and Layer Visual.</span></span> <span data-ttu-id="bff0f-155">Diese werden nicht für low-End-Geräten [(Featureebene 9.1-9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx)empfohlen und sollte überlegt auf high-End-Geräten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bff0f-155">These are not recommended for low end devices [(feature level 9.1-9.3)](https://msdn.microsoft.com/library/windows/desktop/ff476876(v=vs.85).aspx), and should be used judiciously on high end devices.</span></span>
- <span data-ttu-id="bff0f-156">Effekte mit mittlerer Leistungseinbußen enthalten Farbe Matrix, die bestimmte Blend-Effekt BlendModes (Helligkeit, Farbe, Sättigung und Farbton), SpotLight, SceneLightingEffect und (je nach Szenario) BorderEffect.</span><span class="sxs-lookup"><span data-stu-id="bff0f-156">Effects with medium performance impact include Color Matrix, certain Blend Effect BlendModes (Luminosity, Color, Saturation, and Hue), SpotLight, SceneLightingEffect, and (depending on scenario) BorderEffect.</span></span> <span data-ttu-id="bff0f-157">Diese Effekte mit bestimmten Szenarien auf low-End-Geräten funktionieren, aber Vorsicht sollte verwendet werden, wenn verketten und animieren.</span><span class="sxs-lookup"><span data-stu-id="bff0f-157">These effects may work with certain scenarios on low end devices, but care should be used when chaining and animating.</span></span> <span data-ttu-id="bff0f-158">Empfehlen Sie einschränken der Verwendung auf zwei oder weniger und auf Übergänge nur animieren.</span><span class="sxs-lookup"><span data-stu-id="bff0f-158">Recommend restricting use to two or less and animating on transitions only.</span></span>
- <span data-ttu-id="bff0f-159">Alle anderen Effekten geringe Leistung Auswirkung haben und in allen angemessene Szenarien beim animieren und Verkettung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="bff0f-159">All other effects have low performance impact and work in all reasonable scenarios when animating and chaining.</span></span>

## <a name="related-articles"></a><span data-ttu-id="bff0f-160">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="bff0f-160">Related articles</span></span>

- [<span data-ttu-id="bff0f-161">UWP-Techniken für reaktionsfähiges Design</span><span class="sxs-lookup"><span data-stu-id="bff0f-161">UWP Responsive Design Techniques</span></span>](https://docs.microsoft.com/windows/uwp/design/layout/responsive-design)
- [<span data-ttu-id="bff0f-162">UWP Gerät anpassen</span><span class="sxs-lookup"><span data-stu-id="bff0f-162">UWP Device Tailoring</span></span>](https://docs.microsoft.com/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)
