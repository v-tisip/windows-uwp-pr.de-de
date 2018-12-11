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
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a><span data-ttu-id="43db1-104">Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen</span><span class="sxs-lookup"><span data-stu-id="43db1-104">Adding WebVR support to a 3D Babylon.js game</span></span>

<span data-ttu-id="43db1-105">Wenn Sie davon ausgegangen, dass es in virtual-Reality (VR) gut aussehen könnte und -3D-Spielen mit Babylon.js erstellt haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.</span><span class="sxs-lookup"><span data-stu-id="43db1-105">If you've created a 3D game with Babylon.js and thought that it might look great in virtual reality (VR), follow the simple steps in this tutorial to make that a reality.</span></span>

<span data-ttu-id="43db1-106">Wir werden WebVR Unterstützung für das Spiel hier hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="43db1-106">We'll add WebVR support to the game shown here.</span></span> <span data-ttu-id="43db1-107">Einfach, und schließen Sie Xbox-Controller ausprobieren!</span><span class="sxs-lookup"><span data-stu-id="43db1-107">Go ahead and plug in an Xbox controller to try it out!</span></span>


<iframe height='300' scrolling='no' title='<span data-ttu-id="43db1-108">Babylon.js Dino-Spiel mit Babylon.GUI</span><span class="sxs-lookup"><span data-stu-id="43db1-108">Babylon.js dino game using Babylon.GUI</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="43db1-109">Finden Sie unter der Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino-Spiel Babylon.GUI mithilfe</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="43db1-109">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js dino game using Babylon.GUI</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

<span data-ttu-id="43db1-110">Dies ist ein 3D-Spiel, auf eine flache Bildschirm, aber was zu funktioniert, in VR?</span><span class="sxs-lookup"><span data-stu-id="43db1-110">This is a 3D game that works well on a flat screen, but what about in VR?</span></span>
<span data-ttu-id="43db1-111">In diesem Lernprogramm verwenden wir die Schritte es dauert, um sich zu erhalten und mit WebVR durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="43db1-111">In this tutorial, we'll walk through the few steps it takes to get this up and running with WebVR.</span></span> <span data-ttu-id="43db1-112">Wir verwenden ein [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) -Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge nutzen können.</span><span class="sxs-lookup"><span data-stu-id="43db1-112">We’ll use a [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) headset that can tap into the added support for WebVR in Microsoft Edge.</span></span> <span data-ttu-id="43db1-113">Nachdem wir diese Änderungen für das Spiel angewendet haben, können Sie davon ausgehen, dass es auch in anderen Browser/Kopfhörer Kombinationen funktioniert, die WebVR zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="43db1-113">After we apply these changes to the game, you can expect it also to work in other browser/headset combinations that support WebVR.</span></span>



## <a name="prerequisites"></a><span data-ttu-id="43db1-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="43db1-114">Prerequisites</span></span>

- <span data-ttu-id="43db1-115">Einem Text-Editor (z. B. [Visual Studio Code](https://code.visualstudio.com/download))</span><span class="sxs-lookup"><span data-stu-id="43db1-115">A text editor (like [Visual Studio Code](https://code.visualstudio.com/download))</span></span>
- <span data-ttu-id="43db1-116">Xbox-Controller, der an den Computer angeschlossen ist</span><span class="sxs-lookup"><span data-stu-id="43db1-116">An Xbox controller that’s plugged in to your computer</span></span>
- <span data-ttu-id="43db1-117">Windows10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="43db1-117">Windows 10 Creators Update</span></span>
- <span data-ttu-id="43db1-118">Ein Computer mit den [mindestens erforderlichen Spezifikationen zum Ausführen von Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span><span class="sxs-lookup"><span data-stu-id="43db1-118">A computer with the [minimum required specs to run Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span></span>
- <span data-ttu-id="43db1-119">Ein Windows Mixed Reality-Gerät (Optional)</span><span class="sxs-lookup"><span data-stu-id="43db1-119">A Windows Mixed Reality device (Optional)</span></span> 



## <a name="getting-started"></a><span data-ttu-id="43db1-120">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="43db1-120">Getting started</span></span>

<span data-ttu-id="43db1-121">Die einfachste Möglichkeit zum Einstieg ist, das [Windows-Lernprogramme-Web-GitHub-Repository](https://github.com/Microsoft/Windows-tutorials-web), drücken Sie die grüne **Clone or Download** besuchen, die Schaltfläche, und wählen Sie **in Visual Studio öffnen**.</span><span class="sxs-lookup"><span data-stu-id="43db1-121">The simplest way to get started is to visit the [Windows-tutorials-web GitHub repo](https://github.com/Microsoft/Windows-tutorials-web), press the green **Clone or download** button, and select **Open in Visual Studio**.</span></span>

![Schaltfläche „clone or download“](images/3dclone.png)

<span data-ttu-id="43db1-123">Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="43db1-123">If you don't want to clone the project, you can download it as a zip file.</span></span>
<span data-ttu-id="43db1-124">Sie haben dann zwei Ordner, [vor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nach](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span><span class="sxs-lookup"><span data-stu-id="43db1-124">You'll then have two folders, [before](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) and [after](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span></span> <span data-ttu-id="43db1-125">Der Ordner "vorher" ist unser Spiel, bevor alle VR-Features hinzugefügt werden, und der Ordner "nach" das fertiges Spiel mit VR-Unterstützung ist.</span><span class="sxs-lookup"><span data-stu-id="43db1-125">The "before" folder is our game before any VR features are added, and the "after" folder is the finished game with VR support.</span></span>

<span data-ttu-id="43db1-126">Die vor und nach dem Ordner diese Dateien enthalten:</span><span class="sxs-lookup"><span data-stu-id="43db1-126">The before and after folders contain these files:</span></span>
-   <span data-ttu-id="43db1-127">**Texturen /** – ein Ordner, die im Spiel verwendeten Bilder enthält.</span><span class="sxs-lookup"><span data-stu-id="43db1-127">**textures/** - A folder containing any images used in the game.</span></span>
-   <span data-ttu-id="43db1-128">**Css /** – ein Ordner mit den CSS-Code für das Spiel.</span><span class="sxs-lookup"><span data-stu-id="43db1-128">**css/** - A folder containing the CSS for the game.</span></span>
-   <span data-ttu-id="43db1-129">**Js /** – ein Ordner mit den JavaScript-Dateien.</span><span class="sxs-lookup"><span data-stu-id="43db1-129">**js/** - A folder containing the JavaScript files.</span></span> <span data-ttu-id="43db1-130">Die main.js-Datei ist unser Spiel, und die anderen Dateien sind die Bibliotheken verwendet.</span><span class="sxs-lookup"><span data-stu-id="43db1-130">The main.js file is our game, and the other files are the libraries used.</span></span>
-   <span data-ttu-id="43db1-131">**Modelle /** – ein Ordner mit den 3D-Modellen.</span><span class="sxs-lookup"><span data-stu-id="43db1-131">**models/** - A folder containing the 3D models.</span></span> <span data-ttu-id="43db1-132">Für dieses Spiel haben wir nur ein Modell für den Dinosaurier.</span><span class="sxs-lookup"><span data-stu-id="43db1-132">For this game we have only one model, for the dinosaur.</span></span>
-   <span data-ttu-id="43db1-133">**index.html** – die Webseite, die den Spiel Renderer hostet.</span><span class="sxs-lookup"><span data-stu-id="43db1-133">**index.html** - The webpage that hosts the game's renderer.</span></span> <span data-ttu-id="43db1-134">Diese Seite in Microsoft Edge öffnet, startet das Spiel.</span><span class="sxs-lookup"><span data-stu-id="43db1-134">Opening this page in Microsoft Edge launches the game.</span></span>

<span data-ttu-id="43db1-135">Sie können beide Versionen des Spiels, testen, ihre jeweiligen index.html Dateien im Microsoft Edge geöffnet.</span><span class="sxs-lookup"><span data-stu-id="43db1-135">You can test both versions of the game by opening their respective index.html files in Microsoft Edge.</span></span>



## <a name="the-mixed-reality-portal"></a><span data-ttu-id="43db1-136">Das Mixed Reality-Portal</span><span class="sxs-lookup"><span data-stu-id="43db1-136">The Mixed Reality Portal</span></span>

<span data-ttu-id="43db1-137">Wenn Sie noch keine Erfahrung mit Windows Mixed Reality und Windows 10 Creators Update auf einem Computer mit einem kompatiblen Grafikkarte installiert haben, versuchen Sie, öffnen die **Mixed Reality-Portal** -app aus dem Menü "Start" in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="43db1-137">If you're unfamiliar with Windows Mixed Reality and have the Windows 10 Creators Update installed on a computer with a compatible graphics card, try opening the **Mixed Reality Portal** app from the Start menu in Windows 10.</span></span>

![Mixed Reality-Portal-Suche](images/mixed-reality-portal.png)

<span data-ttu-id="43db1-139">Wenn Sie alle Anforderungen erfüllt, können Sie dann Entwicklerfeatures aktivieren und simulieren einer Windows Mixed Reality-Kopfhörer, die an den Computer angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="43db1-139">If you met all the requirements, you can then turn on developer features and simulate a Windows Mixed Reality headset plugged in to your computer.</span></span> <span data-ttu-id="43db1-140">Wenn Sie Glück, eine tatsächliche Kopfhörer in der Nähe sind, schließen Sie es, und führen Sie das Setup.</span><span class="sxs-lookup"><span data-stu-id="43db1-140">If you're fortunate enough to have an actual headset nearby, plug it in and run the setup.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43db1-141">Mixed Reality-Portals muss in diesem Lernprogramm immer geöffnet sein.</span><span class="sxs-lookup"><span data-stu-id="43db1-141">The Mixed Reality Portal must be open at all times during this tutorial.</span></span>

<span data-ttu-id="43db1-142">Sie nun können WebVR mit Microsoft Edge auftreten.</span><span class="sxs-lookup"><span data-stu-id="43db1-142">You're now ready to experience WebVR with Microsoft Edge.</span></span>

## <a name="2d-ui-in-a-virtual-world"></a><span data-ttu-id="43db1-143">2D UI in einer virtuellen Welt</span><span class="sxs-lookup"><span data-stu-id="43db1-143">2D UI in a virtual world</span></span>

>[!NOTE]
> <span data-ttu-id="43db1-144">Beziehen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter abrufen.</span><span class="sxs-lookup"><span data-stu-id="43db1-144">Grab the [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) folder to get the starter sample.</span></span>

<span data-ttu-id="43db1-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR-freundliche, aktivieren Sie zum einfachen erstellen, interaktive Benutzeroberflächen, die gut für VR funktionieren und nicht-VR anzeigt.</span><span class="sxs-lookup"><span data-stu-id="43db1-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) is a VR-friendly library, enabling you to create simple, interactive user interfaces that work well for VR and non-VR displays.</span></span>
<span data-ttu-id="43db1-146">Eine Erweiterung von Babylon.js die `GUI` Bibliothek ist verwendete Throuhout im Beispiel 2D Elemente erstellen.</span><span class="sxs-lookup"><span data-stu-id="43db1-146">An extension to Babylon.js, the `GUI` library is used throuhout the sample to create 2D elements.</span></span>


<span data-ttu-id="43db1-147">Ein 2D Text `GUI` Element erstellt werden kann, mit wenigen Zeilen, je nachdem, wie viele Attribute, die Sie optimieren möchten.</span><span class="sxs-lookup"><span data-stu-id="43db1-147">A 2D text `GUI` element can be created with a few lines depending on how many attributes you want to tweak.</span></span>
<span data-ttu-id="43db1-148">Der folgende Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir Exemplarische Vorgehensweise, was passiert.</span><span class="sxs-lookup"><span data-stu-id="43db1-148">The following code snippet is already in our [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) sample, but let's walkthrough what's happening.</span></span>
<span data-ttu-id="43db1-149">Wir müssen Sie zuerst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="43db1-149">We first make an [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) object to establish what the GUI will cover.</span></span> <span data-ttu-id="43db1-150">Das Beispiel legt diese auf `CreateFullScreenUI()`, d. h. der Benutzeroberfläche deckt den gesamten Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="43db1-150">The sample sets this to `CreateFullScreenUI()`, meaning our UI will cover the entire screen.</span></span> <span data-ttu-id="43db1-151">Mit `AdvancedDynamicTexture` erstellt, wir stellen ein 2D Text-Feld, das angezeigt wird beim Starten das Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.</span><span class="sxs-lookup"><span data-stu-id="43db1-151">With `AdvancedDynamicTexture` created, we then make a 2D text box that appears upon starting the game using `GUI.Rectanlge()` and `GUI.TextBlock()`.</span></span>


<span data-ttu-id="43db1-152">Dieser Code wird in [**"Main.js"**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="43db1-152">This code is added within [**main.js**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168).</span></span>
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


<span data-ttu-id="43db1-153">Dieser Benutzeroberfläche wird angezeigt, nachdem Sie erstellt wurde, jedoch können werden ein- oder mit `isVisible` je nachdem, was im Spiel ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="43db1-153">This UI is visible once created but can be toggled on or off with `isVisible` depending on what's happening in the game.</span></span>
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a><span data-ttu-id="43db1-154">Erkennen von headsets</span><span class="sxs-lookup"><span data-stu-id="43db1-154">Detecting headsets</span></span>

<span data-ttu-id="43db1-155">Es ist üblich, VR-Anwendungen auf zwei Arten von Kameras verfügen, sodass mehrere Szenarien unterstützt werden können.</span><span class="sxs-lookup"><span data-stu-id="43db1-155">It's good practice for VR applications to have two types of cameras so that multiple scenarios can be supported.</span></span> <span data-ttu-id="43db1-156">Für dieses Spiel müssen wir eine Kamera, die erfordert eine funktionierende Kopfhörer zu angeschlossen sein, und eine andere unterstützen, die keine Kopfhörer verwendet.</span><span class="sxs-lookup"><span data-stu-id="43db1-156">For this game, we'll support one camera that requires a working headset to be plugged in, and another that uses no headset.</span></span> <span data-ttu-id="43db1-157">Um zu ermitteln, welche wird das Spiel verwenden müssen wir zunächst überprüfen, ob ein Kopfhörer erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="43db1-157">To determine which one the game will use, we must first check to see whether a headset has been detected.</span></span> <span data-ttu-id="43db1-158">Dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span><span class="sxs-lookup"><span data-stu-id="43db1-158">To do that, we’ll use [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span></span>


<span data-ttu-id="43db1-159">Fügen Sie diesen Code oben `window.addEventListener('DOMContentLoaded')` in **"Main.js"**.</span><span class="sxs-lookup"><span data-stu-id="43db1-159">Add this code above `window.addEventListener('DOMContentLoaded')` in **main.js**.</span></span>
```javascript
var headset;
// If a VR headset is connected, get its info
navigator.getVRDisplays().then(function (displays) {
    if (displays[0]) {
        headset = displays[0];
    }
});
```

<span data-ttu-id="43db1-160">Mit den Informationen gespeichert werden, der `headset` Variable, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="43db1-160">With the info stored in the `headset` variable, we'll now be able to choose the camera that’s right for the user.</span></span>


## <a name="creating-and-selecting-the-initial-camera"></a><span data-ttu-id="43db1-161">Erstellen und Auswählen der Kamera</span><span class="sxs-lookup"><span data-stu-id="43db1-161">Creating and selecting the initial camera</span></span>

<span data-ttu-id="43db1-162">Mit Babylon.js, WebVR hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span><span class="sxs-lookup"><span data-stu-id="43db1-162">With Babylon.js, WebVR can be added quickly by using the [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span></span> <span data-ttu-id="43db1-163">Diese Kamera kann Eingaben über die Tastatur und ermöglicht es Ihnen, eine VR-Kopfhörer verwenden, um Ihre Drehung "Head" zu steuern.</span><span class="sxs-lookup"><span data-stu-id="43db1-163">This camera can take keyboard input and enables you to use a VR headset to control your "head" rotation.</span></span>


### <a name="step-1-checking-for-headsets"></a><span data-ttu-id="43db1-164">Schritt 1: Überprüfen headsets</span><span class="sxs-lookup"><span data-stu-id="43db1-164">Step 1: Checking for headsets</span></span>

<span data-ttu-id="43db1-165">Für die fallback-Kamera, verwenden wir die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit in der ursprünglichen Spiel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="43db1-165">For our fallback camera, we'll be using the [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) that’s currently used in the original game.</span></span>

<span data-ttu-id="43db1-166">Überprüfen wir unsere `headset` Variable, um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.</span><span class="sxs-lookup"><span data-stu-id="43db1-166">We'll check our `headset` variable to determine whether we can use the `WebVRFreeCamera` camera.</span></span>

<span data-ttu-id="43db1-167">Ersetzen Sie `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` mit dem folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="43db1-167">Replace `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` with the following code.</span></span>
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


### <a name="step-2-activating-the-webvrfreecamera"></a><span data-ttu-id="43db1-168">Schritt 2: Aktivieren der WebVRFreeCamera</span><span class="sxs-lookup"><span data-stu-id="43db1-168">Step 2: Activating the WebVRFreeCamera</span></span>
<span data-ttu-id="43db1-169">Um diese Kamera in den meisten Browsern zu aktivieren, muss der Benutzer einige Eingaben durchführen, die die virtuelle Erfahrung anfordert.</span><span class="sxs-lookup"><span data-stu-id="43db1-169">To activate this camera in most browsers, the user must perform some interaction that requests the virtual experience.</span></span>
<span data-ttu-id="43db1-170">Wir werden diese Funktion bis zu einem Mausklick zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="43db1-170">We'll hook this functionality up to a mouse click.</span></span>


<span data-ttu-id="43db1-171">Fügen Sie den Code in `createScene()` Funktion nach `camera.applyGravity = true;` .</span><span class="sxs-lookup"><span data-stu-id="43db1-171">Paste the code within  `createScene()` function after `camera.applyGravity = true;` .</span></span>
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

<span data-ttu-id="43db1-172">Ein Klicken Sie auf das Spiel jetzt erstellt eine Aufforderung wie folgt oder zeigt das Spiel in die Kopfhörer sofort, wenn der Benutzer die Aufforderung vor dem akzeptiert hat.</span><span class="sxs-lookup"><span data-stu-id="43db1-172">A click in the game now creates a prompt like the following, or displays the game in the headset right away if the user has accepted the prompt before.</span></span>

![immersiven Aufforderung](images/immersiveview.png)

<span data-ttu-id="43db1-174">Wir können auch Hinzufügen von Code, der angezeigt wird die `UniversalCamera` anzeigen, bevor wir zu wechseln unsere `WebVRFreeCamera`, sodass der Benutzer das Spiel anstatt ein blaues Fenster betrachten.</span><span class="sxs-lookup"><span data-stu-id="43db1-174">We can also add a piece of code that will display the `UniversalCamera` view before we switch to our `WebVRFreeCamera`, allowing the user to look at the game instead of a blue window.</span></span> 

<span data-ttu-id="43db1-175">Fügen Sie die folgenden nach `engine.runRenderLoop(function () {`.</span><span class="sxs-lookup"><span data-stu-id="43db1-175">Add the following after `engine.runRenderLoop(function () {`.</span></span>
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

### <a name="step-3-adding-gamepad-support"></a><span data-ttu-id="43db1-176">Schritt 3: Hinzufügen von Gamepad-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="43db1-176">Step 3: Adding gamepad support</span></span>

<span data-ttu-id="43db1-177">Da die `WebVRFreeCamera` unterstützt keine anfänglich Gamepads, werden wir unsere Gamepad-Tasten die Pfeiltasten der Tastatur zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="43db1-177">Since the `WebVRFreeCamera` doesn't initially support gamepads, we'll map our gamepad buttons to the keyboard arrow keys.</span></span> <span data-ttu-id="43db1-178">Wir werden dies tun, indem eine Suche in der `inputs` Eigenschaft der Kamera.</span><span class="sxs-lookup"><span data-stu-id="43db1-178">We'll do this by digging into the `inputs` property of the camera.</span></span> <span data-ttu-id="43db1-179">Hinzufügen von der Codes für den linken Joystick nach oben, unten, links und rechts übereinstimmen, mit den Pfeiltasten, ist unsere Gamepad zurück in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="43db1-179">By adding the corresponding codes for left analog stick up, down, left, and right to match up with the arrow keys, our gamepad is back in action.</span></span>


<span data-ttu-id="43db1-180">Fügen Sie diesen Code unten die `scene.onPointerDown = function() {...}` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="43db1-180">Add this code below the `scene.onPointerDown = function() {...}` call.</span></span>
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a><span data-ttu-id="43db1-181">Schritt 4: Versuchen Sie es!</span><span class="sxs-lookup"><span data-stu-id="43db1-181">Step 4: Give it a try!</span></span>

<span data-ttu-id="43db1-182">Wenn wir **"Index.HTML"** mit unseren Kopfhörer öffnen und Gamecontroller angeschlossen, wird eine klicken Sie auf das blaue Spielfenster unser Spiel VR-Modus wechseln!</span><span class="sxs-lookup"><span data-stu-id="43db1-182">If we open **index.html** with our headset and game controller plugged in, a left click on the blue game window will switch our game to VR mode!</span></span> <span data-ttu-id="43db1-183">Fahren Sie fort, und fügen Sie auf Ihre Kopfhörer, um die Ergebnisse zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="43db1-183">Go ahead and put on your headset to check out the results.</span></span> 


<iframe height='300' scrolling='no' title='<span data-ttu-id="43db1-184">Babylon.js Dino-Spiel mit Babylon.GUI - WebVR</span><span class="sxs-lookup"><span data-stu-id="43db1-184">Babylon.js dino game using Babylon.GUI - WebVR</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="43db1-185">Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino-Spiel mit Babylon.GUI - WebVR</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="43db1-185">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js dino game using Babylon.GUI - WebVR</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


## <a name="conclusion"></a><span data-ttu-id="43db1-186">Fazit</span><span class="sxs-lookup"><span data-stu-id="43db1-186">Conclusion</span></span>

<span data-ttu-id="43db1-187">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="43db1-187">Congratulations!</span></span> <span data-ttu-id="43db1-188">Sie haben nun ein vollständiges Babylon.js-Spiel mit WebVR-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="43db1-188">You now have a complete Babylon.js game with WebVR support.</span></span> <span data-ttu-id="43db1-189">Hier können Sie nutzen, was Sie gelernt haben, erstellen ein noch besseres Spiel oder Deaktivieren dieser erstellt.</span><span class="sxs-lookup"><span data-stu-id="43db1-189">From here you can take what you've learned to build an even better game, or build off this one.</span></span>
