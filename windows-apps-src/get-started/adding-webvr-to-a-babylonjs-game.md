---
title: Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen
description: Erfahren Sie, wie ein vorhandenes 3D Babylon.js-Spiel WebVR Unterstützung hinzu.
ms.date: 11/29/2017
ms.topic: article
keywords: Webvr, Edge, Webentwicklung, Babylon, Babylonjs, babylon.js, javascript
ms.localizationpriority: medium
ms.openlocfilehash: 3e2081f0dbe163dcbcf35d83ea111caf573dacfb
ms.sourcegitcommit: 231065c899d0de285584d41e6335251e0c2c4048
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8828097"
---
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a>Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen

Wenn Sie davon ausgegangen, dass es in virtual-Reality (VR) gut aussehen könnte und -3D-Spielen mit Babylon.js erstellt haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.

Wir werden WebVR Unterstützung für das Spiel hier hinzufügen. Einfach, und schließen Sie Xbox-Controller ausprobieren!


<iframe height='300' scrolling='no' title='Babylon.js Dino-Spiel mit Babylon.GUI' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter der Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino-Spiel Babylon.GUI mithilfe</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>

Dies ist ein 3D-Spiel, auf eine flache Bildschirm, aber was zu funktioniert, in VR?
In diesem Lernprogramm verwenden wir die Schritte es dauert, um sich zu erhalten und mit WebVR durchlaufen. Wir verwenden ein [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) -Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge nutzen können. Nachdem wir diese Änderungen für das Spiel angewendet haben, können Sie davon ausgehen, dass es auch in anderen Browser/Kopfhörer Kombinationen funktioniert, die WebVR zu unterstützen.



## <a name="prerequisites"></a>Voraussetzungen

- Einem Text-Editor (z. B. [Visual Studio Code](https://code.visualstudio.com/download))
- Xbox-Controller, der an den Computer angeschlossen ist
- Windows10 Creators Update
- Ein Computer mit den [mindestens erforderlichen Spezifikationen zum Ausführen von Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)
- Ein Windows Mixed Reality-Gerät (Optional) 



## <a name="getting-started"></a>Erste Schritte

Die einfachste Möglichkeit zum Einstieg ist, das [Windows-Lernprogramme-Web-GitHub-Repository](https://github.com/Microsoft/Windows-tutorials-web), drücken Sie die grüne **Clone or Download** besuchen, die Schaltfläche, und wählen Sie **in Visual Studio öffnen**.

![Schaltfläche „clone or download“](images/3dclone.png)

Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.
Sie haben dann zwei Ordner, [vor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nach](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after). Der Ordner "vorher" ist unser Spiel, bevor alle VR-Features hinzugefügt werden, und der Ordner "nach" das fertiges Spiel mit VR-Unterstützung ist.

Die vor und nach dem Ordner diese Dateien enthalten:
-   **Texturen /** – ein Ordner, die im Spiel verwendeten Bilder enthält.
-   **Css /** – ein Ordner mit den CSS-Code für das Spiel.
-   **Js /** – ein Ordner mit den JavaScript-Dateien. Die main.js-Datei ist unser Spiel, und die anderen Dateien sind die Bibliotheken verwendet.
-   **Modelle /** – ein Ordner mit den 3D-Modellen. Für dieses Spiel haben wir nur ein Modell für den Dinosaurier.
-   **index.html** – die Webseite, die den Spiel Renderer hostet. Diese Seite in Microsoft Edge öffnet, startet das Spiel.

Sie können beide Versionen des Spiels, testen, ihre jeweiligen index.html Dateien im Microsoft Edge geöffnet.



## <a name="the-mixed-reality-portal"></a>Das Mixed Reality-Portal

Wenn Sie noch keine Erfahrung mit Windows Mixed Reality und Windows 10 Creators Update auf einem Computer mit einem kompatiblen Grafikkarte installiert haben, versuchen Sie, öffnen die **Mixed Reality-Portal** -app aus dem Menü "Start" in Windows 10.

![Mixed Reality-Portal-Suche](images/mixed-reality-portal.png)

Wenn Sie alle Anforderungen erfüllt, können Sie dann Entwicklerfeatures aktivieren und simulieren einer Windows Mixed Reality-Kopfhörer, die an den Computer angeschlossen. Wenn Sie Glück, eine tatsächliche Kopfhörer in der Nähe sind, schließen Sie es, und führen Sie das Setup.

> [!IMPORTANT]
> Mixed Reality-Portals muss in diesem Lernprogramm immer geöffnet sein.

Sie nun können WebVR mit Microsoft Edge auftreten.

## <a name="2d-ui-in-a-virtual-world"></a>2D UI in einer virtuellen Welt

>[!NOTE]
> Beziehen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter abrufen.

[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR-freundliche, aktivieren Sie zum einfachen erstellen, interaktive Benutzeroberflächen, die gut für VR funktionieren und nicht-VR anzeigt.
Eine Erweiterung von Babylon.js die `GUI` Bibliothek ist verwendete Throuhout im Beispiel 2D Elemente erstellen.


Ein 2D Text `GUI` Element erstellt werden kann, mit wenigen Zeilen, je nachdem, wie viele Attribute, die Sie optimieren möchten.
Der folgende Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir Exemplarische Vorgehensweise, was passiert.
Wir müssen Sie zuerst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI behandelt wird. Das Beispiel legt diese auf `CreateFullScreenUI()`, d. h. der Benutzeroberfläche deckt den gesamten Bildschirm. Mit `AdvancedDynamicTexture` erstellt, wir stellen ein 2D Text-Feld, das angezeigt wird beim Starten das Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.


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


Dieser Benutzeroberfläche wird angezeigt, nachdem Sie erstellt wurde, jedoch können werden ein- oder mit `isVisible` je nachdem, was im Spiel ausgeführt wird.
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a>Erkennen von headsets

Es ist üblich, VR-Anwendungen auf zwei Arten von Kameras verfügen, sodass mehrere Szenarien unterstützt werden können. Für dieses Spiel müssen wir eine Kamera, die erfordert eine funktionierende Kopfhörer zu angeschlossen sein, und eine andere unterstützen, die keine Kopfhörer verwendet. Um zu ermitteln, welche wird das Spiel verwenden müssen wir zunächst überprüfen, ob ein Kopfhörer erkannt wurde. Dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).


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

Mit den Informationen gespeichert werden, der `headset` Variable, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer geeignet ist.


## <a name="creating-and-selecting-the-initial-camera"></a>Erstellen und Auswählen der Kamera

Mit Babylon.js, WebVR hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera). Diese Kamera kann Eingaben über die Tastatur und ermöglicht es Ihnen, eine VR-Kopfhörer verwenden, um Ihre Drehung "Head" zu steuern.


### <a name="step-1-checking-for-headsets"></a>Schritt 1: Überprüfen headsets

Für die fallback-Kamera, verwenden wir die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit in der ursprünglichen Spiel verwendet wird.

Überprüfen wir unsere `headset` Variable, um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.

Ersetzen Sie `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` mit dem folgenden Code.
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
Um diese Kamera in den meisten Browsern zu aktivieren, muss der Benutzer einige Eingaben durchführen, die die virtuelle Erfahrung anfordert.
Wir werden diese Funktion bis zu einem Mausklick zu verknüpfen.


Fügen Sie den Code in `createScene()` Funktion nach `camera.applyGravity = true;` .
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

Ein Klicken Sie auf das Spiel jetzt erstellt eine Aufforderung wie folgt oder zeigt das Spiel in die Kopfhörer sofort, wenn der Benutzer die Aufforderung vor dem akzeptiert hat.

![immersiven Aufforderung](images/immersiveview.png)

Wir können auch Hinzufügen von Code, der angezeigt wird die `UniversalCamera` anzeigen, bevor wir zu wechseln unsere `WebVRFreeCamera`, sodass der Benutzer das Spiel anstatt ein blaues Fenster betrachten. 

Fügen Sie die folgenden nach `engine.runRenderLoop(function () {`.
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

Da die `WebVRFreeCamera` unterstützt keine anfänglich Gamepads, werden wir unsere Gamepad-Tasten die Pfeiltasten der Tastatur zugeordnet. Wir werden dies tun, indem eine Suche in der `inputs` Eigenschaft der Kamera. Hinzufügen von der Codes für den linken Joystick nach oben, unten, links und rechts übereinstimmen, mit den Pfeiltasten, ist unsere Gamepad zurück in Aktion zu sehen.


Fügen Sie diesen Code unten die `scene.onPointerDown = function() {...}` aufrufen.
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a>Schritt 4: Versuchen Sie es!

Wenn wir **"Index.HTML"** mit unseren Kopfhörer öffnen und Gamecontroller angeschlossen, wird eine klicken Sie auf das blaue Spielfenster unser Spiel VR-Modus wechseln! Fahren Sie fort, und fügen Sie auf Ihre Kopfhörer, um die Ergebnisse zu überprüfen. 


<iframe height='300' scrolling='no' title='Babylon.js Dino-Spiel mit Babylon.GUI - WebVR' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino-Spiel mit Babylon.GUI - WebVR</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>


## <a name="conclusion"></a>Fazit

Herzlichen Glückwunsch! Sie haben nun ein vollständiges Babylon.js-Spiel mit WebVR-Unterstützung. Hier können Sie nutzen, was Sie gelernt haben, erstellen ein noch besseres Spiel oder Deaktivieren dieser erstellt.
