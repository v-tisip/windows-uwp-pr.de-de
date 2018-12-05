---
ms.assetid: 3a17e682-40be-41b4-8bd3-fbf0b15259d6
title: Erstellen der App Hello, world (JS)
description: In diesem Lernprogramm erfahren Sie, wie Sie JavaScript und HTML zum Erstellen einer einfachen & \#0034; Hello, World & \#0034; App, die die universelle Windows-Plattform (UWP) auf Windows 10 ausgerichtet ist.
ms.date: 03/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c5b99c95167940c1ae51dbe96a3e43dc6fb0af34
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8701806"
---
# <a name="create-a-hello-world-app-js"></a><span data-ttu-id="5bb50-104">Erstellen der App Hello, world (JS)</span><span class="sxs-lookup"><span data-stu-id="5bb50-104">Create a "Hello, world" app (JS)</span></span>

<span data-ttu-id="5bb50-105">In diesem Lernprogramm erfahren Sie, wie Sie JavaScript und HTML zum Erstellen einer einfachen "Hello, World"-App für die universelle Windows-Plattform (UWP) auf Windows 10 verwenden.</span><span class="sxs-lookup"><span data-stu-id="5bb50-105">This tutorial teaches you how to use JavaScript and HTML to create a simple "Hello, world" app that targets the Universal Windows Platform (UWP) on Windows10.</span></span> <span data-ttu-id="5bb50-106">Mit einem einzigen Projekt in Microsoft Visual Studio können Sie eine app erstellen, die auf jedem Windows 10-Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5bb50-106">With a single project in Microsoft Visual Studio, you can build an app that runs on any Windows10 device.</span></span>

> [!NOTE]
> <span data-ttu-id="5bb50-107">In diesem Lernprogramm wird Visual Studio Community 2017 verwendet.</span><span class="sxs-lookup"><span data-stu-id="5bb50-107">This tutorial is using Visual Studio Community 2017.</span></span> <span data-ttu-id="5bb50-108">Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-108">If you are using a different version of Visual Studio, it may look a little different for you.</span></span>


<span data-ttu-id="5bb50-109">Hier erfahren Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="5bb50-109">Here you'll learn how to:</span></span>

-   <span data-ttu-id="5bb50-110">Erstellen Sie ein neues **Visual Studio 2017** -Projekt, das auf **Windows 10** und die **UWP**abzielt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-110">Create a new **Visual Studio 2017** project that targets **Windows10** and the **UWP**.</span></span>
-   <span data-ttu-id="5bb50-111">Fügen Sie HTML und JavaScript-Inhalt hinzu</span><span class="sxs-lookup"><span data-stu-id="5bb50-111">Add HTML and JavaScript content</span></span>
-   <span data-ttu-id="5bb50-112">Führen Sie das Projekt auf dem lokalen Desktop in Visual Studio aus</span><span class="sxs-lookup"><span data-stu-id="5bb50-112">Run the project on the local desktop in Visual Studio</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5bb50-113">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="5bb50-113">Before you start...</span></span>

-   <span data-ttu-id="5bb50-114">[Was ist eine UWP-App?](universal-application-platform-guide.md).</span><span class="sxs-lookup"><span data-stu-id="5bb50-114">[What's a UWP app?](universal-application-platform-guide.md).</span></span>
-   <span data-ttu-id="5bb50-115">Zum Durcharbeiten dieses Lernprogramms benötigen Sie Windows 10 und Visual Studio2017.</span><span class="sxs-lookup"><span data-stu-id="5bb50-115">To complete this tutorial, you need Windows10 and Visual Studio2017.</span></span> <span data-ttu-id="5bb50-116">[Vorbereiten](get-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="5bb50-116">[Get set up](get-set-up.md).</span></span>
-   <span data-ttu-id="5bb50-117">Außerdem wird davon ausgegangen, dass Sie das Standardfensterlayout in Visual Studio verwenden.</span><span class="sxs-lookup"><span data-stu-id="5bb50-117">We also assume you're using the default window layout in Visual Studio.</span></span> <span data-ttu-id="5bb50-118">Wenn Sie das Standardlayout ändern, können Sie es im Menü **Fenster** mit dem Befehl **Fensterlayout zurücksetzen** wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-118">If you change the default layout, you can reset it in the **Window** menu by using the **Reset Window Layout** command.</span></span>

## <a name="step-1-create-a-new-project-in-visual-studio"></a><span data-ttu-id="5bb50-119">Schritt 1: Erstellen eines neuen Projekts in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5bb50-119">Step 1: Create a new project in Visual Studio.</span></span>

1.  <span data-ttu-id="5bb50-120">Starten Sie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5bb50-120">Launch Visual Studio 2017.</span></span>

2.  <span data-ttu-id="5bb50-121">Wählen Sie im Menü **Datei** die Befehle **Neu > Projekt...** aus, um das Dialogfeld *Neues Projekt* anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-121">From the **File** menu, select **New > Project...** to open the *New Project* dialog.</span></span>

3.  <span data-ttu-id="5bb50-122">Öffnen Sie in der Liste der Vorlagen auf der linken Seite **Installiert > Vorlagen > JavaScript**, und wählen Sie dann **Windows Universal** aus, um eine Liste der UWP-Projektvorlagen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-122">From the list of templates on the left, open **Installed > Templates > JavaScript**, and then choose **Windows Universal** to see the list of UWP project templates.</span></span>

    <span data-ttu-id="5bb50-123">(Wenn keine universellen Vorlagen angezeigt werden, fehlen möglicherweise die Komponenten zum Erstellen von UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="5bb50-123">(If you don't see any Universal templates, you might be missing the components for creating UWP apps.</span></span> <span data-ttu-id="5bb50-124">Sie können die Installation wiederholen und UWP-Unterstützung hinzufügen, indem Sie im Dialogfeld *Neues Projekt* auf **Visual Studio-Installer öffnen** klicken.</span><span class="sxs-lookup"><span data-stu-id="5bb50-124">You can repeat the installation process and add UWP support by clicking **Open Visual Studio installer** on the *New Project* dialog.</span></span> <span data-ttu-id="5bb50-125">Siehe [Vorbereiten](get-set-up.md)</span><span class="sxs-lookup"><span data-stu-id="5bb50-125">See [Get set up](get-set-up.md)</span></span>

4.  <span data-ttu-id="5bb50-126">Wählen Sie die Vorlage **Leere App (universelle Windows-App)** aus, und geben Sie „HelloWorld“ als **Name** ein.</span><span class="sxs-lookup"><span data-stu-id="5bb50-126">Choose the **Blank App (Universal Windows)** template, and enter "HelloWorld" as the **Name**.</span></span> <span data-ttu-id="5bb50-127">Wählen Sie **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="5bb50-127">Select **OK**.</span></span>

    ![Das Fenster für ein neues Projekt](images/win10-js-01.png)

> [!NOTE]
> <span data-ttu-id="5bb50-129">Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5bb50-129">If this is the first time you have used Visual Studio, you might see a Settings dialog asking you to enable **Developer mode**.</span></span> <span data-ttu-id="5bb50-130">Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store.</span><span class="sxs-lookup"><span data-stu-id="5bb50-130">Developer mode is a special setting that enables certain features, such as permission to run apps directly, rather than only from the Store.</span></span> <span data-ttu-id="5bb50-131">Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md).</span><span class="sxs-lookup"><span data-stu-id="5bb50-131">For more information, please read [Enable your device for development](enable-your-device-for-development.md).</span></span> <span data-ttu-id="5bb50-132">Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="5bb50-132">To continue with this guide, select **Developer mode**, click **Yes**, and close the dialog.</span></span>

 ![Aktivieren des Dialogfelds für Entwicklermodus](images/win10-cs-00.png)

5.  <span data-ttu-id="5bb50-134">Das Dialogfeld für die Zielversion/mindestens erforderliche Version wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-134">The target version/minimum version dialog appears.</span></span> <span data-ttu-id="5bb50-135">Die Standardeinstellungen sind für dieses Lernprogramm in Ordnung, wählen Sie daher **OK** aus, um das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-135">The default settings are fine for this tutorial, so select **OK** to create the project.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-02.png)

6.  <span data-ttu-id="5bb50-137">Wenn das neue Projekt geöffnet wird, werden die Dateien im Bereich **Projektmappen-Explorer** auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-137">When your new project opens, its files are displayed in the **Solution Explorer** pane on the right.</span></span> <span data-ttu-id="5bb50-138">Möglicherweise müssen Sie die Registerkarte **Projektmappen-Explorer** anstelle der Registerkarte **Eigenschaften** auswählen, um die Dateien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-138">You may need to choose the **Solution Explorer** tab instead of the **Properties** tab to see your files.</span></span>

    ![Das Fenster „Projektmappen-Explorer“](images/win10-js-02.png)

<span data-ttu-id="5bb50-140">**Leere App (universelle Windows-App)** ist zwar nur eine Minimalvorlage, umfasst aber trotzdem eine Reihe von Dateien.</span><span class="sxs-lookup"><span data-stu-id="5bb50-140">Although the **Blank App (Universal Window)** is a minimal template, it still contains a lot of files.</span></span> <span data-ttu-id="5bb50-141">Diese Dateien werden für alle UWP-Apps mit JavaScript benötigt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-141">These files are essential to all UWP apps using JavaScript.</span></span> <span data-ttu-id="5bb50-142">Sie sind Teil jedes Projekts, das Sie mit Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-142">Every project that you create in Visual Studio contains them.</span></span>


### <a name="whats-in-the-files"></a><span data-ttu-id="5bb50-143">Inhalt der Dateien</span><span class="sxs-lookup"><span data-stu-id="5bb50-143">What's in the files?</span></span>

<span data-ttu-id="5bb50-144">Doppelklicken Sie zum Anzeigen und Bearbeiten einer Datei im Projekt im **Projektmappen-Explorer** auf die gewünschte Datei.</span><span class="sxs-lookup"><span data-stu-id="5bb50-144">To view and edit a file in your project, double-click the file in the **Solution Explorer**.</span></span> 

*<span data-ttu-id="5bb50-145">default.css</span><span class="sxs-lookup"><span data-stu-id="5bb50-145">default.css</span></span>*

-  <span data-ttu-id="5bb50-146">Der von der App verwendete Standard-Stylesheet.</span><span class="sxs-lookup"><span data-stu-id="5bb50-146">The default stylesheet used by the app.</span></span>

*<span data-ttu-id="5bb50-147">main.js</span><span class="sxs-lookup"><span data-stu-id="5bb50-147">main.js</span></span>*

- <span data-ttu-id="5bb50-148">Die JavaScript-Datei „default.js“</span><span class="sxs-lookup"><span data-stu-id="5bb50-148">The default JavaScript file.</span></span> <span data-ttu-id="5bb50-149">Auf sie wird in der Datei index.html verwiesen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-149">It's referenced in the index.html file.</span></span>

*<span data-ttu-id="5bb50-150">index.html</span><span class="sxs-lookup"><span data-stu-id="5bb50-150">index.html</span></span>*

- <span data-ttu-id="5bb50-151">Die Website der App, die beim Start der App geladen und angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5bb50-151">The app's web page, loaded and displayed when the app is launched.</span></span>

*<span data-ttu-id="5bb50-152">Ein Satz mit Logobildern</span><span class="sxs-lookup"><span data-stu-id="5bb50-152">A set of logo images</span></span>*
-   <span data-ttu-id="5bb50-153">„Assets/Square150x150Logo.scale-200.png“ stellt Ihre App im Startmenü dar.</span><span class="sxs-lookup"><span data-stu-id="5bb50-153">Assets/Square150x150Logo.scale-200.png represents your app in the start menu.</span></span>
-   <span data-ttu-id="5bb50-154">„Assets/StoreLogo.png“ stellt Ihre App im Microsoft Store dar.</span><span class="sxs-lookup"><span data-stu-id="5bb50-154">Assets/StoreLogo.png represents your app in the Microsoft Store.</span></span>
-   <span data-ttu-id="5bb50-155">„Assets/SplashScreen.scale-200.png“ ist der Begrüßungsbildschirm, der beim Start der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5bb50-155">Assets/SplashScreen.scale-200.png is the splash screen that appears when your app starts.</span></span>

## <a name="step-2-adding-a-button"></a><span data-ttu-id="5bb50-156">Schritt 2: Hinzufügen von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5bb50-156">Step 2: Adding a button</span></span>

<span data-ttu-id="5bb50-157">Klicken Sie auf *index.html*, um die Datei im Editor auszuwählen, und ändern Sie den darin enthaltenen HTML-Code wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5bb50-157">Click on *index.html* to select it in the editor, and change the HTML it contains to read:</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <title>Hello World</title>
    <script src="js/main.js"></script>
    <link href="css/default.css" rel="stylesheet" />
</head>

<body>
    <p>Click the button..</p>
    <button id="button">Hello world!</button>
</body>

</html>
```

<span data-ttu-id="5bb50-158">Er sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5bb50-158">It should look like this:</span></span>

 ![HTML-Code des Projekts](images/win10-js-03.png)

<span data-ttu-id="5bb50-160">Dieser HTML-Code verweist auf die Datei *main.js*, die das JavaScript enthält, und fügt dann dem Hauptteil der Webseite eine einzelne Textzeile und eine Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="5bb50-160">This HTML references the *main.js* that will contain our JavaScript, and then adds a single line of text and a single button to the body of the web page.</span></span> <span data-ttu-id="5bb50-161">Die Schaltfläche erhält eine *ID*, damit JavaScript darauf verweisen kann.</span><span class="sxs-lookup"><span data-stu-id="5bb50-161">The button is given an *ID* so the JavaScript will be able to reference it.</span></span>


## <a name="step-3-adding-some-javascript"></a><span data-ttu-id="5bb50-162">Schritt3: Hinzufügen von JavaScript</span><span class="sxs-lookup"><span data-stu-id="5bb50-162">Step 3: Adding some JavaScript</span></span>

<span data-ttu-id="5bb50-163">Jetzt fügen wir JavaScript hinzu.</span><span class="sxs-lookup"><span data-stu-id="5bb50-163">Now we'll add the JavaScript.</span></span> <span data-ttu-id="5bb50-164">Klicken Sie auf die Datei *main.js*, um sie auszuwählen, und fügen Sie Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="5bb50-164">Click on *main.js* to select it, and add the following:</span></span>

```javascript
// Your code here!

window.onload = function () {
    document.getElementById("button").onclick = function (evt) {
        sayHello()
    }
}


function sayHello() {
    var messageDialog = new Windows.UI.Popups.MessageDialog("Hello, world!", "Alert");
    messageDialog.showAsync();
}

```

<span data-ttu-id="5bb50-165">Es sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5bb50-165">It should look like this:</span></span>

 ![JavaScript-Code des Projekts](images/win10-js-04.png)

<span data-ttu-id="5bb50-167">In diesem JavaScript werden zwei Funktionen deklariert.</span><span class="sxs-lookup"><span data-stu-id="5bb50-167">This JavaScript declares two functions.</span></span> <span data-ttu-id="5bb50-168">Die Funktion *window.onload* wird automatisch aufgerufen, wenn *index.html* angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5bb50-168">The *window.onload* function is called automatically when *index.html* is displayed.</span></span> <span data-ttu-id="5bb50-169">Die Schaltfläche wird (anhand der angegebenen ID) ermittelt, und es wird ein Onclick-Handler hinzugefügt. Dies ist die Methode, die aufgerufen wird, wenn auf die Schaltfläche geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="5bb50-169">It finds the button (using the ID we declared) and adds an onclick handler: the method that will be called when the button is clicked.</span></span>

<span data-ttu-id="5bb50-170">Die zweite Funktion, *sayHello()*, erstellt ein Dialogfeld und zeigt es an.</span><span class="sxs-lookup"><span data-stu-id="5bb50-170">The second function, *sayHello()*, creates and displays a dialog.</span></span> <span data-ttu-id="5bb50-171">Diese Funktion ist der Funktion *Alert()*, die Sie möglicherweise aus vorheriger JavaScript-Entwicklung kennen, sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="5bb50-171">This is very similar to the *Alert()* function you may know from previous JavaScript development.</span></span>


## <a name="step-4-run-the-app"></a><span data-ttu-id="5bb50-172">Schritt4: Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="5bb50-172">Step 4: Run the app!</span></span>

<span data-ttu-id="5bb50-173">Jetzt können Sie die App ausführen, indem Sie F5 drücken.</span><span class="sxs-lookup"><span data-stu-id="5bb50-173">Now you can run the app by pressing F5.</span></span> <span data-ttu-id="5bb50-174">Die App wird geladen, und die Webseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-174">The app will load, the web page will be displayed.</span></span> <span data-ttu-id="5bb50-175">Klicken Sie auf die Schaltfläche, und das Meldungsdialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bb50-175">Click on the button, and the message dialog will pop-up.</span></span>

 ![Ausführen des Projekts](images/win10-js-05.png)



## <a name="summary"></a><span data-ttu-id="5bb50-177">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="5bb50-177">Summary</span></span>


<span data-ttu-id="5bb50-178">Herzlichen Glückwunsch, Sie haben eine JavaScript-app für Windows 10 und die UWP erstellt!</span><span class="sxs-lookup"><span data-stu-id="5bb50-178">Congratulations, you've created a JavaScript app for Windows10 and the UWP!</span></span> <span data-ttu-id="5bb50-179">Dies ist ein sehr einfaches Beispiel, aber nun können Sie Ihre bevorzugten JavaScript-Bibliotheken und -Frameworks zum Erstellen Ihrer eigenen App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-179">This is a ridiculously simple example, however, you can now start adding your favorite JavaScript libraries and frameworks to create your own app.</span></span> <span data-ttu-id="5bb50-180">Und da es sich um eine UWP-App handelt, können Sie sie im Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="5bb50-180">And as it's a UWP app, you can publish it to the Store.</span></span> <span data-ttu-id="5bb50-181">Beispiele zum Hinzufügen von Drittanbieter-Frameworks finden Sie in diesen Projekten:</span><span class="sxs-lookup"><span data-stu-id="5bb50-181">For example of how third party frameworks can be added, see these  projects:</span></span>

* [<span data-ttu-id="5bb50-182">Ein einfaches 2D-UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und CreateJS</span><span class="sxs-lookup"><span data-stu-id="5bb50-182">A simple 2D UWP game for the Microsoft Store, written in JavaScript and CreateJS</span></span>](get-started-tutorial-game-js2d.md)
* [<span data-ttu-id="5bb50-183">Ein 3D-UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und ThreeJS</span><span class="sxs-lookup"><span data-stu-id="5bb50-183">A 3D UWP game for the Microsoft Store, written in JavaScript and threeJS</span></span>](get-started-tutorial-game-js3d.md)


