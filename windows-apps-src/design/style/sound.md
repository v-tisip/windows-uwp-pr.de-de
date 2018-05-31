---
author: mijacobs
Description: Sound helps complete an application's user experience, and gives them that extra audio edge they need to match the feel of Windows across all platforms.
label: Sound
title: Sound
template: detail.hbs
ms.assetid: 9fa77494-2525-4491-8f26-dc733b6a18f6
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: kisai
design-contact: mattben
dev-contact: joyate
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: dbe59b422a83ad31727928c406a1f4a6dd550301
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "1638394"
---
# <a name="sound"></a><span data-ttu-id="645da-103">Sound</span><span class="sxs-lookup"><span data-stu-id="645da-103">Sound</span></span>

 

<span data-ttu-id="645da-104">Es gibt viele Möglichkeiten, Ihre App mit Sound zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="645da-104">There are many ways to use sound to enhance your app.</span></span> <span data-ttu-id="645da-105">Sie können Sound zur Ergänzung von Benutzeroberflächenelementen einsetzen, um Benutzer akustisch auf Ereignisse aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="645da-105">You can use to sound to supplement other UI elements, enabling users to recognize events audibly.</span></span> <span data-ttu-id="645da-106">Sound ist beispielsweise für Menschen mit Sehbehinderungen ein hilfreiches Benutzeroberflächenelement.</span><span class="sxs-lookup"><span data-stu-id="645da-106">Sound can be an effective user interface element for people with visual disabilities.</span></span> <span data-ttu-id="645da-107">Mit Sound können Sie den Benutzer in das Geschehen einbeziehen, beispielsweise, wenn Sie ein Puzzlespiel mit einer beruhigenden Hintergrundmelodie und ein Horror-/Survivalspiel mit bedrohlichen Soundeffekten unterlegen.</span><span class="sxs-lookup"><span data-stu-id="645da-107">You can use sound to create an atmosphere that immerses the user; for example, you might play a whimsical soundtrack in the background of puzzle game, or use ominous sound effects for a horror/survival game.</span></span>

## <a name="sound-global-api"></a><span data-ttu-id="645da-108">Globale Sound-API</span><span class="sxs-lookup"><span data-stu-id="645da-108">Sound Global API</span></span>

<span data-ttu-id="645da-109">UWP bietet ein einfach zugängliches Soundsystem, bei dem Sie einfach „einen Schalter umlegen“ können und ein beeindruckendes Audioerlebnis für Ihre gesamte App erhalten.</span><span class="sxs-lookup"><span data-stu-id="645da-109">UWP provides an easily accessible sound system that allows you to simply "flip a switch" and get an immersive audio experience across your entire app.</span></span>

<span data-ttu-id="645da-110">Der [**ElementSoundPlayer**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.elementsoundplayer) ist ein integriertes Soundsystem innerhalb von XAML, und wenn es aktiviert ist, spielen alle Standardsteuerelemente automatisch Sounds ab.</span><span class="sxs-lookup"><span data-stu-id="645da-110">The [**ElementSoundPlayer**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.elementsoundplayer) is an integrated sound system within XAML, and when turned on all default controls will play sounds automatically.</span></span>
```C#
ElementSoundPlayer.State = ElementSoundPlayerState.On;
```
<span data-ttu-id="645da-111">Der **ElementSoundPlayer** verfügt über drei Zustände: **Ein**, **Aus** und **Auto**.</span><span class="sxs-lookup"><span data-stu-id="645da-111">The **ElementSoundPlayer** has three different states: **On** **Off** and **Auto**.</span></span>

<span data-ttu-id="645da-112">In der Einstellung **Aus** wird unabhängig davon, wo Ihre App ausgeführt wird, niemals Sound wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="645da-112">If set to **Off**, no matter where your app is run, sound will never play.</span></span> <span data-ttu-id="645da-113">In der Einstellung **Ein** werden für Sounds für Ihre App auf jeder Plattform wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="645da-113">If set to **On** sounds for your app will play on every platform.</span></span>

<span data-ttu-id="645da-114">Das Aktivieren des ElementSoundPlayer ermöglicht automatisch räumliches Audio (3D-Sound).</span><span class="sxs-lookup"><span data-stu-id="645da-114">Enabling ElementSoundPlayer will automatically enable spatial audio (3D sound) as well.</span></span> <span data-ttu-id="645da-115">Um den 3D-Sound (während weiterhin der Sound eingeschaltet ist) zu deaktivieren, deaktivieren Sie die **SpatialAudioMode** vom ElementSoundPlayer:</span><span class="sxs-lookup"><span data-stu-id="645da-115">To disable 3D sound (while still keeping the sound on), disable the **SpatialAudioMode** of the ElementSoundPlayer:</span></span> 

```C#
ElementSoundPlayer.SpatialAudioMode = ElementSpatialAudioMode.Off
```

<span data-ttu-id="645da-116">Die **SpatialAudioMode**-Eigenschaft kann diese Werte erhalten:</span><span class="sxs-lookup"><span data-stu-id="645da-116">The **SpatialAudioMode** property can takes these values:</span></span> 
- <span data-ttu-id="645da-117">**Automatische**: räumliches Audio wird eingeschaltet, wenn der Ton eingeschaltet ist.</span><span class="sxs-lookup"><span data-stu-id="645da-117">**Auto**: Spatial audio will turn on when sound is on.</span></span> 
- <span data-ttu-id="645da-118">**Deaktiviert**: räumliches Audio ist immer ausgeschaltet, selbst wenn Sound eingeschaltet ist.</span><span class="sxs-lookup"><span data-stu-id="645da-118">**Off**: Spatial audio is always off, even if sound is on.</span></span>
- <span data-ttu-id="645da-119">**Ein**: räumliches Audio wird immer wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="645da-119">**On**: Spatial audio will always play.</span></span>

<span data-ttu-id="645da-120">Weitere Informationen zu räumlichem Audio und wie XAML diesen behandelt finden Sie unter [AudioGraph – räumliches Audio](/windows/uwp/audio-video-camera/audio-graphs#spatial-audio).</span><span class="sxs-lookup"><span data-stu-id="645da-120">To learn more about spatial audio and how XAML handles it see [AudioGraph - Spatial Audio](/windows/uwp/audio-video-camera/audio-graphs#spatial-audio).</span></span>

### <a name="sound-for-tv-and-xbox"></a><span data-ttu-id="645da-121">Sound für TV und Xbox</span><span class="sxs-lookup"><span data-stu-id="645da-121">Sound for TV and Xbox</span></span>

<span data-ttu-id="645da-122">Sound ist ein wesentlicher Bestandteil der 10-Fuß-Schnittstelle. Standardmäßig verwendet der **ElementSoundPlayer** den Zustand **Auto**, was bedeutet, dass Sound nur dann wiedergegeben wird, wenn Ihre App auf Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="645da-122">Sound is a key part of the 10-foot experience, and by default, the **ElementSoundPlayer**'s state is **Auto**, meaning that you will only get sound when your app is running on Xbox.</span></span>
<span data-ttu-id="645da-123">Weitere Informationen zur Funktionsweise von Sound für TV und Xbox finden Sie im Artikel [Entwerfen für Xbox und Fernsehgeräte](http://go.microsoft.com/fwlink/?LinkId=760736).</span><span class="sxs-lookup"><span data-stu-id="645da-123">To understand more about designing for Xbox and TV, please see [Designing for Xbox and TV](http://go.microsoft.com/fwlink/?LinkId=760736).</span></span>

## <a name="sound-volume-override"></a><span data-ttu-id="645da-124">Lautstärkeüberschreibung</span><span class="sxs-lookup"><span data-stu-id="645da-124">Sound Volume Override</span></span>

<span data-ttu-id="645da-125">Mit dem **Volume**-Steuerelement kann die Lautstärke aller Sounds innerhalb der App verringert werden.</span><span class="sxs-lookup"><span data-stu-id="645da-125">All sounds within the app can be dimmed with the **Volume** control.</span></span> <span data-ttu-id="645da-126">Allerdings können Sounds innerhalb der App nicht *lauter als die Systemlautstärke* werden.</span><span class="sxs-lookup"><span data-stu-id="645da-126">However, sounds within the app cannot get *louder than the system volume*.</span></span>

<span data-ttu-id="645da-127">Rufen Sie zum Festlegen der Lautstärke der App auf:</span><span class="sxs-lookup"><span data-stu-id="645da-127">To set the app volume level, call:</span></span>
```C#
ElementSoundPlayer.Volume = 0.5;
```
<span data-ttu-id="645da-128">Wobei die maximale Lautstärke (relativ zur Systemlautstärke) 1,0 ist und die minimale 0,0 ist (im Wesentlichen stumm).</span><span class="sxs-lookup"><span data-stu-id="645da-128">Where maximum volume (relative to system volume) is 1.0, and minimum is 0.0 (essentially silent).</span></span>

## <a name="control-level-state"></a><span data-ttu-id="645da-129">Zustand des Steuerungsgrads</span><span class="sxs-lookup"><span data-stu-id="645da-129">Control Level State</span></span>

<span data-ttu-id="645da-130">Wenn der Standardsound eines Steuerelements nicht erwünscht ist, kann er deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="645da-130">If a control's default sound is not desired, it can be disabled.</span></span> <span data-ttu-id="645da-131">Dies erfolgt über die **ElementSoundMode**-Option für das Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="645da-131">This is done through the **ElementSoundMode** on the control.</span></span>

<span data-ttu-id="645da-132">Die **ElementSoundMode**-Option verfügt über zwei Zustände: **Aus** und **Standard**.</span><span class="sxs-lookup"><span data-stu-id="645da-132">The **ElementSoundMode** has two states: **Off** and **Default**.</span></span> <span data-ttu-id="645da-133">Wenn nichts festgelegt wird, hat sie den Zustand **Standard**.</span><span class="sxs-lookup"><span data-stu-id="645da-133">When not set, it is **Default**.</span></span> <span data-ttu-id="645da-134">In der Einstellung **Aus** wird jeder Sound, der durch das Steuerelement wiedergegeben werden soll, stumm geschaltet, *außer der Fokus*.</span><span class="sxs-lookup"><span data-stu-id="645da-134">If set to **Off**, every sound that control plays will be muted *except for focus*.</span></span>

```XAML
<Button Name="ButtonName" Content="More Info" ElementSoundMode="Off"/>
```

```C#
ButtonName.ElementSoundState = ElementSoundMode.Off;
```

## <a name="is-this-the-right-sound"></a><span data-ttu-id="645da-135">Ist das der richtige Sound?</span><span class="sxs-lookup"><span data-stu-id="645da-135">Is This The Right Sound?</span></span>

<span data-ttu-id="645da-136">Beim Erstellen eines benutzerdefinierten Steuerelements oder Ändern des Sounds eines vorhandenen Steuerelements ist es wichtig zu verstehen, wie alle Sounds, die das System bietet, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="645da-136">When creating a custom control, or changing an existing control's sound, it is important to understand the usages of all the sounds the system provides.</span></span>

<span data-ttu-id="645da-137">Jeder Sound bezieht sich auf eine bestimmte grundlegende Benutzerinteraktion, und obwohl Sounds angepasst werden können, um bei einer Interaktion wiedergegeben zu werden, soll dieser Abschnitt die Szenarien erläutern, in denen Sounds verwendet werden sollten, um die Einheitlichkeit aller UWP-Apps zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="645da-137">Each sound relates to a certain basic user interaction, and although sounds can be customized to play on any interaction, this section serves to illustrate the scenarios where sounds should be used to maintain a consistent experience across all UWP apps.</span></span>

### <a name="invoking-an-element"></a><span data-ttu-id="645da-138">Aufrufen eines Elements</span><span class="sxs-lookup"><span data-stu-id="645da-138">Invoking an Element</span></span>

<span data-ttu-id="645da-139">Der in unserem System am häufigsten verwendete durch ein Steuerelement ausgelöste Sound ist der **Invoke**-Sound.</span><span class="sxs-lookup"><span data-stu-id="645da-139">The most common control-triggered sound in our system today is the **Invoke** sound.</span></span> <span data-ttu-id="645da-140">Dieser Sound wird wiedergegeben, wenn ein Benutzer mittels Tippen/Klicken/Eingabe/Leertaste oder Drücken der Taste "A" auf einem Gamepad ein Steuerelement aufruft.</span><span class="sxs-lookup"><span data-stu-id="645da-140">This sound plays when a user invokes a control through a tap/click/enter/space or press of the 'A' button on a gamepad.</span></span>

<span data-ttu-id="645da-141">In der Regel wird dieser Sound nur wiedergegeben, wenn ein Benutzer explizit ein einfaches Steuerelement oder ein Steuerelementteil über ein [Eingabegerät](../input/index.md) anzielt.</span><span class="sxs-lookup"><span data-stu-id="645da-141">Typically, this sound is only played when a user explicitly targets a simple control or control part through an [input device](../input/index.md).</span></span>

<span data-ttu-id="645da-142"><SelectButtonClick.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-142"><SelectButtonClick.mp3 sound clip here></span></span>

<span data-ttu-id="645da-143">Um diesen Sound von einem Steuerelementereignis aus wiederzugeben, rufen Sie einfach die Play-Methode aus dem **ElementSoundPlayer** auf und übergeben sie an **ElementSound.Invoke**:</span><span class="sxs-lookup"><span data-stu-id="645da-143">To play this sound from any control event, simply call the Play method from **ElementSoundPlayer** and pass in **ElementSound.Invoke**:</span></span>
```C#
ElementSoundPlayer.Play(ElementSoundKind.Invoke);
```

### <a name="showing--hiding-content"></a><span data-ttu-id="645da-144">Anzeigen und Ausblenden von Inhalten</span><span class="sxs-lookup"><span data-stu-id="645da-144">Showing & Hiding Content</span></span>

<span data-ttu-id="645da-145">In XAML gibt es viele Flyouts, Dialogfelder und leicht ausblendbare Benutzeroberflächen, und jede Aktion, die eine dieser Überlagerungen auslöst, sollte einen **Show**- oder **Hide**-Sound aufrufen.</span><span class="sxs-lookup"><span data-stu-id="645da-145">There are many flyouts, dialogs and dismissible UIs in XAML, and any action that triggers one of these overlays should call a **Show** or **Hide** sound.</span></span>

<span data-ttu-id="645da-146">Wenn ein Überlagerungs-Inhaltsfenster eingeblendet wird, sollte der **Show**-Sound aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="645da-146">When an overlay content window is brought into view, the **Show** sound should be called:</span></span>

<span data-ttu-id="645da-147"><OverlayIn.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-147"><OverlayIn.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.Show);
```
<span data-ttu-id="645da-148">Wenn dagegen ein Überlagerungs-Inhaltsfenster geschlossen wird (oder einfach ausgeblendet wird), sollte der **Hide**-Sound aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="645da-148">Conversely when an overlay content window is closed (or is light dismissed), the **Hide** sound should be called:</span></span>

<span data-ttu-id="645da-149"><OverlayOut.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-149"><OverlayOut.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.Hide);
```
### <a name="navigation-within-a-page"></a><span data-ttu-id="645da-150">Navigation innerhalb einer Seite</span><span class="sxs-lookup"><span data-stu-id="645da-150">Navigation Within a Page</span></span>

<span data-ttu-id="645da-151">Beim Navigieren zwischen Bereichen oder Ansichten innerhalb einer App-Seite (siehe [Hub](../controls-and-patterns/hub.md) oder [Registerkarten und Pivots](../controls-and-patterns/tabs-pivot.md)) gibt es in der Regel eine bidirektionale Bewegung.</span><span class="sxs-lookup"><span data-stu-id="645da-151">When navigating between panels or views within an app's page (see [Hub](../controls-and-patterns/hub.md) or [Tabs and Pivots](../controls-and-patterns/tabs-pivot.md)), there is typically bidirectional movement.</span></span> <span data-ttu-id="645da-152">Das bedeutet, dass Sie zur nächsten Ansicht bzw. zum nächsten Bereich (oder zur/zum vorherigen) wechseln können, ohne die aktuelle App-Seite zu verlassen, auf der Sie sich befinden.</span><span class="sxs-lookup"><span data-stu-id="645da-152">Meaning you can move to the next view/panel or the previous one, without leaving the current app page you're on.</span></span>

<span data-ttu-id="645da-153">Das Audioerlebnis für dieses Navigationskonzept wird durch die **MovePrevious**- und **MoveNext**-Sounds umgesetzt.</span><span class="sxs-lookup"><span data-stu-id="645da-153">The audio experience around this navigation concept is encompassed by the **MovePrevious** and **MoveNext** sounds.</span></span>

<span data-ttu-id="645da-154">Beim Wechsel zu einer Ansicht bzw. zu einem Bereich, die/der als das *nächste Element* in einer Liste gilt, rufen Sie auf:</span><span class="sxs-lookup"><span data-stu-id="645da-154">When moving to a view/panel that is considered the *next item* in a list, call:</span></span>

<span data-ttu-id="645da-155"><PageTransitionRight.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-155"><PageTransitionRight.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.MoveNext);
```
<span data-ttu-id="645da-156">Und beim Wechsel zu einer vorherigen Ansicht bzw. zu einem vorherigen Bereich in einer Liste, die/der als das *vorherige Element* gilt, rufen Sie auf:</span><span class="sxs-lookup"><span data-stu-id="645da-156">And when moving to a previous view/panel in a list considered the *previous item*, call:</span></span>

<span data-ttu-id="645da-157"><PageTransitionLeft.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-157"><PageTransitionLeft.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.MovePrevious);
```
### <a name="back-navigation"></a><span data-ttu-id="645da-158">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="645da-158">Back Navigation</span></span>

<span data-ttu-id="645da-159">Beim Navigieren von der aktuellen Seite zur vorherigen Seite innerhalb einer App sollte der **GoBack**-Sound aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="645da-159">When navigating from the current page to the previous page within an app the **GoBack** sound should be called:</span></span>

<span data-ttu-id="645da-160"><BackButtonClick.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-160"><BackButtonClick.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.GoBack);
```
### <a name="focusing-on-an-element"></a><span data-ttu-id="645da-161">Fokussieren auf ein Element</span><span class="sxs-lookup"><span data-stu-id="645da-161">Focusing on an Element</span></span>

<span data-ttu-id="645da-162">Der **Focus**-Sound ist der einzige implizite Sound in unserem System.</span><span class="sxs-lookup"><span data-stu-id="645da-162">The **Focus** sound is the only implicit sound in our system.</span></span> <span data-ttu-id="645da-163">Das heißt, dass ein Benutzer nicht mit irgendetwas direkt interagiert, jedoch trotzdem einen Sound hört.</span><span class="sxs-lookup"><span data-stu-id="645da-163">Meaning a user isn't directly interacting with anything, but is still hearing a sound.</span></span>

<span data-ttu-id="645da-164">Das Fokussieren geschieht, wenn ein Benutzer durch eine App navigiert– dies kann mit dem Gamepad, der Tastatur, der Fernbedienung oder mit Kinect geschehen.</span><span class="sxs-lookup"><span data-stu-id="645da-164">Focusing happens when a user navigates through an app, this can be with the gamepad/keyboard/remote or kinect.</span></span> <span data-ttu-id="645da-165">In der Regel wird der **Focus**-Sound *bei PointerEntered- oder Mauszeigeereignissen nicht wiedergegeben*.</span><span class="sxs-lookup"><span data-stu-id="645da-165">Typically the **Focus** sound *does not play on PointerEntered or mouse hover events*.</span></span>

<span data-ttu-id="645da-166">Um ein Steuerelement zur Wiedergabe des **Focus**-Sounds einzurichten, wenn Ihr Steuerelement den Fokus erhält, rufen Sie auf:</span><span class="sxs-lookup"><span data-stu-id="645da-166">To set up a control to play the **Focus** sound when your control receives focus, call:</span></span>

<span data-ttu-id="645da-167"><ElementFocus1.mp3 Audioclip hier></span><span class="sxs-lookup"><span data-stu-id="645da-167"><ElementFocus1.mp3 sound clip here></span></span>

```C#
ElementSoundPlayer.Play(ElementSoundKind.Focus);
```
### <a name="cycling-focus-sounds"></a><span data-ttu-id="645da-168">Wechseln zwischen Focus-Sounds</span><span class="sxs-lookup"><span data-stu-id="645da-168">Cycling Focus Sounds</span></span>

<span data-ttu-id="645da-169">Als zusätzliche Funktion zum Aufrufen von **ElementSound.Focus** wechselt das Soundsystem standardmäßig bei jedem Navigationsaufruf zwischen 4 unterschiedlichen Sounds.</span><span class="sxs-lookup"><span data-stu-id="645da-169">As an added feature to calling **ElementSound.Focus**, the sound system will, by default, cycle through 4 different sounds on each navigation trigger.</span></span> <span data-ttu-id="645da-170">Das bedeutet, dass keine zwei genau gleichen Focus-Sounds direkt nacheinander wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="645da-170">Meaning that no two exact focus sounds will play right after the other.</span></span>

<span data-ttu-id="645da-171">Diese Wechselfunktion soll verhindern, dass die Focus-Sounds monoton werden und durch den Benutzer nicht mehr wahrgenommen werden. Denn Focus-Sounds werden am häufigsten wiedergegeben und sollten daher möglichst unaufdringlich sein.</span><span class="sxs-lookup"><span data-stu-id="645da-171">The purpose behind this cycling feature is to keep the focus sounds from becoming monotonous and from being noticeable by the user; focus sounds will be played most often and therefore should be the most subtle.</span></span>

## <a name="related-articles"></a><span data-ttu-id="645da-172">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="645da-172">Related articles</span></span>

* [<span data-ttu-id="645da-173">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="645da-173">Designing for Xbox and TV</span></span>](http://go.microsoft.com/fwlink/?LinkId=760736)
* [<span data-ttu-id="645da-174">Dokumentation zur ElementSoundPlayer-Klasse</span><span class="sxs-lookup"><span data-stu-id="645da-174">ElementSoundPlayer class documentation</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.elementsoundplayer)
