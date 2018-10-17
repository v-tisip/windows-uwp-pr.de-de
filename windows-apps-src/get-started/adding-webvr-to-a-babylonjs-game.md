---
title: Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen
description: Hier erfahren Sie, wie ein vorhandenes 3D Babylon.js-Spiel WebVR Unterstützung hinzugefügt.
author: abbycar
ms.author: abigailc
ms.date: 11/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Webvr, Edge, Webentwicklung, Babylon, Babylonjs, babylon.js, javascript
ms.localizationpriority: medium
ms.openlocfilehash: 97ef659a178a4c3f40d464fd958e5493454afef7
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4746975"
---
# <a name="adding-webvr-support-to-a-3d-babylonjs-game"></a><span data-ttu-id="08440-104">Hinzufügen von WebVR Unterstützung zu einem Babylon.js-3D-Spielen</span><span class="sxs-lookup"><span data-stu-id="08440-104">Adding WebVR support to a 3D Babylon.js game</span></span>

<span data-ttu-id="08440-105">Wenn Sie ein 3D-Spiel mit Babylon.js erstellt und davon ausgegangen, dass es in virtual-Reality (VR) gut aussehen könnte haben, führen Sie die einfache Schritte in diesem Lernprogramm zu, die die Realität.</span><span class="sxs-lookup"><span data-stu-id="08440-105">If you've created a 3D game with Babylon.js and thought that it might look great in virtual reality (VR), follow the simple steps in this tutorial to make that a reality.</span></span>

<span data-ttu-id="08440-106">Wir werden das hier gezeigte Spiel WebVR Unterstützung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="08440-106">We'll add WebVR support to the game shown here.</span></span> <span data-ttu-id="08440-107">Fahren Sie fort, und schließen Sie Xbox-Controller ausprobieren!</span><span class="sxs-lookup"><span data-stu-id="08440-107">Go ahead and plug in an Xbox controller to try it out!</span></span>


<iframe height='300' scrolling='no' title='<span data-ttu-id="08440-108">Babylon.js Dino-Spiel mit Babylon.GUI</span><span class="sxs-lookup"><span data-stu-id="08440-108">Babylon.js dino game using Babylon.GUI</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/wrOvoj/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="08440-109">Finden Sie unter der Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js Dino-Spiel Babylon.GUI mithilfe</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="08440-109">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/wrOvoj/'>Babylon.js dino game using Babylon.GUI</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

<span data-ttu-id="08440-110">Dies ist ein 3D-Spiel, das auch auf eine flache Bildschirm, aber was über funktioniert in VR?</span><span class="sxs-lookup"><span data-stu-id="08440-110">This is a 3D game that works well on a flat screen, but what about in VR?</span></span>
<span data-ttu-id="08440-111">In diesem Lernprogramm verwenden wir den Schritten es dauert dies bis zu erhalten und mit WebVR durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="08440-111">In this tutorial, we'll walk through the few steps it takes to get this up and running with WebVR.</span></span> <span data-ttu-id="08440-112">Wir verwenden ein [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) -Kopfhörer, die die Unterstützung für das WebVR in Microsoft Edge nutzen können.</span><span class="sxs-lookup"><span data-stu-id="08440-112">We’ll use a [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality) headset that can tap into the added support for WebVR in Microsoft Edge.</span></span> <span data-ttu-id="08440-113">Nachdem wir diese Änderungen für das Spiel angewendet haben, können Sie davon ausgehen, dass es auch in anderen Browser/Kopfhörer Kombinationen funktioniert, die WebVR zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="08440-113">After we apply these changes to the game, you can expect it also to work in other browser/headset combinations that support WebVR.</span></span>



## <a name="prerequisites"></a><span data-ttu-id="08440-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="08440-114">Prerequisites</span></span>

- <span data-ttu-id="08440-115">Eine Text-Editor (z. B. [Visual Studio Code](https://code.visualstudio.com/download))</span><span class="sxs-lookup"><span data-stu-id="08440-115">A text editor (like [Visual Studio Code](https://code.visualstudio.com/download))</span></span>
- <span data-ttu-id="08440-116">Xbox-Controller, der an den Computer angeschlossen ist</span><span class="sxs-lookup"><span data-stu-id="08440-116">An Xbox controller that’s plugged in to your computer</span></span>
- <span data-ttu-id="08440-117">Windows10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="08440-117">Windows 10 Creators Update</span></span>
- <span data-ttu-id="08440-118">Auf einem Computer mit den [mindestens erforderlichen Spezifikationen zum Ausführen von Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span><span class="sxs-lookup"><span data-stu-id="08440-118">A computer with the [minimum required specs to run Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/immersive_headset_setup)</span></span>
- <span data-ttu-id="08440-119">Ein Windows Mixed Reality-Gerät (Optional)</span><span class="sxs-lookup"><span data-stu-id="08440-119">A Windows Mixed Reality device (Optional)</span></span> 



## <a name="getting-started"></a><span data-ttu-id="08440-120">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="08440-120">Getting started</span></span>

<span data-ttu-id="08440-121">Die einfachste Möglichkeit für den Einstieg ist, das [Windows-Lernprogramme-Web-GitHub-Repository](https://github.com/Microsoft/Windows-tutorials-web), besuchen, drücken Sie die grüne **Clone or Download** Schaltfläche ", und wählen Sie **in Visual Studio geöffnet**.</span><span class="sxs-lookup"><span data-stu-id="08440-121">The simplest way to get started is to visit the [Windows-tutorials-web GitHub repo](https://github.com/Microsoft/Windows-tutorials-web), press the green **Clone or download** button, and select **Open in Visual Studio**.</span></span>

![Schaltfläche „clone or download“](images/3dclone.png)

<span data-ttu-id="08440-123">Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="08440-123">If you don't want to clone the project, you can download it as a zip file.</span></span>
<span data-ttu-id="08440-124">Sie haben dann zwei Ordnern, [vor](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) und [nach](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span><span class="sxs-lookup"><span data-stu-id="08440-124">You'll then have two folders, [before](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) and [after](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/after).</span></span> <span data-ttu-id="08440-125">Der Ordner "vor" ist unser Spiel, bevor alle VR-Features hinzugefügt werden, und der Ordner "nach" das fertiges Spiel mit VR-Unterstützung ist.</span><span class="sxs-lookup"><span data-stu-id="08440-125">The "before" folder is our game before any VR features are added, and the "after" folder is the finished game with VR support.</span></span>

<span data-ttu-id="08440-126">Die vorher und Nachher Ordner diese Dateien enthalten:</span><span class="sxs-lookup"><span data-stu-id="08440-126">The before and after folders contain these files:</span></span>
-   <span data-ttu-id="08440-127">**Texturen /** – ein Ordner mit den im Spiel verwendeten Bilder.</span><span class="sxs-lookup"><span data-stu-id="08440-127">**textures/** - A folder containing any images used in the game.</span></span>
-   <span data-ttu-id="08440-128">**Css /** – ein Ordner mit den CSS-Code für das Spiel.</span><span class="sxs-lookup"><span data-stu-id="08440-128">**css/** - A folder containing the CSS for the game.</span></span>
-   <span data-ttu-id="08440-129">**Js /** – ein Ordner mit den JavaScript-Dateien.</span><span class="sxs-lookup"><span data-stu-id="08440-129">**js/** - A folder containing the JavaScript files.</span></span> <span data-ttu-id="08440-130">Die Datei "Main.js" ist unser Spiel, und die anderen Dateien sind die Bibliotheken verwendet.</span><span class="sxs-lookup"><span data-stu-id="08440-130">The main.js file is our game, and the other files are the libraries used.</span></span>
-   <span data-ttu-id="08440-131">**Modelle /** – ein Ordner mit den 3D-Modellen.</span><span class="sxs-lookup"><span data-stu-id="08440-131">**models/** - A folder containing the 3D models.</span></span> <span data-ttu-id="08440-132">Für dieses Spiel gibt es nur ein Modell für den Dinosaurier.</span><span class="sxs-lookup"><span data-stu-id="08440-132">For this game we have only one model, for the dinosaur.</span></span>
-   <span data-ttu-id="08440-133">**index.html** – die Webseite, die den Spiel Renderer hostet.</span><span class="sxs-lookup"><span data-stu-id="08440-133">**index.html** - The webpage that hosts the game's renderer.</span></span> <span data-ttu-id="08440-134">Diese Seite in Microsoft Edge öffnet, startet das Spiel.</span><span class="sxs-lookup"><span data-stu-id="08440-134">Opening this page in Microsoft Edge launches the game.</span></span>

<span data-ttu-id="08440-135">Sie können beide Versionen des Spiels, testen, öffnen Sie dazu ihre jeweiligen "Index.HTML"-Dateien in Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="08440-135">You can test both versions of the game by opening their respective index.html files in Microsoft Edge.</span></span>



## <a name="the-mixed-reality-portal"></a><span data-ttu-id="08440-136">Das Mixed Reality-Portal</span><span class="sxs-lookup"><span data-stu-id="08440-136">The Mixed Reality Portal</span></span>

<span data-ttu-id="08440-137">Wenn Sie noch keine Erfahrung mit Windows Mixed Reality und Windows 10 Creators Update auf einem Computer mit einem kompatiblen Grafikkarte installiert haben, versuchen Sie die **Mixed Reality-Portal** -app aus dem Menü "Start" in Windows 10 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="08440-137">If you're unfamiliar with Windows Mixed Reality and have the Windows 10 Creators Update installed on a computer with a compatible graphics card, try opening the **Mixed Reality Portal** app from the Start menu in Windows 10.</span></span>

![Mixed Reality-Portal-Suche](images/mixed-reality-portal.png)

<span data-ttu-id="08440-139">Wenn Sie alle Anforderungen erfüllt, können Sie dann Entwicklerfeatures aktivieren und simulieren einer Windows Mixed Reality-Kopfhörer an den Computer angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="08440-139">If you met all the requirements, you can then turn on developer features and simulate a Windows Mixed Reality headset plugged in to your computer.</span></span> <span data-ttu-id="08440-140">Wenn Sie Glück, einen tatsächlichen Kopfhörer in der Nähe sind, schließen Sie es, und führen Sie das Setup.</span><span class="sxs-lookup"><span data-stu-id="08440-140">If you're fortunate enough to have an actual headset nearby, plug it in and run the setup.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08440-141">Mixed Reality-Portals müssen immer während dieses Lernprogramms geöffnet sein.</span><span class="sxs-lookup"><span data-stu-id="08440-141">The Mixed Reality Portal must be open at all times during this tutorial.</span></span>

<span data-ttu-id="08440-142">Sie nun können WebVR mit Microsoft Edge auftreten.</span><span class="sxs-lookup"><span data-stu-id="08440-142">You're now ready to experience WebVR with Microsoft Edge.</span></span>

## <a name="2d-ui-in-a-virtual-world"></a><span data-ttu-id="08440-143">2D-UI in einer virtuellen Welt</span><span class="sxs-lookup"><span data-stu-id="08440-143">2D UI in a virtual world</span></span>

>[!NOTE]
> <span data-ttu-id="08440-144">Nehmen Sie den Ordner [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , um das Beispiel Starter abrufen.</span><span class="sxs-lookup"><span data-stu-id="08440-144">Grab the [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) folder to get the starter sample.</span></span>

<span data-ttu-id="08440-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) ist eine Bibliothek VR-freundliche, aktivieren Sie zum einfachen erstellen, interaktive Benutzeroberflächen, eignen sich gut für VR und nicht-VR angezeigt.</span><span class="sxs-lookup"><span data-stu-id="08440-145">[Babylon.GUI](https://doc.babylonjs.com/how_to/gui) is a VR-friendly library, enabling you to create simple, interactive user interfaces that work well for VR and non-VR displays.</span></span>
<span data-ttu-id="08440-146">Eine Erweiterung von Babylon.js die `GUI` Bibliothek ist verwendete Throuhout im Beispiel 2D Elemente erstellen.</span><span class="sxs-lookup"><span data-stu-id="08440-146">An extension to Babylon.js, the `GUI` library is used throuhout the sample to create 2D elements.</span></span>


<span data-ttu-id="08440-147">Ein 2D Text `GUI` Element mit wenigen Zeilen je nachdem, wie viele Attribute Pufferverhalten zu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="08440-147">A 2D text `GUI` element can be created with a few lines depending on how many attributes you want to tweak.</span></span>
<span data-ttu-id="08440-148">Der folgende Codeausschnitt ist bereits in unserem Beispiel [**vor**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) , aber wir Exemplarische Vorgehensweise, was passiert.</span><span class="sxs-lookup"><span data-stu-id="08440-148">The following code snippet is already in our [**before**](https://github.com/Microsoft/Windows-tutorials-web/tree/master/BabylonJS-game-with-WebVR/before) sample, but let's walkthrough what's happening.</span></span>
<span data-ttu-id="08440-149">Wir müssen Sie zuerst eine [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) Objekt herstellen, was die GUI behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="08440-149">We first make an [`AdvancedDynamicTexture`](https://doc.babylonjs.com/how_to/gui#advanceddynamictexture) object to establish what the GUI will cover.</span></span> <span data-ttu-id="08440-150">Das Beispiel legt diese auf `CreateFullScreenUI()`, d. h. unsere UI deckt den gesamten Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="08440-150">The sample sets this to `CreateFullScreenUI()`, meaning our UI will cover the entire screen.</span></span> <span data-ttu-id="08440-151">Mit `AdvancedDynamicTexture` erstellt haben, wir stellen ein 2D Text-Feld, das angezeigt beim Starten wird, das Spiel mit `GUI.Rectanlge()` und `GUI.TextBlock()`.</span><span class="sxs-lookup"><span data-stu-id="08440-151">With `AdvancedDynamicTexture` created, we then make a 2D text box that appears upon starting the game using `GUI.Rectanlge()` and `GUI.TextBlock()`.</span></span>


<span data-ttu-id="08440-152">Dieser Code wird in [**"Main.js"**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="08440-152">This code is added within [**main.js**](https://github.com/Microsoft/Windows-tutorials-web/blob/master/BabylonJS-game-with-WebVR/before/js/main.js#L157-L168).</span></span>
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


<span data-ttu-id="08440-153">Diese Benutzeroberfläche ist sichtbar, nachdem erstellt, aber kann aktiviert oder deaktiviert umgeschaltet werden, mit `isVisible` je nachdem, was im Spiel ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="08440-153">This UI is visible once created but can be toggled on or off with `isVisible` depending on what's happening in the game.</span></span>
```javascript
startUI.isVisible = false;
```



## <a name="detecting-headsets"></a><span data-ttu-id="08440-154">Erkennen von headsets</span><span class="sxs-lookup"><span data-stu-id="08440-154">Detecting headsets</span></span>

<span data-ttu-id="08440-155">Es ist üblich, VR-Anwendungen auf zwei Arten von Kameras verfügen, sodass mehrere Szenarien unterstützt werden können.</span><span class="sxs-lookup"><span data-stu-id="08440-155">It's good practice for VR applications to have two types of cameras so that multiple scenarios can be supported.</span></span> <span data-ttu-id="08440-156">Für dieses Spiel müssen wir eine Kamera, die erfordert eine funktionierende Kopfhörer zu angeschlossen sein und einen anderen unterstützen, die keine Kopfhörer verwendet.</span><span class="sxs-lookup"><span data-stu-id="08440-156">For this game, we'll support one camera that requires a working headset to be plugged in, and another that uses no headset.</span></span> <span data-ttu-id="08440-157">Um zu ermitteln, welche wird das Spiel verwenden müssen wir überprüfen Sie zunächst, ob ein Kopfhörer erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="08440-157">To determine which one the game will use, we must first check to see whether a headset has been detected.</span></span> <span data-ttu-id="08440-158">Dazu verwenden wir [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span><span class="sxs-lookup"><span data-stu-id="08440-158">To do that, we’ll use [`navigator.getVRDisplays()`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getVRDisplays).</span></span>


<span data-ttu-id="08440-159">Fügen Sie diesen Code oben genannten `window.addEventListener('DOMContentLoaded')` in **"Main.js"**.</span><span class="sxs-lookup"><span data-stu-id="08440-159">Add this code above `window.addEventListener('DOMContentLoaded')` in **main.js**.</span></span>
```javascript
var headset;
// If a VR headset is connected, get its info
navigator.getVRDisplays().then(function (displays) {
    if (displays[0]) {
        headset = displays[0];
    }
});
```

<span data-ttu-id="08440-160">Mit den Informationen in gespeicherten der `headset` Variable, wir werden jetzt in der Lage, die Kamera auszuwählen, die für den Benutzer geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="08440-160">With the info stored in the `headset` variable, we'll now be able to choose the camera that’s right for the user.</span></span>


## <a name="creating-and-selecting-the-initial-camera"></a><span data-ttu-id="08440-161">Erstellen und Auswählen der anfänglichen Kamera</span><span class="sxs-lookup"><span data-stu-id="08440-161">Creating and selecting the initial camera</span></span>

<span data-ttu-id="08440-162">Mit Babylon.js, WebVR hinzugefügt werden schnell mithilfe der [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span><span class="sxs-lookup"><span data-stu-id="08440-162">With Babylon.js, WebVR can be added quickly by using the [`WebVRFreeCamera`](http://doc.babylonjs.com/classes/3.1/webvrfreecamera).</span></span> <span data-ttu-id="08440-163">Diese Kamera kann Eingaben über die Tastatur und ermöglicht es Ihnen, eine VR Kopfhörer verwenden, um Ihre Drehung "Head" steuern.</span><span class="sxs-lookup"><span data-stu-id="08440-163">This camera can take keyboard input and enables you to use a VR headset to control your "head" rotation.</span></span>


### <a name="step-1-checking-for-headsets"></a><span data-ttu-id="08440-164">Schritt 1: Suchen nach headsets</span><span class="sxs-lookup"><span data-stu-id="08440-164">Step 1: Checking for headsets</span></span>

<span data-ttu-id="08440-165">Für unsere fallback Kamera verwenden wir die [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) , die derzeit in der ursprünglichen Spiel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="08440-165">For our fallback camera, we'll be using the [`UniversalCamera`](https://doc.babylonjs.com/classes/3.1/universalcamera) that’s currently used in the original game.</span></span>

<span data-ttu-id="08440-166">Überprüfen wir unsere `headset` Variable, um festzustellen, ob wir verwenden können, die `WebVRFreeCamera` Kamera.</span><span class="sxs-lookup"><span data-stu-id="08440-166">We'll check our `headset` variable to determine whether we can use the `WebVRFreeCamera` camera.</span></span>

<span data-ttu-id="08440-167">Ersetzen Sie `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` mit dem folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="08440-167">Replace `camera = new BABYLON.UniversalCamera("Camera", new BABYLON.Vector3(0, 18, -45), scene);` with the following code.</span></span>
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


### <a name="step-2-activating-the-webvrfreecamera"></a><span data-ttu-id="08440-168">Schritt 2: Aktivieren der WebVRFreeCamera</span><span class="sxs-lookup"><span data-stu-id="08440-168">Step 2: Activating the WebVRFreeCamera</span></span>
<span data-ttu-id="08440-169">Um diese Kamera in den meisten Browsern zu aktivieren, muss der Benutzer einige Interaktion mit automatischem, die die virtuelle Umgebung anfordert.</span><span class="sxs-lookup"><span data-stu-id="08440-169">To activate this camera in most browsers, the user must perform some interaction that requests the virtual experience.</span></span>
<span data-ttu-id="08440-170">Wir binden diese Funktionalität bis zu einem Mausklick.</span><span class="sxs-lookup"><span data-stu-id="08440-170">We'll hook this functionality up to a mouse click.</span></span>


<span data-ttu-id="08440-171">Fügen Sie den Code in `createScene()` funktionieren, nachdem `camera.applyGravity = true;` .</span><span class="sxs-lookup"><span data-stu-id="08440-171">Paste the code within  `createScene()` function after `camera.applyGravity = true;` .</span></span>
```javascript
        scene.onPointerDown = function () {
            scene.onPointerDown = undefined
            camera.attachControl(canvas, true);
        }
```

<span data-ttu-id="08440-172">Ein Mausklick in das Spiel jetzt erstellt eine Aufforderung wie folgt oder zeigt das Spiel in die Kopfhörer sofort, wenn der Benutzer die Aufforderung vor dem akzeptiert hat.</span><span class="sxs-lookup"><span data-stu-id="08440-172">A click in the game now creates a prompt like the following, or displays the game in the headset right away if the user has accepted the prompt before.</span></span>

![immersiven Aufforderung](images/immersiveview.png)

<span data-ttu-id="08440-174">Wir können auch einen Codeabschnitt, der angezeigt wird Hinzufügen der `UniversalCamera` anzeigen, bevor wir zu wechseln unsere `WebVRFreeCamera`, so dass der Benutzer das Spiel anstatt ein blaues Fenster betrachten.</span><span class="sxs-lookup"><span data-stu-id="08440-174">We can also add a piece of code that will display the `UniversalCamera` view before we switch to our `WebVRFreeCamera`, allowing the user to look at the game instead of a blue window.</span></span> 

<span data-ttu-id="08440-175">Fügen Sie die folgenden nach `engine.runRenderLoop(function () {`.</span><span class="sxs-lookup"><span data-stu-id="08440-175">Add the following after `engine.runRenderLoop(function () {`.</span></span>
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

### <a name="step-3-adding-gamepad-support"></a><span data-ttu-id="08440-176">Schritt 3: Hinzufügen von Gamepad-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="08440-176">Step 3: Adding gamepad support</span></span>

<span data-ttu-id="08440-177">Da die `WebVRFreeCamera` unterstützt keine anfänglich Gamepads, müssen wir die Pfeiltasten der Tastatur unsere Gamepad-Tasten zuordnen.</span><span class="sxs-lookup"><span data-stu-id="08440-177">Since the `WebVRFreeCamera` doesn't initially support gamepads, we'll map our gamepad buttons to the keyboard arrow keys.</span></span> <span data-ttu-id="08440-178">Wir werden dies tun, indem eine Suche in der `inputs` Eigenschaft der Kamera.</span><span class="sxs-lookup"><span data-stu-id="08440-178">We'll do this by digging into the `inputs` property of the camera.</span></span> <span data-ttu-id="08440-179">Durch das Hinzufügen der Codes für die linken analogstick nach oben, unten, links und rechts, um mit den Pfeiltasten übereinstimmen, sind unsere Gamepads zurück in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="08440-179">By adding the corresponding codes for left analog stick up, down, left, and right to match up with the arrow keys, our gamepad is back in action.</span></span>


<span data-ttu-id="08440-180">Fügen Sie diesen Code unten die `scene.onPointerDown = function() {...}` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="08440-180">Add this code below the `scene.onPointerDown = function() {...}` call.</span></span>
``` javascript
    // Custom input, adding Xbox controller support for left analog stick to map to keyboard arrows
    camera.inputs.attached.keyboard.keysUp.push(211);    // Left analog up
    camera.inputs.attached.keyboard.keysDown.push(212);  // Left analog down
    camera.inputs.attached.keyboard.keysLeft.push(214);  // Left analog left
    camera.inputs.attached.keyboard.keysRight.push(213); // Left analog right
```


### <a name="step-4-give-it-a-try"></a><span data-ttu-id="08440-181">Schritt 4: Versuchen Sie es!</span><span class="sxs-lookup"><span data-stu-id="08440-181">Step 4: Give it a try!</span></span>

<span data-ttu-id="08440-182">Wenn wir **"Index.HTML"** mit unseren Kopfhörer öffnen und Gamecontroller angeschlossen, wird ein Klicken Sie auf das blaue Spielfenster unser Spiel VR-Modus wechseln!</span><span class="sxs-lookup"><span data-stu-id="08440-182">If we open **index.html** with our headset and game controller plugged in, a left click on the blue game window will switch our game to VR mode!</span></span> <span data-ttu-id="08440-183">Fahren Sie fort, und platzieren Sie auf Ihre Kopfhörer auf die Ergebnisse in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="08440-183">Go ahead and put on your headset to check out the results.</span></span> 


<iframe height='300' scrolling='no' title='<span data-ttu-id="08440-184">Mithilfe von Babylon.GUI - WebVR Babylon.js Dino-Spiel</span><span class="sxs-lookup"><span data-stu-id="08440-184">Babylon.js dino game using Babylon.GUI - WebVR</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/RjgpJd/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="08440-185">Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js Dino-Spiel mit Babylon.GUI - WebVR</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="08440-185">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/RjgpJd/'>Babylon.js dino game using Babylon.GUI - WebVR</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


## <a name="conclusion"></a><span data-ttu-id="08440-186">Fazit</span><span class="sxs-lookup"><span data-stu-id="08440-186">Conclusion</span></span>

<span data-ttu-id="08440-187">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="08440-187">Congratulations!</span></span> <span data-ttu-id="08440-188">Sie haben nun ein vollständiges Babylon.js-Spiel mit WebVR Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="08440-188">You now have a complete Babylon.js game with WebVR support.</span></span> <span data-ttu-id="08440-189">Hier können Sie nutzen, was Sie gelernt haben, erstellen Sie ein noch besseres Spiel oder Deaktivieren dieses erstellt.</span><span class="sxs-lookup"><span data-stu-id="08440-189">From here you can take what you've learned to build an even better game, or build off this one.</span></span>
