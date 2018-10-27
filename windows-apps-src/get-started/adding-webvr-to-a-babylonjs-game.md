---
title: Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen
description: Hier erfahren Sie, wie ein vorhandenes 3D Babylon.js-Spiel WebVR Unterstützung hinzugefügt.
author: abbycar
ms.author: abigailc
ms.date: 11/29/2017
ms.topic: article
keywords: Webvr, Edge, Webentwicklung, Babylon, Babylonjs, babylon.js, javascript
ms.localizationpriority: medium
ms.openlocfilehash: 72681c3f91fc2dcbfcc4e4531359d6d668e18b80
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5698171"
---
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a>Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen

Wenn Sie ein 3D-Spiel mit Babylon.js erstellt und davon ausgegangen, dass es in virtual-Reality (VR) gut aussehen könnte haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.

Wir werden das hier gezeigte Spiel WebVR Unterstützung hinzufügen. Fahren Sie fort, und schließen Sie Xbox-Controller ausprobieren!


<iframe height='300' scrolling='no' title='Mithilfe von Babylon.GUI Babylon.js Dino-Spiel' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter der Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino-Spiel Babylon.GUI mithilfe</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>

Dies ist ein 3D-Spiel, das funktioniert gut auf eine flache Bildschirm, aber was über in VR?
In diesem Lernprogramm verwenden wir den Schritten es dauert dies Einstieg und das Ausführung mit WebVR durchlaufen. Wir verwenden ein [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) -Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge nutzen können. Nachdem wir diese Änderungen für das Spiel angewendet haben, können Sie es auch in anderen Browser/Kopfhörer Kombinationen funktioniert, die WebVR unterstützen erwarten.



## <a name="prerequisites"></a>Voraussetzungen

- Einem Text-Editor (z. B. [Visual Studio Code](https://code.visualstudio.com/download))
- Xbox-Controller, der an den Computer angeschlossen ist
- Windows10 Creators Update
- Auf einem Computer mit den [mindestens erforderlichen Spezifikationen zum Ausführen von Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)
- Ein Windows Mixed Reality-Gerät (Optional) 



## <a name="getting-started"></a>Erste Schritte

Die einfachste Möglichkeit zum Einstieg ist, besuchen das [Windows-Lernprogramme-Web-GitHub-Repository](https://github.com/Microsoft/Windows-tutorials-web), drücken Sie die grüne **Klonen oder Herunterladen** Schaltfläche, und wählen Sie **in Visual Studio geöffnet**.

![Schaltfläche „clone or download“](images/3dclone.png)

Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.
Sie haben dann zwei Ordnern, [vor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nach](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after). Der Ordner "vor" ist unser Spiel, bevor alle VR-Features hinzugefügt werden, und der Ordner "nach" das fertiges Spiel mit VR-Unterstützung ist.

Die vor und nach dem Ordner diese Dateien enthalten:
-   **Texturen /** – ein Ordner, die im Spiel verwendeten Bilder enthält.
-   **Css /** – ein Ordner mit den CSS-Code für das Spiel.
-   **Js /** – ein Ordner mit den JavaScript-Dateien. Die main.js-Datei ist unser Spiel, und die anderen Dateien sind die Bibliotheken verwendet.
-   **Modelle /** – ein Ordner mit den 3D-Modellen. Für dieses Spiel gibt es nur ein Modell für den Dinosaurier.
-   **index.html** – die Webseite, die den Spiel Renderer hostet. Diese Seite in Microsoft Edge öffnet, startet das Spiel.

Sie können beide Versionen des Spiels testen, öffnen Sie dazu ihre jeweiligen "Index.HTML" Dateien in Microsoft Edge.



## <a name="the-mixed-reality-portal"></a>Das Mixed Reality-Portal

Wenn Sie noch keine Erfahrung mit Windows Mixed Reality sind und Windows 10 Creators Update auf einem Computer mit einem kompatiblen Grafikkarte installiert haben, versuchen Sie, öffnen die **Mixed Reality-Portal** -app aus dem Menü "Start" in Windows 10.

![Mixed Reality-Portal-Suche](images/mixed-reality-portal.png)

Wenn Sie alle Anforderungen erfüllt, können Sie dann Entwicklerfeatures aktivieren und simulieren einer Windows Mixed Reality-Kopfhörer an den Computer angeschlossen. Wenn Sie Glück, eine tatsächliche Kopfhörer in der Nähe sind, schließen Sie es, und führen Sie das Setup.

> [!IMPORTANT]
> Mixed Reality-Portals müssen immer während dieses Lernprogramms geöffnet sein.

Sie nun können WebVR mit Microsoft Edge auftreten.

## <a name="2d-ui-in-a-virtual-world"></a>2D-UI in einer virtuellen Welt

>[!NOTE]
> Beziehen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter abrufen.

[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR-freundliche, aktivieren Sie zum einfachen erstellen, interaktive Benutzeroberflächen, eignen sich gut für VR und nicht-VR angezeigt.
Eine Erweiterung von Babylon.js die `GUI` Bibliothek ist verwendete Throuhout im Beispiel 2D Elemente erstellen.


Ein 2D Text `GUI` Element mit wenigen Zeilen je nachdem, wie viele Attribute Pufferverhalten zu erstellt werden.
Der folgende Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir Exemplarische Vorgehensweise, was passiert.
Wir stellen Sie zunächst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI behandelt wird. Das Beispiel legt diese auf `CreateFullScreenUI()`, d. h. der Benutzeroberfläche deckt den gesamten Bildschirm. Mit `AdvancedDynamicTexture` erstellt, wir stellen Sie dann ein 2D Text-Feld, das angezeigt wird beim Starten das Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.


Dieser Code wird in [**"Main.js"**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168)hinzugefügt.
```javascript
// GUI
var advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI");

// Start UI
startUI = new BABYLON.GUI.Rectangle("start");
startUI.background = "black"
startUI.alpha = .8;
startUI.thickness = 0;
startUI.height = "60px";
startUI.width = "400px";
advancedTexture.addControl(startUI); 
var tex2 = new BABYLON.GUI.TextBlock();
tex2.text = "Stay away from the dinosaur! \n Plug in an Xbox controller and press A to start";
tex2.color = "white";
startUI.addControl(tex2); 
```


Diese Benutzeroberfläche ist sichtbar, nachdem erstellt, aber kann aktiviert oder deaktiviert umgeschaltet werden, mit `isVisible` je nachdem, was im Spiel ausgeführt wird.
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a>Erkennen von headsets

Es ist üblich, VR Applications zwei Arten von Kameras verfügen, damit mehrere Szenarien unterstützt werden können. Für dieses Spiel müssen wir eine Kamera, die erfordert eine funktionierende Kopfhörer zu angeschlossen sein, und eine andere unterstützen, die keine Kopfhörer verwendet. Um zu ermitteln, welches wird das Spiel verwenden müssen wir zunächst überprüfen, ob ein Kopfhörer erkannt wurde. Dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).


Fügen Sie diesen Code oben `window.addEventListener('DOMContentLoaded')` in **"Main.js"**.
```javascript
var headset;
// If a VR headset is connected, get its info
navigator.getVRDisplays().then(function (displays) {
    if (displays[0]) {
        headset = displays[0];
    }
});
```

Mit den in gespeicherten Informationen der `headset` Variable, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer geeignet ist.


## <a name="creating-and-selecting-the-initial-camera"></a>Erstellen und Auswählen der anfänglichen Kamera

Mit Babylon.js, WebVR hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera). Diese Kamera kann Eingaben über die Tastatur und ermöglicht es Ihnen, eine VR Kopfhörer verwenden, um Ihre Drehung "Head" steuern.


### <a name="step-1-checking-for-headsets"></a>Schritt 1: Suchen nach headsets

Für unsere fallback Kamera verwenden wir die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit im ursprünglichen Spiel verwendet wird.

Überprüfen wir unsere `headset` Variable, um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.

Ersetzen Sie `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` durch den folgenden Code.
```javascript
        if(headset){
            // Create a WebVR camera with the trackPosition property set to false so that we can control movement with the gamepad
            camera = new BABYLON.WebVRFreeCamera("vrcamera", new BABYLON.Vector3(0, 14, 0), scene, true, { trackPosition: false });
            camera.deviceScaleFactor = 1;
        } else {
            // No headset, use universal camera
            camera = new BABYLON.UniversalCamera("camera", new BABYLON.Vector3(0, 18, -45), scene);
        }
```


### <a name="step-2-activating-the-webvrfreecamera"></a>Schritt 2: Aktivieren der WebVRFreeCamera
Um diese Kamera in den meisten Browsern zu aktivieren, muss der Benutzer einige Eingaben durchführen, die die virtuelle Umgebung anfordert.
Wir binden diese Funktionalität bis zu einem Mausklick.


Fügen Sie den Code in `createScene()` funktionieren, nachdem `camera.applyGravity = true;` .
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

Ein Klick in das Spiel jetzt erstellt eine Aufforderung wie folgt oder zeigt das Spiel in die Kopfhörer sofort, wenn der Benutzer die Aufforderung vor dem akzeptiert hat.

![immersiven Aufforderung](images/immersiveview.png)

Wir können auch einen Codeabschnitt, der angezeigt wird Hinzufügen der `UniversalCamera` anzeigen, bevor wir zu wechseln unsere `WebVRFreeCamera`, so dass der Benutzer das Spiel anstatt ein blaues Fenster betrachten. 

Fügen Sie Folgendes nach `engine.runRenderLoop(function () {`.
```javascript
            if (headset) {
                if (!(headset.isPresenting)) {
                    var camera2 = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);
                    scene.activeCamera = camera2;
                } else {
                    scene.activeCamera = camera;
                }
            }
```

### <a name="step-3-adding-gamepad-support"></a>Schritt 3: Hinzufügen von Gamepad-Unterstützung

Da die `WebVRFreeCamera` unterstützt keine anfänglich Gamepads, müssen wir unsere Gamepad-Tasten die Pfeiltasten der Tastatur zugeordnet. Wir werden dies tun, indem eine Suche in der `inputs` -Eigenschaft der Kamera. Durch das Hinzufügen der Codes für die linken analogstick nach oben, unten, links und rechts übereinstimmen, mit den Pfeiltasten, ist unsere Gamepad zurück in Aktion zu sehen.


Fügen Sie diesen Code unten die `scene.onPointerDown = function() {...}` aufrufen.
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a>Schritt 4: Versuchen Sie es!

Wenn wir **"Index.HTML"** mit unserem Kopfhörer öffnen und Gamecontroller angeschlossen, wechselt linken klicken auf das blaue Spielfenster VR-Modus unser Spiel! Fahren Sie fort, und versehen Sie Ihre Kopfhörer auf die Ergebnisse in Betracht ziehen. 


<iframe height='300' scrolling='no' title='Mithilfe von Babylon.GUI - WebVR Babylon.js Dino-Spiel' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino-Spiel mit Babylon.GUI - WebVR</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>


## <a name="conclusion"></a>Fazit

Herzlichen Glückwunsch! Sie haben nun ein vollständiges Babylon.js-Spiel mit WebVR Unterstützung. Hier können Sie nutzen, was Sie zum Erstellen eines Spiels noch besseren oder zum Deaktivieren dieser build gelernt haben.
