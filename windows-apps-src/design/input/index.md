---
description: Optimieren Sie Ihre App für den Stift, Surface Dial und andere Eingabetypen.
title: Eingabe und Interaktionen
keywords: App-Eingaben, Anpassen einer UWP-Anwendung
label: Input and interactions
layout: LandingPage
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
ms.assetid: b771d452-c3ac-4d97-8482-eaf81bf34306
ms.localizationpriority: medium
ms.openlocfilehash: 4f66d808cafcc6fba89cebde352d191335068925
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8897306"
---
# <a name="input-and-interactions"></a>Eingabe und Interaktionen

<!-- <div>
  <img src="images/keyboard/keyboard-hero.jpg" alt="" />
  <img src="images/input-interactions/icons-inputdevices03.png" />
</div> -->

UWP-Apps verarbeiten automatisch eine Vielzahl von Eingaben und können auf zahlreichen Geräten ausgeführt werden. Sie müssen daher keine zusätzlichen Schritte zum Aktivieren der Toucheingabe ausführen. Unter Umständen möchten Sie jedoch Ihre App für bestimmte Eingabe- oder Gerätearten optimieren. Beim Erstellen einer Zeichen-App möchten Sie vielleicht die Behandlung der Stifteingabe anpassen.

Die Design- und Codierungsanweisungen in diesem Abschnitt unterstützen Sie beim Anpassen Ihrer UWP-App für bestimmte Eingabetypen.

<ul class="panelContent cardsH" style="margin-left: 1px">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <!-- <div class="cardImageOuter">
                        <div class="cardImage" style="background-color: #f2f2f2" >
                        <a href="input-primer.md">
                            <img src="images/input-interactions/icons-inputdevices03.png" alt=" " style="display: block; width: 100%; height: auto;" />
                            </a>
                        </div>
                    </div>  -->
                    <div class="cardText">
                        <h3><a href="input-primer.md">Einführung in Eingaben</a></h3>
                        <p>Machen Sie sich mit den verschiedenen Arten von Eingabegeräten sowie ihren Verhaltensweisen, Möglichkeiten und Einschränkungen in Verbindung mit bestimmten Formfaktoren vertraut.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <!-- <div class="cardImageOuter">
                        <div class="cardImage" style="background-color: #f2f2f2">
                        <a href="identify-input-devices.md">
                            <img src="images/landing-page/fluentdesign-app-sm.png" alt=" " style="display: block; width: 100%; height: auto;"/>
                            </a>
                        </div>
                    </div> -->
                    <div class="cardText">
                        <h3><a href="gaze-interactions.md">NEU! Eingabe via Anvisieren</a></h3>
                        <p>Sie können den Blick eines Benutzers anhand von Ort und Bewegung von Augen und Kopf verfolgen.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

<!-- 
## Input primer

See our <b>[Input primer](index.md)</b> to familiarize yourself with each input device type and its behaviors, capabilities, and limitations when paired with certain form factors. -->


<ul class="panelContent cardsL" style="margin-left: 1px">
    <li>              
        <div style="display:block" class="cardSize">
            <div style="display:block" class="cardPadding">
                <div style="display:block" class="card">
                    <div style="display:block" class="cardText">
                        <h3>Eingabe</h3>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/identify-input-devices">Identifizieren von Eingabegeräten</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/handle-pointer-input">Zeiger</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/pen-and-stylus-interactions">Stift und Windows Ink</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/touch-interactions">Toucheingabe</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/mouse-interactions">Maus</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/keyboard-interactions">Tastatur</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/gamepad-and-remote-interactions">Gamepad und Fernbedienung</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/touchpad-interactions">Touchpad</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/windows-wheel-interactions">Surface Dial</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/multiple-input-design-guidelines">Mehrfacheingaben</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/input-injection">Eingabeeinfügung</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/custom-text-input">Benutzerdefinierte Texteingabe</a></p>                        
                    </div>
                </div>
            </div>
        </div>        
    </li>  
    <li>              
        <div style="display:block" class="cardSize">
            <div style="display:block" class="cardPadding">
                <div style="display:block" class="card">
                    <div style="display:block" class="cardText">
                        <h3>Interaktionen</h3>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/drag-and-drop">Drag&Drop</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/guidelines-for-panning">Verschiebung</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/guidelines-for-rotation">Drehung</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/guidelines-for-textselection">Auswählen von Text und Bildern</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/guidelines-for-targeting">Zielbestimmung</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/guidelines-for-visualfeedback">Visuelles Feedback</a></p>
                    </div>
                </div>
            </div>
        </div>        
    </li>
    <li>              
        <div style="display:block" class="cardSize">
            <div style="display:block" class="cardPadding">
                <div style="display:block" class="card">
                    <div style="display:block" class="cardText">
                        <h3>Sprache und KI</h3>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/speech-interactions">Sprache</a></p>
                        <p style="display: block;"><a  href="/windows/uwp/design/input/cortana-interactions">Cortana</a></p>  
                    </div>
                </div>
            </div>
        </div>        
    </li>            
       
</ul>

<!-- <div class="side-by-side">
<div class="side-by-side-content">
<p>
<b>[Surface Dial](windows-wheel-interactions.md)</b><br/>
Learn how to integrate this brand new category of input device into your Windows apps.</br>
This device is intended as a secondary, multi-modal input device that complements or modifies input from a primary device.
</p>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Cortana](cortana-interactions.md)</b><br/>
Extend the basic functionality of Cortana with voice commands that launch and execute a single action in an external application.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Speech](speech-interactions.md)</b><br/>
Integrate speech recognition and text-to-speech (also known as TTS, or speech synthesis) directly into the user experience of your app.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Pen](pen-and-stylus-interactions.md)</b><br/>
Optimize your UWP app for pen input to provide both standard pointer device functionality and the best Windows Ink experience for your users.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Keyboard](keyboard-interactions.md)</b><br/>
Keyboard input is an important part of the overall user interaction experience for apps. The keyboard is indispensable to people with certain disabilities or users who just consider it a more efficient way to interact with an app.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Touch](touch-interactions.md)</b><br/>
UWP includes a number of different mechanisms for handling touch input, all of which enable you to create an immersive experience that your users can explore with confidence.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Touchpad](touchpad-interactions.md)</b><br/>
A touchpad combines both indirect multi-touch input with the precision input of a pointing device, such as a mouse. This combination makes the touchpad suited to both a touch-optimized UI and the smaller targets of productivity apps.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Mouse](mouse-interactions.md)</b><br/>
Mouse input is best suited for user interactions that require precision when pointing and clicking. This inherent precision is naturally supported by the UI of Windows, which is optimized for the imprecise nature of touch.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Gamepad and remote control](gamepad-and-remote-interactions.md)</b><br/>
UWP apps now support gamepad and remote control input. Gamepads and remote controls are the primary input devices for Xbox and TV experiences.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<p>
<b>[Multiple inputs](multiple-input-design-guidelines.md)</b><br/>
To accommodate as many users and devices as possible, we recommend that you design your apps to work with as many input types as possible (gesture, speech, touch, touchpad, mouse, and keyboard). Doing so will maximize flexibility, usability, and accessibility.
</p>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Identify input devices](identify-input-devices.md)</b><br/>
Identify the input devices connected to a Universal Windows Platform (UWP) device and identify their capabilities and attributes.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Handle pointer input](handle-pointer-input.md)</b><br/>
Receive, process, and manage input data from pointing devices, such as touch, mouse, pen/stylus, and touchpad, in Universal Windows Platform (UWP) apps.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p><b>[Custom text input](custom-text-input.md)</b><br/>
The core text APIs in the Windows.UI.Text.Core namespace enable a UWP app to receive text input from any text service supported on Windows devices. This enables the app to receive text in any language and from any input type, like keyboard, speech, or pen.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Selecting text and images](guidelines-for-textselection.md)</b><br/>
This article describes selecting and manipulating text, images, and controls and provides user experience guidelines that should be considered when using these mechanisms in your apps.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<p>
<b>[Panning](guidelines-for-panning.md)</b><br/>
Panning or scrolling lets users navigate within a single view, to display the content of the view that does not fit within the viewport.
</p>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p>
<b>[Optical zoom and resizing](guidelines-for-optical-zoom.md)</b><br/>
This article describes Windows zooming and resizing elements and provides user experience guidelines for using these interaction mechanisms in your apps.
</p>
</div>
<div class="side-by-side-content-right">
<p>
<b>[Rotation](guidelines-for-rotation.md)</b><br/>
This article describes the new Windows UI for rotation and provides user experience guidelines that should be considered when using this new interaction mechanism in your UWP app.
</p>
</div>
</div>
</div>

<div class="side-by-side">
<div class="side-by-side-content">
<div class="side-by-side-content-left">
<p><b>[Targeting](guidelines-for-targeting.md)</b><br/>
Touch targeting in Windows uses the full contact area of each finger that is detected by a touch digitizer. The larger, more complex set of input data reported by the digitizer is used to increase precision when determining the user's intended (or most likely) target.
</p>
</div>
<div class="side-by-side-content-right">
<p><b>[Visual feedback](guidelines-for-visualfeedback.md)</b><br/>
Use visual feedback to show users when their interactions are detected, interpreted, and handled. Visual feedback can help users by encouraging interaction. It indicates the success of an interaction, which improves the user's sense of control. It also relays system status and reduces errors.
</p>
</div>
</div>
</div> -->


