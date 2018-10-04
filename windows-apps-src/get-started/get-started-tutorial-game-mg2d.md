---
title: Erstellen eines UWP-Spiels in MonoGame-2D
description: Ein einfaches UWP-Spiel für den Microsoft Store, geschrieben in c# und MonoGame
author: muhsinking
ms.author: mukin
ms.date: 03/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 5d5f7af2-41a9-4749-ad16-4503c64bb80c
ms.localizationpriority: medium
ms.openlocfilehash: d38465ce02e0aedf854094ede75fc33701b226a6
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4360381"
---
# <a name="create-a-uwp-game-in-monogame-2d"></a><span data-ttu-id="2f5be-104">Erstellen eines UWP-Spiels in MonoGame-2D</span><span class="sxs-lookup"><span data-stu-id="2f5be-104">Create a UWP game in MonoGame 2D</span></span>

## <a name="a-simple-2d-uwp-game-for-the-microsoft-store-written-in-c-and-monogame"></a><span data-ttu-id="2f5be-105">Ein einfaches 2D-UWP-Spiel für den Microsoft Store, geschrieben in C# und MonoGame</span><span class="sxs-lookup"><span data-stu-id="2f5be-105">A simple 2D UWP game for the Microsoft Store, written in C# and MonoGame</span></span>


![Sprite-Blatt für laufenden Dino](images/JS2D_0.png)

## <a name="introduction"></a><span data-ttu-id="2f5be-107">Einführung</span><span class="sxs-lookup"><span data-stu-id="2f5be-107">Introduction</span></span>

<span data-ttu-id="2f5be-108">MonoGame ist ein einfaches Framework für die Spieleentwicklung.</span><span class="sxs-lookup"><span data-stu-id="2f5be-108">MonoGame is a lightweight game development framework.</span></span> <span data-ttu-id="2f5be-109">In diesem Lernprogramm lernen Sie die Grundlagen der Entwicklung von Spielen in MonoGame kennen und erhalten z.B. Informationen zum Laden von Inhalten, Zeichnen und Animieren von Sprites und Behandeln von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-109">This tutorial will teach you the basics of game development in MonoGame, including how to load content, draw sprites, animate them, and handle user input.</span></span> <span data-ttu-id="2f5be-110">Außerdem werden einige erweiterte Konzepte wie die Erkennung von Kollisionen und die Skalierung von Bildschirmen für einen hohen DPI-Wert besprochen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-110">Some more advanced concepts like collision detection and scaling up for high-DPI screens are also discussed.</span></span> <span data-ttu-id="2f5be-111">Dieses Lernprogramm dauert 30 bis 60Minuten.</span><span class="sxs-lookup"><span data-stu-id="2f5be-111">This tutorial takes 30-60 minutes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f5be-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2f5be-112">Prerequisites</span></span>
+   <span data-ttu-id="2f5be-113">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="2f5be-113">Windows 10 and Microsoft Visual Studio 2017.</span></span>  <span data-ttu-id="2f5be-114">[Klicken Sie hier, um zu erfahren, wie Sie Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="2f5be-114">[Click here to learn how to get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="2f5be-115">Das .NET Framework-desktop-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="2f5be-115">The .NET desktop development framework.</span></span> <span data-ttu-id="2f5be-116">Wenn Sie bereits mit Dies installiert haben, können Sie es durch das Visual Studio-Installationsprogramm erneut ausführen, und ändern die Installation von Visual Studio 2017 abrufen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-116">If you don't already have this installed, you can get it by re-running the Visual Studio installer and modifying your installation of Visual Studio 2017.</span></span>
+   <span data-ttu-id="2f5be-117">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-117">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="2f5be-118">[Klicken Sie hier, um Informationen zum Einstieg in C# zu erhalten](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="2f5be-118">[Click here to learn how to get started with C#](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>
+   <span data-ttu-id="2f5be-119">Kenntnisse über die grundlegenden Konzepte der Informatik, wie Klassen, Methoden und Variablen, sind ebenfalls von Vorteil.</span><span class="sxs-lookup"><span data-stu-id="2f5be-119">Familiarity with basic computer science concepts like classes, methods, and variables is a plus.</span></span>

## <a name="why-monogame"></a><span data-ttu-id="2f5be-120">Warum MonoGame?</span><span class="sxs-lookup"><span data-stu-id="2f5be-120">Why MonoGame?</span></span>
<span data-ttu-id="2f5be-121">In Umgebungen für die Spieleentwicklung gibt es ausreichend Optionen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-121">There’s no shortage of options when it comes to game development environments.</span></span> <span data-ttu-id="2f5be-122">Und das Angebot ist groß: von Engines mit vollem Funktionsumfang wie Unity bis hin zu umfassenden und komplexen Multimedia-APIs wie DirectX. Womit soll man beginnen?</span><span class="sxs-lookup"><span data-stu-id="2f5be-122">From full-featured engines like Unity to comprehensive and complex multimedia APIs like DirectX, it can be hard to know where to start.</span></span> <span data-ttu-id="2f5be-123">MonoGame ist eine Sammlung von Tools, die in ihrer Komplexität zwischen einer Game-Engine und einer ausgereiften API wie DirectX liegt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-123">MonoGame is a set of tools, with a level of complexity falling somewhere between a game engine and a grittier API like DirectX.</span></span> <span data-ttu-id="2f5be-124">Sie bietet eine einfach zu verwendende Content-Pipeline und alle erforderlichen Funktionen, um einfache Spiele zu erstellen, die auf einer Vielzahl von Plattformen ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="2f5be-124">It provides an easy-to-use content pipeline, and all the functionality required to create lightweight games that run on a wide variety of platforms.</span></span> <span data-ttu-id="2f5be-125">Das beste MonoGame-apps werden in reinem c#-Code geschrieben, und Sie können sie schnell über den Microsoft Store oder andere ähnliche Plattformen verteilen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-125">Best of all, MonoGame apps are written in pure C#, and you can distribute them quickly via the Microsoft Store or other similar distribution platforms.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="2f5be-126">Code abrufen</span><span class="sxs-lookup"><span data-stu-id="2f5be-126">Get the code</span></span>
<span data-ttu-id="2f5be-127">Wenn Sie das Lernprogramm nicht schrittweise durchgehen, sondern nur MonoGame in Aktion sehen möchten, [klicken Sie hier, um die fertige App abzurufen](https://github.com/Microsoft/Windows-appsample-get-started-mg2d).</span><span class="sxs-lookup"><span data-stu-id="2f5be-127">If you don’t feel like working through the tutorial step-by-step and just want to see MonoGame in action, [click here to get the finished app](https://github.com/Microsoft/Windows-appsample-get-started-mg2d).</span></span>

<span data-ttu-id="2f5be-128">Öffnen Sie das Projekt in Visual Studio 2017, und drücken Sie **F5** , um das Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-128">Open the project in Visual Studio 2017, and press **F5** to run the sample.</span></span> <span data-ttu-id="2f5be-129">Wenn Sie das Projekt zum ersten Mal laden, kann dies möglicherweise etwas länger dauern, da Visual Studio alle NuGet-Pakete abrufen muss, die nicht mit installiert wurden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-129">The first time you do this may take a while, as Visual Studio needs to fetch any NuGet packages that are missing from your installation.</span></span>

<span data-ttu-id="2f5be-130">Wenn Sie dies getan haben, überspringen Sie den nächsten Abschnittzum Einrichten von MonoGame, und sehen Sie sich eine schrittweise Erläuterung des Codes an.</span><span class="sxs-lookup"><span data-stu-id="2f5be-130">If you’ve done this, skip the next section about setting up MonoGame to see a step-by-step walkthrough of the code.</span></span>

<span data-ttu-id="2f5be-131">**Hinweis:** Das in diesem Beispiel erstellte Spiel soll nicht abgeschlossen sein (oder überhaupt Spaß machen).</span><span class="sxs-lookup"><span data-stu-id="2f5be-131">**Note:** The game created in this sample is not meant to be complete (or any fun at all).</span></span> <span data-ttu-id="2f5be-132">Der Zweck besteht darin, die grundlegenden Konzepte der 2D-Entwicklung in MonoGame zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-132">Its only purpose is to demonstrate all the core concepts of 2D development in MonoGame.</span></span> <span data-ttu-id="2f5be-133">Verwenden Sie diesen Code und verbessern Sie ihn – oder beginnen Sie einfach ganz von vorn, nachdem Sie die Grundlagen kennengelernt haben!</span><span class="sxs-lookup"><span data-stu-id="2f5be-133">Feel free to use this code and make something much better—or just start from scratch after you’ve mastered the basics!</span></span>

## <a name="set-up-monogame-project"></a><span data-ttu-id="2f5be-134">Einrichten des MonoGame-Projekts</span><span class="sxs-lookup"><span data-stu-id="2f5be-134">Set up MonoGame project</span></span>
1. <span data-ttu-id="2f5be-135">Installieren Sie **MonoGame 3.6** für Visual Studio aus [MonoGame.net](http://www.monogame.net/).</span><span class="sxs-lookup"><span data-stu-id="2f5be-135">Install **MonoGame 3.6** for Visual Studio from [MonoGame.net](http://www.monogame.net/)</span></span>

2. <span data-ttu-id="2f5be-136">Starten Sie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2f5be-136">Start Visual Studio 2017.</span></span>

3. <span data-ttu-id="2f5be-137">Wählen Sie **Datei->Neu->Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-137">Go to **File -> New -> Project**</span></span>

4. <span data-ttu-id="2f5be-138">Wählen Sie unter Visual C#-Projektvorlagen **MonoGame** und **MonoGame Windows10 Universal-Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-138">Under the Visual C# project templates, select **MonoGame** and **MonoGame Windows 10 Universal Project**</span></span>

5. <span data-ttu-id="2f5be-139">Benennen Sie Ihr Projekt mit „MonoGame2D“, und klicken Sie auf OK.</span><span class="sxs-lookup"><span data-stu-id="2f5be-139">Name your project “MonoGame2D" and select OK.</span></span> <span data-ttu-id="2f5be-140">Wenn das Projekt erstellt wurde, ist es möglicherweise voller Fehler, die aber nach der ersten Ausführung des Projekts beseitigt sein sollten. Dabei werden alle fehlenden NuGet-Pakete installiert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-140">With the project created, it will probably look like it is full of errors—these should go away after you run the project for the first time, and any missing NuGet packages are installed.</span></span>

6. <span data-ttu-id="2f5be-141">Stellen Sie sicher, dass **X86** und **lokaler Computer** als Zielplattform angegeben sind, und drücken Sie **F5**, um das leere Projekt zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-141">Make sure **x86** and **Local Machine** are set as the target platform, and press **F5** to build and run the empty project.</span></span> <span data-ttu-id="2f5be-142">Wenn Sie die oben beschriebenen Schritteausgeführt haben, sollte ein leeres blaues Fenster angezeigt werden, sobald das Projekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="2f5be-142">If you followed the steps above, you should see an empty blue window after the project finishes building.</span></span>

## <a name="method-overview"></a><span data-ttu-id="2f5be-143">Übersicht über die Methoden</span><span class="sxs-lookup"><span data-stu-id="2f5be-143">Method overview</span></span>
<span data-ttu-id="2f5be-144">Nachdem Sie das Projekt erstellt haben, öffnen Sie die **Game1.cs**-Datei aus dem **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-144">Now you’ve created the project, open the **Game1.cs** file from the **Solution Explorer**.</span></span> <span data-ttu-id="2f5be-145">Hier wird ein Großteil der Spiellogik abgelegt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-145">This is where the bulk of the game logic is going to go.</span></span> <span data-ttu-id="2f5be-146">Viele wichtige Methoden werden hier automatisch generiert, wenn Sie ein neues MonoGame-Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-146">Many crucial methods are automatically generated here when you create a new MonoGame project.</span></span> <span data-ttu-id="2f5be-147">Diese Methoden sollen hier kurz erläutert werden:</span><span class="sxs-lookup"><span data-stu-id="2f5be-147">Let’s quickly review them:</span></span>

<span data-ttu-id="2f5be-148">**public Game1()** – Der Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2f5be-148">**public Game1()** The constructor.</span></span> <span data-ttu-id="2f5be-149">Diese Methode wird in diesem Lernprogramm nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-149">We aren’t going to change this method at all for this tutorial.</span></span>

<span data-ttu-id="2f5be-150">**protected override void Initialize()** – Hier werden alle verwendeten Klassenvariablen initialisiert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-150">**protected override void Initialize()** Here we initialize any class variables that are used.</span></span> <span data-ttu-id="2f5be-151">Diese Methode wird zu Beginn des Spiels einmal aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-151">This method is called once at the start of the game.</span></span>

<span data-ttu-id="2f5be-152">**protected override void LoadContent()** – Diese Methode lädt Inhalt (z.B.</span><span class="sxs-lookup"><span data-stu-id="2f5be-152">**protected override void LoadContent()** This method loads content (eg.</span></span> <span data-ttu-id="2f5be-153">Audio, Texturen, Schriftarten) in den Arbeitsspeicher, bevor das Spiel gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-153">textures, audio, fonts) into memory before the game starts.</span></span> <span data-ttu-id="2f5be-154">Wie die Initialize-Methode wird sie beim Starten der App einmal aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-154">Like Initialize, it’s called once when the app starts.</span></span>

<span data-ttu-id="2f5be-155">**protected override void UnloadContent()** – Mit dieser Methode wird Inhalt entfernt, der nicht aus dem Inhalts-Manager stammt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-155">**protected override void UnloadContent()** This method is used to unload non content-manager content.</span></span> <span data-ttu-id="2f5be-156">Diese Methode wird hier nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="2f5be-156">We don’t use this one at all.</span></span>

<span data-ttu-id="2f5be-157">**protected override void Update(GameTime gameTIme)** – Diese Methode wird einmalig bei jedem Zyklus der Spieleschleife aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-157">**protected override void Update(GameTime gameTIme)** This method is called once for every cycle of the game loop.</span></span> <span data-ttu-id="2f5be-158">Hier wird der Status der im Spiel verwendeten Objekte oder Variablen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-158">Here we update the states of any object or variable used in the game.</span></span> <span data-ttu-id="2f5be-159">Dies betrifft auch Position, Geschwindigkeit oder Farbe eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="2f5be-159">This includes things like an object’s position, speed, or color.</span></span> <span data-ttu-id="2f5be-160">Außerdem werden hier Benutzereingaben behandelt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-160">This is also where use input is handled.</span></span> <span data-ttu-id="2f5be-161">Kurz gesagt, behandelt diese Methode alle Teile der Spiellogik mit Ausnahme des Zeichnens von Objekten auf den Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="2f5be-161">In short, this method handles every part of the game logic except drawing objects on screen.</span></span>
<span data-ttu-id="2f5be-162">**protected override void Draw(GameTime gameTime)** – Hier werden Objekte auf den Bildschirm gezeichnet. Dabei wird die Position verwendet, die von der Update-Methode angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="2f5be-162">**protected override void Draw(GameTime gameTime)** This is where objects are drawn on the screen, using the positions given by the Update method.</span></span>

## <a name="draw-a-sprite"></a><span data-ttu-id="2f5be-163">Zeichnen eines Sprite</span><span class="sxs-lookup"><span data-stu-id="2f5be-163">Draw a sprite</span></span>
<span data-ttu-id="2f5be-164">Sie haben das neue MonoGame-Projekt ausgeführt und sehen einen schöne blauen Himmel. Nun fügen wird Boden hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-164">So you’ve run your fresh MonoGame project and found a nice blue sky—let’s add some ground.</span></span>
<span data-ttu-id="2f5be-165">In MonoGame werden der App 2D-Zeichnungen in Form von „Sprites“ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-165">In MonoGame, 2D art is added to the app in the form of “sprites.”</span></span> <span data-ttu-id="2f5be-166">Ein Sprite ist eine Computergrafik, die als eine Einheit bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-166">A sprite is just a computer graphic that is manipulated as a single entity.</span></span> <span data-ttu-id="2f5be-167">Sprites können verschoben, skaliert, geformt, animiert und kombiniert werden, sodass alles erstellt werden kann, was Sie sich im 2D-Raum vorstellen können.</span><span class="sxs-lookup"><span data-stu-id="2f5be-167">Sprites can be moved, scaled, shaped, animated, and combined to create anything you can imagine in the 2D space.</span></span>

### <a name="1-download-a-texture"></a><span data-ttu-id="2f5be-168">1. Herunterladen von Textur</span><span class="sxs-lookup"><span data-stu-id="2f5be-168">1. Download a texture</span></span>
<span data-ttu-id="2f5be-169">Für unsere Zwecke soll das erste Sprite äußerst langweilig sein.</span><span class="sxs-lookup"><span data-stu-id="2f5be-169">For our purposes, this first sprite is going to be extremely boring.</span></span> <span data-ttu-id="2f5be-170">[Klicken Sie hier, um dieses einfache grüne Rechteck herunterzuladen](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/grass.png).</span><span class="sxs-lookup"><span data-stu-id="2f5be-170">[Click here to download this featureless green rectangle](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/grass.png).</span></span>

### <a name="2-add-the-texture-to-the-content-folder"></a><span data-ttu-id="2f5be-171">2. Hinzufügen der Textur zum Inhaltsordner</span><span class="sxs-lookup"><span data-stu-id="2f5be-171">2. Add the texture to the Content folder</span></span>
- <span data-ttu-id="2f5be-172">Öffnen Sie den **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-172">Open the **Solution Explorer**</span></span>
- <span data-ttu-id="2f5be-173">Klicken Sie mit der rechten Maustaste im Ordner **Content** auf **Content.mgcb**, und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-173">Right click **Content.mgcb** in the **Content** folder and select **Open With**.</span></span> <span data-ttu-id="2f5be-174">Wählen Sie aus dem Popupmenü **Monogame-Pipeline** aus, und wählen Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-174">From the popup menu select **Monogame Pipeline**, and select **OK**.</span></span>
- <span data-ttu-id="2f5be-175">Klicken Sie im neuen Fenster mit der rechten Maustaste auf das **Content**-Element, und wählen Sie **Hinzufügen -> Vorhandenes Element** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-175">In the new window, Right-Click the **Content** item and select **Add -> Existing Item**.</span></span>
- <span data-ttu-id="2f5be-176">Suchen Sie das grüne Rechteck im Datei-Browser, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-176">Locate and select the green rectangle in the file browser</span></span>
- <span data-ttu-id="2f5be-177">Nennen Sie das Element „grass.png“, und wählen Sie **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-177">Name the item “grass.png” and select **Add**.</span></span>

### <a name="3-add-class-variables"></a><span data-ttu-id="2f5be-178">3. Hinzufügen von Klassenvariablen</span><span class="sxs-lookup"><span data-stu-id="2f5be-178">3. Add class variables</span></span>
<span data-ttu-id="2f5be-179">Öffnen Sie zum Laden dieses Bilds als Sprite-Textur **Game1.cs**, und fügen Sie die folgenden Klassenvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-179">To load this image as a sprite texture, open **Game1.cs** and add the following class variables.</span></span>

```CSharp
const float SKYRATIO = 2f/3f;
float screenWidth;
float screenHeight;
Texture2D grass;
```

<span data-ttu-id="2f5be-180">Die Variable SKYRATIO gibt an, wie viel der Szene Himmel und wie viel Gras sein soll – in diesem Fall zwei Drittel zu einem Drittel.</span><span class="sxs-lookup"><span data-stu-id="2f5be-180">The SKYRATIO variable tells us how much of the scene we want to be sky versus grass—in this case, two-thirds.</span></span> <span data-ttu-id="2f5be-181">Die Variablen **screenWidth** und **screenHeight** überwachen die Größe des App-Fensters, und in **grass** speichern wir das grüne Rechteck.</span><span class="sxs-lookup"><span data-stu-id="2f5be-181">**screenWidth** and **screenHeight** will keep track of the app window size, while **grass** is where we’ll store our green rectangle.</span></span>

### <a name="4-initialize-class-variables-and-set-window-size"></a><span data-ttu-id="2f5be-182">4. Initialisieren der Klassenvariablen und Festlegen der Fenstergröße</span><span class="sxs-lookup"><span data-stu-id="2f5be-182">4. Initialize class variables and set window size</span></span>
<span data-ttu-id="2f5be-183">Die Variablen **screenWidth** und **screenHeight** müssen noch initialisiert werden. Fügen Sie daher der **Initialize**-Methode diesen Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-183">The **screenWidth** and **screenHeight** variables still need to be initialized, so add this code to the **Initialize** method:</span></span>

```CSharp
ApplicationView.PreferredLaunchWindowingMode = ApplicationViewWindowingMode.FullScreen;

screenHeight = (float)ApplicationView.GetForCurrentView().VisibleBounds.Height;
screenWidth = (float)ApplicationView.GetForCurrentView().VisibleBounds.Width;

this.IsMouseVisible = false;
```

<span data-ttu-id="2f5be-184">Wir haben nun die Höhe und Breite des Bildschirms und den Ansichtsmodus der App auf **Vollbild**festgelegt. Außerdem bleibt die Maus unsichtbar.</span><span class="sxs-lookup"><span data-stu-id="2f5be-184">Along with getting the screen’s height and width, we also set the app’s windowing mode to **Fullscreen**, and make the mouse invisible.</span></span>

### <a name="5-load-the-texture"></a><span data-ttu-id="2f5be-185">5. Laden der Textur</span><span class="sxs-lookup"><span data-stu-id="2f5be-185">5. Load the texture</span></span>
<span data-ttu-id="2f5be-186">Fügen Sie der **LoadContent**-Methode Folgendes hinzu, um die Textur in die grass-Variable zu laden:</span><span class="sxs-lookup"><span data-stu-id="2f5be-186">To load the texture into the grass variable, add the following to the **LoadContent** method:</span></span>

```CSharp
grass = Content.Load<Texture2D>("grass");
```

### <a name="6-draw-the-sprite"></a><span data-ttu-id="2f5be-187">6. Zeichnen des Sprite</span><span class="sxs-lookup"><span data-stu-id="2f5be-187">6. Draw the sprite</span></span>
<span data-ttu-id="2f5be-188">Fügen Sie der **Draw**-Methode die folgenden Zeilen hinzu, um das Rechteck zu zeichnen:</span><span class="sxs-lookup"><span data-stu-id="2f5be-188">To draw the rectangle, add the following lines to the **Draw** method:</span></span>

```CSharp
GraphicsDevice.Clear(Color.CornflowerBlue);
spriteBatch.Begin();
spriteBatch.Draw(grass, new Rectangle(0, (int)(screenHeight * SKYRATIO),
  (int)screenWidth, (int)screenHeight), Color.White);
spriteBatch.End();
```

<span data-ttu-id="2f5be-189">Hier verwenden wir die **spriteBatch.Draw**-Methode, um die angegebene Textur innerhalb der Ränder eines Rechteckobjekts zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="2f5be-189">Here we use the **spriteBatch.Draw** method to place the given texture within the borders of a Rectangle object.</span></span> <span data-ttu-id="2f5be-190">Ein **Rechteck** setzt sich aus den x- und y-Koordinaten seiner oberen linken und unteren rechte Ecke zusammen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-190">A **Rectangle** is defined by the x and y coordinates of its top left and bottom right corner.</span></span> <span data-ttu-id="2f5be-191">Mit den zuvor definierten Variablen **screenWidth**, **screenHeight** und **SKYRATIO** zeichnen wir die Textur des grünen Rechtecks entlang des unteren Drittels des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="2f5be-191">Using the **screenWidth**, **screenHeight**, and **SKYRATIO** variables we defined earlier, we draw the green rectangle texture across the bottom one-third of the screen.</span></span> <span data-ttu-id="2f5be-192">Wenn Sie das Programm ausführen, sehen Sie jetzt den blauen Hintergrund, der teilweise durch das grüne Rechteck abgedeckt ist.</span><span class="sxs-lookup"><span data-stu-id="2f5be-192">If you run the program now you should see the blue background from before, partially covered by the green rectangle.</span></span>

![Grünes Rechteck](images/monogame-tutorial-1.png)

## <a name="scale-to-high-dpi-screens"></a><span data-ttu-id="2f5be-194">Skalierung auf Bildschirme mit hohen DPI-Werten</span><span class="sxs-lookup"><span data-stu-id="2f5be-194">Scale to high DPI screens</span></span>
<span data-ttu-id="2f5be-195">Wenn Sie Visual Studio auf einem Monitor mit hoher Pixeldichte ausführen, wie beispielsweise auf einem Surface Pro oder Surface Studio, könnte es sein, dass das in den obigen Schritten erstellte grüne Rechteck das untere Drittel des Bildschirms nicht vollständig abdeckt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-195">If you’re running Visual Studio on a high pixel-density monitor, like those found on a Surface Pro or Surface Studio, you may find that the green rectangle from the steps above doesn’t quite cover the bottom third of the screen.</span></span> <span data-ttu-id="2f5be-196">Es ist wahrscheinlich nicht an der unteren linken Ecke des Bildschirms verankert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-196">It’s probably floating above the bottom-left corner of the screen.</span></span> <span data-ttu-id="2f5be-197">Um dieses Problem beheben und die Oberfläche des Spiels auf allen Geräten zu vereinheitlichen, müssen wir eine Methode erstellen, mit der bestimmte Werte in Bezug zur Pixeldichte des Bildschirms skaliert werden können:</span><span class="sxs-lookup"><span data-stu-id="2f5be-197">To fix this and unify the experience of our game across all devices, we will need to create a method that scales certain values relative to the screen’s pixel density:</span></span>

```CSharp
public float ScaleToHighDPI(float f)
{
  DisplayInformation d = DisplayInformation.GetForCurrentView();
  f *= (float)d.RawPixelsPerViewPixel;
  return f;
}
```

<span data-ttu-id="2f5be-198">Als Nächstes ersetzen Sie die Initialisierung der Variablen **screenHeight** und **screenWidth"** in der **Initialize**-Methode mit Folgendem:</span><span class="sxs-lookup"><span data-stu-id="2f5be-198">Next replace the initializations of **screenHeight** and **screenWidth** in the **Initialize** method with this:</span></span>

```CSharp
screenHeight = ScaleToHighDPI((float)ApplicationView.GetForCurrentView().VisibleBounds.Height);
screenWidth = ScaleToHighDPI((float)ApplicationView.GetForCurrentView().VisibleBounds.Width);
```

<span data-ttu-id="2f5be-199">Wenn Sie einen Bildschirm mit hohen DPI-Werten verwenden und die App jetzt ausführen, sollte das grüne Rechteck das untere Drittel wie gewünscht abdecken.</span><span class="sxs-lookup"><span data-stu-id="2f5be-199">If you’re using a high DPI screen and try to run the app now, you should see the green rectangle covering the bottom third of the screen as intended.</span></span>

## <a name="build-the-spriteclass"></a><span data-ttu-id="2f5be-200">Erstellen der SpriteClass</span><span class="sxs-lookup"><span data-stu-id="2f5be-200">Build the SpriteClass</span></span>
<span data-ttu-id="2f5be-201">Bevor wir mit der Animation von Sprites beginnen, werden wir eine neue Klasse namens „SpriteClass“ erstellen. Mit ihr können wir die Komplexität der Oberflächenebene der Sprite-Manipulation reduzieren.</span><span class="sxs-lookup"><span data-stu-id="2f5be-201">Before we start animating sprites, we’re going to make a new class called “SpriteClass,” which will let us reduce the surface-level complexity of sprite manipulation.</span></span>

### <a name="1-create-a-new-class"></a><span data-ttu-id="2f5be-202">1. Erstellen einer neuen Klasse</span><span class="sxs-lookup"><span data-stu-id="2f5be-202">1. Create a new class</span></span>
<span data-ttu-id="2f5be-203">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MonoGame2D (Universal Windows)**, und wählen Sie **Hinzufügen -> Klasse** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-203">In the **Solution Explorer**, right-click **MonoGame2D (Universal Windows)** and select **Add -> Class**.</span></span> <span data-ttu-id="2f5be-204">Nennen Sie die Klasse „SpriteClass.cs“, und wählen Sie dann **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-204">Name the class “SpriteClass.cs” then select **Add**.</span></span>

### <a name="2-add-class-variables"></a><span data-ttu-id="2f5be-205">2. Hinzufügen von Klassenvariablen</span><span class="sxs-lookup"><span data-stu-id="2f5be-205">2. Add class variables</span></span>
<span data-ttu-id="2f5be-206">Fügen Sie der Klasse, die Sie gerade erstellt haben, den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-206">Add this code to the class you just created:</span></span>

```CSharp
public Texture2D texture
{
  get;
}

public float x
{
  get;
  set;
}

public float y
{
  get;
  set;
}

public float angle
{
  get;
  set;
}

public float dX
{
  get;
  set;
}

public float dY
{
  get;
  set;
}

public float dA
{
  get;
  set;
}

public float scale
{
  get;
  set;
}
```

<span data-ttu-id="2f5be-207">Hier richten wir die Klassenvariablen ein, die wir zum Zeichnen und Animieren eines Sprite benötigen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-207">Here we set up the class variables we need to draw and animate a sprite.</span></span> <span data-ttu-id="2f5be-208">Die Variablen **x** und **y** stellen die aktuelle Position des Sprite auf der Ebene dar, während die Variable **angle** der aktuelle Winkel des Sprite in Grad ist (0 – aufrecht, 90 – um 90Grad im Uhrzeigersinn geneigt).</span><span class="sxs-lookup"><span data-stu-id="2f5be-208">The **x** and **y** variables represent the sprite’s current position on the plane, while the **angle** variable is the sprite’s current angle in degrees (0 being upright, 90 being tilted 90 degrees clockwise).</span></span> <span data-ttu-id="2f5be-209">Beachten Sie unbedingt, dass **x** und **y** für diese Klasse die Koordinaten des **Mittelpunkts** des Sprite darstellen (der Standardursprung befindet sich in der oberen linken Ecke).</span><span class="sxs-lookup"><span data-stu-id="2f5be-209">It’s important to note that, for this class, **x** and **y** represent the coordinates of the **center** of the sprite, (the default origin is the top-left corner).</span></span> <span data-ttu-id="2f5be-210">Damit wird es einfacher, Sprites zu drehen, da sie sich um einen beliebigen angegebenen Ursprung drehen. Durch die Drehung um den Mittelpunkt erhalten wir eine einheitliche Drehbewegung.</span><span class="sxs-lookup"><span data-stu-id="2f5be-210">This is makes rotating sprites easier, as they will rotate around whatever origin they are given, and rotating around the center gives us a uniform spinning motion.</span></span>

<span data-ttu-id="2f5be-211">Danach haben wir **dX**, **dY** und **dA**, die die Änderungsraten der Variablen **x**, **y** und **angle** pro Sekunde darstellen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-211">After this, we have **dX**, **dY**, and **dA**, which are the per-second rates of change for the **x**, **y**, and **angle** variables respectively.</span></span>

### <a name="3-create-a-constructor"></a><span data-ttu-id="2f5be-212">3. Erstellen eines Konstruktors</span><span class="sxs-lookup"><span data-stu-id="2f5be-212">3. Create a constructor</span></span>
<span data-ttu-id="2f5be-213">Beim Erstellen einer Instanz der **SpriteClass** statten wir den Konstruktor mit dem Grafikgerät aus **Game1.cs**, dem Projektordnerpfad zu der Textur und der gewünschten Skalierung der Textur in Bezug zu ihrer Originalgröße aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-213">When creating an instance of **SpriteClass**, we provide the constructor with the graphics device from **Game1.cs**, the path to the texture relative to the project folder, and the desired scale of the texture relative to its original size.</span></span> <span data-ttu-id="2f5be-214">Wir richten die übrigen Klassenvariablen in der Update-Methode ein, nachdem wir das Spiel gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-214">We’ll set the rest of the class variables after we start the game, in the update method.</span></span>

```CSharp
public SpriteClass (GraphicsDevice graphicsDevice, string textureName, float scale)
{
  this.scale = scale;
  if (texture == null)
  {
    using (var stream = TitleContainer.OpenStream(textureName))
    {
      texture = Texture2D.FromStream(graphicsDevice, stream);
    }
  }
}
```

### <a name="4-update-and-draw"></a><span data-ttu-id="2f5be-215">4. Aktualisieren und Zeichnen</span><span class="sxs-lookup"><span data-stu-id="2f5be-215">4. Update and Draw</span></span>
<span data-ttu-id="2f5be-216">Es gibt noch einige Methoden, die wir der SpriteClass-Deklaration hinzufügen müssen:</span><span class="sxs-lookup"><span data-stu-id="2f5be-216">There are still a couple of methods we need to add to the SpriteClass declaration:</span></span>

```CSharp
public void Update (float elapsedTime)
{
  this.x += this.dX * elapsedTime;
  this.y += this.dY * elapsedTime;
  this.angle += this.dA * elapsedTime;
}

public void Draw (SpriteBatch spriteBatch)
{
  Vector2 spritePosition = new Vector2(this.x, this.y);
  spriteBatch.Draw(texture, spritePosition, null, Color.White, this.angle, new Vector2(texture.Width/2, texture.Height/2), new Vector2(scale, scale), SpriteEffects.None, 0f);
}
```

<span data-ttu-id="2f5be-217">Die **Update** SpriteClass-Methode wird in der **Update**-Methode von Game1.cs aufgerufen. Mit ihr werden die Werte **x**, **y** und **angle** der Sprites auf der Grundlage ihrer jeweiligen Änderungsraten aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-217">The **Update** SpriteClass method is called in the **Update** method of Game1.cs, and is used to update the sprites **x**, **y**, and **angle** values based on their respective rates of change.</span></span>

<span data-ttu-id="2f5be-218">Die **Draw** -Methode wird in der **Draw**-Methode von Game1.cs aufgerufen. Mit ihr wird das Sprite im Fenster des Spiels gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2f5be-218">The **Draw** method is called in the **Draw** method of Game1.cs, and is used to draw the sprite in the game window.</span></span>

## <a name="user-input-and-animation"></a><span data-ttu-id="2f5be-219">Benutzereingaben und Animation</span><span class="sxs-lookup"><span data-stu-id="2f5be-219">User input and animation</span></span>
<span data-ttu-id="2f5be-220">Wir haben die SpriteClass erstellt und nutzen diese nun, um zwei neue Spielobjekte zu erstellen: zunächst einen Avatar, den der Spieler mit den Pfeiltasten und der LEERTASTE steuern kann.</span><span class="sxs-lookup"><span data-stu-id="2f5be-220">Now we have the SpriteClass built, we’ll use it to create two new game objects, The first is an avatar that the player can control with the arrow keys and the space bar.</span></span> <span data-ttu-id="2f5be-221">Das zweite Objekt ist ein Hindernis, dem der Spieler ausweichen muss.</span><span class="sxs-lookup"><span data-stu-id="2f5be-221">The second is an object that the player must avoid</span></span>

### <a name="1-get-the-textures"></a><span data-ttu-id="2f5be-222">1. Herunterladen von Texturen</span><span class="sxs-lookup"><span data-stu-id="2f5be-222">1. Get the textures</span></span>
<span data-ttu-id="2f5be-223">Für den Avatar des Spielers verwenden wir die Ninja-Katze von Microsoft, die auf einem riesigen Tyrannosaurus Rex reitet.</span><span class="sxs-lookup"><span data-stu-id="2f5be-223">For the player’s avatar we’re going to use Microsoft’s very own ninja cat, riding on his trusty t-rex.</span></span> <span data-ttu-id="2f5be-224">[Klicken Sie hier, um das Bild herunterzuladen](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/ninja-cat-dino.png).</span><span class="sxs-lookup"><span data-stu-id="2f5be-224">[Click here to download the image](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/ninja-cat-dino.png).</span></span>

<span data-ttu-id="2f5be-225">Nun geht es um das Hindernis, dem der Spieler ausweichen muss.</span><span class="sxs-lookup"><span data-stu-id="2f5be-225">Now for the obstacle that the player needs to avoid.</span></span> <span data-ttu-id="2f5be-226">Was hassen eine Ninja-Katze und ein fleischfressender Dinosaurier am meisten?</span><span class="sxs-lookup"><span data-stu-id="2f5be-226">What do ninja-cats and carnivorous dinosaurs both hate more than anything?</span></span> <span data-ttu-id="2f5be-227">Gemüse!</span><span class="sxs-lookup"><span data-stu-id="2f5be-227">Eating their veggies!</span></span> <span data-ttu-id="2f5be-228">[Klicken Sie hier, um das Bild herunterzuladen](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/broccoli.png).</span><span class="sxs-lookup"><span data-stu-id="2f5be-228">[Click here to download the image](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/broccoli.png).</span></span>

<span data-ttu-id="2f5be-229">Genauso wie zuvor bei dem grünen Rechteck fügen Sie diese Bilder nun über die **MonoGame-Pipeline** in **Content.mgcb** hinzu. Nennen Sie sie „ninja-cat-dino.png“ und „broccoli.png“.</span><span class="sxs-lookup"><span data-stu-id="2f5be-229">Just as before with the green rectangle, add these images to **Content.mgcb** via the **MonoGame Pipeline**, naming them “ninja-cat-dino.png” and “broccoli.png” respectively.</span></span>

### <a name="2-add-class-variables"></a><span data-ttu-id="2f5be-230">2. Hinzufügen von Klassenvariablen</span><span class="sxs-lookup"><span data-stu-id="2f5be-230">2. Add class variables</span></span>
<span data-ttu-id="2f5be-231">Fügen Sie folgenden Code zur Liste der Klassenvariablen in **Game1.cs** hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-231">Add the following code to the list of class variables in **Game1.cs**:</span></span>

```CSharp
SpriteClass dino;
SpriteClass broccoli;

bool spaceDown;
bool gameStarted;

float broccoliSpeedMultiplier;
float gravitySpeed;
float dinoSpeedX;
float dinoJumpY;
float score;

Random random;
```

<span data-ttu-id="2f5be-232">**dino** und **broccoli** sind unsere SpriteClass-Variablen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-232">**dino** and **broccoli** are our SpriteClass variables.</span></span> <span data-ttu-id="2f5be-233">**dino** stellt den Avatar des Spielers dar, während **broccoli** das Brokkoli-Hindernis ist.</span><span class="sxs-lookup"><span data-stu-id="2f5be-233">**dino** will hold the player avatar, while **broccoli** holds the broccoli obstacle.</span></span>

<span data-ttu-id="2f5be-234">**spaceDown** überwacht, ob die LEERTASTE gehalten oder nach unten gedrückt und losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-234">**spaceDown** keeps track of whether the spacebar is being held down as opposed to pressed and released.</span></span>

<span data-ttu-id="2f5be-235">**gameStarted** gibt an, ob der Benutzer das Spiel zum ersten Mal gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="2f5be-235">**gameStarted** tells us whether the user has started the game for the first time.</span></span>

<span data-ttu-id="2f5be-236">**broccoliSpeedMultiplier** bestimmt, wie schnell das Brokkoli-Hindernis sich über den Bildschirm bewegt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-236">**broccoliSpeedMultiplier** determines how fast the broccoli obstacle moves across the screen.</span></span>

<span data-ttu-id="2f5be-237">**gravitySpeed** bestimmt, wie schnell der Avatar des Spielers nach einem Sprung wieder nach unten beschleunigt wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-237">**gravitySpeed** determines how fast the player avatar accelerates downward after a jump.</span></span>

<span data-ttu-id="2f5be-238">**dinoSpeedX** und **dinoJumpY** bestimmen, wie schnell der Avatar des Spielers sich bewegt und springt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-238">**dinoSpeedX** and **dinoJumpY** determine how fast the player avatar moves and jumps.</span></span>
<span data-ttu-id="2f5be-239">score verfolgt, wie vielen Hindernissen der Spieler erfolgreich ausgewichen ist.</span><span class="sxs-lookup"><span data-stu-id="2f5be-239">score tracks how many obstacles the player has successfully dodged.</span></span>

<span data-ttu-id="2f5be-240">Schließlich wird mit **random** dem Verhalten des Brokkoli-Hindernisses ein Grad an Zufälligkeit hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-240">Finally, **random** will be used to add some randomness to the behavior of the broccoli obstacle.</span></span>

### <a name="3-initialize-variables"></a><span data-ttu-id="2f5be-241">3. Initialisieren von Variablen</span><span class="sxs-lookup"><span data-stu-id="2f5be-241">3. Initialize variables</span></span>
<span data-ttu-id="2f5be-242">Als Nächstes müssen diese Variablen initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-242">Next we need to initialize these variables.</span></span> <span data-ttu-id="2f5be-243">Fügen Sie in der Initialize-Methode den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-243">Add the following code to the Initialize method:</span></span>

```CSharp
broccoliSpeedMultiplier = 0.5f;
spaceDown = false;
gameStarted = false;
score = 0;
random = new Random();
dinoSpeedX = ScaleToHighDPI(1000f);
dinoJumpY = ScaleToHighDPI(-1200f);
gravitySpeed = ScaleToHighDPI(30f);
```

<span data-ttu-id="2f5be-244">Beachten Sie, dass die letzten drei Variablen für Geräte mit hohen DPI-Werten skaliert werden müssen, da sie eine Änderungsrate in Pixel angegeben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-244">Note that the last three variables need to be scaled for high DPI devices, because they specify a rate of change in pixels.</span></span>

### <a name="4-construct-spriteclasses"></a><span data-ttu-id="2f5be-245">4. Erstellen von SpriteClasses</span><span class="sxs-lookup"><span data-stu-id="2f5be-245">4. Construct SpriteClasses</span></span>
<span data-ttu-id="2f5be-246">Wir erstellen SpriteClass-Objekte in der **LoadContent**-Methode.</span><span class="sxs-lookup"><span data-stu-id="2f5be-246">We will construct SpriteClass objects in the **LoadContent** method.</span></span> <span data-ttu-id="2f5be-247">Fügen Sie dem vorhandenen Code diesen Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-247">Add this code to what you already have there:</span></span>

```CSharp
dino = new SpriteClass(GraphicsDevice, "Content/ninja-cat-dino.png", ScaleToHighDPI(1f));
broccoli = new SpriteClass(GraphicsDevice, "Content/broccoli.png", ScaleToHighDPI(0.2f));
```

<span data-ttu-id="2f5be-248">Das Brokkoli-Bild ist viel größer, als es im Spiel angezeigt werden soll. Daher müssen wir es auf das 0,2-Fache seiner ursprünglichen Größe skalieren.</span><span class="sxs-lookup"><span data-stu-id="2f5be-248">The broccoli image is quite a lot larger than we want it to appear in the game, so we’ll scale it down to 0.2 times its original size.</span></span>

### <a name="5-program-obstacle-behavior"></a><span data-ttu-id="2f5be-249">5. Programmierung des Verhaltens des Hindernisses</span><span class="sxs-lookup"><span data-stu-id="2f5be-249">5. Program obstacle behavior</span></span>
<span data-ttu-id="2f5be-250">Der Brokkoli soll über den Bildschirm hinausreichen und in Richtung des Avatars des Spielers wandern, der dem Hindernis ausweichen muss.</span><span class="sxs-lookup"><span data-stu-id="2f5be-250">We want the broccoli to spawn somewhere offscreen, and head in the direction of the player’s avatar, so they need to dodge it.</span></span> <span data-ttu-id="2f5be-251">Dazu fügen Sie der **Game1.cs**-Klasse diese Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-251">To accomplish they, add this method to the **Game1.cs** class:</span></span>

```CSharp
public void SpawnBroccoli()
{
  int direction = random.Next(1, 5);
  switch (direction)
  {
    case 1:
      broccoli.x = -100;
      broccoli.y = random.Next(0, (int)screenHeight);
      break;
    case 2:
      broccoli.y = -100;
      broccoli.x = random.Next(0, (int)screenWidth);
      break;
    case 3:
      broccoli.x = screenWidth + 100;
      broccoli.y = random.Next(0, (int)screenHeight);
      break;
    case 4:
      broccoli.y = screenHeight + 100;
      broccoli.x = random.Next(0, (int)screenWidth);
      break;
  }

  if (score % 5 == 0) broccoliSpeedMultiplier += 0.2f;

  broccoli.dX = (dino.x - broccoli.x) * broccoliSpeedMultiplier;
  broccoli.dY = (dino.y - broccoli.y) * broccoliSpeedMultiplier;
  broccoli.dA = 7f;
}
```

<span data-ttu-id="2f5be-252">Der erste Teil der Methode bestimmt, von welchem Punkt außerhalb des Bildschirms das Brokkoli-Objekt ausgehen soll. Dazu werden zwei Zufallszahlen erzeugt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-252">The first part of the of the method determines what off screen point the broccoli object will spawn from, using two random numbers.</span></span>

<span data-ttu-id="2f5be-253">Im zweiten Teil wird bestimmt, wie schnell der Brokkoli sich bewegt, wobei die Geschwindigkeit vom aktuellen Spielstand abhängt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-253">The second part determines how fast the broccoli will travel, which is determined by the current score.</span></span> <span data-ttu-id="2f5be-254">Wenn der Spieler fünf Brokkoli ausgewichen ist, erhöht sich die Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="2f5be-254">It will get faster for every five broccoli the player successfully dodges.</span></span>

<span data-ttu-id="2f5be-255">Der dritte Teil legt die Richtung der Bewegung des Brokkoli-Sprite fest.</span><span class="sxs-lookup"><span data-stu-id="2f5be-255">The third part sets the direction of the broccoli sprite’s motion.</span></span> <span data-ttu-id="2f5be-256">Wenn der Brokkoli auftaucht, bewegt er sich in Richtung des Spielers-Avatars (Dino).</span><span class="sxs-lookup"><span data-stu-id="2f5be-256">It heads in the direction of the player avatar (dino) when the broccoli is spawned.</span></span> <span data-ttu-id="2f5be-257">Er erhält außerdem den **dA**-Wert 7f, was bewirkt, dass der Brokkoli bei der Jagd nach dem Spieler durch die Luft wirbelt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-257">We also give it a **dA** value of 7f, which will cause the broccoli to spin through the air as it chases the player.</span></span>

### <a name="6-program-game-starting-state"></a><span data-ttu-id="2f5be-258">6. Programmieren des Anfangszustands des Spiels</span><span class="sxs-lookup"><span data-stu-id="2f5be-258">6. Program game starting state</span></span>
<span data-ttu-id="2f5be-259">Bevor wir mit der Tastatureingabe fortfahren, müssen wir eine Methode angeben, mit der der Anfangszustand der beiden von uns erstellten Objekte festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-259">Before we can move on to handling keyboard input, we need a method that sets the initial game state of the two objects we’ve created.</span></span> <span data-ttu-id="2f5be-260">Das Spiel soll nicht sofort gestartet werden, wenn die App ausgeführt wird. Vielmehr soll der Benutzer es manuell starten, indem er die LEERTASTE drückt.</span><span class="sxs-lookup"><span data-stu-id="2f5be-260">Rather than the game starting as soon as the app runs, we want the user to start it manually, by pressing the spacebar.</span></span> <span data-ttu-id="2f5be-261">Fügen Sie den folgenden Code hinzu, mit dem der ursprüngliche Zustand der animierten Objekte festgelegt und der Punktestand zurückgesetzt wird:</span><span class="sxs-lookup"><span data-stu-id="2f5be-261">Add the following code, which sets the initial state of the animated objects, and resets the score:</span></span>

```CSharp
public void StartGame()
{
  dino.x = screenWidth / 2;
  dino.y = screenHeight * SKYRATIO;
  broccoliSpeedMultiplier = 0.5f;
  SpawnBroccoli();  
  score = 0;
}
```

### <a name="7-handle-keyboard-input"></a><span data-ttu-id="2f5be-262">7. Behandeln von Tastatureingaben</span><span class="sxs-lookup"><span data-stu-id="2f5be-262">7. Handle keyboard input</span></span>
<span data-ttu-id="2f5be-263">Als Nächstes benötigen wir eine neue Methode zum Behandeln von Benutzereingaben über die Tastatur.</span><span class="sxs-lookup"><span data-stu-id="2f5be-263">Next we need a new method to handle user input via the keyboard.</span></span> <span data-ttu-id="2f5be-264">Fügen Sie diese Methode zu **Game1.cs** hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-264">Add this this method to **Game1.cs**:</span></span>

```CSharp
void KeyboardHandler()
{
  KeyboardState state = Keyboard.GetState();

  // Quit the game if Escape is pressed.
  if (state.IsKeyDown(Keys.Escape))
  {
    Exit();
  }

  // Start the game if Space is pressed.
  if (!gameStarted)
  {
    if (state.IsKeyDown(Keys.Space))
    {
      StartGame();
      gameStarted = true;
      spaceDown = true;
      gameOver = false;
    }
    return;
  }            
  // Jump if Space is pressed
  if (state.IsKeyDown(Keys.Space) || state.IsKeyDown(Keys.Up))
  {
    // Jump if the Space is pressed but not held and the dino is on the floor
    if (!spaceDown && dino.y >= screenHeight * SKYRATIO - 1) dino.dY = dinoJumpY;

    spaceDown = true;
  }
  else spaceDown = false;

  // Handle left and right
  if (state.IsKeyDown(Keys.Left)) dino.dX = dinoSpeedX * -1;

  else if (state.IsKeyDown(Keys.Right)) dino.dX = dinoSpeedX;
  else dino.dX = 0;
}
```

<span data-ttu-id="2f5be-265">Wir sehen oben eine Reihe von vier „Wenn“-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="2f5be-265">Above we have a series of four if-statements:</span></span>

<span data-ttu-id="2f5be-266">Die erste beendet das Spiel, wenn die **Escape**-Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-266">The first quits the game if the **Escape** key is pressed.</span></span>

<span data-ttu-id="2f5be-267">Die zweite startet das Spiel, wenn die **LEERTASTE** gedrückt wird, und das Spiel ist noch nicht gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="2f5be-267">The second starts the game if the **Space** key is pressed, and the game is not already started.</span></span>

<span data-ttu-id="2f5be-268">Die dritte lässt den Dino-Avatar springen, wenn die **LEERTASTE** gedrückt wird. Dazu wird die **dY**-Eigenschaft geändert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-268">The third makes the dino avatar jump if **Space** is pressed, by changing its **dY** property.</span></span> <span data-ttu-id="2f5be-269">Beachten Sie, dass der Spieler nur springen kann, wenn er auf dem „Boden“ ist (dino.y = screenHeight \* SKYRATIO). Außerdem springt er nur, wenn LEERTASTE einmal gedrückt und nicht gehalten wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-269">Note that the player cannot jump unless they are on the “ground” (dino.y = screenHeight \* SKYRATIO), and will also not jump if the space key is being help down rather than pressed once.</span></span> <span data-ttu-id="2f5be-270">Dies verhindert, dass der Dino nach Spielstart sofort springt, weil die LEERTASTE auch zum Starten des Spiels gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-270">This stops the dino from jumping as soon as the game is started, piggybacking on the same keypress that starts the game.</span></span>

<span data-ttu-id="2f5be-271">Mit der letzten „Wenn“-Anweisung wird überprüft, ob die Pfeile nach links oder rechts gedrückt werden. Wenn dies der Fall ist, wird die **dX** -Eigenschaft des Dinos entsprechend geändert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-271">Finally, the last if/else clause checks if the left or right directional arrows are being pressed, and if so changes the dino’s **dX** property accordingly.</span></span>

<span data-ttu-id="2f5be-272">**Aufgabe:** Schaffen Sie es, dass die obige Tastatureingabemethode mit dem WASD-Eingabeschema genauso wie mit den Pfeiltasten funktioniert?</span><span class="sxs-lookup"><span data-stu-id="2f5be-272">**Challenge:** can you make the keyboard handling method above work with the WASD input scheme as well as the arrow keys?</span></span>

### <a name="8-add-logic-to-the-update-method"></a><span data-ttu-id="2f5be-273">8. Hinzufügen von Logik zur Update-Methode</span><span class="sxs-lookup"><span data-stu-id="2f5be-273">8. Add logic to the Update method</span></span>
<span data-ttu-id="2f5be-274">Als Nächstes müssen wir für alle diese Teile Logik zur **Update**-Methode in **Game1.cs** hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="2f5be-274">Next we need to add logic for all of these parts to the **Update** method in **Game1.cs**:</span></span>

```CSharp
float elapsedTime = (float)gameTime.ElapsedGameTime.TotalSeconds;
KeyboardHandler(); // Handle keyboard input
// Update animated SpriteClass objects based on their current rates of change
dino.Update(elapsedTime);
broccoli.Update(elapsedTime);

// Accelerate the dino downward each frame to simulate gravity.
dino.dY += gravitySpeed;

// Set game floor so the player does not fall through it
if (dino.y > screenHeight * SKYRATIO)
{
  dino.dY = 0;
  dino.y = screenHeight * SKYRATIO;
}

// Set game edges to prevent the player from moving offscreen
if (dino.x > screenWidth - dino.texture.Width/2)
{
  dino.x = screenWidth - dino.texture.Width/2;
  dino.dX = 0;
}
if (dino.x < 0 + dino.texture.Width/2)
{
  dino.x = 0 + dino.texture.Width/2;
  dino.dX = 0;
}

// If the broccoli goes offscreen, spawn a new one and iterate the score
if (broccoli.y > screenHeight+100 || broccoli.y < -100 || broccoli.x > screenWidth+100 || broccoli.x < -100)
{
  SpawnBroccoli();
  score++;
}
```

### <a name="9-draw-spriteclass-objects"></a><span data-ttu-id="2f5be-275">9. Zeichnen von SpriteClass-Objekten</span><span class="sxs-lookup"><span data-stu-id="2f5be-275">9. Draw SpriteClass objects</span></span>
<span data-ttu-id="2f5be-276">Fügen Sie zum Schluss der **Draw**-Methode in **Game1.cs** direkt nach dem letzten Aufruf von **spriteBatch.Draw** den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-276">Finally, add the following code to the **Draw** method of **Game1.cs**, just after the last call of **spriteBatch.Draw**:</span></span>

```CSharp
broccoli.Draw(spriteBatch);
dino.Draw(spriteBatch);
```

<span data-ttu-id="2f5be-277">In MonoGame werden neue Aufrufe von **spriteBatch.Draw** über alle vorherigen Aufrufe gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2f5be-277">In MonoGame, new calls of **spriteBatch.Draw** will draw over any prior calls.</span></span> <span data-ttu-id="2f5be-278">Dies bedeutet, dass das Brokkoli- und das Dino-Sprite über das vorhandene Gras-Sprite gezeichnet werden, sodass sie unabhängig von ihrer Position niemals dahinter verborgen werden können.</span><span class="sxs-lookup"><span data-stu-id="2f5be-278">This means that both the broccoli and the dino sprite will be drawn over the  existing grass sprite, so they can never be hidden behind it regardless of their position.</span></span>

<span data-ttu-id="2f5be-279">Führen Sie das Spiel nun aus, und bewegen Sie den Dino mit den Pfeiltasten und der LEERTASTE.</span><span class="sxs-lookup"><span data-stu-id="2f5be-279">Try running the game now, and moving around the dino with the arrow keys and the spacebar.</span></span> <span data-ttu-id="2f5be-280">Wenn Sie die oben beschriebenen Schritteausgeführt haben, sollten Sie Ihren Avatar innerhalb des Spielfensters bewegen können, und der Brokkoli sollte immer schneller werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-280">If you followed the steps above, you should be able to make your avatar move within the game window, and the broccoli should at an ever-increasing speed.</span></span>

![Spieler-Avatar und Hindernis](images/monogame-tutorial-2.png)

## <a name="render-text-with-spritefont"></a><span data-ttu-id="2f5be-282">Rendern von Text mit SpriteFont</span><span class="sxs-lookup"><span data-stu-id="2f5be-282">Render text with SpriteFont</span></span>
<span data-ttu-id="2f5be-283">Mit dem obigen Code überwachen wir im Hintergrund die Punktzahl des Spielers, aber wir teilen dem Spieler das Ergebnis nicht mit.</span><span class="sxs-lookup"><span data-stu-id="2f5be-283">Using the code above, we keep track of the player’s score behind the scenes, but we don’t actually tell the player what it is.</span></span> <span data-ttu-id="2f5be-284">Außerdem gibt es beim Start der App eine wenig intuitive Einführung: Der Spieler sieht ein blaues und ein grünes Fenster, weiß aber nicht, dass er die LEERTASTE drücken muss, damit es losgeht.</span><span class="sxs-lookup"><span data-stu-id="2f5be-284">We also have a fairly unintuitive introduction when the app starts up—the player sees a blue and green window, but has no way of knowing they need to press Space to get things rolling.</span></span>

<span data-ttu-id="2f5be-285">Zur Behebung dieser Probleme nutzen wir eine neue Art von MonoGame-Objekt mit dem Namen **SpriteFonts**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-285">To fix both these problems, we’re going to use a new kind of MonoGame object called **SpriteFonts**.</span></span>

### <a name="1-create-spritefont-description-files"></a><span data-ttu-id="2f5be-286">1. Erstellen von Beschreibungsdateien mit SpriteFont</span><span class="sxs-lookup"><span data-stu-id="2f5be-286">1. Create SpriteFont description files</span></span>
<span data-ttu-id="2f5be-287">Suchen Sie im **Projektmappen-Explorer** den Ordner **Content**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-287">In the **Solution Explorer** find the **Content** folder.</span></span> <span data-ttu-id="2f5be-288">Klicken Sie in diesem Ordner mit der rechten Maustaste auf die Datei **Content.mgcb**, und wählen Sie **Öffnen mit** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-288">In this folder, Right-Click the **Content.mgcb** file and select **Open With**.</span></span> <span data-ttu-id="2f5be-289">Wählen Sie aus dem Popupmenü **MonoGame-Pipeline** aus, und drücken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-289">From the popup menu select **MonoGame Pipeline**, then press **OK**.</span></span> <span data-ttu-id="2f5be-290">Klicken Sie im neuen Fenster mit der rechten Maustaste auf das **Content**-Element, und wählen Sie **Hinzufügen -> Neues Element** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-290">In the new window, Right-Click the **Content** item and select **Add -> New Item**.</span></span> <span data-ttu-id="2f5be-291">Wählen Sie **SpriteFont-Beschreibung** aus, benennen Sie sie mit „Score“, und drücken Sie **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f5be-291">Select **SpriteFont Description**, name it “Score” and press **OK**.</span></span> <span data-ttu-id="2f5be-292">Dann fügen Sie auf die gleiche Weise eine andere SpriteFont-Beschreibung mit dem Namen „GameState“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-292">Then, add another SpriteFont description named “GameState” using the same procedure.</span></span>

### <a name="2-edit-descriptions"></a><span data-ttu-id="2f5be-293">2. Bearbeiten von Beschreibungen</span><span class="sxs-lookup"><span data-stu-id="2f5be-293">2. Edit descriptions</span></span>
<span data-ttu-id="2f5be-294">Klicken Sie mit der rechten Maustaste auf den **Content**-Ordner in der **MonoGame-Pipeline**, und wählen Sie **Dateispeicherort öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="2f5be-294">Right click the **Content** folder in the **MonoGame Pipeline** and select **Open File Location**.</span></span> <span data-ttu-id="2f5be-295">Ein Ordner mit der soeben erstellten SpriteFont-Beschreibung sollte angezeigt werden. Er sollte zudem alle Bilder enthalten, die Sie dem Content-Ordner bisher hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-295">You should see a folder with the SpriteFont description files that you just created, as well as any images you’ve added to the Content folder so far.</span></span> <span data-ttu-id="2f5be-296">Sie können jetzt das Fenster „MonoGame-Pipeline“ speichern und schließen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-296">You can now close and save the MonoGame Pipeline window.</span></span> <span data-ttu-id="2f5be-297">Öffnen Sie aus dem **Datei-Explorer** heraus beide Beschreibungsdateien in einem Text-Editor (Visual Studio, Notepad++, Atom usw.).</span><span class="sxs-lookup"><span data-stu-id="2f5be-297">From the **File Explorer** open both description files in a text editor (Visual Studio, NotePad++, Atom, etc).</span></span>

<span data-ttu-id="2f5be-298">Jede Beschreibung enthält eine Reihe von Werten, die die SpriteFont beschreiben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-298">Each description contains a number of values that describe the SpriteFont.</span></span> <span data-ttu-id="2f5be-299">Wir werden einige Änderungen vornehmen:</span><span class="sxs-lookup"><span data-stu-id="2f5be-299">We're going to make a few changes:</span></span>

<span data-ttu-id="2f5be-300">Ändern Sie in **Score.spritefont** den **<Size>**-Wert von 12 auf 36.</span><span class="sxs-lookup"><span data-stu-id="2f5be-300">In **Score.spritefont**, change the **<Size>** value from 12 to 36.</span></span>

<span data-ttu-id="2f5be-301">Ändern Sie in **GameState.spritefont** den **<Size>**-Wert von 12 auf 72 und den **<FontName>**-Wert von Arial in Agency.</span><span class="sxs-lookup"><span data-stu-id="2f5be-301">In **GameState.spritefont**, change the **<Size>** value from 12 to 72, and the **<FontName>** value from Arial to Agency.</span></span> <span data-ttu-id="2f5be-302">Agency ist eine weitere Schriftart, die standardmäßig auf Windows10-Computern bereitgestellt wird und dem Begrüßungsbildschirm mehr Flair verleiht.</span><span class="sxs-lookup"><span data-stu-id="2f5be-302">Agency is another font that comes standard with Windows 10 machines, and will add some flair to our intro screen.</span></span>

### <a name="3-load-spritefonts"></a><span data-ttu-id="2f5be-303">3. Laden von SpriteFonts</span><span class="sxs-lookup"><span data-stu-id="2f5be-303">3. Load SpriteFonts</span></span>
<span data-ttu-id="2f5be-304">Zurück in Visual Studio fügen wir zuerst eine neue Textur für den Begrüßungsbildschirm hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-304">Back in Visual Studio, we’re first going to add a new texture for the intro splash screen.</span></span> <span data-ttu-id="2f5be-305">[Klicken Sie hier, um das Bild herunterzuladen](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/start-splash.png).</span><span class="sxs-lookup"><span data-stu-id="2f5be-305">[Click here to download the image](https://github.com/Microsoft/Windows-appsample-get-started-mg2d/blob/master/MonoGame2D/Content/start-splash.png).</span></span>

<span data-ttu-id="2f5be-306">Fügen Sie wie zuvor die Textur zum Projekt hinzu, indem Sie mit der rechten Maustaste auf „Content“ klicken und **Hinzufügen -> Vorhandenes Element** auswählen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-306">As before, add the texture to the project by right-clicking the Content and selecting **Add -> Existing Item**.</span></span> <span data-ttu-id="2f5be-307">Nennen Sie das neue Element „start-splash.png“.</span><span class="sxs-lookup"><span data-stu-id="2f5be-307">Name the new item “start-splash.png”.</span></span>

<span data-ttu-id="2f5be-308">Als Nächstes fügen Sie die folgenden Klassenvariablen in **Game1.cs** hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-308">Next, add the following class variables to **Game1.cs**:</span></span>

```CSharp
Texture2D startGameSplash;
SpriteFont scoreFont;
SpriteFont stateFont;
```

<span data-ttu-id="2f5be-309">Dann fügen Sie der **LoadContent**-Methode die folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-309">Then add these lines to the **LoadContent** method:</span></span>

```CSharp
startGameSplash = Content.Load<Texture2D>("start-splash");
scoreFont = Content.Load<SpriteFont>("Score");
stateFont = Content.Load<SpriteFont>("GameState");
```

### <a name="4-draw-the-score"></a><span data-ttu-id="2f5be-310">4. Zeichnen der Punktezahl</span><span class="sxs-lookup"><span data-stu-id="2f5be-310">4. Draw the score</span></span>
<span data-ttu-id="2f5be-311">Wechseln Sie in die **Draw**-Methode von **Game1.cs**, und fügen Sie unmittelbar vor **spriteBatch.End();** den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-311">Go to the **Draw** method of **Game1.cs** and add the following code just before **spriteBatch.End();**</span></span>

```CSharp
spriteBatch.DrawString(scoreFont, score.ToString(),
new Vector2(screenWidth - 100, 50), Color.Black);
```

<span data-ttu-id="2f5be-312">Der obige Code verwendet die Sprite-Beschreibung, die wir erstellt haben (Arial Größe 36), um den Punktestand des Spielers in der Nähe der oberen rechten Ecke des Bildschirms zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-312">The code above uses the sprite description we created (Arial Size 36) to draw the player’s current score near the top right corner of the screen.</span></span>

### <a name="5-draw-horizontally-centered-text"></a><span data-ttu-id="2f5be-313">5. Zeichnen von horizontal zentriertem Text</span><span class="sxs-lookup"><span data-stu-id="2f5be-313">5. Draw horizontally centered text</span></span>
<span data-ttu-id="2f5be-314">Wenn Sie ein Spiel erstellen, möchten Sie häufig Text zeichnen, die entweder horizontal oder vertikal zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="2f5be-314">When making a game, you will often want to draw text that is centered, either horizontally or vertically.</span></span> <span data-ttu-id="2f5be-315">Wenn Sie den Einführungstext horizontal zentrieren möchten, fügen Sie der **Draw**-Methode unmittelbar vor dem **spriteBatch.End();** diesen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-315">To horizontally center the introductory text, add this code to the **Draw** method just before **spriteBatch.End();**</span></span>

```CSharp
if (!gameStarted)
{
  // Fill the screen with black before the game starts
  spriteBatch.Draw(startGameSplash, new Rectangle(0, 0,
  (int)screenWidth, (int)screenHeight), Color.White);

  String title = "VEGGIE JUMP";
  String pressSpace = "Press Space to start";

  // Measure the size of text in the given font
  Vector2 titleSize = stateFont.MeasureString(title);
  Vector2 pressSpaceSize = stateFont.MeasureString(pressSpace);

  // Draw the text horizontally centered
  spriteBatch.DrawString(stateFont, title,
  new Vector2(screenWidth / 2 - titleSize.X / 2, screenHeight / 3),
  Color.ForestGreen);
  spriteBatch.DrawString(stateFont, pressSpace,
  new Vector2(screenWidth / 2 - pressSpaceSize.X / 2,
  screenHeight / 2), Color.White);
  }
```

<span data-ttu-id="2f5be-316">Zunächst erstellen wir zwei Zeichenfolgen, eine für jede zu zeichnende Textzeile.</span><span class="sxs-lookup"><span data-stu-id="2f5be-316">First we create two Strings, one for each line of text we want to draw.</span></span> <span data-ttu-id="2f5be-317">Als Nächstes messen wird die Breite und Höhe jeder Zeile beim Drucken mit der **SpriteFont.MeasureString(String)**-Methode.</span><span class="sxs-lookup"><span data-stu-id="2f5be-317">Next, we measure the width and height of each line when printed, using the **SpriteFont.MeasureString(String)** method.</span></span> <span data-ttu-id="2f5be-318">Dadurch können wir die Größe als **Vector2**-Objekt mit der **X**-Eigenschaft für die Breite und der **Y**-Eigenschaft für die Höhe angeben.</span><span class="sxs-lookup"><span data-stu-id="2f5be-318">This gives us the size as a **Vector2** object, with the **X** property containing its width, and **Y** its height.</span></span>

<span data-ttu-id="2f5be-319">Zuletzt zeichnen wir die einzelnen Zeilen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-319">Finally, we draw each line.</span></span> <span data-ttu-id="2f5be-320">Wenn Sie den Text horizontal zentrieren möchten, legen Sie den **X**-Wert des Positionsvektors auf den gleichen Wert wie **screenWidth / 2 - textSize.X / 2** fest.</span><span class="sxs-lookup"><span data-stu-id="2f5be-320">To center the text horizontally, we make the **X** value of it’s position vector equal to **screenWidth / 2 - textSize.X / 2**</span></span>

<span data-ttu-id="2f5be-321">**Aufgabe:** Was müssen Sie tun, damit der obige Text vertikal und horizontal zentriert wird?</span><span class="sxs-lookup"><span data-stu-id="2f5be-321">**Challenge:** how would you change the procedure above to center the text vertically as well as horizontally?</span></span>

<span data-ttu-id="2f5be-322">Starten Sie das Spiel.</span><span class="sxs-lookup"><span data-stu-id="2f5be-322">Try running the game.</span></span> <span data-ttu-id="2f5be-323">Sehen Sie den Begrüßungsbildschirm?</span><span class="sxs-lookup"><span data-stu-id="2f5be-323">Do you see the intro splash screen?</span></span> <span data-ttu-id="2f5be-324">Wird die Punktezahl mit jedem Ausweichen vor einem Brokkoli erhöht?</span><span class="sxs-lookup"><span data-stu-id="2f5be-324">Does the score count up each time the broccoli respawns?</span></span>

![Begrüßungsbildschirm](images/monogame-tutorial-3.png)

## <a name="collision-detection"></a><span data-ttu-id="2f5be-326">Erkennung von Kollisionen</span><span class="sxs-lookup"><span data-stu-id="2f5be-326">Collision detection</span></span>
<span data-ttu-id="2f5be-327">Nun haben wir einen Brokkoli, der den Spieler verfolgt. Außerdem gibt es eine Punktzahl, die sich immer dann erhöht, wenn der Spieler ausweicht. Aber im Moment gibt es noch keinen Weg, das Spiel auch zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="2f5be-327">So we have a broccoli that follows you around, and we have a score that ticks up each time a new one spawns—but as it is there is no way to actually lose this game.</span></span> <span data-ttu-id="2f5be-328">Wir müssen wissen, ob das Dino-Sprite und das Brokkoli-Sprite kollidieren, und falls sie dies tun, muss das Spiel als beendet erklärt werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-328">We need a way to know if the dino and broccoli sprites collide, and if when they do, to declare the game over.</span></span>

### <a name="1-rectangular-collision"></a><span data-ttu-id="2f5be-329">1. Rechteckige Kollision</span><span class="sxs-lookup"><span data-stu-id="2f5be-329">1. Rectangular collision</span></span>
<span data-ttu-id="2f5be-330">Beim Erkennen von Kollisionen in einem Spiel werden Objekte oft vereinfacht, damit die nötigen Berechnungen nicht allzu kompliziert werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-330">When detecting collisions in a game, objects are often simplified to reduce the complexity of the math involved.</span></span> <span data-ttu-id="2f5be-331">Wir behandeln sowohl den Avatar des Spielers als auch das Brokkoli-Hindernis als Rechtecke, um eine Kollision dieser Objekte erkennen zu können.</span><span class="sxs-lookup"><span data-stu-id="2f5be-331">We are going to treat both the player avatar and broccoli obstacle as rectangles for the purpose of detecting collision between them.</span></span>

<span data-ttu-id="2f5be-332">Öffnen Sie **SpriteClass.cs**, und fügen Sie eine neue Klassenvariable hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-332">Open **SpriteClass.cs** and add a new class variable:</span></span>

```CSharp
const float HITBOXSCALE = .5f;
```

<span data-ttu-id="2f5be-333">Dieser Wert stellt dar, inwieweit dem Spieler eine erkannte Kollision „verziehen“ wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-333">This value will represent how “forgiving” the collision detection is for the player.</span></span> <span data-ttu-id="2f5be-334">Mit dem Wert .5f werden die Kanten des Rechtecks, in dem der Dino mit dem Brokkoli kollidieren kann – häufig auch „Hitbox“ genannt – auf die Hälfte der Gesamtgröße der Textur verkleinert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-334">With a value of .5f, the edges of the rectangle in which the dino can collide with the broccoli—often call the “hitbox”—will be half of the full size of the texture.</span></span> <span data-ttu-id="2f5be-335">Damit können die Ecken der beiden Texturen in wenigen Fällen kollidieren, ohne dass Teile des Bildes tatsächlich sichtbar kollidieren.</span><span class="sxs-lookup"><span data-stu-id="2f5be-335">This will result in few instances where the corners of the two textures collide, without any parts of the images actually appearing to touch.</span></span> <span data-ttu-id="2f5be-336">Passen Sie diesen Wert nach Bedarf an.</span><span class="sxs-lookup"><span data-stu-id="2f5be-336">Feel free to tweak this value to your personal taste.</span></span>

<span data-ttu-id="2f5be-337">Fügen Sie dann eine neue Methode zu **SpriteClass.cs** hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-337">Next, add a new method to **SpriteClass.cs**:</span></span>

```CSharp
public bool RectangleCollision(SpriteClass otherSprite)
{
  if (this.x + this.texture.Width * this.scale * HITBOXSCALE / 2 < otherSprite.x - otherSprite.texture.Width * otherSprite.scale / 2) return false;
  if (this.y + this.texture.Height * this.scale * HITBOXSCALE / 2 < otherSprite.y - otherSprite.texture.Height * otherSprite.scale / 2) return false;
  if (this.x - this.texture.Width * this.scale * HITBOXSCALE / 2 > otherSprite.x + otherSprite.texture.Width * otherSprite.scale / 2) return false;
  if (this.y - this.texture.Height * this.scale * HITBOXSCALE / 2 > otherSprite.y + otherSprite.texture.Height * otherSprite.scale / 2) return false;
  return true;
}
```

<span data-ttu-id="2f5be-338">Diese Methode bestimmt, ob zwei rechteckige Objekte kollidiert sind.</span><span class="sxs-lookup"><span data-stu-id="2f5be-338">This method detects if two rectangular objects have collided.</span></span> <span data-ttu-id="2f5be-339">Mit dem Algorithmus wird getestet, ob eine Lücke zwischen den Seiten des Rechtecks vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2f5be-339">The algorithm works by testing to see if there is a gap between any of the side sides of the rectangles.</span></span> <span data-ttu-id="2f5be-340">Wenn es eine Lücke gibt, ist keine Kollision erfolgt – wenn keine Lücke vorhanden ist, muss eine Kollision vorliegen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-340">If there is any gap, there is no collision—if no gap exists, there must be a collision.</span></span>

### <a name="2-load-new-textures"></a><span data-ttu-id="2f5be-341">2. Laden neuer Texturen</span><span class="sxs-lookup"><span data-stu-id="2f5be-341">2. Load new textures</span></span>

<span data-ttu-id="2f5be-342">Öffnen Sie dann **Game1.cs**, und fügen Sie zwei neue Klassenvariablen hinzu: eine zum Speichern der Sprite-Textur für das Spielende und einen booleschen Wert, mit dem Zustand des Spiels überwacht wird:</span><span class="sxs-lookup"><span data-stu-id="2f5be-342">Then, open **Game1.cs** and add two new class variables, one to store the game over sprite texture, and a Boolean to track the game’s state:</span></span>

```CSharp
Texture2D gameOverTexture;
bool gameOver;
```

<span data-ttu-id="2f5be-343">Anschließend initialisieren Sie **gameOver** in der **Initialize**-Methode:</span><span class="sxs-lookup"><span data-stu-id="2f5be-343">Then, initialize **gameOver** in the **Initialize** method:</span></span>

```CSharp
gameOver = false;
```

<span data-ttu-id="2f5be-344">Laden Sie schließlich die Textur in der **LoadContent**-Methode in **gameOverTexture**:</span><span class="sxs-lookup"><span data-stu-id="2f5be-344">Finally, load the texture into **gameOverTexture** in the **LoadContent** method:</span></span>

```CSharp
gameOverTexture = Content.Load<Texture2D>("game-over");
```

### <a name="3-implement-game-over-logic"></a><span data-ttu-id="2f5be-345">3. Implementieren der Logik für das Spielende</span><span class="sxs-lookup"><span data-stu-id="2f5be-345">3. Implement “game over” logic</span></span>
<span data-ttu-id="2f5be-346">Fügen Sie der **Update**-Methode direkt nach dem Aufruf der **KeyboardHandler**-Methode diesen Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2f5be-346">Add this code to the **Update** method, just after the **KeyboardHandler** method is called:</span></span>

```CSharp
if (gameOver)
{
  dino.dX = 0;
  dino.dY = 0;
  broccoli.dX = 0;
  broccoli.dY = 0;
  broccoli.dA = 0;
}
```

<span data-ttu-id="2f5be-347">Dadurch werden nach Spielende alle Bewegungen beendet, und das Dino- und das Brokkoli-Sprite werden in ihrer aktuellen Position fixiert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-347">This will cause all motion to stop when the game has ended, freezing the dino and broccoli sprites in their current positions.</span></span>

<span data-ttu-id="2f5be-348">Als Nächstes fügen Sie am Ende der **Update**-Methode unmittelbar vor **base.Update(gameTime)** diese Zeile ein:</span><span class="sxs-lookup"><span data-stu-id="2f5be-348">Next, at the end of the **Update** method, just before **base.Update(gameTime)**, add this line:</span></span>

```CSharp
if (dino.RectangleCollision(broccoli)) gameOver = true;
```

<span data-ttu-id="2f5be-349">Dadurch wird die **RectangleCollision**-Methode aufgerufen, die wir in **SpriteClass** erstellt haben, und das Spiel als „beendet“ markiert, wenn der Wert „true“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2f5be-349">This calls the **RectangleCollision** method we created in **SpriteClass**, and flags the game as over if it returns true.</span></span>

### <a name="4-add-user-input-for-resetting-the-game"></a><span data-ttu-id="2f5be-350">4. Hinzufügen von Benutzereingaben für das Zurücksetzen des Spiels</span><span class="sxs-lookup"><span data-stu-id="2f5be-350">4. Add user input for resetting the game</span></span>
<span data-ttu-id="2f5be-351">Fügen Sie der **KeyboardHandler**-Methode diesen Code hinzu, damit die Benutzer das Spiel durch Drücken der EINGABETASTE zurücksetzen können:</span><span class="sxs-lookup"><span data-stu-id="2f5be-351">Add this code to the **KeyboardHandler** method, to allow the user to reset them game if they press Enter:</span></span>

```CSharp
if (gameOver && state.IsKeyDown(Keys.Enter))
{
  StartGame();
  gameOver = false;
}
```

### <a name="5-draw-game-over-splash-and-text"></a><span data-ttu-id="2f5be-352">5. Zeichnen des „Spielende“-Splash und -Textes</span><span class="sxs-lookup"><span data-stu-id="2f5be-352">5. Draw game over splash and text</span></span>
<span data-ttu-id="2f5be-353">Abschließend fügen Sie der Draw-Methode direkt nach dem ersten Aufruf von **spriteBatch.Draw** (dies sollte der Aufruf sein, mit dem die Gras-Textur gezeichnet wird) diesen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5be-353">Finally, add this code to the Draw method, just after the first call of **spriteBatch.Draw** (this should be the call that draws the grass texture).</span></span>

```CSharp
if (gameOver)
{
  // Draw game over texture
  spriteBatch.Draw(gameOverTexture, new Vector2(screenWidth / 2 - gameOverTexture.Width / 2, screenHeight / 4 - gameOverTexture.Width / 2), Color.White);

  String pressEnter = "Press Enter to restart!";

  // Measure the size of text in the given font
  Vector2 pressEnterSize = stateFont.MeasureString(pressEnter);

  // Draw the text horizontally centered
  spriteBatch.DrawString(stateFont, pressEnter, new Vector2(screenWidth / 2 - pressEnterSize.X / 2, screenHeight - 200), Color.White);
}
```

<span data-ttu-id="2f5be-354">Hier verwenden wir dieselbe Methode wie zuvor zum Zeichnen von horizontal zentriertem Text, wobei wir wieder die Schriftart aus dem Begrüßungsbildschirm verwenden. Außerdem wird **gameOverTexture** in der oberen Hälfte des Fensters zentriert.</span><span class="sxs-lookup"><span data-stu-id="2f5be-354">Here we use the same method as before to draw text horizontally centered (reusing the font we used for the intro splash), as well as centering **gameOverTexture** in the top half of the window.</span></span>

<span data-ttu-id="2f5be-355">Nun sind Sie fertig.</span><span class="sxs-lookup"><span data-stu-id="2f5be-355">And we’re done!</span></span> <span data-ttu-id="2f5be-356">Starten Sie das Spiel erneut.</span><span class="sxs-lookup"><span data-stu-id="2f5be-356">Try running the game again.</span></span> <span data-ttu-id="2f5be-357">Wenn Sie die oben beschriebenen Schritteausgeführt haben, sollte das Spiel jetzt beendet werden, wenn der Dino mit dem Brokkoli kollidiert. Dann sollte der Spieler zum Neustarten des Spiels durch Drücken der EINGABETASTE aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-357">If you followed the steps above, the game should now end when the dino collides with the broccoli, and the player should be prompted to restart the game by pressing the Enter key.</span></span>

![Spielende](images/monogame-tutorial-4.png)

## <a name="publish-to-the-microsoft-store"></a><span data-ttu-id="2f5be-359">Im Microsoft Store veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="2f5be-359">Publish to the Microsoft Store</span></span>
<span data-ttu-id="2f5be-360">Da wir dieses Spiel als UWP-app erstellt haben, ist es möglich, dieses Projekt im Microsoft Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-360">Because we built this game as a UWP app, it is possible to publish this project to the Microsoft Store.</span></span> <span data-ttu-id="2f5be-361">Dazu müssen Sie einige Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="2f5be-361">There are a few steps to the process.</span></span>

<span data-ttu-id="2f5be-362">Sie müssen als Windows-Entwickler [registriert](https://developer.microsoft.com/en-us/store/register) sein.</span><span class="sxs-lookup"><span data-stu-id="2f5be-362">You must be [registered](https://developer.microsoft.com/en-us/store/register) as a Windows Developer.</span></span>

<span data-ttu-id="2f5be-363">Sie müssen die [Prüfliste für App-Übermittlung](https://docs.microsoft.com/en-us/windows/uwp/publish/app-submissions) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-363">You must use the [app submission checklist](https://docs.microsoft.com/en-us/windows/uwp/publish/app-submissions).</span></span>

<span data-ttu-id="2f5be-364">Die App muss zur [Zertifizierung](https://docs.microsoft.com/en-us/windows/uwp/publish/the-app-certification-process) eingereicht werden.</span><span class="sxs-lookup"><span data-stu-id="2f5be-364">The app must be submitted for [certification](https://docs.microsoft.com/en-us/windows/uwp/publish/the-app-certification-process).</span></span>

<span data-ttu-id="2f5be-365">Weitere Informationen finden Sie unter [Veröffentlichen Ihrer UWP-app](https://developer.microsoft.com/en-us/store/publish-apps).</span><span class="sxs-lookup"><span data-stu-id="2f5be-365">For more details, see [Publishing your UWP app](https://developer.microsoft.com/en-us/store/publish-apps).</span></span>
