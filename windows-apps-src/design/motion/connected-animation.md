---
author: mijacobs
description: Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.
title: Verbundene Animationen
template: detail.hbs
ms.author: jimwalk
ms.date: 10/04/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: conrwi
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 51cf9dd0d28590d86bf05cc16634e465e260626c
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6182813"
---
# <a name="connected-animation-for-uwp-apps"></a><span data-ttu-id="f17ad-104">Verbundene Animation für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="f17ad-104">Connected animation for UWP apps</span></span>

<span data-ttu-id="f17ad-105">Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren.</span><span class="sxs-lookup"><span data-stu-id="f17ad-105">Connected animations let you create a dynamic and compelling navigation experience by animating the transition of an element between two different views.</span></span> <span data-ttu-id="f17ad-106">So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-106">This helps the user maintain their context and provides continuity between the views.</span></span>

<span data-ttu-id="f17ad-107">In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten, während eine Änderung im UI-Inhalt Quellansicht über den Bildschirm von seinem Standort in der Quellansicht zu seinem Ziel in der neuen Ansicht "fortsetzen".</span><span class="sxs-lookup"><span data-stu-id="f17ad-107">In a connected animation, an element appears to "continue" between two views during a change in UI content, flying across the screen from its location in the source view to its destination in the new view.</span></span> <span data-ttu-id="f17ad-108">Dies betont den gemeinsamen Inhalt zwischen den Ansichten und entsteht ein schönen, dynamischen Effekt als Teil eines Übergangs.</span><span class="sxs-lookup"><span data-stu-id="f17ad-108">This emphasizes the common content between the views and creates a beautiful and dynamic effect as part of a transition.</span></span>

> <span data-ttu-id="f17ad-109">**Wichtige APIs**: [ConnectedAnimation-Klasse](/uwp/api/windows.ui.xaml.media.animation.connectedanimation), [ConnectedAnimationService-Klasse](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice)</span><span class="sxs-lookup"><span data-stu-id="f17ad-109">**Important APIs**:  [ConnectedAnimation class](/uwp/api/windows.ui.xaml.media.animation.connectedanimation), [ConnectedAnimationService class](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice)</span></span>

## <a name="see-it-in-action"></a><span data-ttu-id="f17ad-110">Sehen Sie es in Aktion</span><span class="sxs-lookup"><span data-stu-id="f17ad-110">See it in action</span></span>

<span data-ttu-id="f17ad-111">In diesem kurzen Video verwendet eine app eine verbundene Animation, um ein Element animieren als "so lange" Teil der Überschrift der nächsten Seite weiterbesteht.</span><span class="sxs-lookup"><span data-stu-id="f17ad-111">In this short video, an app uses a connected animation to animate an item image as it "continues" to become part of the header of the next page.</span></span> <span data-ttu-id="f17ad-112">Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-112">The effect helps maintain user context across the transition.</span></span>

![Verbundene Animationen](images/connected-animations/example.gif)

<!-- 
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=b2daa5ee%2Dbe15%2D4503%2Db541%2D1328a6587c36&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

## <a name="video-summary"></a><span data-ttu-id="f17ad-114">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f17ad-114">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev005/player]

## <a name="connected-animation-and-the-fluent-design-system"></a><span data-ttu-id="f17ad-115">Verbundene Animationen und das Fluent Design-System</span><span class="sxs-lookup"><span data-stu-id="f17ad-115">Connected animation and the Fluent Design System</span></span>

 <span data-ttu-id="f17ad-116">Mit dem Fluent Design-System erstellen Sie moderne Oberflächen, die Licht, Tiefe, Bewegung, Material und Skalierungsmöglichkeiten beinhalten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-116">The Fluent Design System helps you create modern, bold UI that incorporates light, depth, motion, material, and scale.</span></span> <span data-ttu-id="f17ad-117">Verbundene Animation ist eine Komponente des Fluent Design-Systems, die Bewegung in Ihre App bringt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-117">Connected animation is a Fluent Design System component that adds motion to your app.</span></span> <span data-ttu-id="f17ad-118">Weitere Informationen finden Sie in der [Fluent Design für UWP-Übersicht](../fluent-design-system/index.md).</span><span class="sxs-lookup"><span data-stu-id="f17ad-118">To learn more, see the [Fluent Design for UWP overview](../fluent-design-system/index.md).</span></span>

## <a name="why-connected-animation"></a><span data-ttu-id="f17ad-119">Warum eine verbundene Animation?</span><span class="sxs-lookup"><span data-stu-id="f17ad-119">Why connected animation?</span></span>

<span data-ttu-id="f17ad-120">Beim Navigieren zwischen Seiten ist es wichtig, dass der Benutzer versteht, welcher neue Inhalt nach der Navigation dargestellt wird und in welcher Beziehung dieser zu seiner Absicht beim Navigieren steht.</span><span class="sxs-lookup"><span data-stu-id="f17ad-120">When navigating between pages, it’s important for the user to understand what new content is being presented after the navigation and how it relates to their intent when navigating.</span></span> <span data-ttu-id="f17ad-121">Verbundene Animationen bieten eine leistungsstarke visuelle Metapher, die die Beziehung zwischen zwei Ansichten hervorhebt, indem sie den Fokus des Benutzers auf den gemeinsamen Inhalt zwischen diesen beiden lenkt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-121">Connected animations provide a powerful visual metaphor that emphasizes the relationship between two views by drawing the user’s focus to the content shared between them.</span></span> <span data-ttu-id="f17ad-122">Darüber hinaus fügen verbundene Animationen der Seitennavigation visuelle Spannung und einen Feinschliff hinzu, die dazu beitragen können, dass sich die Bewegungsgestaltung Ihrer App von anderen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="f17ad-122">Additionally, connected animations add visual interest and polish to page navigation that can help differentiate the motion design of your app.</span></span>

## <a name="when-to-use-connected-animation"></a><span data-ttu-id="f17ad-123">Verwendungsszenarien für verbundene Animationen</span><span class="sxs-lookup"><span data-stu-id="f17ad-123">When to use connected animation</span></span>

<span data-ttu-id="f17ad-124">Verbundene Animationen werden in der Regel bei einem Seitenwechsel verwendet, sie können jedoch immer verwendet werden, wenn Sie Inhalt in einer UI ändern und möchten, dass der Benutzerkontext beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="f17ad-124">Connected animations are generally used when changing pages, though they can be applied to any experience where you are changing content in a UI and want the user to maintain context.</span></span> <span data-ttu-id="f17ad-125">Sie sollten es in Betracht ziehen, eine verbundene Animation anstelle eines [Drills in einem Navigationsübergangs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) zu verwenden, wenn die Quell- und die Zielansicht ein gemeinsames Bild oder ein anderes gemeinsames UI-Element aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-125">You should consider using a connected animation instead of a [drill in navigation transition](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.animation.navigationthemetransition.aspx) whenever there is an image or other piece of UI shared between the source and destination views.</span></span>

## <a name="configure-connected-animation"></a><span data-ttu-id="f17ad-126">Konfigurieren von verbundenen animation</span><span class="sxs-lookup"><span data-stu-id="f17ad-126">Configure connected animation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f17ad-127">Dieses Feature erfordert, dass die Ziel Version Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher.</span><span class="sxs-lookup"><span data-stu-id="f17ad-127">This feature requires that your app's Target version be Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later.</span></span> <span data-ttu-id="f17ad-128">Die Konfigurations-Eigenschaft ist nicht verfügbar in frühere SDKs.</span><span class="sxs-lookup"><span data-stu-id="f17ad-128">The Configuration property is not available in earlier SDKs.</span></span> <span data-ttu-id="f17ad-129">Sie können eine minimale niedrigere Version als SDK 17763 Ziel mit adaptivem Code oder bedingten XAML.</span><span class="sxs-lookup"><span data-stu-id="f17ad-129">You can target a Minimum version lower than SDK 17763 using adaptive code or conditional XAML.</span></span> <span data-ttu-id="f17ad-130">Weitere Informationen finden Sie unter [versionsadaptive apps](/debug-test-perf/version-adaptive-apps).</span><span class="sxs-lookup"><span data-stu-id="f17ad-130">For more info, see [Version adaptive apps](/debug-test-perf/version-adaptive-apps).</span></span>

<span data-ttu-id="f17ad-131">Ab Windows 10, Version 1809, weiter verbundene Animationen Benutzeroberflächenelement Fluent Design durch die Bereitstellung der Animation Konfigurationen zugeschnitten speziell für Vorwärts und rückwärts Navigation zwischen Seiten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-131">Starting in Windows 10, version 1809, connected animations further embody Fluent design by providing animation configurations tailored specifically for forward and backwards page navigation.</span></span>

<span data-ttu-id="f17ad-132">Sie haben eine Animation-Konfiguration durch Festlegen der Konfiguration-Eigenschaft auf die ConnectedAnimation angeben.</span><span class="sxs-lookup"><span data-stu-id="f17ad-132">You specify an animation configuration by setting the Configuration property on the ConnectedAnimation.</span></span> <span data-ttu-id="f17ad-133">(Wir zeigen Beispiele hierfür im nächsten Abschnitt.)</span><span class="sxs-lookup"><span data-stu-id="f17ad-133">(We’ll show examples of this in the next section.)</span></span>

<span data-ttu-id="f17ad-134">Diese Tabelle beschreibt die verfügbaren Varianten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-134">This table describes the available configurations.</span></span> <span data-ttu-id="f17ad-135">Weitere Informationen zu den Bewegung Prinzipien in diese Animationen angewendet finden Sie unter [Direktionalität und Schwerkraft](index.md).</span><span class="sxs-lookup"><span data-stu-id="f17ad-135">For more information about the motion principles applied in these animations, see [Directionality and gravity](index.md).</span></span>

| [<span data-ttu-id="f17ad-136">GravityConnectedAnimationConfiguration</span><span class="sxs-lookup"><span data-stu-id="f17ad-136">GravityConnectedAnimationConfiguration</span></span>]() |
| - |
| <span data-ttu-id="f17ad-137">Dies ist die Standardkonfiguration, und es wird empfohlen, für die Vorwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="f17ad-137">This is the default configuration, and is recommended for forward navigation.</span></span> |
<span data-ttu-id="f17ad-138">Wie der Benutzer in der app (A zu B) vorwärts navigiert, wird das verbundene Element physisch "außerhalb der Seite innen" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-138">As the user navigates forward in the app (A to B), the connected element appears to physically “pull off the page”.</span></span> <span data-ttu-id="f17ad-139">Dadurch wird das Element erscheint, um im Z-Raum voranzubringen und klappt etwas als Effekt der Schwerkraft Teilnahme an halten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-139">In doing so, the element appears to move forward in z-space and drops a bit as an effect of gravity taking hold.</span></span> <span data-ttu-id="f17ad-140">Um die Effekte der Schwerkraft zu umgehen, wird das Element erhält Geschwindigkeit und in die endgültige Position beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-140">To overcome the effects of gravity, the element gains velocity and accelerates into its final position.</span></span> <span data-ttu-id="f17ad-141">Das Ergebnis ist eine Animation "Skalierung und Dip".</span><span class="sxs-lookup"><span data-stu-id="f17ad-141">The result is a “scale and dip” animation.</span></span> |

| [<span data-ttu-id="f17ad-142">DirectConnectedAnimationConfiguration</span><span class="sxs-lookup"><span data-stu-id="f17ad-142">DirectConnectedAnimationConfiguration</span></span>]() |
| - |
| <span data-ttu-id="f17ad-143">Wenn der Benutzer rückwärts in der app (B a) navigiert, ist die Animation direkter.</span><span class="sxs-lookup"><span data-stu-id="f17ad-143">As the user navigates backwards in the app (B to A), the animation is more direct.</span></span> <span data-ttu-id="f17ad-144">Das verbundene Element übersetzt linear B in ein mit einem Decelerate kubische Bézierkurven-Beschleunigungsfunktion.</span><span class="sxs-lookup"><span data-stu-id="f17ad-144">The connected element linearly translates from B to A using a decelerate cubic Bezier easing function.</span></span> <span data-ttu-id="f17ad-145">Die Rückwärtsnavigation visuelle Angebot für zurückgesetzt den Benutzer auf ihren vorherigen Zustand so schnell wie möglich und gleichzeitig den Kontext für den Ablauf der Navigation.</span><span class="sxs-lookup"><span data-stu-id="f17ad-145">The backwards visual affordance returns the user to their previous state as fast as possible while still maintaining the context of the navigation flow.</span></span> |

| [<span data-ttu-id="f17ad-146">BasicConnectedAnimationConfiguration</span><span class="sxs-lookup"><span data-stu-id="f17ad-146">BasicConnectedAnimationConfiguration</span></span>]() |
| - |
| <span data-ttu-id="f17ad-147">Dies ist der Standardwert (und nur) Animation in Versionen vor Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) verwendet.</span><span class="sxs-lookup"><span data-stu-id="f17ad-147">This is the default (and only) animation used in versions prior to Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)).</span></span> |

### <a name="connectedanimationservice-configuration"></a><span data-ttu-id="f17ad-148">ConnectedAnimationService-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f17ad-148">ConnectedAnimationService configuration</span></span>

<span data-ttu-id="f17ad-149">Die [ConnectedAnimationService](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice) -Klasse verfügt über zwei Eigenschaften, die für die einzelnen Animationen anstelle der Dienst gelten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-149">The [ConnectedAnimationService](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice) class has two properties that apply to the individual animations rather than the overall service.</span></span>

- [<span data-ttu-id="f17ad-150">DefaultDuration</span><span class="sxs-lookup"><span data-stu-id="f17ad-150">DefaultDuration</span></span>](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.defaultduration)
- [<span data-ttu-id="f17ad-151">DefaultEasingFunction</span><span class="sxs-lookup"><span data-stu-id="f17ad-151">DefaultEasingFunction</span></span>](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.defaulteasingfunction)

<span data-ttu-id="f17ad-152">Um die verschiedenen Effekte zu erzielen, einige Konfigurationen diese Eigenschaften auf ConnectedAnimationService ignorieren und stattdessen ihre eigenen Werte, wie in dieser Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f17ad-152">To achieve the various effects, some configurations ignore these properties on ConnectedAnimationService and use their own values instead, as described in this table.</span></span>

| <span data-ttu-id="f17ad-153">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f17ad-153">Configuration</span></span> | <span data-ttu-id="f17ad-154">Hinsicht DefaultDuration?</span><span class="sxs-lookup"><span data-stu-id="f17ad-154">Respects DefaultDuration?</span></span> | <span data-ttu-id="f17ad-155">Hinsicht DefaultEasingFunction?</span><span class="sxs-lookup"><span data-stu-id="f17ad-155">Respects DefaultEasingFunction?</span></span> |
| - | - | - |
| <span data-ttu-id="f17ad-156">Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="f17ad-156">Gravity</span></span> | <span data-ttu-id="f17ad-157">Ja</span><span class="sxs-lookup"><span data-stu-id="f17ad-157">Yes</span></span> | <span data-ttu-id="f17ad-158">Ja\*</span><span class="sxs-lookup"><span data-stu-id="f17ad-158">Yes\*</span></span> <br/> <span data-ttu-id="f17ad-159">\**Die grundlegende Übersetzung von A zu B verwendet diese Beschleunigungsfunktion, aber "Schwerkraft Dip" verfügt über einen eigenen Beschleunigungsfunktion.*</span><span class="sxs-lookup"><span data-stu-id="f17ad-159">\**The basic translation from A to B uses this easing function, but the "gravity dip" has its own easing function.*</span></span>  |
| <span data-ttu-id="f17ad-160">Direkte</span><span class="sxs-lookup"><span data-stu-id="f17ad-160">Direct</span></span> | <span data-ttu-id="f17ad-161">Nein</span><span class="sxs-lookup"><span data-stu-id="f17ad-161">No</span></span> <br/> *<span data-ttu-id="f17ad-162">Wird über 150 ms animiert.</span><span class="sxs-lookup"><span data-stu-id="f17ad-162">Animates over 150ms.</span></span>*| <span data-ttu-id="f17ad-163">Nein</span><span class="sxs-lookup"><span data-stu-id="f17ad-163">No</span></span> <br/> *<span data-ttu-id="f17ad-164">Verwendet die Beschleunigungsfunktion Decelerate.</span><span class="sxs-lookup"><span data-stu-id="f17ad-164">Uses the Decelerate easing function.</span></span>* |
| <span data-ttu-id="f17ad-165">Einfach</span><span class="sxs-lookup"><span data-stu-id="f17ad-165">Basic</span></span> | <span data-ttu-id="f17ad-166">Ja</span><span class="sxs-lookup"><span data-stu-id="f17ad-166">Yes</span></span> | <span data-ttu-id="f17ad-167">Ja</span><span class="sxs-lookup"><span data-stu-id="f17ad-167">Yes</span></span> |

## <a name="how-to-implement-connected-animation"></a><span data-ttu-id="f17ad-168">Verbundene Animationen Implementierung</span><span class="sxs-lookup"><span data-stu-id="f17ad-168">How to implement connected animation</span></span>

<span data-ttu-id="f17ad-169">Das Einrichten einer verbundenen Animation besteht aus zwei Schritten:</span><span class="sxs-lookup"><span data-stu-id="f17ad-169">Setting up a connected animation involves two steps:</span></span>

1. <span data-ttu-id="f17ad-170">*Vorbereiten* eines Animationsobjekts auf der Quellseite, die das System anzeigt, dass das Quellelement der verbundenen Animation teilnimmt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-170">*Prepare* an animation object on the source page, which indicates to the system that the source element will participate in the connected animation.</span></span>
1. <span data-ttu-id="f17ad-171">*Starten Sie* die Animation auf der Zielseite einen Verweis auf das Zielelement übergeben.</span><span class="sxs-lookup"><span data-stu-id="f17ad-171">*Start* the animation on the destination page, passing a reference to the destination element.</span></span>

<span data-ttu-id="f17ad-172">Beim Navigieren von der Quellseite, rufen Sie [ConnectedAnimationService.GetForCurrentView](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getforcurrentview) , um eine Instanz von ConnectedAnimationService zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-172">When navigating from the source page, call [ConnectedAnimationService.GetForCurrentView](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getforcurrentview) to get an instance of ConnectedAnimationService.</span></span> <span data-ttu-id="f17ad-173">Eine Animation vorbereiten, rufen [PrepareToAnimate](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.preparetoanimate) in dieser Instanz auf und übergeben Sie einen eindeutigen Schlüssel und das Element der Benutzeroberfläche, die, das Sie in den Übergang verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-173">To prepare an animation, call [PrepareToAnimate](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.preparetoanimate) on this instance, and pass in a unique key and the UI element you want to use in the transition.</span></span> <span data-ttu-id="f17ad-174">Mithilfe des eindeutigen Schlüssels können Sie die Animation später auf der Seite "Ziel" abrufen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-174">The unique key lets you retrieve the animation later on the destination page.</span></span>

```csharp
ConnectedAnimationService.GetForCurrentView()
    .PrepareToAnimate("forwardAnimation", SourceImage);
```

<span data-ttu-id="f17ad-175">Bei der Navigation, starten Sie die Animation in der Zielseite.</span><span class="sxs-lookup"><span data-stu-id="f17ad-175">When the navigation occurs, start the animation in the destination page.</span></span> <span data-ttu-id="f17ad-176">Rufen Sie zum Starten der Animation [ConnectedAnimation.TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart) auf.</span><span class="sxs-lookup"><span data-stu-id="f17ad-176">To start the animation, call [ConnectedAnimation.TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart).</span></span> <span data-ttu-id="f17ad-177">Sie können die richtige Animationsinstanz abrufen, indem Sie mit dem eindeutigen Schlüssel, den Sie beim Erstellen der Animation angegeben haben, [ConnectedAnimationService.GetAnimation](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getanimation) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-177">You can retrieve the right animation instance by calling [ConnectedAnimationService.GetAnimation](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice.getanimation) with the unique key you provided when creating the animation.</span></span>

```csharp
ConnectedAnimation animation =
    ConnectedAnimationService.GetForCurrentView().GetAnimation("forwardAnimation");
if (animation != null)
{
    animation.TryStart(DestinationImage);
}
```

### <a name="forward-navigation"></a><span data-ttu-id="f17ad-178">Vorwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="f17ad-178">Forward navigation</span></span>

<span data-ttu-id="f17ad-179">Dieses Beispiel zeigt, wie Sie ConnectedAnimationService zum Erstellen eines Übergangs für Vorwärts-Navigation zwischen zwei Seiten (Page_A, Page_B).</span><span class="sxs-lookup"><span data-stu-id="f17ad-179">This example shows how to use ConnectedAnimationService to create a transition for forward navigation between two pages (Page_A to Page_B).</span></span>

<span data-ttu-id="f17ad-180">Die empfohlene Animation Konfiguration für Vorwärtsnavigation ist [GravityConnectedAnimationConfiguration]().</span><span class="sxs-lookup"><span data-stu-id="f17ad-180">The recommended animation configuration for forward navigation is [GravityConnectedAnimationConfiguration]().</span></span> <span data-ttu-id="f17ad-181">Dies ist die Standardeinstellung, daher müssen Sie nicht die [Konfiguration](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.configuration) -Eigenschaft festgelegt, es sei denn, Sie eine andere Konfiguration angeben möchten.</span><span class="sxs-lookup"><span data-stu-id="f17ad-181">This is the default, so you don't need to set the [Configuration](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.configuration) property unless you want to specify a different configuration.</span></span>

<span data-ttu-id="f17ad-182">Richten Sie die Animation auf der Quellseite aus.</span><span class="sxs-lookup"><span data-stu-id="f17ad-182">Set up the animation in the source page.</span></span>

```xaml
<!-- Page_A.xaml -->

<Image x:Name="SourceImage"
       HorizontalAlignment="Left" VerticalAlignment="Top"
       Width="200" Height="200"
       Stretch="Fill"
       Source="Assets/StoreLogo.png"
       PointerPressed="SourceImage_PointerPressed"/>
```

```csharp
// Page_A.xaml.cs

private void SourceImage_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    // Navigate to detail page.
    // Suppress the default animation to avoid conflict with the connected animation.
    Frame.Navigate(typeof(Page_B), null, new SuppressNavigationTransitionInfo());
}

protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
{
    ConnectedAnimationService.GetForCurrentView()
        .PrepareToAnimate("forwardAnimation", SourceImage);
    // You don't need to explicitly set the Configuration property because
    // the recommended Gravity configuration is default.
    // For custom animation, use:
    // animation.Configuration = new BasicConnectedAnimationConfiguration();
}
```

<span data-ttu-id="f17ad-183">Starten Sie die Animation in der Zielseite.</span><span class="sxs-lookup"><span data-stu-id="f17ad-183">Start the animation in the destination page.</span></span>

```xaml
<!-- Page_B.xaml -->

<Image x:Name="DestinationImage"
       Width="400" Height="400"
       Stretch="Fill"
       Source="Assets/StoreLogo.png" />
```

```csharp
// Page_B.xaml.cs

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    ConnectedAnimation animation =
        ConnectedAnimationService.GetForCurrentView().GetAnimation("forwardAnimation");
    if (animation != null)
    {
        animation.TryStart(DestinationImage);
    }
}
```

### <a name="back-navigation"></a><span data-ttu-id="f17ad-184">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="f17ad-184">Back navigation</span></span>

<span data-ttu-id="f17ad-185">Für die Rückwärtsnavigation (Page_B, Page_A), führen Sie die gleichen Schritte, aber die Quell- und Zieldatenträger Seiten umgekehrt werden.</span><span class="sxs-lookup"><span data-stu-id="f17ad-185">For back navigation (Page_B to Page_A), you follow the same steps, but the source and destination pages are reversed.</span></span>

<span data-ttu-id="f17ad-186">Wenn der Benutzer zurück navigiert, erwarten sie die app so schnell wie möglich in den vorherigen Zustand zurückgegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="f17ad-186">When the user navigates back, they expect the app to be returned to the previous state as soon as possible.</span></span> <span data-ttu-id="f17ad-187">Daher ist die empfohlene Konfiguration [DirectConnectedAnimationConfiguration]().</span><span class="sxs-lookup"><span data-stu-id="f17ad-187">Therefore, the recommended configuration is [DirectConnectedAnimationConfiguration]().</span></span> <span data-ttu-id="f17ad-188">Diese Animation ist schneller direkter und Decelerate geschwindigkeitsverlauf verwendet.</span><span class="sxs-lookup"><span data-stu-id="f17ad-188">This animation is quicker, more direct, and uses the decelerate easing.</span></span>

<span data-ttu-id="f17ad-189">Richten Sie die Animation auf der Quellseite aus.</span><span class="sxs-lookup"><span data-stu-id="f17ad-189">Set up the animation in the source page.</span></span>

```csharp
// Page_B.xaml.cs

protected override void OnNavigatingFrom(NavigatingCancelEventArgs e)
{
    if (e.NavigationMode == NavigationMode.Back)
    {
        ConnectedAnimationService.GetForCurrentView()
            .PrepareToAnimate("backAnimation", DestinationImage);

        // Use the recommended configuration for back animation.
        animation.Configuration = new DirectConnectedAnimationConfiguration();
    }
}
```

<span data-ttu-id="f17ad-190">Starten Sie die Animation in der Zielseite.</span><span class="sxs-lookup"><span data-stu-id="f17ad-190">Start the animation in the destination page.</span></span>

```csharp
// Page_A.xaml.cs

protected override void OnNavigatedTo(NavigationEventArgs e)
{
    base.OnNavigatedTo(e);

    ConnectedAnimation animation =
        ConnectedAnimationService.GetForCurrentView().GetAnimation("backAnimation");
    if (animation != null)
    {
        animation.TryStart(SourceImage);
    }
}
```

<span data-ttu-id="f17ad-191">Zwischen dem Zeitpunkt, die die Animation eingerichtet ist und wenn es gestartet wird wird das Quellelement eingefroren über anderen UI in der app angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-191">Between the time that the animation is set up and when it's started, the source element appears frozen above other UI in the app.</span></span> <span data-ttu-id="f17ad-192">Auf diese Weise können Sie gleichzeitig weitere Übergangsanimationen ausführen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-192">This lets you perform any other transition animations simultaneously.</span></span> <span data-ttu-id="f17ad-193">Aus diesem Grund sollten nicht Sie länger als ~ 250 Millisekunden zwischen den beiden Schritten warten, da das Vorhandensein des Quellelements Quellelements stören kann.</span><span class="sxs-lookup"><span data-stu-id="f17ad-193">For this reason, you shouldn't wait more than ~250 milliseconds in between the two steps because the presence of the source element may become distracting.</span></span> <span data-ttu-id="f17ad-194">Wenn Sie eine Animation vorbereiten und diese nicht innerhalb von drei Sekunden starten, wird sie vom System gelöscht und alle folgenden Aufrufe von [TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart) schlagen fehl.</span><span class="sxs-lookup"><span data-stu-id="f17ad-194">If you prepare an animation and do not start it within three seconds, the system will dispose of the animation and any subsequent calls to [TryStart](/uwp/api/windows.ui.xaml.media.animation.connectedanimation.trystart) will fail.</span></span>

## <a name="connected-animation-in-list-and-grid-experiences"></a><span data-ttu-id="f17ad-195">Verbundene Animationen in Listen- und Rasterumgebungen</span><span class="sxs-lookup"><span data-stu-id="f17ad-195">Connected animation in list and grid experiences</span></span>

<span data-ttu-id="f17ad-196">Sie werden wahrscheinlich häufig verbundene Animationen aus einem Listen- oder Rastersteuerelement erstellen wollen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-196">Often, you will want to create a connected animation from or to a list or grid control.</span></span> <span data-ttu-id="f17ad-197">Die beiden Methoden können auf [ListView](/uwp/api/windows.ui.xaml.controls.listview) und [GridView](/uwp/api/windows.ui.xaml.controls.gridview), [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) und [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync), Sie um diesen Prozess zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-197">You can use the two methods on [ListView](/uwp/api/windows.ui.xaml.controls.listview) and [GridView](/uwp/api/windows.ui.xaml.controls.gridview), [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) and [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync), to simplify this process.</span></span>

<span data-ttu-id="f17ad-198">Nehmen wir beispielsweise an, Sie haben eine **ListView**, die ein Element mit dem Namen „PortraitEllipse” in der Datenvorlage enthält.</span><span class="sxs-lookup"><span data-stu-id="f17ad-198">For example, say you have a **ListView** that contains an element with the name "PortraitEllipse" in its data template.</span></span>

```xaml
<ListView x:Name="ContactsListView" Loaded="ContactsListView_Loaded">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="vm:ContactsItem">
            <Grid>
                …
                <Ellipse x:Name="PortraitEllipse" … />
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

<span data-ttu-id="f17ad-199">Rufen Sie zum Vorbereiten einer verbundenen Animation mit der Ellipse für ein bestimmtes Element die [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) Methode mit einem eindeutigen Schlüssel, das Element und den Namen "PortraitEllipse" ein.</span><span class="sxs-lookup"><span data-stu-id="f17ad-199">To prepare a connected animation with the ellipse corresponding to a given list item, call the [PrepareConnectedAnimation](/uwp/api/windows.ui.xaml.controls.listviewbase.prepareconnectedanimation) method with a unique key, the item, and the name "PortraitEllipse".</span></span>

```csharp
void PrepareAnimationWithItem(ContactsItem item)
{
     ContactsListView.PrepareConnectedAnimation("portrait", item, "PortraitEllipse");
}
```

<span data-ttu-id="f17ad-200">Verwenden Sie zum Starten einer Animation mit diesem Element als Ziel, z. B. wenn aus einer Detailansicht zurück navigiert [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync).</span><span class="sxs-lookup"><span data-stu-id="f17ad-200">To start an animation with this element as the destination, such as when navigating back from a detail view, use [TryStartConnectedAnimationAsync](/uwp/api/windows.ui.xaml.controls.listviewbase.trystartconnectedanimationasync).</span></span> <span data-ttu-id="f17ad-201">Wenn Sie die Datenquelle für die ListView gerade geladen haben, wartet TryStartConnectedAnimationAsync mit dem Start der Animation, bis der entsprechende Elementcontainer erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f17ad-201">If you have just loaded the data source for the ListView, TryStartConnectedAnimationAsync will wait to start the animation until the corresponding item container has been created.</span></span>

```csharp
private void ContactsListView_Loaded(object sender, RoutedEventArgs e)
{
    ContactsItem item = GetPersistedItem(); // Get persisted item
    if (item != null)
    {
        ContactsListView.ScrollIntoView(item);
        ConnectedAnimation animation =
            ConnectedAnimationService.GetForCurrentView().GetAnimation("portrait");
        if (animation != null)
        {
            await ContactsListView.TryStartConnectedAnimationAsync(
                animation, item, "PortraitEllipse");
        }
    }
}
```

## <a name="coordinated-animation"></a><span data-ttu-id="f17ad-202">Koordinierte Animation</span><span class="sxs-lookup"><span data-stu-id="f17ad-202">Coordinated animation</span></span>

![Koordinierte Animation](images/connected-animations/coordinated_example.gif)

<!--
<iframe width=640 height=360 src='https://microsoft.sharepoint.com/portals/hub/_layouts/15/VideoEmbedHost.aspx?chId=552c725c%2De353%2D4118%2Dbd2b%2Dc2d0584c9848&amp;vId=9066bbbe%2Dcf58%2D4ab4%2Db274%2D595616f5d0a0&amp;width=640&amp;height=360&amp;autoPlay=false&amp;showInfo=true' allowfullscreen></iframe>
-->

<span data-ttu-id="f17ad-204">Eine *koordinierte Animation* besteht eine besondere Art von Eingangsanimation, bei denen ein Element zusammen mit dem verbundenen Animationsziel zusammen mit dem verbundenen Animationselement über den Bildschirm bewegt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-204">A *coordinated animation* is a special type of entrance animation where an element appears along with the connected animation target, animating in tandem with the connected animation element as it moves across the screen.</span></span> <span data-ttu-id="f17ad-205">Koordinierte Animationen können einem Übergang weitere visuelle Spannung hinzufügen und die Aufmerksamkeit des Benutzers auf den Kontext lenken, den die Quell- und die Zielansicht teilen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-205">Coordinated animations can add more visual interest to a transition and further draw the user’s attention to the context that is shared between the source and destination views.</span></span> <span data-ttu-id="f17ad-206">In diesen Bildern wird die Beschriftungs-UI für das Element mithilfe einer koordinierten Animation animiert.</span><span class="sxs-lookup"><span data-stu-id="f17ad-206">In these images, the caption UI for the item is animating using a coordinated animation.</span></span>

<span data-ttu-id="f17ad-207">Bei eine koordinierte Animation die Schwerkraft Konfiguration verwendet, wird die Schwerkraft auf dem verbundenen Animationselement sowohl die koordinierte Elemente angewendet.</span><span class="sxs-lookup"><span data-stu-id="f17ad-207">When a coordinated animation uses the gravity configuration, gravity is applied to both the connected animation element and the coordinated elements.</span></span> <span data-ttu-id="f17ad-208">Die koordinierte Elemente werden zusammen mit dem verbundenen Element "swoop" werden, damit die Elemente wirklich koordiniert.</span><span class="sxs-lookup"><span data-stu-id="f17ad-208">The coordinated elements will "swoop" alongside the connected element so the elements stay truly coordinated.</span></span>

<span data-ttu-id="f17ad-209">Verwenden Sie die Überladung von **TryStart** mit zwei Parametern, um koordinierte Elemente zu einer verbundenen Animation hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f17ad-209">Use the two-parameter overload of **TryStart** to add coordinated elements to a connected animation.</span></span> <span data-ttu-id="f17ad-210">Dieses Beispiel zeigt eine koordinierte Animation von einem Rasterlayout mit dem Namen "DescriptionRoot", die zusammen mit einem verbundenen Animationselement mit dem Namen "coverimage gestartet" eingibt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-210">This example demonstrates a coordinated animation of a Grid layout named "DescriptionRoot" that enters in tandem with a connected animation element named "CoverImage".</span></span>

```xaml
<!-- DestinationPage.xaml -->
<Grid>
    <Image x:Name="CoverImage" />
    <Grid x:Name="DescriptionRoot" />
</Grid>
```

```csharp
// DestinationPage.xaml.cs
void OnNavigatedTo(NavigationEventArgs e)
{
    var animationService = ConnectedAnimationService.GetForCurrentView();
    var animation = animationService.GetAnimation("coverImage");

    if (animation != null)
    {
        // Don’t need to capture the return value as we are not scheduling any subsequent
        // animations
        animation.TryStart(CoverImage, new UIElement[] { DescriptionRoot });
     }
}
```

## <a name="dos-and-donts"></a><span data-ttu-id="f17ad-211">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="f17ad-211">Do’s and don’ts</span></span>

- <span data-ttu-id="f17ad-212">Verwenden Sie eine verbundene Animation bei Seitenübergängen, bei denen ein Element zwischen der Quell- und der Zielseite geteilt wird.</span><span class="sxs-lookup"><span data-stu-id="f17ad-212">Use a connected animation in page transitions where an element is shared between the source and destination pages.</span></span>
- <span data-ttu-id="f17ad-213">Verwenden Sie [GravityConnectedAnimationConfiguration]() für die Vorwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="f17ad-213">Use [GravityConnectedAnimationConfiguration]() for forward navigation.</span></span>
- <span data-ttu-id="f17ad-214">Verwenden Sie [DirectConnectedAnimationConfiguration]() für die Rückwärtsnavigation.</span><span class="sxs-lookup"><span data-stu-id="f17ad-214">Use [DirectConnectedAnimationConfiguration]() for back navigation.</span></span>
- <span data-ttu-id="f17ad-215">Warten Sie nicht auf Netzwerkanfragen Netzwerkanfragen oder andere zeitaufwendige asynchrone Vorgänge vorbereiten und dem Starten einer verbundenen Animation.</span><span class="sxs-lookup"><span data-stu-id="f17ad-215">Don't wait on network requests or other long-running asynchronous operations in between preparing and starting a connected animation.</span></span> <span data-ttu-id="f17ad-216">Möglicherweise müssen Sie die erforderlichen Informationen laden, um den Übergang vorab auszuführen, oder ein Platzhalterbild mit niedriger Auflösung verwenden, während ein Bild mit hoher Auflösung in der Zielansicht geladen wird.</span><span class="sxs-lookup"><span data-stu-id="f17ad-216">You may need to pre-load the necessary information to run the transition ahead of time, or use a low-resolution placeholder image while a high-resolution image loads in the destination view.</span></span>
- <span data-ttu-id="f17ad-217">Verwenden Sie [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) , um zu verhindern, dass eine übergangsanimation in einem **Frame** bei Verwendung **ConnectedAnimationService**, da verbundene Animationen gedacht sind nicht gleichzeitig mit der Standardnavigation verwendet werden sollen wechselt.</span><span class="sxs-lookup"><span data-stu-id="f17ad-217">Use [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) to prevent a transition animation in a **Frame** if you are using **ConnectedAnimationService**, since connected animations aren't meant to be used simultaneously with the default navigation transitions.</span></span> <span data-ttu-id="f17ad-218">Weitere Informationen zur Verwendung von Navigationsübergängen finden Sie unter [NavigationThemeTransition](/uwp/api/Windows.UI.Xaml.Media.Animation.NavigationThemeTransition).</span><span class="sxs-lookup"><span data-stu-id="f17ad-218">See [NavigationThemeTransition](/uwp/api/Windows.UI.Xaml.Media.Animation.NavigationThemeTransition) for more info on how to use navigation transitions.</span></span>

## <a name="download-the-code-samples"></a><span data-ttu-id="f17ad-219">Codebeispiele herunterladen</span><span class="sxs-lookup"><span data-stu-id="f17ad-219">Download the code samples</span></span>

<span data-ttu-id="f17ad-220">Ein [Beispiel für eine verbundene Animation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) finden Sie in der [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs)-Beispielgalerie.</span><span class="sxs-lookup"><span data-stu-id="f17ad-220">See the [Connected Animation sample](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/ConnectedAnimationSample) in the [WindowsUIDevLabs](https://github.com/Microsoft/WindowsUIDevLabs) sample gallery.</span></span>

## <a name="related-articles"></a><span data-ttu-id="f17ad-221">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f17ad-221">Related articles</span></span>

[<span data-ttu-id="f17ad-222">ConnectedAnimation</span><span class="sxs-lookup"><span data-stu-id="f17ad-222">ConnectedAnimation</span></span>](/uwp/api/windows.ui.xaml.media.animation.connectedanimation)

[<span data-ttu-id="f17ad-223">ConnectedAnimationService</span><span class="sxs-lookup"><span data-stu-id="f17ad-223">ConnectedAnimationService</span></span>](/uwp/api/windows.ui.xaml.media.animation.connectedanimationservice)

[<span data-ttu-id="f17ad-224">NavigationThemeTransition</span><span class="sxs-lookup"><span data-stu-id="f17ad-224">NavigationThemeTransition</span></span>](/uwp/api/Windows.UI.Xaml.Media.Animation.NavigationThemeTransition)
