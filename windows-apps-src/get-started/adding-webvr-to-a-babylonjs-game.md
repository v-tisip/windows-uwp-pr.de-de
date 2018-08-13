---
title: Hinzufügen der Unterstützung von WebVR mit einem 3D Babylon.js Spiel
description: Hier erfahren Sie, wie eine vorhandene 3D Babylon.js Spiel WebVR Unterstützung hinzugefügt.
author: abbycar
ms.author: abigailc
ms.date: 11/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Webvr, Edge, Webentwicklung, Babylon, Babylonjs, babylon.js, javascript
ms.localizationpriority: medium
ms.openlocfilehash: 41665e8719493bb658f9926947061b1b5f81a139
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1018650"
---
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a>Hinzufügen der Unterstützung von WebVR mit einem 3D Babylon.js Spiel

Wenn Sie davon ausgegangen, dass es hervorragend für virtuelle Realität (VR) aussehen könnte und ein 3D Spiel mit Babylon.js erstellt haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.

Wir werden mit dem hier dargestellten Spiel WebVR Unterstützung hinzufügen. Fahren Sie fort, und schließen Sie eine Xbox Controller ausprobieren!


<iframe height='300' scrolling='no' title='Babylon.js Dino Spiel mit Babylon.GUI' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter dem Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino Spiel mit Babylon.GUI</a> durch Microsoft-Edge-Dokumente (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>

Dies ist ein 3D Spiel, die auch auf einem flachen Bildschirm, aber was zu funktioniert in VR?
In diesem Lernprogramm werden wir den Schritten es dauert dies Einstieg und mit WebVR durchlaufen. Wir verwenden eine [Gemischte Realität Windows](https://developer.microsoft.com/en-us/windows/mixed-reality) Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge hinzugefügt nutzen können. Nachdem wir diese Änderungen auf dem Spiel anwenden möchten, können Sie davon ausgehen es auch in andere Browser/Kopfhörer Kombinationen aus arbeiten, die WebVR unterstützen.



## <a name="prerequisites"></a>Voraussetzungen

- Einen Text-Editor (wie [Visual Studio-Code](https://code.visualstudio.com/download))
- Ein Xbox Domänencontroller, der an Ihren Computer angeschlossen ist
- Windows10 Creators Update
- Einen Computer mit den [mindestens erforderlichen Spezifikationen gemischten Realität Windows ausführen](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)
- Eine gemischte Realität Windows-Gerät (Optional) 



## <a name="getting-started"></a>Erste Schritte

Die einfachste Möglichkeit zum Einstieg ist die [Windows-Lernprogramme-Web GitHub Repo](https://github.com/Microsoft/Windows-tutorials-web)besuchen, drücken Sie die grüne **Clone oder Download** Schaltfläche aus, und wählen Sie **in Visual Studio öffnen**.

![Schaltfläche „clone or download“](images/3dclone.png)

Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.
Sie müssen Sie zwei Ordner, [bevor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nachdem](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after). Der Ordner "vor" ist unsere Spiel, bevor alle VR Features hinzugefügt wurden, und der Ordner "nach" das fertige Spiel mit VR Support ist.

Die vor und nach dem Ordner diese Dateien enthalten:
-   **Strukturen /** – ein Ordner, in das Spiel verwendete Bilder enthält.
-   **Css /** – einen Ordner mit den CSS-Code für das Spiel.
-   **Js /** – einen Ordner mit der JavaScript-Dateien. Die Datei main.js ist unsere Spiel, und die anderen Dateien sind die verwendeten Bibliotheken.
-   **Modelle /** – einen Ordner mit der 3D Modelle. Für dieses Spiel müssen wir nur ein Modell für die Dinosaur.
-   **index.html** - die Webseite, die das Spiel Renderer gehostet wird. Öffnen auf dieser Seite in Microsoft Edge startet das Spiel.

Sie können beide Versionen des Spiels testen, indem Sie ihre jeweiligen index.html-Dateien in Microsoft Edge öffnen.



## <a name="the-mixed-reality-portal"></a>Das Portal gemischten Realität

Wenn Sie mit Windows gemischten Realität nicht vertraut sind und die Windows 10 Ersteller-Updates auf einem Computer mit eine kompatible Grafikkarte installiert haben, versuchen Sie die **Gemischte Realität Portal** app über das Startmenü in Windows 10 zu öffnen.

![Gemischte Realität Portal-Suche](images/mixed-reality-portal.png)

Wenn Sie alle Anforderungen erfüllt, können Sie dann Funktionen für Entwickler aktivieren und die simulieren einer gemischten Windows-Realität Kopfhörer an Ihren Computer angeschlossen. Wenn Sie Glück, in der Nähe eines tatsächlichen Kopfhörer sind, schließen Sie es, und führen Sie Setup.

> [!IMPORTANT]
> Die gemischte Realität Portal müssen jederzeit während dieses Lernprogramm geöffnet sein.

Sie nun können WebVR mit Microsoft-Edge-Umgebung zu bieten.

## <a name="2d-ui-in-a-virtual-world"></a>2D Benutzeroberfläche in einer virtuellen Welt

>[!NOTE]
> Nehmen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter erhalten möchten.

[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR lesbar, aktivieren Sie zum einfachen Erstellen interaktiver Benutzeroberflächen, eignen sich gut für VR und nicht-VR angezeigt.
Eine Erweiterung von Babylon.js die `GUI` Bibliothek verwendete Throuhout 2D Elemente erstellen des Beispiels ist.


Ein 2D Text `GUI` Element kann erstellt werden, mit ein paar Zeilen je nach wie viele Attribute, die Sie anpassen möchten.
Im folgenden Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir exemplarischen Vorgehensweise, was geschieht.
Wir stellen Sie zunächst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI abdecken soll. Im Beispiel wird dies auf `CreateFullScreenUI()`, d. h., unserer Benutzeroberfläche deckt den ganzen Bildschirm. Mit `AdvancedDynamicTexture` erstellt, wir stellen ein 2D Textfeld, das angezeigt wird beim Starten der Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.


Dieser Code wird in [**main.js**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168)hinzugefügt.
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


Diese Benutzeroberfläche ist sichtbar, nachdem erstellt wurde, jedoch können ein- oder ausschalten umgeschaltet werden, mit `isVisible` je nachdem, was im Spiel passiert.
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a>Erkennen von headsets

Es wird empfohlen für VR Applikationen auf zwei Arten von Kameras verfügen, sodass mehrere Szenarien unterstützt werden können. Für dieses Spiel werden wir eine Kamera, die erforderlich sind, eine Kopfhörer arbeiten, angeschlossen sein, und ein weiteres Video unterstützt, die keine Kopfhörer verwendet. Zum bestimmen, welche wird das Spiel verwenden wir zunächst müssen Sie überprüfen, ob ein Kopfhörer erkannt wurde. Klicken Sie dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).


Fügen Sie diesen Code oben `window.addEventListener('DOMContentLoaded')` in **main.js**.
```javascript
var headset;
// If a VR headset is connected, get its info
navigator.getVRDisplays().then(function (displays) {
    if (displays[0]) {
        headset = displays[0];
    }
});
```

Mit der Info gespeichert, der `headset` Variablen, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer die richtige Wahl ist.


## <a name="creating-and-selecting-the-initial-camera"></a>Erstellen und Auswählen der anfänglichen Kamera

Mit Babylon.js, WebVR kann hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera). Diese Kamera kann Tastatureingaben und ermöglicht es Ihnen, eine VR Kopfhörer verwenden, um Ihre Drehung "Head" steuern.


### <a name="step-1-checking-for-headsets"></a>Schritt 1: Suchen nach headsets

Für unsere fallback Kamera, wir verwenden werden die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit in der ursprünglichen Spiel verwendet wird.

Microsoft prüft unsere `headset` Variable um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.

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
Zum Aktivieren dieser Kamera in den meisten Browsern muss der Benutzer einige Eingaben ausführen, der die virtuelle Erfahrung Anforderungen.
Wir binden diese Funktionalität bis klicken mit der Maus zu.


Fügen Sie den Code in `createScene()` Funktion nach `camera.applyGravity = true;` .
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

Ein Klicken in das Spiel jetzt eine Aufforderung wie folgt erstellt oder zeigt das Spiel in der Kopfhörer sofort, wenn der Benutzer die Aufforderung, bevor angenommen hat.

![fesselnden Aufforderung](images/immersiveview.png)

Wir können auch hinzufügen einen Codeabschnitt angezeigt werden die die `UniversalCamera` anzeigen, bevor wir zu wechseln, unsere `WebVRFreeCamera`, dem der Benutzer das Spiel anstelle einer blauen Fenster betrachten. 

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

Da die `WebVRFreeCamera` unterstützt keine Gamepads, zunächst werden wir die Pfeiltasten Tastatur unsere Gamepad Schaltflächen zuordnen. Wir geschieht dies durch eine Suche in der `inputs` -Eigenschaft des der Kamera. Hinzufügen der Codes für linken analoge Stick nach oben, unten, links und rechts, um mit der Pfeiltasten Übereinstimmung zu bringen, ist unsere Gamepad in der Praxis.


Fügen Sie diesen Code unter der `scene.onPointerDown = function() {...}` aufrufen.
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a>Schritt 4: Probieren sie es!

Wenn wir **index.html** öffnen Sie mit unserem Kopfhörer und Gamecontroller angeschlossen, wird eine klicken Sie auf das blaue Spiel Fenster unsere Spiel zum VR Modus wechseln! Fahren Sie fort, und platzieren Sie auf Ihre Kopfhörer, um die Ergebnisse auszuchecken. 


<iframe height='300' scrolling='no' title='Babylon.js Dino Spiel mit Babylon.GUI - WebVR' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>Finden Sie unter dem Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino Spiel mit Babylon.GUI - WebVR</a> durch Microsoft-Edge-Dokumente (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.
</iframe>


## <a name="conclusion"></a>Fazit

Herzlichen Glückwunsch! Sie haben nun eine vollständige Babylon.js Spiel mit WebVR Support. Hier können Sie die Gelernte Sie erstellen eine noch bessere Spiel, oder erstellen Sie diese nutzen.
