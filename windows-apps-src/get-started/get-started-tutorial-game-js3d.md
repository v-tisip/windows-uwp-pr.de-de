---
title: Lernprogramm für die ersten Schritte – ein 3D-UWP-Spiel in JavaScript
description: Ein UWP-Spiel für den Microsoft Store, geschrieben in JavaScript mit three.js
author: abbycar
ms.author: abigailc
ms.date: 03/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: fb4249b2-f93c-4993-9e4d-57a62c04be66
ms.localizationpriority: medium
ms.openlocfilehash: fa3722c5b011d16ca793b3541efe124b7c255dfd
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5471665"
---
# <a name="creating-a-3d-javascript-game-using-threejs"></a><span data-ttu-id="2d47d-104">Erstellen eines 3D-JavaScript-Spiels mit three.js</span><span class="sxs-lookup"><span data-stu-id="2d47d-104">Creating a 3D JavaScript game using three.js</span></span>

## <a name="introduction"></a><span data-ttu-id="2d47d-105">Einführung</span><span class="sxs-lookup"><span data-stu-id="2d47d-105">Introduction</span></span>

<span data-ttu-id="2d47d-106">Für Webentwickler oder JavaScript-Tüftler ist die Entwicklung von UWP-Apps mit JavaScript eine einfache Möglichkeit, ihre Apps auf der ganzen Welt zu vertreiben.</span><span class="sxs-lookup"><span data-stu-id="2d47d-106">For web developers or JavaScript tinkerers, developing UWP apps with JavaScript is an easy way in to getting your apps out to the world.</span></span> <span data-ttu-id="2d47d-107">Sie müssen sich dadurch nicht um das Lernen einer Sprache wie C# oder C++ kümmern.</span><span class="sxs-lookup"><span data-stu-id="2d47d-107">No need to worry about learning a language like C# or C++!</span></span>

<span data-ttu-id="2d47d-108">In diesem Beispiel werden wir von den Vorteilen der **three.js**-Bibliothek profitieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-108">For this sample, we’re going to be taking advantage of the **three.js** library.</span></span> <span data-ttu-id="2d47d-109">Diese Bibliothek baut auf WebGL auf, einer API, die zum Rendern von 2D- und 3D-Grafiken für Webbrowser verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-109">This library builds off of WebGL, an API that's used for rendering 2D and 3D graphics for web browsers.</span></span> <span data-ttu-id="2d47d-110">**three.js** verwendet diese komplizierte API und vereinfacht sie, wodurch die 3D-Entwicklung viel einfacher wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-110">**three.js** takes this complicated API and simplifies it, making 3D development much easier.</span></span> 


<span data-ttu-id="2d47d-111">Möchten Sie einen Blick auf die App werfen, die wir erstellen werden, bevor Sie weiterlesen?</span><span class="sxs-lookup"><span data-stu-id="2d47d-111">Want to get a glimpse of the app we'll be making before reading further?</span></span> <span data-ttu-id="2d47d-112">Probieren Sie sie auf CodePen aus!</span><span class="sxs-lookup"><span data-stu-id="2d47d-112">Check it out on CodePen!</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-113">Finales Dino-Spiel</span><span class="sxs-lookup"><span data-stu-id="2d47d-113">Dino game final</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/NpKejy/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-114">Weitere Informationen finden Sie im Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/NpKejy/'>Finales Dino-Spiel</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-114">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/NpKejy/'>Dino game final</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

> [!NOTE] 
> <span data-ttu-id="2d47d-115">Dies ist kein vollständiges Spiel; Dieses Skript dient zu zeigen, wie mit JavaScript und einer Drittanbieterbibliothek um eine app im Microsoft Store veröffentlichen möchten bereit zu machen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-115">This is a not a complete game; it is designed to demonstrate using JavaScript and a third-party library to make an app ready to publish to the Microsoft Store.</span></span>


## <a name="requirements"></a><span data-ttu-id="2d47d-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2d47d-116">Requirements</span></span>

<span data-ttu-id="2d47d-117">Um dieses Projekt auszuprobieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2d47d-117">To play with this project, you'll need the following:</span></span>
-   <span data-ttu-id="2d47d-118">Einen Windows-Computer (oder einen virtuellen Computer) mit der aktuellen Version von Windows10.</span><span class="sxs-lookup"><span data-stu-id="2d47d-118">A Windows computer (or a virtual machine) running the current version of Windows 10.</span></span>
-   <span data-ttu-id="2d47d-119">Eine Kopie von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d47d-119">A copy of Visual Studio.</span></span> <span data-ttu-id="2d47d-120">Die kostenlose Visual Studio Community Edition kann von der [Visual Studio-Homepage](http://visualstudio.com/) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-120">The free Visual Studio Community Edition can be downloaded from the [Visual Studio homepage](http://visualstudio.com/).</span></span>
<span data-ttu-id="2d47d-121">Dieses Projekt verwendet die **three.js**-JavaScript-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="2d47d-121">This project makes use of the **three.js** JavaScript library.</span></span> <span data-ttu-id="2d47d-122">**three.js** ist unter der MIT-Lizenz veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="2d47d-122">**three.js** is released under the MIT license.</span></span> <span data-ttu-id="2d47d-123">Diese Bibliothek ist bereits im Projekt vorhanden (suchen Sie nach `js/libs` in der Projektmappen-Explorer-Ansicht).</span><span class="sxs-lookup"><span data-stu-id="2d47d-123">This library is already present in the project (look for `js/libs` in the Solution Explorer view).</span></span> <span data-ttu-id="2d47d-124">Weitere Informationen zu dieser Bibliothek finden Sie auf der [**three.js**](https://threejs.org/)-Startseite.</span><span class="sxs-lookup"><span data-stu-id="2d47d-124">More information about this library can be found at the [**three.js**](https://threejs.org/) home page.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2d47d-125">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="2d47d-125">Getting started</span></span>

<span data-ttu-id="2d47d-126">Der vollständige Quellcode für die App befindet sich in [GitHub](https://github.com/Microsoft/Windows-appsample-get-started-js3d).</span><span class="sxs-lookup"><span data-stu-id="2d47d-126">The complete source code for the app is stored on [GitHub](https://github.com/Microsoft/Windows-appsample-get-started-js3d).</span></span>

<span data-ttu-id="2d47d-127">Die einfachste Möglichkeit ist es, GitHub zu besuchen, auf die grüne Schaltfläche „Clone or download“ zu klicken und „In Visual Studio öffnen“ auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-127">The simplest way to get started is to visit GitHub, click on the green Clone or download button, and select Open in Visual Studio.</span></span> 

![Schaltfläche „clone or download“](images/3dclone.png)

<span data-ttu-id="2d47d-129">Wenn Sie das Projekt nicht klonen möchten, können Sie es als Zip-Datei herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-129">If you don't want to clone the project, you can download it as a zip file.</span></span>
<span data-ttu-id="2d47d-130">Nachdem die Projektmappe in Visual Studio geladen wurde, sehen Sie mehrere Dateien, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="2d47d-130">Once the solution has been loaded into Visual Studio, you'll see several files, including:</span></span>
-   <span data-ttu-id="2d47d-131">Images/ – ein Ordner, der die verschiedenen Symbole enthält, die für UWP-Apps erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2d47d-131">Images/ - a folder containing the various icons required by UWP apps.</span></span>
- <span data-ttu-id="2d47d-132">css / – ein Ordner, der die CSS enthält, die verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-132">css/ - a folder containing the CSS to be used.</span></span>
-   <span data-ttu-id="2d47d-133">js / – ein Ordner mit den JavaScript-Dateien.</span><span class="sxs-lookup"><span data-stu-id="2d47d-133">js/ - a folder containing the JavaScript files.</span></span> <span data-ttu-id="2d47d-134">Die main.js-Datei ist unser Spiel, während die anderen Dateien Drittanbieterbibliotheken sind.</span><span class="sxs-lookup"><span data-stu-id="2d47d-134">The main.js file is our game while the other files are the third-party libraries.</span></span>
-   <span data-ttu-id="2d47d-135">models/ – ein Ordner mit den 3D-Modellen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-135">models/ - a folder containing the 3D models.</span></span> <span data-ttu-id="2d47d-136">Für dieses Spiel gibt es nur ein Modell für den Dinosaurier.</span><span class="sxs-lookup"><span data-stu-id="2d47d-136">For this game, we only have one for the dinosaur.</span></span>
-   <span data-ttu-id="2d47d-137">index.html – die Webseite, die den Spiel-Renderer hostet.</span><span class="sxs-lookup"><span data-stu-id="2d47d-137">index.html - the webpage that hosts the game's renderer.</span></span>

<span data-ttu-id="2d47d-138">Jetzt können Sie das Spiel ausführen!</span><span class="sxs-lookup"><span data-stu-id="2d47d-138">Now you can run the game!</span></span>

<span data-ttu-id="2d47d-139">Drücken Sie F5, um die App zu starten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-139">Press F5 to start the app.</span></span> <span data-ttu-id="2d47d-140">Sie sollten ein Fenster sehen, das Sie auffordert, auf den Bildschirm zu klicken.</span><span class="sxs-lookup"><span data-stu-id="2d47d-140">You should see a window open, prompting you to click on the screen.</span></span> <span data-ttu-id="2d47d-141">Sie sehen außerdem einen Dinosaurier, der sich im Hintergrund bewegt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-141">You’ll also see a dinosaur moving around in the background.</span></span> <span data-ttu-id="2d47d-142">Schließen Sie das Spiel, damit wir jetzt die App und ihre wichtigsten Komponenten untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="2d47d-142">Go ahead and close out of the game and we’ll begin examining the app and its key components.</span></span>

> [!NOTE] 
> <span data-ttu-id="2d47d-143">Hat etwas nicht geklappt?</span><span class="sxs-lookup"><span data-stu-id="2d47d-143">Something go wrong?</span></span> <span data-ttu-id="2d47d-144">Stellen Sie sicher, dass Sie Visual Studio mit Web-Unterstützung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="2d47d-144">Be sure you have installed Visual Studio with web support.</span></span> <span data-ttu-id="2d47d-145">Sie können dies überprüfen, indem Sie ein neues Projekt erstellen. Wenn es keine Unterstützung für JavaScript gibt, müssen Sie Visual Studio neu installieren und das Feld „Microsoft Web Developer Tools“ aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-145">You can check by creating a new project - if there is no support for JavaScript, you will need to re-install Visual Studio and check the Microsoft Web Developer Tools box.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="2d47d-146">Exemplarische Vorgehensweise</span><span class="sxs-lookup"><span data-stu-id="2d47d-146">Walkthrough</span></span>

<span data-ttu-id="2d47d-147">Wenn Sie das Spiel starten, werden Sie dazu aufgefordert, auf den Bildschirm zu klicken.</span><span class="sxs-lookup"><span data-stu-id="2d47d-147">When you start up this game, you’ll see a prompt to click on the screen.</span></span> <span data-ttu-id="2d47d-148">Die [Pointer-Lock-API](https://developer.mozilla.org/docs/Web/API/Pointer_Lock_API) wird verwendet, damit Sie die Maus verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2d47d-148">The [Pointer Lock API](https://developer.mozilla.org/docs/Web/API/Pointer_Lock_API) is used to allow you to look around with your mouse.</span></span> <span data-ttu-id="2d47d-149">Das Bewegen erfolgt durch Drücken der Pfeiltasten W, A, S, D.</span><span class="sxs-lookup"><span data-stu-id="2d47d-149">Moving is done by pressing the W, A, S, D/arrow keys.</span></span>
<span data-ttu-id="2d47d-150">Das Ziel dieses Spiels ist es, sich vom Dinosaurier fernzuhalten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-150">The goal of this game is to stay away from the dinosaur.</span></span> <span data-ttu-id="2d47d-151">Sobald der Dinosaurier nah genug bei Ihnen ist, beginnt er, Ihnen nachzujagen, bis Sie entweder außerhalb seines Bereichs gelangen oder das Spiel verlieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-151">Once the dinosaur is close enough to you, it’ll start chasing you until you either get out of range or get too close and lose the game.</span></span>

### <a name="1-setting-up-your-initial-html-file"></a><span data-ttu-id="2d47d-152">1. Einrichten der initialen HTML-Datei</span><span class="sxs-lookup"><span data-stu-id="2d47d-152">1. Setting up your initial HTML file</span></span>

<span data-ttu-id="2d47d-153">In **index.html** müssen Sie zuerst etwas HTML-Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-153">Within **index.html**, you'll need to add a little HTML to get started.</span></span> <span data-ttu-id="2d47d-154">Diese Datei ist die Standardwebseite, die unsere App enthält.</span><span class="sxs-lookup"><span data-stu-id="2d47d-154">This file is the default web page that contains our app.</span></span>

<span data-ttu-id="2d47d-155">Jetzt werden wir diese mit den Bibliotheken einrichten, die wir verwenden werden, und der `div` (mit dem Namen `container`), die wir verwenden, um unsere Grafiken zu rendern.</span><span class="sxs-lookup"><span data-stu-id="2d47d-155">Right now, we'll set it up with the libraries we'll be using and the `div` (named `container`) that we'll use to render our graphics to.</span></span> <span data-ttu-id="2d47d-156">Außerdem legen wir fest, dass diese zu unserer **main.js** (unserem Spielcode) zeigt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-156">We'll also set it to point to our **main.js** (our game code).</span></span>


```html
<!DOCTYPE html>
<html lang='en'>

<head>
    <link rel="stylesheet" type="text/css" href="css/stylesheet.css" />
</head>

    <body>
        <div id='container'></div>
        <script src='js/libs/three.js'></script>
        <script src="js/controls/PointerLockControls.js"></script>
        <script src="js/main.js"></script>
    </body>

</html>
```


<span data-ttu-id="2d47d-157">Nachdem unsere Starter-HTML nun einsatzbereit ist, können wir uns **main.js** zuwenden und einige Grafiken erstellen!</span><span class="sxs-lookup"><span data-stu-id="2d47d-157">Now that we have our starter HTML ready to go, let's head over to **main.js** and make some graphics!</span></span>

### <a name="2-creating-your-scene"></a><span data-ttu-id="2d47d-158">2. Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="2d47d-158">2. Creating your scene</span></span>

<span data-ttu-id="2d47d-159">Im Abschnitt zu exemplarischen Vorgehensweisen werden wir die Grundlage für das Spiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-159">In the section of the walkthrough we're going to adding the foundation of the game.</span></span>

<span data-ttu-id="2d47d-160">Beginnen wir damit, eine `scene` auszuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-160">We'll start off by fleshing out a `scene`.</span></span> <span data-ttu-id="2d47d-161">Eine `scene` in **three.js** ist der Ort, in dem Ihre Kamera, Objekte und Lichter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-161">A `scene` in **three.js** is where your camera, objects, and lights will be added.</span></span> <span data-ttu-id="2d47d-162">Sie benötigen auch einen Renderer, der aufnimmt, was die Kamera in der Szene sieht, und dies angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-162">You'll also need a renderer which will take what your camera sees in the scene and display it.</span></span>

<span data-ttu-id="2d47d-163">In **main.js** erstellen wir eine Funktion, die all dies erledigt und `init()` heißt. Sie ruft einige zusätzliche Funktionen auf:</span><span class="sxs-lookup"><span data-stu-id="2d47d-163">In **main.js** we'll make a function that does all of this called `init()` which calls on some additional functions:</span></span>

```javascript
var UNITWIDTH = 90; // Width of a cubes in the maze
var UNITHEIGHT = 45; // Height of the cubes in the maze

var camera, scene, renderer;

init();
animate();

function init() {
    // Create the scene where everything will go
    scene = new THREE.Scene();

    // Add some fog for effects
    scene.fog = new THREE.FogExp2(0xcccccc, 0.0015);

    // Set render settings
    renderer = new THREE.WebGLRenderer();
    renderer.setClearColor(scene.fog.color);
    renderer.setPixelRatio(window.devicePixelRatio);
    renderer.setSize(window.innerWidth, window.innerHeight);

    // Get the HTML container and connect renderer to it
    var container = document.getElementById('container');
    container.appendChild(renderer.domElement);

    // Set camera position and view details
    camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 1, 2000);
    camera.position.y = 20; // Height the camera will be looking from
    camera.position.x = 0;
    camera.position.z = 0;

    // Add the camera
    scene.add(camera);

    // Add the walls(cubes) of the maze
    createMazeCubes();

    // Add lights to the scene
    addLights();

    // Listen for if the window changes sizes and adjust
    window.addEventListener('resize', onWindowResize, false);
}

```

<span data-ttu-id="2d47d-164">Die anderen Funktionen, die wir erstellen müssen, sind:</span><span class="sxs-lookup"><span data-stu-id="2d47d-164">The other functions we'll need to create include:</span></span>
- `createMazeCubes()`
- `addLights()`
- `onWindowResize()`
- `animate()` / `render()`
- <span data-ttu-id="2d47d-165">Einheitskonvertierungsfunktionen</span><span class="sxs-lookup"><span data-stu-id="2d47d-165">Unit conversion functions</span></span>

#### <a name="createmazecubes"></a><span data-ttu-id="2d47d-166">createMazeCubes()</span><span class="sxs-lookup"><span data-stu-id="2d47d-166">createMazeCubes()</span></span>

<span data-ttu-id="2d47d-167">Die `createMazeCubes()`-Funktion wird einen einfachen Würfel zu unserer Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-167">The `createMazeCubes()` function will add a simple cube to our scene.</span></span> <span data-ttu-id="2d47d-168">Später verwenden wir die Funktion, um viele Würfel hinzuzufügen und unser Labyrinth zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-168">Later on we'll make the funcion add many cubes to make our maze.</span></span>

```javascript
function createMazeCubes() {

  // Make the shape of the cube that is UNITWIDTH wide/deep, and UNITHEIGHT tall
  var cubeGeo = new THREE.BoxGeometry(UNITWIDTH, UNITHEIGHT, UNITWIDTH);
  // Make the material of the cube and set it to blue
  var cubeMat = new THREE.MeshPhongMaterial({
    color: 0x81cfe0,
  });
  
  // Combine the geometry and material to make the cube
  var cube = new THREE.Mesh(cubeGeo, cubeMat);

  // Add the cube to the scene
  scene.add(cube);

  // Update the cube's position
  cube.position.y = UNITHEIGHT / 2;
  cube.position.x = 0;
  cube.position.z = -100;
  // rotate the cube by 30 degrees
  cube.rotation.y = degreesToRadians(30);
}

```

#### <a name="addlights"></a><span data-ttu-id="2d47d-169">addLights()</span><span class="sxs-lookup"><span data-stu-id="2d47d-169">addLights()</span></span>

<span data-ttu-id="2d47d-170">Die `addLights()`-Funktion ist eine einfache Funktion, welche die Erstellung unserer Lichter gruppiert und diese zur Szene hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-170">The `addLights()` function is a simple function that groups the creation of our lights and adds them to the scene.</span></span>

```javascript
function addLights() {
  var lightOne = new THREE.DirectionalLight(0xffffff);
  lightOne.position.set(1, 1, 1);
  scene.add(lightOne);

  // Add a second light with half the intensity
  var lightTwo = new THREE.DirectionalLight(0xffffff, .5);
  lightTwo.position.set(1, -1, -1);
  scene.add(lightTwo);
}
```

#### <a name="onwindowresize"></a><span data-ttu-id="2d47d-171">onWindowResize()</span><span class="sxs-lookup"><span data-stu-id="2d47d-171">onWindowResize()</span></span>

<span data-ttu-id="2d47d-172">Die `onWindowResize`-Funktion wird aufgerufen, wenn der Ereignis-Listener hört, dass ein `resize`-Ereignis ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="2d47d-172">The `onWindowResize` function is called whenever our event listener hears that a `resize` event was fired.</span></span> <span data-ttu-id="2d47d-173">Dies geschieht, wenn der Benutzer die Größe des Fensters anpasst.</span><span class="sxs-lookup"><span data-stu-id="2d47d-173">This happens whenever the user adjusts the size of the window.</span></span> <span data-ttu-id="2d47d-174">In diesem Fall möchten wir sicherstellen, dass das Bild proportional bleibt und im gesamten Fenster angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-174">If this happens, we want to make sure tha the image stays proportional and can be seen in the entire window.</span></span>

```javascript
function onWindowResize() {

  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();

  renderer.setSize(window.innerWidth, window.innerHeight);
}
```

#### <a name="animate"></a><span data-ttu-id="2d47d-175">animate()</span><span class="sxs-lookup"><span data-stu-id="2d47d-175">animate()</span></span>

<span data-ttu-id="2d47d-176">Zuletzt benötigen wir unsere `animate()`-Funktion, die auch die `render()`-Funktion aufrufen wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-176">The last thing we'll need is our `animate()` function, which will also call the `render()` function.</span></span> <span data-ttu-id="2d47d-177">Die [`requestAnimationFrame()`](https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame)-Funktion wird verwendet, um unseren Renderer kontinuierlich zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-177">The [`requestAnimationFrame()`](https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame) function is used to constantly update our renderer.</span></span> <span data-ttu-id="2d47d-178">Später verwenden wir diese Funktionen, um unseren Renderer mit Animationen wie dem Bewegen im Labyrinth zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-178">Later on, we'll use these functions to update our renderer with cool animations like moving around the maze.</span></span>

```javascript
function animate() {
    render();
    // Keep updating the renderer
    requestAnimationFrame(animate);
}

function render() {
    renderer.render(scene, camera);
}
```

#### <a name="unit-conversion-functions"></a><span data-ttu-id="2d47d-179">Einheitskonvertierungsfunktionen</span><span class="sxs-lookup"><span data-stu-id="2d47d-179">Unit conversion functions</span></span>

<span data-ttu-id="2d47d-180">In **three.js** werden Drehungen im Bogenmaß gemessen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-180">In **three.js** rotations are measured in radians.</span></span> <span data-ttu-id="2d47d-181">Um dies für uns zu vereinfachen, fügen wir einige Funktionen hinzu, damit wir einfach zwischen Grad und Bogenmaß/Radianten konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="2d47d-181">To make things easy for us, we'll go ahead and add some functions so that we can easily convert between degrees and radians.</span></span> 


```javascript
function degreesToRadians(degrees) {
  return degrees * Math.PI / 180;
}

function radiansToDegrees(radians) {
  return radians * 180 / Math.PI;
}
```

<span data-ttu-id="2d47d-182">Wer würde sich merken, dass 30Grad 523Radianten sind?</span><span class="sxs-lookup"><span data-stu-id="2d47d-182">Who would remember that 30 degrees is .523 radians?</span></span> <span data-ttu-id="2d47d-183">Es ist sehr viel einfacher, `degreesToRadians(30)` durchzuführen, um unsere Drehung zu erhalten, was in unserer `createMazeCubes()`-Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-183">It's much simpler to instead do `degreesToRadians(30)` to get our rotation amount which is used in our `createMazeCubes()` function.</span></span>

___

<span data-ttu-id="2d47d-184">Das war relativ viel Code, aber nun haben wir einen wunderschönen Würfel, der zu unserem `container` gerendert wird!</span><span class="sxs-lookup"><span data-stu-id="2d47d-184">That was quite a bit of code to take in, but we now have a beautiful cube the is rendered to our `container`!</span></span> <span data-ttu-id="2d47d-185">Sehen Sie sich die Ergebnisse in CodePen an.</span><span class="sxs-lookup"><span data-stu-id="2d47d-185">Check out the results in the CodePen.</span></span>

<span data-ttu-id="2d47d-186">Sie können den gesamten JavaScript-Inhalt kopieren und in diesen in CodePen einfügen, wenn Probleme aufgetreten sind, oder diesen bearbeiten, um die Lichter anzupassen und einige Farben zu ändern.</span><span class="sxs-lookup"><span data-stu-id="2d47d-186">You can copy and paste all the JavaScript in this CodePen to get caught up if you encountered issues, or edit it to adjust some lights and change some colors.</span></span> 

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-187">Licht, Kamera, Cube!</span><span class="sxs-lookup"><span data-stu-id="2d47d-187">Lights, camera, cube!</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/YZWygZ/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-188">Sehen Sie sich den Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/YZWygZ/'>Licht, Kamera, Cube!</a></span><span class="sxs-lookup"><span data-stu-id="2d47d-188">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/YZWygZ/'>Lights, camera, cube!</a></span></span> <span data-ttu-id="2d47d-189">von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-189">by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


### <a name="3-making-the-maze"></a><span data-ttu-id="2d47d-190">3. Erstellen des Labyrinths</span><span class="sxs-lookup"><span data-stu-id="2d47d-190">3. Making the maze</span></span>

<span data-ttu-id="2d47d-191">Auch wenn das Ansehen eines Würfels bereits atemberaubend ist, ist ein ganzes Labyrinth aus Würfeln noch beeindruckender!</span><span class="sxs-lookup"><span data-stu-id="2d47d-191">While staring at a cube is breathtaking, what’s even better is a whole maze made out of cubes!</span></span> <span data-ttu-id="2d47d-192">Es ist ein ziemlich bekanntes Geheimnis in der Spiele-Community, dass eine der schnellsten Möglichkeiten für das Erstellen eines Labyrinths das Platzieren von Würfeln mit einem 2D-Array ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-192">It’s a pretty well-known secret in the games community that one of the quickest ways to creating a level is by placing cubes all over with a 2D array.</span></span>
 
![Labyrinth, das mit einem 2D-Array erstellt wurde](images/dinomap.png)

<span data-ttu-id="2d47d-194">Das Platzieren von 1ern bei Würfeln und von 0ern bei Leerräumen bietet eine manuelle und einfache Methode zum Erstellen bzw. Optimieren des Labyrinths.</span><span class="sxs-lookup"><span data-stu-id="2d47d-194">Placing 1’s where cubes are and 0’s where empty space is allows for a manual and simple way for you to create/tweak the maze.</span></span>

<span data-ttu-id="2d47d-195">Wir erreichen dies, indem wir unsere alte `createMazeCubes()`-Funktion mit einer Funktion mit geschachtelter Schleife ersetzen, um mehrere Würfel zu erstellen und zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-195">We achieve this by replacing our old `createMazeCubes()` function with one that uses a nested loop to create and place multiple cubes.</span></span> <span data-ttu-id="2d47d-196">Anschließend erstellen wir einen Arraynamen `collidableObjects` und fügen die Würfel für die Kollisionserkennung später in diesem Lernprogramm hinzu:</span><span class="sxs-lookup"><span data-stu-id="2d47d-196">We'll also create an array name `collidableObjects` and add the cubes to it for collision detection later in this tutorial:</span></span>

```javascript
var totalCubesWide; // How many cubes wide the maze will be
var collidableObjects = []; // An array of collidable objects used later

function createMazeCubes() {
  // Maze wall mapping, assuming even square
  // 1's are cubes, 0's are empty space
  var map = [
    [0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, ],
    [0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, ],
    [0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 1, 1, 1, 1, 0, 1, 1, 0, 0, ],
    [0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, ],
    [1, 1, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 1, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 1, 1, ],
    [0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 1, 1, 1, 0, 1, 0, 0, 0, 0, 0, ],
    [1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 0, 1, 1, 0, 1, 0, 0, 0, 0, 0, ],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ],
    [1, 1, 1, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 1, 0, 1, 1, 1, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, ],
    [0, 0, 1, 1, 1, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, ]
  ];

  // wall details
  var cubeGeo = new THREE.BoxGeometry(UNITWIDTH, UNITHEIGHT, UNITWIDTH);
  var cubeMat = new THREE.MeshPhongMaterial({
    color: 0x81cfe0,
  });

  // Keep cubes within boundry walls
  var widthOffset = UNITWIDTH / 2;
  // Put the bottom of the cube at y = 0
  var heightOffset = UNITHEIGHT / 2;
  
  // See how wide the map is by seeing how long the first array is
  totalCubesWide = map[0].length;

  // Place walls where 1`s are
  for (var i = 0; i < totalCubesWide; i++) {
    for (var j = 0; j < map[i].length; j++) {
      // If a 1 is found, add a cube at the corresponding position
      if (map[i][j]) {
        // Make the cube
        var cube = new THREE.Mesh(cubeGeo, cubeMat);
        // Set the cube position
        cube.position.z = (i - totalCubesWide / 2) * UNITWIDTH + widthOffset;
        cube.position.y = heightOffset;
        cube.position.x = (j - totalCubesWide / 2) * UNITWIDTH + widthOffset;
        // Add the cube
        scene.add(cube);
        // Used later for collision detection
        collidableObjects.push(cube);
      }
    }
  }
    // The size of the maze will be how many cubes wide the array is * the width of a cube
    mapSize = totalCubesWide * UNITWIDTH;
}

```

<span data-ttu-id="2d47d-197">Da wir nun wissen, wie viele Würfel verwendet werden (und wie groß sie sind), können wir jetzt die berechnete `mapSize`-Variable verwenden, um die Dimensionen der Grundebene festzulegen:</span><span class="sxs-lookup"><span data-stu-id="2d47d-197">Now that we know how many cubes are being used (and how big they are), we can now use the calculated `mapSize` variable to set the dimensions of the ground plane:</span></span>

```javascript
var mapSize;    // The width/depth of the maze

function createGround() {
    // Create ground geometry and material
    var groundGeo = new THREE.PlaneGeometry(mapSize, mapSize);
    var groundMat = new THREE.MeshPhongMaterial({ color: 0xA0522D, side: THREE.DoubleSide});

    var ground = new THREE.Mesh(groundGeo, groundMat);
    ground.position.set(0, 1, 0);
    // Rotate the place to ground level
    ground.rotation.x = degreesToRadians(90);
    scene.add(ground);
}
```

<span data-ttu-id="2d47d-198">Der letzte Teil des Labyrinths, den wir hinzufügen, sind die Umfassungswände, die alles beherbergen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-198">The last piece of the maze we'll add is perimeter walls to box everything in.</span></span> <span data-ttu-id="2d47d-199">Wir werden eine Schleife verwenden, um zwei Ebenen (unsere Wände) gleichzeitig zu erstellen, und verwenden die `mapSize`-Variable, die wir in `createGround()` berechnet haben, um zu bestimmen, wie breit diese sein sollen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-199">We'll use a loop to make two planes (our walls) at a time, using the `mapSize` variable we calculated in `createGround()` to determine how wide they should be.</span></span> <span data-ttu-id="2d47d-200">Die neuen Wände werden auch zu unserem `collidableObjects`-Array für die zukünftige Kollisionserkennung hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="2d47d-200">The new walls will also be added to our `collidableObjects` array for future collision detection:</span></span>

```javascript
function createPerimWalls() {
    var halfMap = mapSize / 2;  // Half the size of the map
    var sign = 1;               // Used to make an amount positive or negative

    // Loop through twice, making two perimeter walls at a time
    for (var i = 0; i < 2; i++) {
        var perimGeo = new THREE.PlaneGeometry(mapSize, UNITHEIGHT);
        // Make the material double sided
        var perimMat = new THREE.MeshPhongMaterial({ color: 0x464646, side: THREE.DoubleSide });
        // Make two walls
        var perimWallLR = new THREE.Mesh(perimGeo, perimMat);
        var perimWallFB = new THREE.Mesh(perimGeo, perimMat);

        // Create left/right wall
        perimWallLR.position.set(halfMap * sign, UNITHEIGHT / 2, 0);
        perimWallLR.rotation.y = degreesToRadians(90);
        scene.add(perimWallLR);
        // Used later for collision detection
        collidableObjects.push(perimWallLR);
        // Create front/back wall
        perimWallFB.position.set(0, UNITHEIGHT / 2, halfMap * sign);
        scene.add(perimWallFB);

        // Used later for collision detection
        collidableObjects.push(perimWallFB);

        sign = -1; // Swap to negative value
    }
}
```


<span data-ttu-id="2d47d-201">Vergessen Sie nicht, einen Aufruf zu `createGround()` und `createPerimWalls` nach `createMazeCubes()` in Ihrer `init()` -Funktion hinzuzufügen, damit diese kompiliert werden!</span><span class="sxs-lookup"><span data-stu-id="2d47d-201">Don't forget to add a call to `createGround()` and `createPerimWalls` after `createMazeCubes()` in your `init()` function so that they get compiled!</span></span>
___

<span data-ttu-id="2d47d-202">Wir haben nun ein ansprechendes Labyrinth, das wir betrachten können, können jedoch nicht wirklich einen Eindruck erhalten, wie toll es wirklich ist, da die Kamera nur einen bestimmten Ort anzeigt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-202">We now have a beautiful maze to look at but can't really get a feel for just how cool it is because our camera is stuck in one spot.</span></span> <span data-ttu-id="2d47d-203">Es ist an der Zeit, einen Schritt weiter zu gehen und einige Kamerasteuerelemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-203">It's time to kick this game up a notch and add in some camera controls.</span></span>

<span data-ttu-id="2d47d-204">Testen Sie in CodePen Dinge wie das Ändern von Farben der Würfel oder das Entfernen des Bodens, indem Sie `createGround()` in der `init()`-Funktion auskommentieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-204">Feel free to test things out in the CodePen like changing the colors of the cubes or removing the ground by commenting out `createGround()` in the `init()` function.</span></span>


<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-205">Labyrinth erstellen</span><span class="sxs-lookup"><span data-stu-id="2d47d-205">Maze building</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/JWKYzG/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-206">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/JWKYzG/'>Labyrintherstellung</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-206">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/JWKYzG/'>Maze building</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="4-allowing-the-player-to-look-around"></a><span data-ttu-id="2d47d-207">4. Zulassen , dass sich der Spieler umsehen kann</span><span class="sxs-lookup"><span data-stu-id="2d47d-207">4. Allowing the player to look around</span></span>

<span data-ttu-id="2d47d-208">Jetzt ist es an der Zeit, in das Labyrinth zu gehen und uns umzusehen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-208">Now it’s time to get in that maze and start looking around.</span></span> <span data-ttu-id="2d47d-209">Dazu verwenden wir die **PointerLockControls.js**-Bibliothek und die Kamera.</span><span class="sxs-lookup"><span data-stu-id="2d47d-209">To do this we’ll be using the **PointerLockControls.js** library and our camera.</span></span>

<span data-ttu-id="2d47d-210">Die **PoinerLockControls.js**-Bibliothek verwendet die Maus, um die Kamera in die Richtung zu drehen, in der der Mauszeiger bewegt wird, sodass sich der Spieler umsehen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-210">The **PoinerLockControls.js** library uses the mouse to rotate the camera in the direction that the mouse is moved, allowing the player to look around.</span></span> 

<span data-ttu-id="2d47d-211">Zuerst fügen wir einige neue Elemente zu unserer **index.html**-Datei hinzu:</span><span class="sxs-lookup"><span data-stu-id="2d47d-211">First let's add some new elements to our **index.html** file:</span></span>

```html
<div id="blocker">
    <div id="instructions">
    <strong>Click to look!</strong>
    </div>
</div>

<script src="main.js"></script>
```

<span data-ttu-id="2d47d-212">Sie benötigen auch alle CSS in CodePen am Ende dieses Abschnitts.</span><span class="sxs-lookup"><span data-stu-id="2d47d-212">You'll also need all the CSS in the CodePen at the bottom of this section.</span></span> <span data-ttu-id="2d47d-213">Diese sollten in Ihre **stylesheet.css**-Datei eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-213">It should be pasted into your **stylesheet.css** file.</span></span>

<span data-ttu-id="2d47d-214">Wechseln Sie zurück zu **main.js**, fügen Sie ein paar neue globale Variablen hinzu; `controls` zum Speichern unseres Controllers, `controlsEnabled`, um den Zustand des Controllers nachzuverfolgen, und `blocker`, um das `blocker`-Element in **index.html** abzurufen:</span><span class="sxs-lookup"><span data-stu-id="2d47d-214">Switching back to **main.js**, add a few new global variables; `controls` to store our controller, `controlsEnabled` to keep track of the controller state, and `blocker` to grab the `blocker` element in **index.html**:</span></span>

```javascript
var controls;
var controlsEnabled = false;

// HTML elements to be changed
var blocker = document.getElementById('blocker');
```


<span data-ttu-id="2d47d-215">In unserer `init()`-Funktion können wir jetzt ein neues `PoinerLockControls`-Objekt erstellen, dieses unserer `camera` übergeben, und dann die `camera` hinzufügen (Zugriff mit `controls.getObject()`).</span><span class="sxs-lookup"><span data-stu-id="2d47d-215">Now in our `init()` function we can make a new `PoinerLockControls` object, pass it our `camera`, and add the `camera` (accessed with `controls.getObject()`).</span></span>

```javascript
controls = new THREE.PointerLockControls(camera);
scene.add(controls.getObject());
```

<span data-ttu-id="2d47d-216">Die Kamera ist jetzt verbunden, jedoch müssen wir nun Maus und Controller interagieren lassen, damit wir uns umsehen können.</span><span class="sxs-lookup"><span data-stu-id="2d47d-216">The camera is now connected, but we need to somehow let the mouse and controller interact so that we can look around.</span></span> 

<span data-ttu-id="2d47d-217">In dieser Situation kommt die [Pointer-Lock-API](https://docs.microsoft.com/microsoft-edge/dev-guide/dom/pointer-lock) ins Spiel, mit der wir die Mausbewegungen mit unserer Kamera verbinden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-217">For this situation, the [Pointer Lock API](https://docs.microsoft.com/microsoft-edge/dev-guide/dom/pointer-lock) comes to the rescue by letting us connect mouse movements to our camera.</span></span> <span data-ttu-id="2d47d-218">Die Pointer-Lock-API sorgt dafür, dass die Maus ausgeblendet wird, um ein intensiveres Erlebnis zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-218">The Pointer Lock API also makes the mouse disappear for a more immersive experience.</span></span> <span data-ttu-id="2d47d-219">Durch Drücken der ESC-Taste beenden wir die Maus-Kamera-Verbindung und sorgen dafür, dass die Maus wieder angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-219">By pressing ESC we end the mouse to camera connection and make the mouse reappear.</span></span> <span data-ttu-id="2d47d-220">Das Hinzufügen der `getPointerLock()`- und `lockChange()`-Funktionen hilft uns, genau das zu tun.</span><span class="sxs-lookup"><span data-stu-id="2d47d-220">Additions of the `getPointerLock()` and `lockChange()` functions will help us do just that.</span></span>

<span data-ttu-id="2d47d-221">Die `getPointerLock()`-Funktion wartet auf einen Mausklick.</span><span class="sxs-lookup"><span data-stu-id="2d47d-221">The `getPointerLock()` function listens for when a mouse click happens.</span></span> <span data-ttu-id="2d47d-222">Nach dem Klick versucht unser gerendertes Spiel (im `container`-Element), die Kontrolle über die Maus zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-222">After the click, our rendered game (in the `container` element) tries to get control of the mouse.</span></span> <span data-ttu-id="2d47d-223">Wir fügen auch einen Ereignislistener hinzu, um zu erkennen, wenn der Spieler die Sperre aktiviert oder deaktiviert, was wiederum `lockChange()` aufruft.</span><span class="sxs-lookup"><span data-stu-id="2d47d-223">We also add an event listener to detect when the player activates or deactivates the lock which then calls `lockChange()`.</span></span> 

```javascript
function getPointerLock() {
  document.onclick = function () {
    container.requestPointerLock();
  }
  document.addEventListener('pointerlockchange', lockChange, false); 
}

```

<span data-ttu-id="2d47d-224">Unsere `lockChange()`-Funktion muss die Steuerelemente und das `blocker`-Element deaktivieren oder aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2d47d-224">Our `lockChange()` function needs to either disable or enable the controls and `blocker` element.</span></span> <span data-ttu-id="2d47d-225">Wir können den Status der Zeiger-Sperre ermitteln, indem wir überprüfen, ob das Ziel der [`pointerLockElement`](https://developer.mozilla.org/docs/Web/API/Document/pointerLockElement)-Eigenschaft für Mausereignisse zu unserem `container` festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-225">We can determine the state of the pointer lock by checking if the [`pointerLockElement`](https://developer.mozilla.org/docs/Web/API/Document/pointerLockElement) property's target for mouse events is set to our `container`.</span></span>

```javascript
function lockChange() {
    // Turn on controls
    if (document.pointerLockElement === container) {
        // Hide blocker and instructions
        blocker.style.display = "none";
        controls.enabled = true;
    // Turn off the controls
    } else {
      // Display the blocker and instruction
        blocker.style.display = "";
        controls.enabled = false;
    }
}
```

<span data-ttu-id="2d47d-226">Jetzt können wir einen Aufruf zu `getPointerLock()` unmittelbar vor unserer `init()`-Funktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-226">Now we can add a call to `getPointerLock()` just before our `init()` function.</span></span>
```javascript
// Get the pointer lock state
getPointerLock();
init();
animate();
```

---

<span data-ttu-id="2d47d-227">Zu diesem Zeitpunkt haben wir nun die Möglichkeit, **uns umzusehen**, aber der echte „Wow“-Faktor ist die Möglichkeit, **sich zu bewegen**.</span><span class="sxs-lookup"><span data-stu-id="2d47d-227">At this point we now have the ability to **look** around, but the real 'wow' factor is being able to **move** around.</span></span> <span data-ttu-id="2d47d-228">Nun geht es mit Vektoren etwas mathematischer zu, aber was wären 3D-Grafiken ohne etwas Mathematik?</span><span class="sxs-lookup"><span data-stu-id="2d47d-228">Things are about to get a little mathematical with vectors, but what's 3D graphics without a bit of math?</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-229">Umsehen</span><span class="sxs-lookup"><span data-stu-id="2d47d-229">Look around</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/gmwbMo/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-230">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/gmwbMo/'>Sich umsehen</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-230">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/gmwbMo/'>Look around</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


### <a name="5-adding-player-movement"></a><span data-ttu-id="2d47d-231">5. Hinzufügen der Spielerbewegung</span><span class="sxs-lookup"><span data-stu-id="2d47d-231">5. Adding player movement</span></span>

<span data-ttu-id="2d47d-232">Damit sich unser Spieler bewegen kann, müssen wir an unsere Berechnungen zurückdenken.</span><span class="sxs-lookup"><span data-stu-id="2d47d-232">To dig into how to get our player moving, we've got to think back to our calculus days.</span></span> <span data-ttu-id="2d47d-233">Wir möchten Geschwindigkeit (Bewegung) auf die `camera` entlang eines bestimmten Vektors (Richtung) anwenden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-233">We want to apply velocity (movement) to the `camera` along a certain vector (direction).</span></span>

<span data-ttu-id="2d47d-234">Jetzt fügen wir einige globale Variablen zum Nachverfolgen der Richtung hinzu, in die sich der Spieler bewegt, und legen einen anfänglichen Geschwindigkeitsvektor fest:</span><span class="sxs-lookup"><span data-stu-id="2d47d-234">Let's add a few more global variables to keep track of which direction the player is moving, and set an initial velocity vector:</span></span>

```javascript
// Flags to determine which direction the player is moving
var moveForward = false;
var moveBackward = false;
var moveLeft = false;
var moveRight = false;

// Velocity vector for the player
var playerVelocity = new THREE.Vector3();

// How fast the player will move
var PLAYERSPEED = 800.0;

var clock;
```

<span data-ttu-id="2d47d-235">Legen Sie zu Beginn der `init()`-Funktion für `clock` ein neues `Clock`-Objekt fest.</span><span class="sxs-lookup"><span data-stu-id="2d47d-235">In the beginning of the `init()` function, set `clock` to a new `Clock` object.</span></span> <span data-ttu-id="2d47d-236">Wir verwenden dies, um die Zeitdifferenz (Delta) nachzuverfolgen, die benötigt wird, um neue Frames zu rendern.</span><span class="sxs-lookup"><span data-stu-id="2d47d-236">We'll be using this to keep track of the change in time (delta) it takes to render new frames.</span></span> <span data-ttu-id="2d47d-237">Sie müssen auch einen Aufruf zu `listenForPlayerMovement()` hinzufügen, was die Benutzereingaben erfasst.</span><span class="sxs-lookup"><span data-stu-id="2d47d-237">You'll also need to add a call to `listenForPlayerMovement()`, which gathers user input.</span></span> 

```
clock = new THREE.Clock();
listenForPlayerMovement();
```

<span data-ttu-id="2d47d-238">Unsere `listenForPlayerMovement()`-Funktion ist das, was unsere Richtungszustände ändern wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-238">Our `listenForPlayerMovement()` function is what will be flipping our direction states.</span></span> <span data-ttu-id="2d47d-239">Am Ende der Funktion haben wir zwei Ereignislistener, die darauf warten, dass Tasten gedrückt und losgelassen werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-239">At the bottom of the function we have two event listeners that are waiting for keys to be pressed and released.</span></span> <span data-ttu-id="2d47d-240">Nachdem eines dieser Ereignisse ausgelöst wurde, werden wir anschließend überprüfen, ob es sich um eine Taste handelt, mit der wir eine Bewegung beenden oder auslösen möchten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-240">Once one of these events are fired, we'll then check to see if it's a key that we want to trigger or stop movement.</span></span>

<span data-ttu-id="2d47d-241">Für dieses Spiel haben wir festgelegt, dass sich der Spieler mit den Tasten W, A, S und D oder den Pfeiltasten bewegen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-241">For this game, we've set it up so that the player can move around with the W, A, S, D keys or the arrow keys.</span></span>

```javascript
function listenForPlayerMovement() {
    
    // A key has been pressed
    var onKeyDown = function(event) {

    switch (event.keyCode) {

      case 38: // up
      case 87: // w
        moveForward = true;
        break;

      case 37: // left
      case 65: // a
        moveLeft = true;
        break;

      case 40: // down
      case 83: // s
        moveBackward = true;
        break;

      case 39: // right
      case 68: // d
        moveRight = true;
        break;
    }
  };

  // A key has been released
    var onKeyUp = function(event) {

    switch (event.keyCode) {

      case 38: // up
      case 87: // w
        moveForward = false;
        break;

      case 37: // left
      case 65: // a
        moveLeft = false;
        break;

      case 40: // down
      case 83: // s
        moveBackward = false;
        break;

      case 39: // right
      case 68: // d
        moveRight = false;
        break;
    }
  };

  // Add event listeners for when movement keys are pressed and released
  document.addEventListener('keydown', onKeyDown, false);
  document.addEventListener('keyup', onKeyUp, false);
}
```

<span data-ttu-id="2d47d-242">Da wir nun bestimmen können, welche Richtung der Benutzer einschlagen möchte (das wird jetzt als `true` in einem der globalen Richtungsflags gespeichert), ist es Zeit für eine Aktion.</span><span class="sxs-lookup"><span data-stu-id="2d47d-242">Now that we're able to determine which direction the user wants to go (which is now stored as `true` in one of the global direction flags), it's time for some action.</span></span> <span data-ttu-id="2d47d-243">Diese Aktion wird in Form der `animatePlayer()`-Funktion ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-243">This action happens to come in the form of the `animatePlayer()` function.</span></span>

<span data-ttu-id="2d47d-244">Diese Funktion wird innerhalb von `animate()` aufgerufen und an `delta` übergeben, um die Zeitdifferenz zwischen Frames zu ändern, damit die Bewegung bei Änderungen der Framerate nicht asynchron erscheint:</span><span class="sxs-lookup"><span data-stu-id="2d47d-244">This function will be called from within `animate()`, passing in `delta` to get the change in time between frames so that our movement doesn't seem out of sync during changes in framerate:</span></span>

```javascript
function animate() {
  render();
  requestAnimationFrame(animate);
  // Get the change in time between frames
  var delta = clock.getDelta();
  animatePlayer(delta);
}
```

<span data-ttu-id="2d47d-245">Jetzt ist es Zeit für den unterhaltsamen Teil!</span><span class="sxs-lookup"><span data-stu-id="2d47d-245">Now it's time for the fun part!</span></span> <span data-ttu-id="2d47d-246">Unser Bewegungsvektor (`playerVeloctiy`) verfügt über drei Parameter `(x, y, z)`, wobei `y` die vertikale Bewegung ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-246">Our momentum vector (`playerVeloctiy`) has three parameters, `(x, y, z)`, with `y` being the vertical momentum.</span></span> <span data-ttu-id="2d47d-247">Da wir in diesem Spiel nicht springen, arbeiten wir nur mit den Parametern `x` und `z`.</span><span class="sxs-lookup"><span data-stu-id="2d47d-247">Since we aren't doing any jumping in this game, we'll only be working with the `x` and `z` parameters.</span></span> <span data-ttu-id="2d47d-248">Dieser Vektor ist anfänglich auf (0, 0, 0) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-248">Initially this vector is set to (0, 0, 0).</span></span>

<span data-ttu-id="2d47d-249">Wie im folgenden Code dargestellt, erfolgen einige Checks, um zu sehen, welche Richtungsflags auf `true` gedreht sind.</span><span class="sxs-lookup"><span data-stu-id="2d47d-249">As seen in the code below, a series of checks are done to see which direction flag is flipped to `true`.</span></span> <span data-ttu-id="2d47d-250">Wenn wir die Richtung haben, addieren wir zu `x` und `y` oder subtrahieren davon, um Bewegung in die entsprechende Richtung anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-250">Once we have the direction, we add or subtract from `x` and `y` to apply momentum in that direction.</span></span> <span data-ttu-id="2d47d-251">Wenn keine Bewegungstasten gedrückt werden, wird der Vektor zurück zu `(0, 0, 0)` gesetzt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-251">If no movement keys are being pressed, the vector will be set back to `(0, 0, 0)`.</span></span>


```javascript

function animatePlayer(delta) {
  // Gradual slowdown
  playerVelocity.x -= playerVelocity.x * 10.0 * delta;
  playerVelocity.z -= playerVelocity.z * 10.0 * delta;

  if (moveForward) {
    playerVelocity.z -= PLAYERSPEED * delta;
  } 
  if (moveBackward) {
    playerVelocity.z += PLAYERSPEED * delta;
  } 
  if (moveLeft) {
    playerVelocity.x -= PLAYERSPEED * delta;
  } 
  if (moveRight) {
    playerVelocity.x += PLAYERSPEED * delta;
  }
  if( !( moveForward || moveBackward || moveLeft ||moveRight)) {
    // No movement key being pressed. Stop movememnt
    playerVelocity.x = 0;
    playerVelocity.z = 0;
  }
  controls.getObject().translateX(playerVelocity.x * delta);
  controls.getObject().translateZ(playerVelocity.z * delta);
}
```

<span data-ttu-id="2d47d-252">Am Ende werden die aktualisierten `x`- und `y`-Werte als Übersetzungen auf die Kamera angewendet, damit sich der Spieler tatsächlich bewegen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-252">In the end, we apply the whatever the updated `x` and `y` values are to the camera as translations to make the player actually move.</span></span>

---

<span data-ttu-id="2d47d-253">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="2d47d-253">Congratulations!</span></span> <span data-ttu-id="2d47d-254">Sie haben nun eine vom Spieler gesteuerte bewegbare Kamera, mit der sich der Spieler umsehen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-254">You now have a player controlled camera that can move and look around.</span></span> <span data-ttu-id="2d47d-255">Wir können immer noch direkt durch die Wände laufen, darum kümmern wir uns jedoch etwas später.</span><span class="sxs-lookup"><span data-stu-id="2d47d-255">We still slip right through walls, but that's something to worry about later.</span></span> <span data-ttu-id="2d47d-256">Als Nächstes fügen wir unseren Dinosaurier hinzu.</span><span class="sxs-lookup"><span data-stu-id="2d47d-256">Next we'll add our dinosaur.</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-257">Bewegen</span><span class="sxs-lookup"><span data-stu-id="2d47d-257">Move around</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/qrbKZg/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-258">Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/qrbKZg/'>bewegen</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-258">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/qrbKZg/'>Move around</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

> [!NOTE]
> <span data-ttu-id="2d47d-259">Wenn Sie diese Steuerelemente in Ihrer UWP-App verwenden, bemerken Sie möglicherweise verzögerte Bewegungen und nicht registrierte `keyUp`-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="2d47d-259">If you use these controls in your UWP app you may experience movement lag and unregistered `keyUp` events.</span></span> <span data-ttu-id="2d47d-260">Wir untersuchen dies gerade und hoffen, diesen Teil des Beispiels bald beheben zu können!</span><span class="sxs-lookup"><span data-stu-id="2d47d-260">We're looking into this and hope to fix this portion of the sample soon!</span></span>

### <a name="6-load-that-dino"></a><span data-ttu-id="2d47d-261">6. Laden des Dinosauriers</span><span class="sxs-lookup"><span data-stu-id="2d47d-261">6. Load that dino!</span></span>

<span data-ttu-id="2d47d-262">Wenn Sie das Repository dieses Projekts geklont oder heruntergeladen haben, sehen Sie einen `models`-Ordner, der `dino.json` enthält.</span><span class="sxs-lookup"><span data-stu-id="2d47d-262">If you cloned or downloaded this projects repo, you'll see a `models` folder with `dino.json` inside.</span></span> <span data-ttu-id="2d47d-263">Diese JSON-Datei ist ein 3D-Dinosaurier-Modell, das von Blender erstellt und exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="2d47d-263">This JSON file is a 3D dinosaur model that was made and exported from Blender.</span></span>


<span data-ttu-id="2d47d-264">Wir müssen weitere globale Variablen hinzufügen, damit dieser Dino verwendet werden kann:</span><span class="sxs-lookup"><span data-stu-id="2d47d-264">We'll have to add more global variables to get this dino loaded up:</span></span>

```javascript
var DINOSCALE = 20;  // How big our dino is scaled to

var clock;
var dino;
var loader = new THREE.JSONLoader();

var instructions = document.getElementById('instructions');
```

<span data-ttu-id="2d47d-265">Nachdem wir unseren `JSONLoader` erstellt haben, geben wir den Pfad an unsere **dino.json**-Datei weiter, sowie einen Rückruf mit der Geometrie und dem Material, das aus der Datei abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="2d47d-265">Now that we have our `JSONLoader` created, we'll pass in the path to our **dino.json** and a callback with the geometry and materials gathered from the file.</span></span>
<span data-ttu-id="2d47d-266">Das Laden des Dinos ist eine asynchrone Aufgabe, was bedeutet, dass nichts gerendert wird, bis der Dino vollständig geladen ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-266">Loading the dino is an asynchronous task, meaning nothing will render until the dino is completely loaded.</span></span> <span data-ttu-id="2d47d-267">In unserer Datei **index.html** haben wir die Zeichenfolge im `instructions`-Element in `"Loading..."` geändert, damit der Spieler weiß, dass etwas ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-267">In our **index.html** we changed the string in the `instructions` element to `"Loading..."` to let the player know things are in progress.</span></span>

<span data-ttu-id="2d47d-268">Aktualisieren Sie nach dem Laden des Dinos das `instructions`-Element mit den tatsächlichen Spielanweisungen, und verschieben Sie die `animate()`-Funktion vom Ende von `init()` an das Ende des Funktionsrückrufs (unten angezeigt):</span><span class="sxs-lookup"><span data-stu-id="2d47d-268">After the dino is loaded, update the `instructions` element with the actual instructions of the game, and move the `animate()` function from the end of `init()` to the end of the function callback seen below:</span></span>

```javascript
   // load the dino JSON model and start animating once complete
    loader.load('./models/dino.json', function (geometry, materials) {


        // Get the geometry and materials from the JSON
        var dinoObject = new THREE.Mesh(geometry, new THREE.MultiMaterial(materials));

        // Scale the size of the dino
        dinoObject.scale.set(DINOSCALE, DINOSCALE, DINOSCALE);
        dinoObject.rotation.y = degreesToRadians(-90);
        dinoObject.position.set(30, 0, -400);
        dinoObject.name = "dino";
        scene.add(dinoObject);
        
        // Store the dino
        dino = scene.getObjectByName("dino"); 

        // Model is loaded, switch from "Loading..." to instruction text
        instructions.innerHTML = "<strong>Click to Play!</strong> </br></br> W,A,S,D or arrow keys = move </br>Mouse = look around";

        // Call the animate function so that animation begins after the model is loaded
        animate();
    });
```

---

<span data-ttu-id="2d47d-269">Wir haben nun unser Dinomodell geladen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-269">We now have our dino model loaded in.</span></span> <span data-ttu-id="2d47d-270">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="2d47d-270">Check it out!</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-271">Hinzufügen des Dinos</span><span class="sxs-lookup"><span data-stu-id="2d47d-271">Adding the dino</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/xqOwBw/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-272">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/xqOwBw/'>Hinzufügen des Dinos</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-272">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/xqOwBw/'>Adding the dino</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="7-move-that-dino"></a><span data-ttu-id="2d47d-273">7. Den Dino in Bewegung bringen!</span><span class="sxs-lookup"><span data-stu-id="2d47d-273">7. Move that dino!</span></span>

<span data-ttu-id="2d47d-274">Künstliche Intelligenz für ein Spiel zu erstellen, kann äußerst komplex werden, weshalb wir für dieses Beispiel ein einfaches Bewegungsverhalten für diesen Dino festlegen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-274">Creating AI for a game can get extremely complex, so for this example we'll make this dino have a simple movement behavior.</span></span> <span data-ttu-id="2d47d-275">Unser Dino wird geradeaus laufen, an Wänden entlang laufen und in der Ferne im Nebel verschwinden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-275">Our dino will move straight, slipping its way through walls and off into the distant fog.</span></span>

<span data-ttu-id="2d47d-276">Zu diesem Zweck fügen Sie zunächst die globale Variable `dinoVelocity` hinzu.</span><span class="sxs-lookup"><span data-stu-id="2d47d-276">To do this, first add the global variable `dinoVelocity`.</span></span>

```javascript
var DINOSPEED = 400.0;

var dinoVelocity = new THREE.Vector3();
```
 <span data-ttu-id="2d47d-277">Als Nächstes rufen Sie die `animateDino()`-Funktion aus der `animation()`-Funktion auf und fügen den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2d47d-277">Next, call the `animateDino()` function from the `animation()` function and add in the below code:</span></span>

```javascript
function animateDino(delta) {
    // Gradual slowdown
    dinoVelocity.x -= dinoVelocity.x * 10.0 * delta;
    dinoVelocity.z -= dinoVelocity.z * 10.0 * delta;

    dinoVelocity.z += DINOSPEED * delta;
    // Move the dino
    dino.translateZ(dinoVelocity.z * delta);
}
```
---

<span data-ttu-id="2d47d-278">Zu beobachten, wie der Dino verschwindet, ist nicht sehr unterhaltsam, aber wenn wir Kollisionserkennung hinzufügen, wird es interessanter.</span><span class="sxs-lookup"><span data-stu-id="2d47d-278">Watching the dino sail away isn't very fun, but once we add collision detection things will get more interesting.</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-279">Bewegen des Dinos – kein Kollision</span><span class="sxs-lookup"><span data-stu-id="2d47d-279">Moving the dino - no collision</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/jBMbbL/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-280">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/jBMbbL/'>Bewegen des Dinos – kein Kollision</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-280">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/jBMbbL/'>Moving the dino - no collision</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="8-collision-detection-for-the-player"></a><span data-ttu-id="2d47d-281">8. Kollisionserkennung für den Spieler</span><span class="sxs-lookup"><span data-stu-id="2d47d-281">8. Collision detection for the player</span></span>

<span data-ttu-id="2d47d-282">Jetzt können sich der Spieler und der Dino bewegen, jedoch gibt es immer noch das lästige Problem, dass jeder durch Wände gehen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-282">So we now have the player and the dino moving around, but there's still that annoying issue with everyone going through walls.</span></span> <span data-ttu-id="2d47d-283">Als wir unsere Würfel und Wände weiter oben in diesem Lernprogramm hinzugefügt haben, übertrugen wir sie in das `collidableObjects`-Array.</span><span class="sxs-lookup"><span data-stu-id="2d47d-283">When we first started adding our cubes and walls earlier in this tutorial, we pushed them into the `collidableObjects` array.</span></span> <span data-ttu-id="2d47d-284">Dieses Array verwenden wir, um festzustellen, ob ein Spieler zu nahe an etwas ist, wo er nicht durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-284">This array is what we'll be using to tell if a player is too close to something they can't walk through.</span></span>

<span data-ttu-id="2d47d-285">Wir werden Raycasters verwenden, um zu bestimmen, wann eine Überschneidung stattfinden wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-285">We'll be using raycasters to determine when an intersection is about to occur.</span></span> <span data-ttu-id="2d47d-286">Sie können sich einen Raycaster als Laserstrahl vorstellen, der aus der Kamera in eine angegebene Richtung geht und zurückmeldet, wenn er ein Objekt antrifft, und angibt, wie weit es entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-286">You could imagine a raycaster as a laser beam coming out of the camera at some specified direction, reporting back if it hit an object and exactly how far away it is.</span></span>

```javascript
var PLAYERCOLLISIONDISTANCE = 20;
```

<span data-ttu-id="2d47d-287">Wir erstellen eine neue Funktion namens `detectPlayerCollision()`, die `true` zurückgibt, wenn der Spieler zu nahe an einem kollisionsfähigen Objekt ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-287">We'll be making a new function called `detectPlayerCollision()` that will return `true` if the player is too close to a collidable object.</span></span>
<span data-ttu-id="2d47d-288">Für den Spieler werden wir ein Raycaster verwenden, das ändert, auf welche Richtung es zeigt, je nachdem, in welche Richtung der Spieler geht.</span><span class="sxs-lookup"><span data-stu-id="2d47d-288">For the player, we're going to apply one raycaster to it, changing which direction it's pointing depending on which direction they're going.</span></span>

<span data-ttu-id="2d47d-289">Zu diesem Zweck erstellen wir `rotationMatrix`, eine nicht definierte Matrix.</span><span class="sxs-lookup"><span data-stu-id="2d47d-289">To do this, we create `rotationMatrix`, an undefined matrix.</span></span> <span data-ttu-id="2d47d-290">Wenn wir überprüfen, in welche Richtung wir gehen, erhalten wir entweder eine definierte `rotationMatrix` oder eine nicht definierte, wenn Sie weitergehen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-290">As we check which direction we're going, we'll end up with either a defined `rotationMatrix`, or undefined if you're moving forward.</span></span>
<span data-ttu-id="2d47d-291">Wenn sie definiert ist, wird `rotationMatrix` auf die Richtung der Steuerelemente angewendet.</span><span class="sxs-lookup"><span data-stu-id="2d47d-291">If defined, the `rotationMatrix` will be applied to the direction of the controls.</span></span> 

<span data-ttu-id="2d47d-292">Dann wird ein Raycaster erstellt, das bei der Kamera beginnt und in die `cameraDirection`-Richtung reicht.</span><span class="sxs-lookup"><span data-stu-id="2d47d-292">A raycaster will then be created, starting from and camera and reaching out in the `cameraDirection` direction.</span></span>


```javascript
function detectPlayerCollision() {
    // The rotation matrix to apply to our direction vector
    // Undefined by default to indicate ray should coming from front
    var rotationMatrix;
    // Get direction of camera
    var cameraDirection = controls.getDirection(new THREE.Vector3(0, 0, 0)).clone();

    // Check which direction we're moving (not looking)
    // Flip matrix to that direction so that we can reposition the ray
    if (moveBackward) {
        rotationMatrix = new THREE.Matrix4();
        rotationMatrix.makeRotationY(degreesToRadians(180));
    }
    else if (moveLeft) {
        rotationMatrix = new THREE.Matrix4();
        rotationMatrix.makeRotationY(degreesToRadians(90));
    }
    else if (moveRight) {
        rotationMatrix = new THREE.Matrix4();
        rotationMatrix.makeRotationY(degreesToRadians(270));
    }

    // Player is not moving forward, apply rotation matrix needed
    if (rotationMatrix !== undefined) {
        cameraDirection.applyMatrix4(rotationMatrix);
    }

    // Apply ray to player camera
    var rayCaster = new THREE.Raycaster(controls.getObject().position, cameraDirection);

    // If our ray hit a collidable object, return true
    if (rayIntersect(rayCaster, PLAYERCOLLISIONDISTANCE)) {
        return true;
    } else {
        return false;
    }
}
```

<span data-ttu-id="2d47d-293">Unsere `detectPlayerCollision()`-Funktion basiert auf der `rayIntersect()`-Hilfsfunktion.</span><span class="sxs-lookup"><span data-stu-id="2d47d-293">Our `detectPlayerCollision()` function relies on the `rayIntersect()` helper function.</span></span>
<span data-ttu-id="2d47d-294">Diese nimmt einen Raycaster und einen Wert, der darstellt, wie nah wir zu einem Objekt im `collidableObjects`-Array gehen können, bevor eine Kollision auftritt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-294">This takes a raycaster and value representing how close we can get to an object in the `collidableObjects` array before determining a collision has occured.</span></span>

```javascript
function rayIntersect(ray, distance) {
    var intersects = ray.intersectObjects(collidableObjects);
    for (var i = 0; i < intersects.length; i++) {
        // Check if there's a collision
        if (intersects[i].distance < distance) {
            return true;
        }
    }
    return false;
}
```

<span data-ttu-id="2d47d-295">Nachdem wir nun ermitteln können, wann eine Kollision auftreten wird, können wir unsere `animatePlayer()`-Funktion optimieren:</span><span class="sxs-lookup"><span data-stu-id="2d47d-295">Now that we can determine when a collision is about to occur, we can spruce up our `animatePlayer()` function:</span></span>

```javascript
function animatePlayer(delta) {
    // Gradual slowdown
    playerVelocity.x -= playerVelocity.x * 10.0 * delta;
    playerVelocity.z -= playerVelocity.z * 10.0 * delta;

    // If no collision and a movement key is being pressed, apply movement velocity
    if (detectPlayerCollision() == false) {
        if (moveForward) {
            playerVelocity.z -= PLAYERSPEED * delta;
        }
        if (moveBackward) {
            playerVelocity.z += PLAYERSPEED * delta;
        } 
        if (moveLeft) {
            playerVelocity.x -= PLAYERSPEED * delta;
        }
        if (moveRight) {
            playerVelocity.x += PLAYERSPEED * delta;
        }

        controls.getObject().translateX(playerVelocity.x * delta);
        controls.getObject().translateZ(playerVelocity.z * delta);
    } else {
        // Collision or no movement key being pressed. Stop movememnt
        playerVelocity.x = 0;
        playerVelocity.z = 0;
    }
}
```

---

<span data-ttu-id="2d47d-296">Wir haben jetzt die Kollisionserkennung für den Spieler und versuchen jetzt, gegen einige Wänden zu rennen!</span><span class="sxs-lookup"><span data-stu-id="2d47d-296">We now have player collision detection, so go ahead and try to run into some walls!</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-297">Verschieben des Spielers – kein Kollision</span><span class="sxs-lookup"><span data-stu-id="2d47d-297">Moving the player - collision</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/qraOeO/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-298">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/qraOeO/'>Bewegen des Spielers – kein Kollision</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-298">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/qraOeO/'>Moving the player - collision</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


### <a name="9-collision-detection-and-animation-for-dino"></a><span data-ttu-id="2d47d-299">9. Kollisionserkennung und Animationen für den Dino</span><span class="sxs-lookup"><span data-stu-id="2d47d-299">9. Collision detection and animation for dino</span></span>

<span data-ttu-id="2d47d-300">Jetzt müssen wir verhindern, dass unser Dino durch Wände läuft, und stattdessen festlegen, dass er in eine zufällige Richtung wechselt, sobald er einem kollisionsfähigen Objekt zu nahe kommt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-300">It's time to stop our dino from moving through walls, and instead have it go a random direction once it's too close to a collidable object.</span></span>

<span data-ttu-id="2d47d-301">Lassen Sie uns zuerst herausfinden, wann unser Dino kollidiert.</span><span class="sxs-lookup"><span data-stu-id="2d47d-301">First let's figure out when our dino has a collision.</span></span> 

<span data-ttu-id="2d47d-302">Wir müssen eine andere globale Variable für die Kollisionserkennung festlegen:</span><span class="sxs-lookup"><span data-stu-id="2d47d-302">We'll need to set anothe global variable for the collision distance:</span></span>

```javascript
var DINOCOLLISIONDISTANCE = 55;     
```

<span data-ttu-id="2d47d-303">Nachdem wir angegeben haben, bei welchem Abstand unser Dino kollidieren soll, fügen wir eine ähnliche Funktion wie `detectPlayerCollision()` hinzu, aber etwas einfacher.</span><span class="sxs-lookup"><span data-stu-id="2d47d-303">Now that we've specifed at what distance we want our dino to collide at, let's add a function similar to `detectPlayerCollision()`, but a bit simpler.</span></span>
<span data-ttu-id="2d47d-304">Die `detectDinoCollision`-Funktion ist einfach, da wir immer ein Raycaster haben, das direkt aus der Vorderseite des Dinos kommt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-304">The `detectDinoCollision` function is simple in that we always have one raycaster coming straight out the front of the dino.</span></span> <span data-ttu-id="2d47d-305">Es ist keine Drehung erforderlich wie bei der Spielerkollision.</span><span class="sxs-lookup"><span data-stu-id="2d47d-305">No need to rotate it around like for the player collision.</span></span>

```javascript
function detectDinoCollision() {
    // Get the rotation matrix from dino
    var matrix = new THREE.Matrix4();
    matrix.extractRotation(dino.matrix);
    // Create direction vector
    var directionFront = new THREE.Vector3(0, 0, 1);

    // Get the vectors coming from the front of the dino
    directionFront.applyMatrix4(matrix);

    // Create raycaster
    var rayCasterF = new THREE.Raycaster(dino.position, directionFront);
    // If we have a front collision, we have to adjust our direction so return true
    if (rayIntersect(rayCasterF, DINOCOLLISIONDISTANCE))
        return true;
    else
        return false;
}
```

<span data-ttu-id="2d47d-306">Werfen wir einen Blick darauf, wie unsere endgültige `animateDino()`-Funktion aussehen wird, wenn sie Kollisionserkennung enthält:</span><span class="sxs-lookup"><span data-stu-id="2d47d-306">Let's take a peek at what our final `animateDino()` function will look like when hooked up with collision detection:</span></span>


```javascript
function animateDino(delta) {
    // Gradual slowdown
    dinoVelocity.x -= dinoVelocity.x * 10.0 * delta;
    dinoVelocity.z -= dinoVelocity.z * 10.0 * delta;


    // If no collision, apply movement velocity
    if (detectDinoCollision() == false) {
        dinoVelocity.z += DINOSPEED * delta;
        // Move the dino
        dino.translateZ(dinoVelocity.z * delta);

    } else {
        // Collision. Adjust direction
        var directionMultiples = [-1, 1, 2];
        var randomIndex = getRandomInt(0, 2);
        var randomDirection = degreesToRadians(90 * directionMultiples[randomIndex]);

        dinoVelocity.z += DINOSPEED * delta;
        dino.rotation.y += randomDirection;
    }
}
```

<span data-ttu-id="2d47d-307">Wir möchten, dass sich unser Dino um -90, 90 oder um 180Grad dreht.</span><span class="sxs-lookup"><span data-stu-id="2d47d-307">We always want our dino to turn either -90, 90, or 180 degrees.</span></span> <span data-ttu-id="2d47d-308">Dazu haben wir das `directionMultiples`-Array erstellt, das diese Zahlen erzeugt, wenn es mit 90 multipliziert wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-308">To make this straight forward, above we've made the `directionMultiples` array which will produce these numbers when multiplied by 90.</span></span>
<span data-ttu-id="2d47d-309">Für eine zufällige Auswahl der Drehungsgradzahl haben wir die `getRandomInt()`-Hilfsfunktion hinzugefügt, die einen Wert von 0, 1 oder 2 nimmt, welcher einen zufälligen Index des Arrays darstellt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-309">To make selecting the rotation degrees random, we've added the `getRandomInt()` helper function to grab a value of 0, 1, or 2, which will represent a random index of the array.</span></span>

```javascript
function getRandomInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min)) + min;
}
```

<span data-ttu-id="2d47d-310">Nachdem dieser Vorgang abgeschlossen ist, multiplizieren wir den zufälligen Index des Arrays mit 90, um die Gradanzahl (in Radianten konvertiert) der Drehung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-310">Once this is all done, we multiply the random index of the array by 90 to get the degree (converted to radians) of rotation.</span></span>
<span data-ttu-id="2d47d-311">Durch Hinzufügen dieses Werts zur `y`-Drehung des Dinos mit `dino.rotation.y += randomDirection;` macht der Dino jetzt bei Kollisionen zufällige Drehungen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-311">By adding this value to the dino's `y` rotation with `dino.rotation.y += randomDirection;`, the dino now makes random turns upon collision.</span></span>


---

<span data-ttu-id="2d47d-312">Wir haben es geschafft!</span><span class="sxs-lookup"><span data-stu-id="2d47d-312">We did it!</span></span> <span data-ttu-id="2d47d-313">Wir haben jetzt einen Dino mit künstlicher Intelligenz, der sich in unserem Labyrinth bewegen kann!</span><span class="sxs-lookup"><span data-stu-id="2d47d-313">We now have a dino with AI that can move around our maze!</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-314">Bewegen des Dinos – Kollisionen</span><span class="sxs-lookup"><span data-stu-id="2d47d-314">Moving the dino - collision</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/bqwMXZ/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-315">Finden Sie unter den Stift <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/bqwMXZ/'>Bewegen des Dinos – Kollisionen</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-315">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/bqwMXZ/'>Moving the dino - collision</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="10-starting-the-chase"></a><span data-ttu-id="2d47d-316">10. Starten der Jagd</span><span class="sxs-lookup"><span data-stu-id="2d47d-316">10. Starting the chase</span></span>

<span data-ttu-id="2d47d-317">Sobald der Dino innerhalb einer bestimmten Entfernung zum Spieler ist, möchten wir ihm nachjagen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-317">Once the dino is within a certain distance to the player, we want it to start chasing them.</span></span> <span data-ttu-id="2d47d-318">Da dies nur ein Beispiel ist, gibt es keine erweiterten Algorithmen für den Dino, der vom Spieler verfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="2d47d-318">Since this is just an example, there aren't any advanced algorithms applied for the dino to track the player down.</span></span> <span data-ttu-id="2d47d-319">Stattdessen wird der Dino den Spieler ansehen und zu ihm laufen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-319">Instead, the dino will look at the player and walk towards them.</span></span> <span data-ttu-id="2d47d-320">In einem offenen Teil des Labyrinths funktioniert dies gut, aber der Dino bleibt stecken, wenn eine Wand im Weg ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-320">In an open part of the maze this works great, but the dino does get stuck when a wall is in the way.</span></span>

<span data-ttu-id="2d47d-321">In unserer `animate()`-Funktion fügen wir eine boolesche Variable hinzu, die durch das festgelegt ist, was von `triggerChase()` zurückgegeben wird:</span><span class="sxs-lookup"><span data-stu-id="2d47d-321">In our `animate()` function we'll add a boolean variable that is determined by what is returned by `triggerChase()`:</span></span>

```javascript
function animate() {
    render();
    requestAnimationFrame(animate);

    // Get the change in time between frames
    var delta = clock.getDelta();

    // If the player is in dino's range, trigger the chase
    var isBeingChased = triggerChase();

    animateDino(delta);
    animatePlayer(delta);
}
```

<span data-ttu-id="2d47d-322">Unsere `triggerChase`-Funktion überprüft, ob der Spieler im Jagdbereich des Dinos ist, und sorgt dann dafür, dass der Dino immer den Spieler ansieht, wodurch er in Richtung des Spielers gehen kann.</span><span class="sxs-lookup"><span data-stu-id="2d47d-322">Our `triggerChase` function will check to see if the player is in chasing range of the dino, and then make the dino always face the player, which allows it to move in the player's direction.</span></span> 

```javascript
function triggerChase() {
    // Check if in dino detection range of the player
    if (dino.position.distanceTo(controls.getObject().position) < 300) {
        // Set the dino target's y value to the current y value. We only care about x and z for movement.
        var lookTarget = new THREE.Vector3();
        lookTarget.copy(controls.getObject().position);
        lookTarget.y = dino.position.y;

        // Make dino face camera
        dino.lookAt(lookTarget);

        // Get distance between dino and camera with a unit offset
        // Game over when dino is the value of CATCHOFFSET units away from camera
        var distanceFrom = Math.round(dino.position.distanceTo(controls.getObject().position)) - CATCHOFFSET;
        // Alert and display distance between camera and dino
        dinoAlert.innerHTML = "Dino has spotted you! Distance from you: " + distanceFrom;
        dinoAlert.style.display = '';
        return true;
        // Not in agro range, don't start distance countdown
    } else {
        dinoAlert.style.display = 'none';
        return false;
    }
}
```

<span data-ttu-id="2d47d-323">In der zweiten Hälfte von `triggerChase` geht es um das Anzeigen von Text, der dem Spieler mitteilt, wie weit der Dino entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-323">The second half of `triggerChase` deals with displaying some text that lets the player know how far away the dino is.</span></span> <span data-ttu-id="2d47d-324">Wir sehen uns auch `CATCHOFFSET` an, womit wir angeben, wie weit `0` entfernt sein sollte.</span><span class="sxs-lookup"><span data-stu-id="2d47d-324">We also introduce `CATCHOFFSET` to specify how far away `0` should be.</span></span> <span data-ttu-id="2d47d-325">Wenn wir keinen Ausgleich hätten, wäre `0` direkt über dem Spieler, was nicht sehr passend für das Ende wäre.</span><span class="sxs-lookup"><span data-stu-id="2d47d-325">If we didn't have the offset, `0` would be right on top of the player which doesn't make for a very cinematic end to all this.</span></span>



```javascript
var dinoAlert = document.getElementById('dino-alert');
dinoAlert.style.display = 'none';
```

---

<span data-ttu-id="2d47d-326">An dieser Stelle haben wir einen wilden Dinosaurier, der beginnt, den Spieler zu verfolgen, sobald dieser ihm zu nahe kommt, und nicht anhält, bis sich seine Position über dem Spieler befindet.</span><span class="sxs-lookup"><span data-stu-id="2d47d-326">At this point we have a wild dinosaur that starts following the player once you get too close, and doesn't stop until it's position is on top of the player.</span></span>
<span data-ttu-id="2d47d-327">Der letzte Schrittist es, einige Bedingungen für das Spielende hinzuzufügen, sobald der Dino `CATCHOFFSET` Einheiten entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-327">The final step is to add some game over conditions once the dino is `CATCHOFFSET` units away.</span></span>

<iframe height='300' scrolling='no' title='<span data-ttu-id="2d47d-328">Der Jagd</span><span class="sxs-lookup"><span data-stu-id="2d47d-328">The chase</span></span>' src='//codepen.io/MicrosoftEdgeDocumentation/embed/preview/NpRBqR/?height=300&theme-id=23761&default-tab=result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="2d47d-329">Weitere Informationen finden Sie im Pen zu <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/NpRBqR/'>Die Jagd</a> von Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) auf <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="2d47d-329">See the Pen <a href='https://codepen.io/MicrosoftEdgeDocumentation/pen/NpRBqR/'>The chase</a> by Microsoft Edge Docs (<a href='https://codepen.io/MicrosoftEdgeDocumentation'>@MicrosoftEdgeDocumentation</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>


### <a name="11-ending-the-game"></a><span data-ttu-id="2d47d-330">11. Spielende</span><span class="sxs-lookup"><span data-stu-id="2d47d-330">11. Ending the game</span></span>


<span data-ttu-id="2d47d-331">Wir haben einen langen Weg von einem einfachen Würfel aus bestritten, und jetzt ist es Zeit, zum Ende zu kommen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-331">We've come a long away from a simple cube, and now it's time to end things.</span></span>

<span data-ttu-id="2d47d-332">Zuerst legen wir eine Variable fest, um nachzuverfolgen, ob das Spiel vorbei ist oder nicht:</span><span class="sxs-lookup"><span data-stu-id="2d47d-332">Let's first set a variable to keep track of whether the game is over or not:</span></span>

```javascript
var gameOver = false;
```

<span data-ttu-id="2d47d-333">Jetzt müssen wir unsere `animate()`-Funktion ein letztes Mal aktualisieren, um zu überprüfen, ob der Dino zu nahe am Spieler ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-333">Now we need to update our `animate()` function one last time to check if the dino is too close to the player.</span></span>
<span data-ttu-id="2d47d-334">Ist der Dino zu nah, beginnen wir eine neue Funktion namens `caught()` und beenden die Bewegung des Spielers und Dinos, falls nicht, geht es wie gewohnt weiter, und Spieler und Dino bewegen sich weiter.</span><span class="sxs-lookup"><span data-stu-id="2d47d-334">If the dino is too close, we'll start a new function called `caught()` and will stop the player and dino from moving, if not, we'll carry on with business as usual and let the player and dino move around.</span></span>

```javascript
function animate() {
    render();
    requestAnimationFrame(animate);

    // Get the change in time between frames
    var delta = clock.getDelta();
    // Update our frames per second monitor

    // If the player is in dino's range, trigger the chase
    var isBeingChased = triggerChase();
    // If the player is too close, trigger the end of the game
    if (dino.position.distanceTo(controls.getObject().position) < CATCHOFFSET) {
        caught();
    // Player is at an undetected distance
    // Keep the dino moving and let the player keep moving too
    } else {
        animateDino(delta);
        animatePlayer(delta);
    }
}
```

<span data-ttu-id="2d47d-335">Wenn der Dino den Spieler fängt, zeigt `caught()` unser `blocker`-Element an und aktualisiert den Text, um anzugeben, dass das Spiel verloren wurde.</span><span class="sxs-lookup"><span data-stu-id="2d47d-335">If the dino catches the player, `caught()` will display our `blocker` element and update the text to indicate that the game has been lost.</span></span>
<span data-ttu-id="2d47d-336">Die `gameOver`-Variable ist ebenfalls auf `true` festgelegt, wodurch wir erfahren, dass das Spiel vorbei ist.</span><span class="sxs-lookup"><span data-stu-id="2d47d-336">The `gameOver` variable is also set to `true`, which now lets us know the game is over.</span></span>  


```javascript
function caught() {
    blocker.style.display = '';
    instructions.innerHTML = "GAME OVER </br></br></br> Press ESC to restart";
    gameOver = true;
    instructions.style.display = '';
    dinoAlert.style.display = 'none';
}
```


<span data-ttu-id="2d47d-337">Da wir nun wissen, ob das Spiel vorbei ist oder nicht, können wir eine diesbezügliche Überprüfung zu unserer `lockChange()`-Funktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-337">Now that we know whether the game is over or not, we can add a check for game over to our `lockChange()` function.</span></span>
<span data-ttu-id="2d47d-338">Wenn der Benutzer ESC drückt, nachdem das Spiel vorbei ist, können wir `location.reload` hinzufügen, um das Spiel erneut zu starten.</span><span class="sxs-lookup"><span data-stu-id="2d47d-338">Now when the user presses ESC once the game is over, we can add `location.reload` to restart the game.</span></span>

```javascript
function lockChange() {
    if (document.pointerLockElement === container) {
        blocker.style.display = "none";
        controls.enabled = true;
    } else {
        if (gameOver) {
            location.reload();
        }
        blocker.style.display = "";
        controls.enabled = false;
    }
}
```

---

<span data-ttu-id="2d47d-339">Das war's.</span><span class="sxs-lookup"><span data-stu-id="2d47d-339">That's it!</span></span> <span data-ttu-id="2d47d-340">Es war ein langer Weg, aber nun haben wir ein Spiel mit **three.js** erstellt.</span><span class="sxs-lookup"><span data-stu-id="2d47d-340">It was quite the journey, but we now have a game made with **three.js**.</span></span>

<span data-ttu-id="2d47d-341">Gehen Sie zurück an den Anfang der Seite, wo Sie den [finalen CodePen](#introduction) finden!</span><span class="sxs-lookup"><span data-stu-id="2d47d-341">Head back up to the top of the page to see the [final CodePen](#introduction)!</span></span>


## <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="2d47d-342">Veröffentlichung im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2d47d-342">Publishing to the Microsoft Store</span></span>
<span data-ttu-id="2d47d-343">Nachdem Sie nun eine UWP-app haben, ist es möglich, veröffentlichen, an den Microsoft Store (vorausgesetzt, dass Sie diese zunächst verbessert haben!) Es gibt einige Schritte durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="2d47d-343">Now you have a UWP app, it is possible to publish it to the Microsoft Store (assuming you have improved it first!) There are a few steps to the process.</span></span>

1.  <span data-ttu-id="2d47d-344">Sie müssen als Windows-Entwickler [registriert](https://developer.microsoft.com/store/register) sein.</span><span class="sxs-lookup"><span data-stu-id="2d47d-344">You must be [registered](https://developer.microsoft.com/store/register) as a Windows Developer.</span></span>
2.  <span data-ttu-id="2d47d-345">Verwenden Sie die [Prüfliste für App-Übermittlung](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span><span class="sxs-lookup"><span data-stu-id="2d47d-345">You must use the app submission [checklist](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span></span>
3.  <span data-ttu-id="2d47d-346">Die App muss zur [Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process) eingereicht werden.</span><span class="sxs-lookup"><span data-stu-id="2d47d-346">The app must be submitted for [certification](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process).</span></span>
<span data-ttu-id="2d47d-347">Weitere Informationen finden Sie unter [Veröffentlichen Ihrer UWP-app](https://developer.microsoft.com/store/publish-apps).</span><span class="sxs-lookup"><span data-stu-id="2d47d-347">For more details, see [Publishing your UWP app](https://developer.microsoft.com/store/publish-apps).</span></span>

