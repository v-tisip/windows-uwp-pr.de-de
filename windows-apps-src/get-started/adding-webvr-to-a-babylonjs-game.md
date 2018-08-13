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
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a><span data-ttu-id="14869-104">Hinzufügen der Unterstützung von WebVR mit einem 3D Babylon.js Spiel</span><span class="sxs-lookup"><span data-stu-id="14869-104">Adding WebVR support to a 3D Babylon.js game</span></span>

<span data-ttu-id="14869-105">Wenn Sie davon ausgegangen, dass es hervorragend für virtuelle Realität (VR) aussehen könnte und ein 3D Spiel mit Babylon.js erstellt haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.</span><span class="sxs-lookup"><span data-stu-id="14869-105">If you've created a 3D game with Babylon.js and thought that it might look great in virtual reality (VR), follow the simple steps in this tutorial to make that a reality.</span></span>

<span data-ttu-id="14869-106">Wir werden mit dem hier dargestellten Spiel WebVR Unterstützung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="14869-106">We'll add WebVR support to the game shown here.</span></span> <span data-ttu-id="14869-107">Fahren Sie fort, und schließen Sie eine Xbox Controller ausprobieren!</span><span class="sxs-lookup"><span data-stu-id="14869-107">Go ahead and plug in an Xbox controller to try it out!</span></span>


<iframe height='300' scrolling='no' title='<span data-ttu-id="14869-108">Babylon.js Dino Spiel mit Babylon.GUI</span><span class="sxs-lookup"><span data-stu-id="14869-108">Babylon.js dino game using Babylon.GUI</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="14869-109">Finden Sie unter dem Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino Spiel mit Babylon.GUI</a> durch Microsoft-Edge-Dokumente (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="14869-109">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js dino game using Babylon.GUI</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

<span data-ttu-id="14869-110">Dies ist ein 3D Spiel, die auch auf einem flachen Bildschirm, aber was zu funktioniert in VR?</span><span class="sxs-lookup"><span data-stu-id="14869-110">This is a 3D game that works well on a flat screen, but what about in VR?</span></span>
<span data-ttu-id="14869-111">In diesem Lernprogramm werden wir den Schritten es dauert dies Einstieg und mit WebVR durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="14869-111">In this tutorial, we'll walk through the few steps it takes to get this up and running with WebVR.</span></span> <span data-ttu-id="14869-112">Wir verwenden eine [Gemischte Realität Windows](https://developer.microsoft.com/en-us/windows/mixed-reality) Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge hinzugefügt nutzen können.</span><span class="sxs-lookup"><span data-stu-id="14869-112">We’ll use a [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) headset that can tap into the added support for WebVR in Microsoft Edge.</span></span> <span data-ttu-id="14869-113">Nachdem wir diese Änderungen auf dem Spiel anwenden möchten, können Sie davon ausgehen es auch in andere Browser/Kopfhörer Kombinationen aus arbeiten, die WebVR unterstützen.</span><span class="sxs-lookup"><span data-stu-id="14869-113">After we apply these changes to the game, you can expect it also to work in other browser/headset combinations that support WebVR.</span></span>



## <a name="prerequisites"></a><span data-ttu-id="14869-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="14869-114">Prerequisites</span></span>

- <span data-ttu-id="14869-115">Einen Text-Editor (wie [Visual Studio-Code](https://code.visualstudio.com/download))</span><span class="sxs-lookup"><span data-stu-id="14869-115">A text editor (like [Visual Studio Code](https://code.visualstudio.com/download))</span></span>
- <span data-ttu-id="14869-116">Ein Xbox Domänencontroller, der an Ihren Computer angeschlossen ist</span><span class="sxs-lookup"><span data-stu-id="14869-116">An Xbox controller that’s plugged in to your computer</span></span>
- <span data-ttu-id="14869-117">Windows10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="14869-117">Windows 10 Creators Update</span></span>
- <span data-ttu-id="14869-118">Einen Computer mit den [mindestens erforderlichen Spezifikationen gemischten Realität Windows ausführen](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span><span class="sxs-lookup"><span data-stu-id="14869-118">A computer with the [minimum required specs to run Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span></span>
- <span data-ttu-id="14869-119">Eine gemischte Realität Windows-Gerät (Optional)</span><span class="sxs-lookup"><span data-stu-id="14869-119">A Windows Mixed Reality device (Optional)</span></span> 



## <a name="getting-started"></a><span data-ttu-id="14869-120">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="14869-120">Getting started</span></span>

<span data-ttu-id="14869-121">Die einfachste Möglichkeit zum Einstieg ist die [Windows-Lernprogramme-Web GitHub Repo](https://github.com/Microsoft/Windows-tutorials-web)besuchen, drücken Sie die grüne **Clone oder Download** Schaltfläche aus, und wählen Sie **in Visual Studio öffnen**.</span><span class="sxs-lookup"><span data-stu-id="14869-121">The simplest way to get started is to visit the [Windows-tutorials-web GitHub repo](https://github.com/Microsoft/Windows-tutorials-web), press the green **Clone or download** button, and select **Open in Visual Studio**.</span></span>

![Schaltfläche „clone or download“](images/3dclone.png)

<span data-ttu-id="14869-123">Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="14869-123">If you don't want to clone the project, you can download it as a zip file.</span></span>
<span data-ttu-id="14869-124">Sie müssen Sie zwei Ordner, [bevor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nachdem](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span><span class="sxs-lookup"><span data-stu-id="14869-124">You'll then have two folders, [before](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) and [after](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span></span> <span data-ttu-id="14869-125">Der Ordner "vor" ist unsere Spiel, bevor alle VR Features hinzugefügt wurden, und der Ordner "nach" das fertige Spiel mit VR Support ist.</span><span class="sxs-lookup"><span data-stu-id="14869-125">The "before" folder is our game before any VR features are added, and the "after" folder is the finished game with VR support.</span></span>

<span data-ttu-id="14869-126">Die vor und nach dem Ordner diese Dateien enthalten:</span><span class="sxs-lookup"><span data-stu-id="14869-126">The before and after folders contain these files:</span></span>
-   <span data-ttu-id="14869-127">**Strukturen /** – ein Ordner, in das Spiel verwendete Bilder enthält.</span><span class="sxs-lookup"><span data-stu-id="14869-127">**textures/** - A folder containing any images used in the game.</span></span>
-   <span data-ttu-id="14869-128">**Css /** – einen Ordner mit den CSS-Code für das Spiel.</span><span class="sxs-lookup"><span data-stu-id="14869-128">**css/** - A folder containing the CSS for the game.</span></span>
-   <span data-ttu-id="14869-129">**Js /** – einen Ordner mit der JavaScript-Dateien.</span><span class="sxs-lookup"><span data-stu-id="14869-129">**js/** - A folder containing the JavaScript files.</span></span> <span data-ttu-id="14869-130">Die Datei main.js ist unsere Spiel, und die anderen Dateien sind die verwendeten Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="14869-130">The main.js file is our game, and the other files are the libraries used.</span></span>
-   <span data-ttu-id="14869-131">**Modelle /** – einen Ordner mit der 3D Modelle.</span><span class="sxs-lookup"><span data-stu-id="14869-131">**models/** - A folder containing the 3D models.</span></span> <span data-ttu-id="14869-132">Für dieses Spiel müssen wir nur ein Modell für die Dinosaur.</span><span class="sxs-lookup"><span data-stu-id="14869-132">For this game we have only one model, for the dinosaur.</span></span>
-   <span data-ttu-id="14869-133">**index.html** - die Webseite, die das Spiel Renderer gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="14869-133">**index.html** - The webpage that hosts the game's renderer.</span></span> <span data-ttu-id="14869-134">Öffnen auf dieser Seite in Microsoft Edge startet das Spiel.</span><span class="sxs-lookup"><span data-stu-id="14869-134">Opening this page in Microsoft Edge launches the game.</span></span>

<span data-ttu-id="14869-135">Sie können beide Versionen des Spiels testen, indem Sie ihre jeweiligen index.html-Dateien in Microsoft Edge öffnen.</span><span class="sxs-lookup"><span data-stu-id="14869-135">You can test both versions of the game by opening their respective index.html files in Microsoft Edge.</span></span>



## <a name="the-mixed-reality-portal"></a><span data-ttu-id="14869-136">Das Portal gemischten Realität</span><span class="sxs-lookup"><span data-stu-id="14869-136">The Mixed Reality Portal</span></span>

<span data-ttu-id="14869-137">Wenn Sie mit Windows gemischten Realität nicht vertraut sind und die Windows 10 Ersteller-Updates auf einem Computer mit eine kompatible Grafikkarte installiert haben, versuchen Sie die **Gemischte Realität Portal** app über das Startmenü in Windows 10 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="14869-137">If you're unfamiliar with Windows Mixed Reality and have the Windows 10 Creators Update installed on a computer with a compatible graphics card, try opening the **Mixed Reality Portal** app from the Start menu in Windows 10.</span></span>

![Gemischte Realität Portal-Suche](images/mixed-reality-portal.png)

<span data-ttu-id="14869-139">Wenn Sie alle Anforderungen erfüllt, können Sie dann Funktionen für Entwickler aktivieren und die simulieren einer gemischten Windows-Realität Kopfhörer an Ihren Computer angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="14869-139">If you met all the requirements, you can then turn on developer features and simulate a Windows Mixed Reality headset plugged in to your computer.</span></span> <span data-ttu-id="14869-140">Wenn Sie Glück, in der Nähe eines tatsächlichen Kopfhörer sind, schließen Sie es, und führen Sie Setup.</span><span class="sxs-lookup"><span data-stu-id="14869-140">If you're fortunate enough to have an actual headset nearby, plug it in and run the setup.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14869-141">Die gemischte Realität Portal müssen jederzeit während dieses Lernprogramm geöffnet sein.</span><span class="sxs-lookup"><span data-stu-id="14869-141">The Mixed Reality Portal must be open at all times during this tutorial.</span></span>

<span data-ttu-id="14869-142">Sie nun können WebVR mit Microsoft-Edge-Umgebung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="14869-142">You're now ready to experience WebVR with Microsoft Edge.</span></span>

## <a name="2d-ui-in-a-virtual-world"></a><span data-ttu-id="14869-143">2D Benutzeroberfläche in einer virtuellen Welt</span><span class="sxs-lookup"><span data-stu-id="14869-143">2D UI in a virtual world</span></span>

>[!NOTE]
> <span data-ttu-id="14869-144">Nehmen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter erhalten möchten.</span><span class="sxs-lookup"><span data-stu-id="14869-144">Grab the [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) folder to get the starter sample.</span></span>

<span data-ttu-id="14869-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR lesbar, aktivieren Sie zum einfachen Erstellen interaktiver Benutzeroberflächen, eignen sich gut für VR und nicht-VR angezeigt.</span><span class="sxs-lookup"><span data-stu-id="14869-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) is a VR-friendly library, enabling you to create simple, interactive user interfaces that work well for VR and non-VR displays.</span></span>
<span data-ttu-id="14869-146">Eine Erweiterung von Babylon.js die `GUI` Bibliothek verwendete Throuhout 2D Elemente erstellen des Beispiels ist.</span><span class="sxs-lookup"><span data-stu-id="14869-146">An extension to Babylon.js, the `GUI` library is used throuhout the sample to create 2D elements.</span></span>


<span data-ttu-id="14869-147">Ein 2D Text `GUI` Element kann erstellt werden, mit ein paar Zeilen je nach wie viele Attribute, die Sie anpassen möchten.</span><span class="sxs-lookup"><span data-stu-id="14869-147">A 2D text `GUI` element can be created with a few lines depending on how many attributes you want to tweak.</span></span>
<span data-ttu-id="14869-148">Im folgenden Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir exemplarischen Vorgehensweise, was geschieht.</span><span class="sxs-lookup"><span data-stu-id="14869-148">The following code snippet is already in our [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) sample, but let's walkthrough what's happening.</span></span>
<span data-ttu-id="14869-149">Wir stellen Sie zunächst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI abdecken soll.</span><span class="sxs-lookup"><span data-stu-id="14869-149">We first make an [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) object to establish what the GUI will cover.</span></span> <span data-ttu-id="14869-150">Im Beispiel wird dies auf `CreateFullScreenUI()`, d. h., unserer Benutzeroberfläche deckt den ganzen Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="14869-150">The sample sets this to `CreateFullScreenUI()`, meaning our UI will cover the entire screen.</span></span> <span data-ttu-id="14869-151">Mit `AdvancedDynamicTexture` erstellt, wir stellen ein 2D Textfeld, das angezeigt wird beim Starten der Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.</span><span class="sxs-lookup"><span data-stu-id="14869-151">With `AdvancedDynamicTexture` created, we then make a 2D text box that appears upon starting the game using `GUI.Rectanlge()` and `GUI.TextBlock()`.</span></span>


<span data-ttu-id="14869-152">Dieser Code wird in [**main.js**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="14869-152">This code is added within [**main.js**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168).</span></span>
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


<span data-ttu-id="14869-153">Diese Benutzeroberfläche ist sichtbar, nachdem erstellt wurde, jedoch können ein- oder ausschalten umgeschaltet werden, mit `isVisible` je nachdem, was im Spiel passiert.</span><span class="sxs-lookup"><span data-stu-id="14869-153">This UI is visible once created but can be toggled on or off with `isVisible` depending on what's happening in the game.</span></span>
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a><span data-ttu-id="14869-154">Erkennen von headsets</span><span class="sxs-lookup"><span data-stu-id="14869-154">Detecting headsets</span></span>

<span data-ttu-id="14869-155">Es wird empfohlen für VR Applikationen auf zwei Arten von Kameras verfügen, sodass mehrere Szenarien unterstützt werden können.</span><span class="sxs-lookup"><span data-stu-id="14869-155">It's good practice for VR applications to have two types of cameras so that multiple scenarios can be supported.</span></span> <span data-ttu-id="14869-156">Für dieses Spiel werden wir eine Kamera, die erforderlich sind, eine Kopfhörer arbeiten, angeschlossen sein, und ein weiteres Video unterstützt, die keine Kopfhörer verwendet.</span><span class="sxs-lookup"><span data-stu-id="14869-156">For this game, we'll support one camera that requires a working headset to be plugged in, and another that uses no headset.</span></span> <span data-ttu-id="14869-157">Zum bestimmen, welche wird das Spiel verwenden wir zunächst müssen Sie überprüfen, ob ein Kopfhörer erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="14869-157">To determine which one the game will use, we must first check to see whether a headset has been detected.</span></span> <span data-ttu-id="14869-158">Klicken Sie dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span><span class="sxs-lookup"><span data-stu-id="14869-158">To do that, we’ll use [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span></span>


<span data-ttu-id="14869-159">Fügen Sie diesen Code oben `window.addEventListener('DOMContentLoaded')` in **main.js**.</span><span class="sxs-lookup"><span data-stu-id="14869-159">Add this code above `window.addEventListener('DOMContentLoaded')` in **main.js**.</span></span>
```javascript
var headset;
// If a VR headset is connected, get its info
navigator.getVRDisplays().then(function (displays) {
    if (displays[0]) {
        headset = displays[0];
    }
});
```

<span data-ttu-id="14869-160">Mit der Info gespeichert, der `headset` Variablen, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer die richtige Wahl ist.</span><span class="sxs-lookup"><span data-stu-id="14869-160">With the info stored in the `headset` variable, we'll now be able to choose the camera that’s right for the user.</span></span>


## <a name="creating-and-selecting-the-initial-camera"></a><span data-ttu-id="14869-161">Erstellen und Auswählen der anfänglichen Kamera</span><span class="sxs-lookup"><span data-stu-id="14869-161">Creating and selecting the initial camera</span></span>

<span data-ttu-id="14869-162">Mit Babylon.js, WebVR kann hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span><span class="sxs-lookup"><span data-stu-id="14869-162">With Babylon.js, WebVR can be added quickly by using the [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span></span> <span data-ttu-id="14869-163">Diese Kamera kann Tastatureingaben und ermöglicht es Ihnen, eine VR Kopfhörer verwenden, um Ihre Drehung "Head" steuern.</span><span class="sxs-lookup"><span data-stu-id="14869-163">This camera can take keyboard input and enables you to use a VR headset to control your "head" rotation.</span></span>


### <a name="step-1-checking-for-headsets"></a><span data-ttu-id="14869-164">Schritt 1: Suchen nach headsets</span><span class="sxs-lookup"><span data-stu-id="14869-164">Step 1: Checking for headsets</span></span>

<span data-ttu-id="14869-165">Für unsere fallback Kamera, wir verwenden werden die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit in der ursprünglichen Spiel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="14869-165">For our fallback camera, we'll be using the [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) that’s currently used in the original game.</span></span>

<span data-ttu-id="14869-166">Microsoft prüft unsere `headset` Variable um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.</span><span class="sxs-lookup"><span data-stu-id="14869-166">We'll check our `headset` variable to determine whether we can use the `WebVRFreeCamera` camera.</span></span>

<span data-ttu-id="14869-167">Ersetzen Sie `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="14869-167">Replace `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` with the following code.</span></span>
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


### <a name="step-2-activating-the-webvrfreecamera"></a><span data-ttu-id="14869-168">Schritt 2: Aktivieren der WebVRFreeCamera</span><span class="sxs-lookup"><span data-stu-id="14869-168">Step 2: Activating the WebVRFreeCamera</span></span>
<span data-ttu-id="14869-169">Zum Aktivieren dieser Kamera in den meisten Browsern muss der Benutzer einige Eingaben ausführen, der die virtuelle Erfahrung Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="14869-169">To activate this camera in most browsers, the user must perform some interaction that requests the virtual experience.</span></span>
<span data-ttu-id="14869-170">Wir binden diese Funktionalität bis klicken mit der Maus zu.</span><span class="sxs-lookup"><span data-stu-id="14869-170">We'll hook this functionality up to a mouse click.</span></span>


<span data-ttu-id="14869-171">Fügen Sie den Code in `createScene()` Funktion nach `camera.applyGravity = true;` .</span><span class="sxs-lookup"><span data-stu-id="14869-171">Paste the code within  `createScene()` function after `camera.applyGravity = true;` .</span></span>
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

<span data-ttu-id="14869-172">Ein Klicken in das Spiel jetzt eine Aufforderung wie folgt erstellt oder zeigt das Spiel in der Kopfhörer sofort, wenn der Benutzer die Aufforderung, bevor angenommen hat.</span><span class="sxs-lookup"><span data-stu-id="14869-172">A click in the game now creates a prompt like the following, or displays the game in the headset right away if the user has accepted the prompt before.</span></span>

![fesselnden Aufforderung](images/immersiveview.png)

<span data-ttu-id="14869-174">Wir können auch hinzufügen einen Codeabschnitt angezeigt werden die die `UniversalCamera` anzeigen, bevor wir zu wechseln, unsere `WebVRFreeCamera`, dem der Benutzer das Spiel anstelle einer blauen Fenster betrachten.</span><span class="sxs-lookup"><span data-stu-id="14869-174">We can also add a piece of code that will display the the `UniversalCamera` view before we switch to our `WebVRFreeCamera`, allowing the user to look at the game instead of a blue window.</span></span> 

<span data-ttu-id="14869-175">Fügen Sie die folgenden nach `engine.runRenderLoop(function () {`.</span><span class="sxs-lookup"><span data-stu-id="14869-175">Add the following after `engine.runRenderLoop(function () {`.</span></span>
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

### <a name="step-3-adding-gamepad-support"></a><span data-ttu-id="14869-176">Schritt 3: Hinzufügen von Gamepad-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="14869-176">Step 3: Adding gamepad support</span></span>

<span data-ttu-id="14869-177">Da die `WebVRFreeCamera` unterstützt keine Gamepads, zunächst werden wir die Pfeiltasten Tastatur unsere Gamepad Schaltflächen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="14869-177">Since the `WebVRFreeCamera` doesn't initially support gamepads, we'll map our gamepad buttons to the keyboard arrow keys.</span></span> <span data-ttu-id="14869-178">Wir geschieht dies durch eine Suche in der `inputs` -Eigenschaft des der Kamera.</span><span class="sxs-lookup"><span data-stu-id="14869-178">We'll do this by digging into the `inputs` property of the camera.</span></span> <span data-ttu-id="14869-179">Hinzufügen der Codes für linken analoge Stick nach oben, unten, links und rechts, um mit der Pfeiltasten Übereinstimmung zu bringen, ist unsere Gamepad in der Praxis.</span><span class="sxs-lookup"><span data-stu-id="14869-179">By adding the corresponding codes for left analog stick up, down, left, and right to match up with the arrow keys, our gamepad is back in action.</span></span>


<span data-ttu-id="14869-180">Fügen Sie diesen Code unter der `scene.onPointerDown = function() {...}` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="14869-180">Add this code below the `scene.onPointerDown = function() {...}` call.</span></span>
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a><span data-ttu-id="14869-181">Schritt 4: Probieren sie es!</span><span class="sxs-lookup"><span data-stu-id="14869-181">Step 4: Give it a try!</span></span>

<span data-ttu-id="14869-182">Wenn wir **index.html** öffnen Sie mit unserem Kopfhörer und Gamecontroller angeschlossen, wird eine klicken Sie auf das blaue Spiel Fenster unsere Spiel zum VR Modus wechseln!</span><span class="sxs-lookup"><span data-stu-id="14869-182">If we open **index.html** with our headset and game controller plugged in, a left click on the blue game window will switch our game to VR mode!</span></span> <span data-ttu-id="14869-183">Fahren Sie fort, und platzieren Sie auf Ihre Kopfhörer, um die Ergebnisse auszuchecken.</span><span class="sxs-lookup"><span data-stu-id="14869-183">Go ahead and put on your headset to check out the results.</span></span> 


<iframe height='300' scrolling='no' title='<span data-ttu-id="14869-184">Babylon.js Dino Spiel mit Babylon.GUI - WebVR</span><span class="sxs-lookup"><span data-stu-id="14869-184">Babylon.js dino game using Babylon.GUI - WebVR</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="14869-185">Finden Sie unter dem Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino Spiel mit Babylon.GUI - WebVR</a> durch Microsoft-Edge-Dokumente (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="14869-185">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js dino game using Babylon.GUI - WebVR</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


## <a name="conclusion"></a><span data-ttu-id="14869-186">Fazit</span><span class="sxs-lookup"><span data-stu-id="14869-186">Conclusion</span></span>

<span data-ttu-id="14869-187">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="14869-187">Congratulations!</span></span> <span data-ttu-id="14869-188">Sie haben nun eine vollständige Babylon.js Spiel mit WebVR Support.</span><span class="sxs-lookup"><span data-stu-id="14869-188">You now have a complete Babylon.js game with WebVR support.</span></span> <span data-ttu-id="14869-189">Hier können Sie die Gelernte Sie erstellen eine noch bessere Spiel, oder erstellen Sie diese nutzen.</span><span class="sxs-lookup"><span data-stu-id="14869-189">From here you can take what you've learned to build an even better game, or build off this one.</span></span>
