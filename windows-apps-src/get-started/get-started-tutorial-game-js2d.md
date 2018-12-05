---
title: Erstellen eines UWP-Spiels in JavaScript
description: Ein einfaches UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und CreateJS
ms.date: 02/09/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 01af8254-b073-445e-af4c-e474528f8aa3
ms.localizationpriority: medium
ms.openlocfilehash: ae8daa6141eadaac699fc49b8ec4796f1dde5c91
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8732809"
---
# <a name="create-a-uwp-game-in-javascript"></a><span data-ttu-id="053bd-104">Erstellen eines UWP-Spiels in JavaScript</span><span class="sxs-lookup"><span data-stu-id="053bd-104">Create a UWP game in JavaScript</span></span>

## <a name="a-simple-2d-uwp-game-for-the-microsoft-store-written-in-javascript-and-createjs"></a><span data-ttu-id="053bd-105">Ein einfaches 2D-UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und CreateJS</span><span class="sxs-lookup"><span data-stu-id="053bd-105">A simple 2D UWP game for the Microsoft Store, written in JavaScript and CreateJS</span></span>


![Sprite-Blatt für laufenden Dino](images/JS2D_1.png)


## <a name="introduction"></a><span data-ttu-id="053bd-107">Einführung</span><span class="sxs-lookup"><span data-stu-id="053bd-107">Introduction</span></span>


<span data-ttu-id="053bd-108">Veröffentlichen einer app auf der Microsoft Store bedeutet, dass Sie können freigeben (oder verkaufen!) mit Millionen von Menschen auf vielen verschiedenen Geräten.</span><span class="sxs-lookup"><span data-stu-id="053bd-108">Publishing an app to the Microsoft Store means you can share it (or sell it!) with millions of people, on many different devices.</span></span>  

<span data-ttu-id="053bd-109">Um Ihre app an den Microsoft Store veröffentlichen müssen sie als UWP (universelle Windows-Plattform)-app geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-109">In order to publish your app to the Microsoft Store it must be written as a UWP (Universal Windows Platform) app.</span></span> <span data-ttu-id="053bd-110">UWP ist jedoch extrem flexibel und unterstützt eine Vielzahl von Sprachen und Frameworks.</span><span class="sxs-lookup"><span data-stu-id="053bd-110">However the UWP is extremely flexible, and supports a wide variety of languages and frameworks.</span></span> <span data-ttu-id="053bd-111">Dieses Beispiel ist ein einfaches Spiel, das in JavaScript geschrieben ist und mehrere CreateJS-Bibliotheken nutzt. Es veranschaulicht, wie Sprites gezeichnet werden, eine Spielschleife erstellt wird, Tastatur und Maus unterstützt werden und die Anpassung an verschiedene Bildschirmgrößen erfolgt.</span><span class="sxs-lookup"><span data-stu-id="053bd-111">To prove the point, this sample is a simple game written in JavaScript, making use of several CreateJS libraries, and demonstrates how to draw sprites, create a game loop, support the keyboard and mouse, and adapt to different screen sizes.</span></span>

<span data-ttu-id="053bd-112">Dieses Projekt wurde mit JavaScript unter Verwendung von Visual Studio erstellt.</span><span class="sxs-lookup"><span data-stu-id="053bd-112">This project is built with JavaScript using Visual Studio.</span></span> <span data-ttu-id="053bd-113">Mit einigen geringfügigen Änderungen kann es auch auf einer Website gehostet oder an andere Plattformen angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-113">With some minor changes, it can also hosted on a website or adapted to other platforms.</span></span> 

<span data-ttu-id="053bd-114">**Hinweis:** Dies ist kein vollständiges (oder gutes!) Spiel; Dieses Skript dient zu zeigen, wie mit JavaScript und das dritte Partei Bibliothek stellen eine app im Microsoft Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="053bd-114">**Note:** This is a not a complete (or good!) game; it is designed to demonstrate using JavaScript and a third party library to make an app ready to publish to the Microsoft Store.</span></span>


## <a name="requirements"></a><span data-ttu-id="053bd-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="053bd-115">Requirements</span></span>

<span data-ttu-id="053bd-116">Um dieses Projekt auszuprobieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="053bd-116">To play with this project, you'll need the following:</span></span>

* <span data-ttu-id="053bd-117">Einen Windows-Computer (oder einen virtuellen Computer) mit der aktuellen Version von Windows10.</span><span class="sxs-lookup"><span data-stu-id="053bd-117">A Windows computer (or a virtual machine) running the current version of Windows 10.</span></span>
* <span data-ttu-id="053bd-118">Eine Kopie von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="053bd-118">A copy of Visual Studio.</span></span> <span data-ttu-id="053bd-119">Die kostenlose Visual Studio Community Edition kann von der [Visual Studio-Homepage](http://visualstudio.com) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-119">The free Visual Studio Community Edition can be downloaded from the [Visual Studio homepage](http://visualstudio.com).</span></span>

<span data-ttu-id="053bd-120">Dieses Projekt verwendet das CreateJS-JavaScript-Framework.</span><span class="sxs-lookup"><span data-stu-id="053bd-120">This project makes use of the CreateJS JavaScript framework.</span></span> <span data-ttu-id="053bd-121">Bei CreateJS handelt es sich um einen kostenlosen Satz von Tools mit MIT-Lizenz, welche die Erstellung Sprite-basierter Spiele erleichtern sollen.</span><span class="sxs-lookup"><span data-stu-id="053bd-121">CreateJS is a free set of tools, released under a MIT license, designed to make it easy to create sprite-based games.</span></span> <span data-ttu-id="053bd-122">Die CreateJS-Bibliotheken sind bereits im Projekt vorhanden (suchen Sie nach *js/easeljs-0.8.2.min.js* und *js/preloadjs-0.6.2.min.js* in der Projektmappen-Explorer-Ansicht).</span><span class="sxs-lookup"><span data-stu-id="053bd-122">The CreateJS libraries are already present in the project (look for *js/easeljs-0.8.2.min.js*, and *js/preloadjs-0.6.2.min.js* in the Solution Explorer view).</span></span> <span data-ttu-id="053bd-123">Weitere Informationen zu CreateJS finden Sie unter der [CreateJS-Startseite](http://www.createjs.com).</span><span class="sxs-lookup"><span data-stu-id="053bd-123">More information about CreateJS can be found at the [CreateJS home page](http://www.createjs.com).</span></span>


## <a name="getting-started"></a><span data-ttu-id="053bd-124">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="053bd-124">Getting started</span></span>

<span data-ttu-id="053bd-125">Der vollständige Quellcode für die App befindet sich in [GitHub](https://github.com/Microsoft/Windows-appsample-get-started-js2d).</span><span class="sxs-lookup"><span data-stu-id="053bd-125">The complete source code for the app is stored on [GitHub](https://github.com/Microsoft/Windows-appsample-get-started-js2d).</span></span>

<span data-ttu-id="053bd-126">Die einfachste Möglichkeit ist es, GitHub zu besuchen, auf die grüne Schaltfläche **Clone or download** zu klicken und **In Visual Studio öffnen** auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="053bd-126">The simplest way to get started it to visit GitHub, click on the green **Clone or download** button, and select **Open in Visual Studio**.</span></span> 

![Klonen des Repositorys](images/JS2D_2.png)

<span data-ttu-id="053bd-128">Sie können das Projekt auch als Zip-Datei herunterladen oder andere Standardverfahren zum Arbeiten mit [GitHub-Projekten](https://msdn.microsoft.com/en-us/windows/uwp/get-started/get-uwp-app-samples) nutzen.</span><span class="sxs-lookup"><span data-stu-id="053bd-128">You can also download the project as a zip file, or use any other standard ways to work with [GitHub projects](https://msdn.microsoft.com/en-us/windows/uwp/get-started/get-uwp-app-samples).</span></span>

<span data-ttu-id="053bd-129">Nachdem die Projektmappe in Visual Studio geladen wurde, sehen Sie mehrere Dateien, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="053bd-129">Once the solution has been loaded into Visual Studio, you'll see several files, including:</span></span>

* <span data-ttu-id="053bd-130">Images/ – ein Ordner mit den verschiedenen Symbolen, die von UWP-Apps benötigt werden, sowie das SpriteSheet des Spiels und einige andere Bitmaps.</span><span class="sxs-lookup"><span data-stu-id="053bd-130">Images/ - a folder containing the various icons required by UWP apps, as well as the game's SpriteSheet and some other bitmaps.</span></span>
* <span data-ttu-id="053bd-131">js / – ein Ordner mit den JavaScript-Dateien.</span><span class="sxs-lookup"><span data-stu-id="053bd-131">js/ - a folder containing the JavaScript files.</span></span> <span data-ttu-id="053bd-132">Die main.js-Datei ist unser Spiel, die anderen Dateien sind EaselJS und PreloadJS.</span><span class="sxs-lookup"><span data-stu-id="053bd-132">The main.js file is our game, the other files are EaselJS and PreloadJS.</span></span>
* <span data-ttu-id="053bd-133">index.html – die Webseite, die das Canvas-Objekt enthält, welches die Grafiken des Spiels hostet.</span><span class="sxs-lookup"><span data-stu-id="053bd-133">index.html - the webpage which contains the canvas object which hosts the game's graphics.</span></span>

<span data-ttu-id="053bd-134">Jetzt können Sie das Spiel ausführen!</span><span class="sxs-lookup"><span data-stu-id="053bd-134">Now you can run the game!</span></span>

<span data-ttu-id="053bd-135">Drücken Sie **F5** zum Ausführen der App.</span><span class="sxs-lookup"><span data-stu-id="053bd-135">Press **F5** to start the app running.</span></span> <span data-ttu-id="053bd-136">Ein Fenster geöffnet, und unseren vertrauten Dinosaurier in einer (idyllischen Wenn auch kargen) Landschaft sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-136">You should see a window open, and our familiar dinosaur standing in an idyllic (if sparse) landscape.</span></span> <span data-ttu-id="053bd-137">Wir werden jetzt die App untersuchen, einige wichtige Teile erklären und währenddessen den Rest der Features entsperren.</span><span class="sxs-lookup"><span data-stu-id="053bd-137">We will now examine the app, explain some important parts, and unlock the rest of the features as we go.</span></span>

![Ein ganz normaler Dinosaurier mit einer Ninja-Katze auf seinem Rücken](images/JS2D_3.png)

<span data-ttu-id="053bd-139">**Hinweis:** Hat etwas nicht geklappt?</span><span class="sxs-lookup"><span data-stu-id="053bd-139">**Note:** Something go wrong?</span></span> <span data-ttu-id="053bd-140">Stellen Sie sicher, dass Sie Visual Studio mit Web-Unterstützung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="053bd-140">Be sure you have installed Visual Studio with web support.</span></span> <span data-ttu-id="053bd-141">Sie können dies überprüfen, indem Sie ein neues Projekt erstellen. Wenn es keine Unterstützung für JavaScript gibt, müssen Sie Visual Studio neu installieren und das Feld *Microsoft Web Developer Tools* aktivieren.</span><span class="sxs-lookup"><span data-stu-id="053bd-141">You can check by creating a new project - if there is no support for JavaScript, you will need to re-install Visual Studio and check the *Microsoft Web Developer Tools* box.</span></span>

## <a name="walkthough"></a><span data-ttu-id="053bd-142">Exemplarische Vorgehensweise</span><span class="sxs-lookup"><span data-stu-id="053bd-142">Walkthough</span></span>

<span data-ttu-id="053bd-143">Wenn Sie das Spiel mit F5 gestartet haben, wundern Sie sich vielleicht, was gerade passiert.</span><span class="sxs-lookup"><span data-stu-id="053bd-143">If you started the game with F5, you're probably wondering what is going on.</span></span> <span data-ttu-id="053bd-144">Und die Antwort lautet "nicht viel", da ein Großteil des Codes derzeit auskommentiert ist. Bisher alles, was Sie sehen, ist der Dinosaurier und unwirksame darauf, die LEERTASTE zu drücken.</span><span class="sxs-lookup"><span data-stu-id="053bd-144">And the answer is "not a lot", as a lot of the code is currently commented-out. So far, all you'll see is the dinosaur, and a ineffectual plea to press Space.</span></span> 

### <a name="1-setting-the-stage"></a><span data-ttu-id="053bd-145">1. Festlegen der Phase</span><span class="sxs-lookup"><span data-stu-id="053bd-145">1. Setting the Stage</span></span>

<span data-ttu-id="053bd-146">Wenn Sie **index.html** öffnen und untersuchen, sehen Sie, dass die Datei fast leer ist.</span><span class="sxs-lookup"><span data-stu-id="053bd-146">If you open and examine **index.html**, you'll see it's almost empty.</span></span> <span data-ttu-id="053bd-147">Diese Datei ist die Standardwebseite, die unsere App enthält, und erledigt nur zwei wichtige Dinge.</span><span class="sxs-lookup"><span data-stu-id="053bd-147">This file is the default web page that contains our app, and it does only two important things.</span></span> <span data-ttu-id="053bd-148">Sie enthält zuerst den JavaScript-Quellcode für die CreateJS-Bibliotheken **EaselJS** und **PreloadJS**, und zudem **main.js** (unsere eigene Quellcodedatei).</span><span class="sxs-lookup"><span data-stu-id="053bd-148">First, it includes the JavaScript source code for the **EaselJS** and **PreloadJS** CreateJS libraries, and also **main.js** (our own source code file).</span></span>
<span data-ttu-id="053bd-149">Zweitens definiert sie ein &lt;Canvas&gt;-Tag, in dem all unsere Grafiken angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-149">Second, it defines a &lt;canvas&gt; tag, which is where all our graphics are going to appear.</span></span> <span data-ttu-id="053bd-150">Ein &lt;Canvas&gt; ist eine Standardkomponente eines HTML5-Dokuments.</span><span class="sxs-lookup"><span data-stu-id="053bd-150">A &lt;canvas&gt; is a standard HTML5 document component.</span></span> <span data-ttu-id="053bd-151">Wir geben ihm einen Namen (gameCanvas), damit unser Code **main.js** darauf verweisen kann.</span><span class="sxs-lookup"><span data-stu-id="053bd-151">We give it a name (gameCanvas) so our code in **main.js** can reference it.</span></span> <span data-ttu-id="053bd-152">Wenn Sie Ihr eigenes JavaScript-Spiel von Grund auf neu schreiben möchten, müssen Sie die Dateien **EaselJS** und **PreloadJS** in Ihre Projektmappe kopieren und dann ein Canvas-Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="053bd-152">By the way, if you are going to write your own JavaScript game from scratch, you too will need to copy the **EaselJS** and **PreloadJS** files into your solution, and then create a canvas object.</span></span>

<span data-ttu-id="053bd-153">Von EaselJS erhalten wir ein neues Objekt, das *Phase* genannt wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-153">EaselJS provides us with a new object called a *stage*.</span></span> <span data-ttu-id="053bd-154">Die Phase ist mit dem Canvas verknüpft und dient zum Anzeigen von Bildern und Text.</span><span class="sxs-lookup"><span data-stu-id="053bd-154">The stage is linked to the canvas, and is used for displaying images and text.</span></span> <span data-ttu-id="053bd-155">Alle Objekte, die auf der Bühne angezeigt werden sollen, müssen zunächst als untergeordnetes Element der Bühne wie folgt hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="053bd-155">Any object we want to be displayed on the stage must first be added as a child of the stage, like this:</span></span>

```
    stage.addChild(myObject);
```

<span data-ttu-id="053bd-156">Sie sehen, dass diese Codezeile mehrmals in **main.js** angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="053bd-156">You will see that line of code appear several times in **main.js**</span></span>

<span data-ttu-id="053bd-157">Jetzt ist ein guter Zeitpunkt zum Öffnen von **main.js**.</span><span class="sxs-lookup"><span data-stu-id="053bd-157">Speaking of which, now is a good time to open **main.js**.</span></span>

### <a name="2-loading-the-bitmaps"></a><span data-ttu-id="053bd-158">2. Laden der Bitmaps</span><span class="sxs-lookup"><span data-stu-id="053bd-158">2. Loading the bitmaps</span></span>

<span data-ttu-id="053bd-159">EaselJS bietet verschiedene Arten von Grafikobjekten.</span><span class="sxs-lookup"><span data-stu-id="053bd-159">EaselJS provides us with several different types of graphical objects.</span></span> <span data-ttu-id="053bd-160">Wir können einfache Formen (z.B. das blaue Rechteck für den Himmel) oder Bitmaps (z.B. die Wolken, die wir hinzufügen möchten), Textobjekte und Sprites erstellen.</span><span class="sxs-lookup"><span data-stu-id="053bd-160">We can create simple shapes (such as the blue rectangle used for the sky), or bitmaps (such as the clouds we're about to add), text objects, and sprites.</span></span> <span data-ttu-id="053bd-161">Sprites verwenden ein (SpriteSheet) [http://createjs.com/docs/easeljs/classes/SpriteSheet.html]: eine einzelne Bitmap, die mehrere Bilder enthält.</span><span class="sxs-lookup"><span data-stu-id="053bd-161">Sprites use a (SpriteSheet)[http://createjs.com/docs/easeljs/classes/SpriteSheet.html]: a single bitmap containing multiple images.</span></span> <span data-ttu-id="053bd-162">Beispielsweise verwenden wir dieses SpriteSheet zum Speichern des anderen Frames der Dinosaurier-Animation:</span><span class="sxs-lookup"><span data-stu-id="053bd-162">For example, we use this SpriteSheet to store the different frame of dinosaur animation:</span></span>

![Sprite-Blatt für laufenden Dino](images/JS2D_4.png)

<span data-ttu-id="053bd-164">Wir bringen den Dinosaurier zum Laufen, indem wir die verschiedenen Frames definieren und festlegen, wie schnell sie in diesem Code animiert werden sollen:</span><span class="sxs-lookup"><span data-stu-id="053bd-164">We make the dinosaur walk, by defining the different frames and how fast they should be animated in this code:</span></span>

```
    // Define the animated dino walk using a spritesheet of images,
    // and also a standing-still state, and a knocked-over state.
    var data = {
        images: [loader.getResult("dino")],
        frames: { width: 373, height: 256 },
        animations: {
            stand: 0,
            lying: { 
                frames: [0, 1],
                speed: 0.1
            },
            walk: {
                frames: [0, 1, 2, 3, 2, 1],
                speed: 0.4
            }
        }
    }

    var spriteSheet = new createjs.SpriteSheet(data);
    dino_walk = new createjs.Sprite(spriteSheet, "walk");
    dino_stand = new createjs.Sprite(spriteSheet, "stand");
    dino_lying = new createjs.Sprite(spriteSheet, "lying");

```

<span data-ttu-id="053bd-165">Jetzt werden wir einige kleine Wolken zur Bühne hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="053bd-165">Right now, we're going to add some little fluffy clouds to the stage.</span></span> <span data-ttu-id="053bd-166">Wenn das Spiel ausgeführt wird, sollen sie über den Bildschirm schweben.</span><span class="sxs-lookup"><span data-stu-id="053bd-166">Once the game is running, they'll drift across the screen.</span></span> <span data-ttu-id="053bd-167">Das Bild für die Cloud befindet sich bereits in der Projektmappe im Ordner *images*.</span><span class="sxs-lookup"><span data-stu-id="053bd-167">The image for the cloud is already in the solution, in the *images* folder.</span></span>

<span data-ttu-id="053bd-168">Sehen Sie sich **main.js** an, bis Sie die Funktion **init()** finden.</span><span class="sxs-lookup"><span data-stu-id="053bd-168">Look through **main.js** until you find the **init()** function.</span></span> <span data-ttu-id="053bd-169">Diese wird aufgerufen, wenn das Spiel gestartet wird, und dort beginnen wir mit der Einrichtung unserer Grafikobjekte.</span><span class="sxs-lookup"><span data-stu-id="053bd-169">This is called when the game starts, and it's where we begin to set up all our graphic objects.</span></span>

<span data-ttu-id="053bd-170">Suchen Sie den folgenden Code, und entfernen Sie die Kommentare (\\) aus der Zeile, die auf das Wolkenbild verweist.</span><span class="sxs-lookup"><span data-stu-id="053bd-170">Find the following code, and remove the comments (\\) from the line that references the cloud image.</span></span>

```
 manifest = [
        { src: "walkingDino-SpriteSheet.png", id: "dino" },
        { src: "barrel.png", id: "barrel" },
        { src: "fluffy-cloud-small.png", id: "cloud" },
    ];
```

<span data-ttu-id="053bd-171">JavaScript benötigt etwas Hilfe, wenn es darum geht, Ressourcen wie Bilder zu laden, weshalb wir ein Feature der CreateJS-Bibliothek verwenden, das Bilder vorab laden kann und [LoadQueue](http://www.createjs.com/docs/preloadjs/classes/LoadQueue.html) heißt.</span><span class="sxs-lookup"><span data-stu-id="053bd-171">JavaScript needs a little help when it comes to loading resources such as images, and so we're using a feature of the CreateJS library that can preload images, called a [LoadQueue](http://www.createjs.com/docs/preloadjs/classes/LoadQueue.html).</span></span> <span data-ttu-id="053bd-172">Wir wissen nicht, wie lange es dauert, die Bilder zu laden, weshalb wir LoadQueue verwenden, um dies auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="053bd-172">We're can't be sure how long it will take the images to load, so we use the LoadQueue to take care of it.</span></span> <span data-ttu-id="053bd-173">Sobald die Bilder verfügbar sind, wird die Warteschlange uns mitteilen, dass sie bereit sind.</span><span class="sxs-lookup"><span data-stu-id="053bd-173">Once the images are available, the queue will tell us they are ready.</span></span> <span data-ttu-id="053bd-174">Zu diesem Zweck erstellen wir zuerst ein neues Objekt, das all unsere Bilder enthält, und erstellen dann ein LoadQueue-Objekt.</span><span class="sxs-lookup"><span data-stu-id="053bd-174">In order to do that, we first create a new object that lists all our images, and then we create a LoadQueue object.</span></span> <span data-ttu-id="053bd-175">Sie sehen im Code unten, wie dieses eingerichtet ist, um eine Funktion namens **loadingComplete()** aufzurufen, wenn alles bereit ist.</span><span class="sxs-lookup"><span data-stu-id="053bd-175">You'll see in the code below how it is set-up to call a function called **loadingComplete()** when everything is ready.</span></span>

```
    // Now we create a special queue, and finally a handler that is
    // called when they are loaded. The queue object is provided by preloadjs.

    loader = new createjs.LoadQueue(false);
    loader.addEventListener("complete", loadingComplete);
    loader.loadManifest(manifest, true, "../images/");
```    

<span data-ttu-id="053bd-176">Wenn die Funktion **loadingComplete()** aufgerufen wird, sind die Bilder geladen und können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-176">When the function **loadingComplete()** is called, the images are loaded and ready to use.</span></span> <span data-ttu-id="053bd-177">Sie sehen einen auskommentierten Abschnitt, der die Wolken erstellt, sobald die Bitmap verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="053bd-177">You'll see a commented-out section that creates the clouds, now their bitmap is available.</span></span> <span data-ttu-id="053bd-178">Entfernen Sie die Kommentare, damit der Abschnitt wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="053bd-178">Remove the comments, so it looks like this:</span></span>

```
    // Create some clouds to drift by..
    for (var i = 0; i < 3; i++) {
        cloud[i] = new createjs.Bitmap(loader.getResult("cloud"));
        cloud[i].x = Math.random()*1024; // Random start location
        cloud[i].y = 64 + i * 48;
        stage.addChild(cloud[i]);
    }
```
<span data-ttu-id="053bd-179">Dieser Code erstellt drei Cloudobjekte, die jeweils das vorab geladene Bild verwenden, definiert deren Position und fügt diese anschließend zur Bühne hinzu.</span><span class="sxs-lookup"><span data-stu-id="053bd-179">This code creates three cloud objects each using our pre-loaded image, defines their location, and then adds them to the stage.</span></span>

<span data-ttu-id="053bd-180">Führen Sie die App erneut aus (durch Drücken von F5), und Sie werden sehen, dass unsere Wolken angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-180">Run the app again (press F5) and you'll see our clouds have appeared.</span></span>

### <a name="3-moving-the-clouds"></a><span data-ttu-id="053bd-181">3. Bewegen der Wolken</span><span class="sxs-lookup"><span data-stu-id="053bd-181">3. Moving the clouds</span></span>

<span data-ttu-id="053bd-182">Jetzt werden wir die Wolken bewegen.</span><span class="sxs-lookup"><span data-stu-id="053bd-182">Now we're going to make the clouds move.</span></span> <span data-ttu-id="053bd-183">Das Geheimnis für das Bewegen der Wolken – und aller anderen Elemente – ist, eine [Ticker](http://www.createjs.com/docs/easeljs/classes/Ticker.html)-Funktion einzurichten, die wiederholt mehrmals pro Sekunde aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-183">The secret to moving clouds - and moving anything, in fact - is to set-up a [ticker](http://www.createjs.com/docs/easeljs/classes/Ticker.html) function that is repeatedly called multiple times a second.</span></span> <span data-ttu-id="053bd-184">Jedes Mal, wenn diese Funktion aufgerufen wird, wird die Grafik an einem etwas anderen Ort neu gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="053bd-184">Every time this function is called, it redraws the graphics in a slightly different place.</span></span>

<p data-height="500" data-theme-id="23761" data-slug-hash="vxZVRK" data-default-tab="result" data-user="MicrosoftEdgeDocumentation" data-embed-version="2" data-pen-title="CreateJS - Animating clouds" data-preview="true" data-editable="true" class="codepen"><span data-ttu-id="053bd-185">Sehen Sie sich den Pen <a href="https://codepen.io/MicrosoftEdgeDocumentation/pen/vxZVRK/">CreateJS – Animieren von Wolken</a> von Microsoft Edge Docs (<a href="http://codepen.io/MicrosoftEdgeDocumentation">@MicrosoftEdgeDocumentation</a>) auf <a href="http://codepen.io">CodePen</a> an.</span><span class="sxs-lookup"><span data-stu-id="053bd-185">See the Pen <a href="https://codepen.io/MicrosoftEdgeDocumentation/pen/vxZVRK/">CreateJS - Animating clouds</a> by Microsoft Edge Docs (<a href="http://codepen.io/MicrosoftEdgeDocumentation">@MicrosoftEdgeDocumentation</a>) on <a href="http://codepen.io">CodePen</a>.</span></span></p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
 
<span data-ttu-id="053bd-186">Der Code dazu ist bereits in der Datei **main.js** vorhanden, die von der CreateJS-Bibliothek EaselJS bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-186">The code to do that is already in the **main.js** file, provided by the CreateJS library, EaselJS.</span></span> <span data-ttu-id="053bd-187">Es sieht ungefähr so aus:</span><span class="sxs-lookup"><span data-stu-id="053bd-187">It looks like this:</span></span>

```
    // Set up the game loop and keyboard handler.
    // The keyword 'tick' is required to automatically animated the sprite.
    createjs.Ticker.timingMode = createjs.Ticker.RAF;
    createjs.Ticker.addEventListener("tick", gameLoop);
```

<span data-ttu-id="053bd-188">Dieser Code ruft eine Funktion namens **gameLoop()** mit zwischen 30 und 60 Frames pro Sekunde auf.</span><span class="sxs-lookup"><span data-stu-id="053bd-188">This code will call a function called **gameLoop()** between 30 and 60 frames a second.</span></span> <span data-ttu-id="053bd-189">Die genaue Geschwindigkeit hängt von der Geschwindigkeit Ihres Computers ab.</span><span class="sxs-lookup"><span data-stu-id="053bd-189">The exact speed depends on the speed of your computer.</span></span>

<span data-ttu-id="053bd-190">Suchen Sie nach der **gameLoop()**-Funktion. Unten zum Ende hin sehen Sie eine Funktion namens **animateClouds()**.</span><span class="sxs-lookup"><span data-stu-id="053bd-190">Look for the **gameLoop()** function, and down towards the end you'll see a function called **animateClouds()**.</span></span> <span data-ttu-id="053bd-191">Bearbeiten Sie sie, damit sie nicht mehr auskommentiert ist.</span><span class="sxs-lookup"><span data-stu-id="053bd-191">Edit it so that it is not commented out.</span></span>

```
    // Move clouds
    animateClouds();
```

<span data-ttu-id="053bd-192">Wenn Sie die Definition dieser Funktion betrachten, sehen Sie, wie diese jede Wolke nacheinander nimmt und deren X-Koordinate ändert.</span><span class="sxs-lookup"><span data-stu-id="053bd-192">If you look at the defintion of this function, you'll see how it takes each cloud in turn, and changes its x co-ordinate.</span></span> <span data-ttu-id="053bd-193">Wenn die X-Koordinate außerhalb der Bildschirmseite liegt, wird sie nach ganz rechts zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="053bd-193">If the x-ordinate is off the side of screen, it is reset to the far right.</span></span> <span data-ttu-id="053bd-194">Jede Wolke bewegt sich also mit einer etwas unterschiedlichen Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="053bd-194">Each cloud also moves at a slightly different speed.</span></span>

```
function animate_clouds()
{
    // Move the cloud sprites across the sky. If they get to the left edge, 
    // move them over to the right.

    for (var i = 0; i < 3; i++) {    
        cloud[i].x = cloud[i].x - (i+1);
        if (cloud[i].x < -128)
            cloud[i].x = width + 128;
    }
}
```

<span data-ttu-id="053bd-195">Wenn Sie die App jetzt ausführen, sehen Sie, dass sich die Wolken bewegen.</span><span class="sxs-lookup"><span data-stu-id="053bd-195">If you run the app now, you'll see that the clouds have started drifting.</span></span> <span data-ttu-id="053bd-196">Jetzt haben wir also Bewegung!</span><span class="sxs-lookup"><span data-stu-id="053bd-196">Finally we have motion!</span></span>

### <a name="4-adding-keyboard-and-mouse-input"></a><span data-ttu-id="053bd-197">4. Hinzufügen von Tastatur- und Mauseingaben</span><span class="sxs-lookup"><span data-stu-id="053bd-197">4. Adding keyboard and mouse input</span></span>

<span data-ttu-id="053bd-198">Ein Spiel, mit dem Sie nicht interagieren können, ist kein Spiel.</span><span class="sxs-lookup"><span data-stu-id="053bd-198">A game that you can't interact with isn't a game.</span></span> <span data-ttu-id="053bd-199">Wir müssen dem Spieler also ermöglichen, die Tastatur oder Maus zu verwenden, um eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="053bd-199">So let's allow the player to use the keyboard or the mouse to do something.</span></span> <span data-ttu-id="053bd-200">In der **loadingComplete()**-Funktion sehen Sie Folgendes.</span><span class="sxs-lookup"><span data-stu-id="053bd-200">Back in the **loadingComplete()** function, you'll see the following.</span></span> <span data-ttu-id="053bd-201">Entfernen Sie die Kommentare.</span><span class="sxs-lookup"><span data-stu-id="053bd-201">Remove the comments.</span></span>

```
    // This code will call the method 'keyboardPressed' is the user presses a key.
    this.document.onkeydown = keyboardPressed;

    // Add support for mouse clicks
    stage.on("stagemousedown", mouseClicked);
```

<span data-ttu-id="053bd-202">Wir haben jetzt zwei Funktionen, die aufgerufen werden, wenn der Spieler eine Taste drückt oder mit der Maus klickt.</span><span class="sxs-lookup"><span data-stu-id="053bd-202">We now have two functions being called whenever the player hits a key or clicks the mouse.</span></span> <span data-ttu-id="053bd-203">Beide Ereignisse rufen **userDidSomething()** auf, eine Funktion, welche die Gamestate-Variable untersucht, um zu entscheiden, was das Spiel derzeit ausführt und was daher als Nächstes passieren muss.</span><span class="sxs-lookup"><span data-stu-id="053bd-203">Both event will call **userDidSomething()**, a function which looks at the gamestate variable to decide what the game is currently doing, and what needs to happen next as a result.</span></span>

<span data-ttu-id="053bd-204">Gamestate ist ein Entwurfsmuster, das häufig in Spielen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-204">Gamestate is a common design pattern used in games.</span></span> <span data-ttu-id="053bd-205">Alles, was passiert, erfolgt in der **gameLoop()**-Funktion, die vom Ticker-Timer aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-205">Everything that happens, happens in the **gameLoop()** function called by the ticker timer.</span></span> <span data-ttu-id="053bd-206">Die gameLoop()-Funktion verfolgt, ob das Spiel gespielt wird, das Spiel gerade vorbei ist, das Spiel jetzt begonnen werden kann oder einen anderen vom Autor definierten Zustand hat, und verwendet eine Variable.</span><span class="sxs-lookup"><span data-stu-id="053bd-206">The gameLoop() keeps track of whether the game is playing, or in a "game over state", or a "ready-to-play state", or any other states defined by the author, using a variable.</span></span> <span data-ttu-id="053bd-207">Diese Zustandsvariable wird in einer Switch-Anweisung getestet und definiert, welche anderen Funktionen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-207">This state variable is tested in a switch statement, and that defines what other functions are called.</span></span> <span data-ttu-id="053bd-208">Wenn der Zustand auf „Wiedergabe“ festgelegt ist, werden die Funktionen, welche den Dinosaurier springen lassen und die Fässer verschieben, aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="053bd-208">So if the state is set to "playing", the functions to make the dinosaur jump and make the barrels move will be called.</span></span> <span data-ttu-id="053bd-209">Wenn der Dinosaurier getötet wird, wird die Gamestate-Variable auf den Zustand „Spiel beendet“ gesetzt und die Meldung „Game over!“</span><span class="sxs-lookup"><span data-stu-id="053bd-209">If the dinosaur is killed by something, the gamestate variable will be set to "game over state", and the "Game over!"</span></span> <span data-ttu-id="053bd-210">wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="053bd-210">message will be displayed instead.</span></span> <span data-ttu-id="053bd-211">Wenn Sie an Spielentwurfsmustern interessiert sind, ist das Buch [Game Programming Patterns](http://gameprogrammingpatterns.com/) sehr hilfreich.</span><span class="sxs-lookup"><span data-stu-id="053bd-211">If you are interested in game design patterns, the book [Game Programming Patterns](http://gameprogrammingpatterns.com/) is very helpful.</span></span>

<span data-ttu-id="053bd-212">Führen Sie die App erneut aus, anschließend können Sie mit dem Spiel beginnen.</span><span class="sxs-lookup"><span data-stu-id="053bd-212">Try running the app again, and finally you'll be able to start playing.</span></span> <span data-ttu-id="053bd-213">Drücken Sie die Leertaste (oder klicken mit der Maus oder tippen auf den Bildschirm), damit etwas passiert.</span><span class="sxs-lookup"><span data-stu-id="053bd-213">Press space (or click the mouse, or tap the screen) to start things happening.</span></span> 

<span data-ttu-id="053bd-214">Sie sehen ein Fass, das auf Sie zurollt: Drücken Sie genau zum richtigen Zeitpunkt erneut die Leertaste oder klicken Sie, sodass der Dinosaurier wegspringt.</span><span class="sxs-lookup"><span data-stu-id="053bd-214">You'll see a barrel come rolling towards you: press space or click again at just the right time, and the dinosaur will leap.</span></span> <span data-ttu-id="053bd-215">Wenn Sie nicht den richtigen Zeitpunkt erwischen, ist das Spiel vorüber.</span><span class="sxs-lookup"><span data-stu-id="053bd-215">Time it wrong, and your game is over.</span></span>

<span data-ttu-id="053bd-216">Das Fass ist genauso animiert wie die Wolken (auch wenn es jedes Mal schneller wird), und wir überprüfen die Position des Dinosauriers und des Fasses, um sicherzustellen, dass sie nicht kollidieren:</span><span class="sxs-lookup"><span data-stu-id="053bd-216">The barrel is animated in the same way as the clouds (although it gets faster each time), and we check the position of the dinosaur and the barrel to make sure they haven't collided:</span></span>

```
 // Very simple check for collision between dino and barrel
                if ((barrel.x > 220 && barrel.x < 380)
                    &&
                    (!jumping))
                {
                    barrel.x = 380;
                    GameState = GameStateEnum.GameOver;
                }
```

<span data-ttu-id="053bd-217">Wenn der Dinosaurier nicht springt und das Fass in der Nähe ist, ändert der Code die Zustandsvariable in den Zustand, den wir *GameOver* genannt haben.</span><span class="sxs-lookup"><span data-stu-id="053bd-217">If the dinosaur isn't jumping and the barrel is nearby, the code changes the state varaible to the state we've called *GameOver*.</span></span> <span data-ttu-id="053bd-218">Wie Sie sich denken können, beendet *GameOver* das Spiel.</span><span class="sxs-lookup"><span data-stu-id="053bd-218">As you can imagine, *GameOver* stops the game.</span></span>

<span data-ttu-id="053bd-219">So sind die wichtigsten Mechanismen unseres Spiels abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="053bd-219">And so the main mechanics of our game are complete.</span></span>

### <a name="5-resizing-support"></a><span data-ttu-id="053bd-220">5. Unterstützen der Größenanpassung</span><span class="sxs-lookup"><span data-stu-id="053bd-220">5. Resizing support</span></span>

<span data-ttu-id="053bd-221">Wir sind jetzt fast fertig!</span><span class="sxs-lookup"><span data-stu-id="053bd-221">We're almost done here!</span></span> <span data-ttu-id="053bd-222">Zuvor gibt es noch ein lästiges Problem, das wir zuerst lösen müssen.</span><span class="sxs-lookup"><span data-stu-id="053bd-222">But before we stop, there is one annoying problem to take care of first.</span></span> <span data-ttu-id="053bd-223">Versuchen Sie, die Größe des Fensters anzupassen, wenn das Spiel ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-223">When the game is running, try resizing the window.</span></span> <span data-ttu-id="053bd-224">Sie sehen, dass das Spiel schnell durcheinandergerät und Objekte nicht länger dort sind, wo sie sein sollen.</span><span class="sxs-lookup"><span data-stu-id="053bd-224">You'll see that the game quickly becomes very messed-up, as objects are no longer where they should be.</span></span> <span data-ttu-id="053bd-225">Wir können dies beheben, indem wir einen Handler für das Fenstergrößeänderungsereignis erstellen, das generiert wird, wenn der Spieler die Fenstergröße ändert oder das Gerät vom Quer- ins Hochformat gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="053bd-225">We can take care of that by creating a handler for the window resizing event generated when the player resizes the window, or when the device is rotated from landscape to portrait.</span></span>

<span data-ttu-id="053bd-226">Der Code dazu ist bereits vorhanden (tatsächlich rufen wir ihn auf, wenn das Spiel erstmalig gestartet wird, um sicherzustellen, dass die Standardfenstergröße funktioniert. Wenn eine UWP-App gestartet wird, wissen Sie nicht sicher, welche Größe das Fenster haben wird).</span><span class="sxs-lookup"><span data-stu-id="053bd-226">The code to do this is already present (in fact, we call it when the game first starts, to make sure the default window size works, because when a UWP app is launched, you can't be certain what size the window will be).</span></span>

<span data-ttu-id="053bd-227">Kommentieren Sie diese Zeile einfach aus, um die Funktion aufrufen, wenn das Bildschirmgrößenereignis ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="053bd-227">Just uncomment this line to call the function when the screen size event is fired:</span></span>

```
    // This code makes the app call the method 'resizeGameWindow' if the user resizes the current window.
     window.addEventListener('resize', resizeGameWindow);
```

<span data-ttu-id="053bd-228">Wenn Sie die App erneut ausführen, sollten Sie jetzt die Größe des Fensters anpassen können und bessere Ergebnisse erhalten.</span><span class="sxs-lookup"><span data-stu-id="053bd-228">If you run the app again, you should now be able to resize the window and get better results.</span></span>

## <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="053bd-229">Veröffentlichung im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="053bd-229">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="053bd-230">Nachdem Sie nun eine UWP-app haben, ist es möglich, veröffentlichen, an den Microsoft Store (vorausgesetzt, dass Sie diese zunächst verbessert haben!)</span><span class="sxs-lookup"><span data-stu-id="053bd-230">Now you have a UWP app, it is possible to publish it to the Microsoft Store (assuming you have improved it first!)</span></span> 

<span data-ttu-id="053bd-231">Dazu müssen Sie einige Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="053bd-231">There are a few steps to the process.</span></span>

1. <span data-ttu-id="053bd-232">Sie müssen als Windows-Entwickler [registriert](https://developer.microsoft.com/en-us/store/register) sein.</span><span class="sxs-lookup"><span data-stu-id="053bd-232">You must be [registered](https://developer.microsoft.com/en-us/store/register) as a Windows Developer.</span></span>
2. <span data-ttu-id="053bd-233">Verwenden Sie die [Prüfliste für App-Übermittlung](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span><span class="sxs-lookup"><span data-stu-id="053bd-233">You must use the app submission [checklist](https://msdn.microsoft.com/windows/uwp/publish/app-submissions).</span></span>
3. <span data-ttu-id="053bd-234">Die App muss zur [Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process) eingereicht werden.</span><span class="sxs-lookup"><span data-stu-id="053bd-234">The app must be submitted for [certification](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process).</span></span>

<span data-ttu-id="053bd-235">Weitere Informationen finden Sie in der [Veröffentlichung Ihrer UWP-app](https://developer.microsoft.com/en-us/store/publish-apps).</span><span class="sxs-lookup"><span data-stu-id="053bd-235">For more details, see [Publishing your UWP app](https://developer.microsoft.com/en-us/store/publish-apps).</span></span>

## <a name="suggestions-for-other-features"></a><span data-ttu-id="053bd-236">Vorschläge für andere Features.</span><span class="sxs-lookup"><span data-stu-id="053bd-236">Suggestions for other features.</span></span>

<span data-ttu-id="053bd-237">Was jetzt?</span><span class="sxs-lookup"><span data-stu-id="053bd-237">What next?</span></span> <span data-ttu-id="053bd-238">Hier sind einige Vorschläge für Features, die Sie zu Ihrer (hoffentlich bald) preisgekrönten App hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="053bd-238">Here are a few suggestions for features to add to your (soon to be) award-winning app.</span></span>

1. <span data-ttu-id="053bd-239">Soundeffekte</span><span class="sxs-lookup"><span data-stu-id="053bd-239">Sound effects.</span></span> <span data-ttu-id="053bd-240">Die CreateJS-Bibliothek bietet Audiounterstützung mit einer Bibliothek namens [SoundJS](http://www.createjs.com/soundjs).</span><span class="sxs-lookup"><span data-stu-id="053bd-240">The CreateJS library includes support for sound, with a library called [SoundJS](http://www.createjs.com/soundjs).</span></span>
2. <span data-ttu-id="053bd-241">Gamepad-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="053bd-241">Gamepad support.</span></span> <span data-ttu-id="053bd-242">Es gibt eine [verfügbare API](https://gamedevelopment.tutsplus.com/tutorials/using-the-html5-gamepad-api-to-add-controller-support-to-browser-games--cms-21345).</span><span class="sxs-lookup"><span data-stu-id="053bd-242">There is an [API available](https://gamedevelopment.tutsplus.com/tutorials/using-the-html5-gamepad-api-to-add-controller-support-to-browser-games--cms-21345).</span></span>
3. <span data-ttu-id="053bd-243">Erstellen Sie ein viel, viel besseres Spiel!</span><span class="sxs-lookup"><span data-stu-id="053bd-243">Make it a much, much better game!</span></span> <span data-ttu-id="053bd-244">Dieser Teil ist Ihre Aufgabe, aber es gibt zahlreiche Ressourcen online.</span><span class="sxs-lookup"><span data-stu-id="053bd-244">That part is up to you, but there are lots of resources available online.</span></span> 

## <a name="other-links"></a><span data-ttu-id="053bd-245">Weitere Links</span><span class="sxs-lookup"><span data-stu-id="053bd-245">Other links</span></span>

* [<span data-ttu-id="053bd-246">Erstellen Sie ein einfaches Windows-Spiel mit JavaScript</span><span class="sxs-lookup"><span data-stu-id="053bd-246">Make a simple Windows game with JavaScript</span></span>](https://www.sitepoint.com/creating-a-simple-windows-8-game-with-javascript-game-basics-createjseaseljs/)
* [<span data-ttu-id="053bd-247">Auswählen einer HTML/JS-Spielengine</span><span class="sxs-lookup"><span data-stu-id="053bd-247">Picking an HTML/JS game engine</span></span>](https://html5gameengine.com/)
* [<span data-ttu-id="053bd-248">Verwenden von CreateJS in Ihrem JS-basierten Spiel</span><span class="sxs-lookup"><span data-stu-id="053bd-248">Using CreateJS in your JS based game</span></span>](https://blogs.msdn.microsoft.com/cbowen/2012/09/19/using-createjs-in-your-javascript-based-windows-8-game/)
* [<span data-ttu-id="053bd-249">Spielentwicklungskurse auf LinkedIn Learning</span><span class="sxs-lookup"><span data-stu-id="053bd-249">Game development courses on LinkedIn Learning</span></span>](https://www.linkedin.com/learning/topics/game-development)
