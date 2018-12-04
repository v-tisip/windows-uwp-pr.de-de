---
title: Einrichten des Spieleprojekts
description: Im ersten Schritt für die Erstellung Ihres Spiels richten Sie ein Projekt in Microsoft Visual Studio so ein, dass Sie möglichst wenig Aufwand mit der Bearbeitung der Codeinfrastruktur haben.
ms.assetid: 9fde90b3-bf79-bcb3-03b6-d38ab85803f2
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Einrichtung, directx
ms.localizationpriority: medium
ms.openlocfilehash: 252d7ccb8e50e773a19282afaf19bb18d4c5d5a6
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8470866"
---
# <a name="set-up-the-game-project"></a><span data-ttu-id="e2c73-104">Einrichten des Spieleprojekts</span><span class="sxs-lookup"><span data-stu-id="e2c73-104">Set up the game project</span></span>

<span data-ttu-id="e2c73-105">Dieses Thema erläutert das Einrichten eines einfachen UWP-DirectX-Spiels mit den Vorlagen in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2c73-105">This topic goes through how to setup a simple UWP DirectX game using the templates in Visual Studio.</span></span> <span data-ttu-id="e2c73-106">Im ersten Schritt für die Erstellung Ihres Spiels richten Sie ein Projekt in Microsoft Visual Studio so ein, dass Sie möglichst wenig Aufwand mit der Bearbeitung der Codeinfrastruktur haben.</span><span class="sxs-lookup"><span data-stu-id="e2c73-106">The first step in assembling your game is to set up a project in Microsoft Visual Studio in such a way that you minimize the amount of code infrastructure work you need to do.</span></span> <span data-ttu-id="e2c73-107">Lernen Sie, sich eine Menge Zeit und Arbeit ersparen, wenn Sie die richtige Vorlage verwenden und das Projekt speziell für die Spieleentwicklung konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e2c73-107">Learn to save set up time when you use the right template and configure the project specifically for game development.</span></span>

## <a name="objectives"></a><span data-ttu-id="e2c73-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="e2c73-108">Objectives</span></span>

* <span data-ttu-id="e2c73-109">Richten Sie ein Direct3D-Spieleprojekt in Visual Studio mit einer Vorlage ein.</span><span class="sxs-lookup"><span data-stu-id="e2c73-109">Set up a Direct3D game project in Visual Studio using a template</span></span>
* <span data-ttu-id="e2c73-110">Verstehen Sie den Haupteinstiegspunkt des Spiels durch Untersuchen der **App**-Quelldateien</span><span class="sxs-lookup"><span data-stu-id="e2c73-110">Understand the game's main entry point by examining the **App** source files</span></span>
* <span data-ttu-id="e2c73-111">Prüfen Sie die Datei **package.appxmanifest**</span><span class="sxs-lookup"><span data-stu-id="e2c73-111">Review the project's **package.appxmanifest** file</span></span>
* <span data-ttu-id="e2c73-112">Erfahren Sie, welche Spieleentwicklungstools und Support im Projekt enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e2c73-112">Find out what game dev tools and support are included with the project</span></span>

## <a name="how-to-set-up-the-game-project"></a><span data-ttu-id="e2c73-113">Einrichten des Spieleprojekts</span><span class="sxs-lookup"><span data-stu-id="e2c73-113">How to set up the game project</span></span>

<span data-ttu-id="e2c73-114">Wenn Sie Erfahrung mit der Entwicklung von UWP haben, empfehlen wir die Verwendung von Vorlagen in Visual Studio, um die grundlegende Codestruktur einzurichten.</span><span class="sxs-lookup"><span data-stu-id="e2c73-114">If you're new to Universal Windows Platform (UWP) development, we recommend the use of templates in Visual Studio to set up the basic code structure.</span></span>

>[!Note]
><span data-ttu-id="e2c73-115">Dieser Artikel ist Teil einer Lernprogrammreihe basierend auf einem Beispiel für ein Spiel.</span><span class="sxs-lookup"><span data-stu-id="e2c73-115">This article is part of a tutorial series based on a game sample.</span></span> <span data-ttu-id="e2c73-116">Sie erhalten den neuesten Code unter [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="e2c73-116">You can get the latest code at [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="e2c73-117">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-117">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="e2c73-118">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="e2c73-118">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

### <a name="use-directx-template-to-create-a-project"></a><span data-ttu-id="e2c73-119">Verwenden Sie DirectX-Vorlagen, um ein Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="e2c73-119">Use DirectX template to create a project</span></span>

<span data-ttu-id="e2c73-120">Eine Visual Studio-Vorlage ist eine Sammlung von Einstellungen und Codedateien, die abhängig von der bevorzugten Sprache und Technologie auf eine bestimmte Art von App ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="e2c73-120">A Visual Studio template is a collection of settings and code files that target a specific type of app based on the preferred language and technology.</span></span> <span data-ttu-id="e2c73-121">In Microsoft Visual Studio2017 finden Sie eine Reihe von Vorlagen, die app-Entwicklung Spiels und der Grafik deutlich vereinfachen können.</span><span class="sxs-lookup"><span data-stu-id="e2c73-121">In Microsoft Visual Studio2017, you'll find a number of templates that can dramatically ease game and graphics app development.</span></span> <span data-ttu-id="e2c73-122">Ohne Verwendung einer Vorlage müssen Sie einen Großteil des grundlegenden Rendering- und Anzeigeframeworks für die Grafik selbst entwickeln, was insbesondere für neue Spieleentwickler recht mühsam sein kann.</span><span class="sxs-lookup"><span data-stu-id="e2c73-122">If you don't use a template, you must develop much of the basic graphics rendering and display framework yourself, which can be a bit of a chore to a new game developer.</span></span>

<span data-ttu-id="e2c73-123">Die richtige Vorlage für dieses Tutorial ist die Vorlage **DirectX 11 App (Universal Windows)**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-123">The template used for this tutorial is titled **DirectX 11 App (Universal Windows)**.</span></span> 

<span data-ttu-id="e2c73-124">Schritte zum Erstellen eines DirectX 11-Spieleprojekts in Visual Studio11:</span><span class="sxs-lookup"><span data-stu-id="e2c73-124">Steps to create a DirectX 11 game project in Visual Studio:</span></span>
1.  <span data-ttu-id="e2c73-125">Wählen Sie **Datei...** &gt; **Neu**  &gt; **Projekt...**</span><span class="sxs-lookup"><span data-stu-id="e2c73-125">Select **File...** &gt; **New**  &gt; **Project...**</span></span>
2.  <span data-ttu-id="e2c73-126">Wählen Sie im linken Bereich **installiert**&gt; **Vorlagen** &gt; **Visual C++** &gt; **universelle Windows-Apps**</span><span class="sxs-lookup"><span data-stu-id="e2c73-126">In the left pane, select **Installed** &gt; **Templates** &gt; **Visual C++** &gt; **Windows Universal**</span></span>
3.  <span data-ttu-id="e2c73-127">Wählen Sie im mittleren Bereich **DirectX11-App (universelle Windows-App)** aus</span><span class="sxs-lookup"><span data-stu-id="e2c73-127">In the center pane, select **DirectX 11 App (Universal Windows)**</span></span>
4.  <span data-ttu-id="e2c73-128">Geben Sie Ihrem Spieleprojekt einen Namen, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-128">Give your game project a name, and click **OK**.</span></span>

![Bildschirmfoto, das zeigt, wie die DirectX11-Vorlage zum Erstellen eines neuen Spieleprojekts ausgewählt wird](images/simple-dx-game-setup-new-project.png)

<span data-ttu-id="e2c73-130">Diese Vorlage enthält das grundlegende Framework für eine UWP-App, für die DirectX mit C++ verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e2c73-130">This template provides you with the basic framework for a UWP app using DirectX with C++.</span></span> <span data-ttu-id="e2c73-131">Drücken Sie F5, um die App zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-131">Click F5 to build and run it.</span></span> <span data-ttu-id="e2c73-132">Ist das nicht ein hübscher blauer Bildschirm?</span><span class="sxs-lookup"><span data-stu-id="e2c73-132">Check out that powder blue screen.</span></span> <span data-ttu-id="e2c73-133">Mit der Vorlage werden mehrere Codedateien erstellt, die die grundlegenden Funktionen für eine UWP-App mit DirectX und C++ enthalten.</span><span class="sxs-lookup"><span data-stu-id="e2c73-133">The template creates multiple code files containing the basic functionality for a UWP app using DirectX with C++.</span></span>

## <a name="review-the-apps-main-entry-point-by-understanding-iframeworkview"></a><span data-ttu-id="e2c73-134">Überprüfen Sie den Haupteinstiegspunkt der App, indem Sie IFrameworkView verstehen</span><span class="sxs-lookup"><span data-stu-id="e2c73-134">Review the app's main entry point by understanding IFrameworkView</span></span>

<span data-ttu-id="e2c73-135">Die **App**-Klasse beerbt die **IFrameworkView**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="e2c73-135">The **App** class inherits from the **IFrameworkView** class.</span></span>

### <a name="inspect-apph"></a><span data-ttu-id="e2c73-136">Überprüfen Sie **App.h**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-136">Inspect **App.h**.</span></span>

<span data-ttu-id="e2c73-137">erstellen Sie die folgenden fünf Methoden in **App.h** &mdash; [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495), [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509), [**Load**](https://msdn.microsoft.com/library/windows/apps/hh700501), [**Run**](https://msdn.microsoft.com/library/windows/apps/hh700505), and [**Uninitialize**](https://msdn.microsoft.com/library/windows/apps/hh700523) bei der Implementierung der [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700469)-Schnittstelle, die den Ansichtsanbieter definiert.</span><span class="sxs-lookup"><span data-stu-id="e2c73-137">Let's quickly look at the 5 methods in **App.h** &mdash; [**Initialize**](https://msdn.microsoft.com/library/windows/apps/hh700495), [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509), [**Load**](https://msdn.microsoft.com/library/windows/apps/hh700501), [**Run**](https://msdn.microsoft.com/library/windows/apps/hh700505), and [**Uninitialize**](https://msdn.microsoft.com/library/windows/apps/hh700523) when implementing the [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700469) interface that defines a view provider.</span></span> <span data-ttu-id="e2c73-138">Diese Methoden werden vom App-Singleton ausgeführt, der beim Spielstart erstellt wird. Sie laden alle vom Spiel benötigten Ressourcen und stellen eine Verbindung zwischen den entsprechenden Ereignishandlern her.</span><span class="sxs-lookup"><span data-stu-id="e2c73-138">These methods are run by the app singleton that is created when your game is launched, and load all your app's resources as well as connect the appropriate event handlers.</span></span>

```cpp
    // Main entry point for our app. Connects the app with the Windows shell and handle application lifecycle events.
    ref class App sealed : public Windows::ApplicationModel::Core::IFrameworkView
    {
    public:
        App();

        // IFrameworkView Methods.
        virtual void Initialize(Windows::ApplicationModel::Core::CoreApplicationView^ applicationView);
        virtual void SetWindow(Windows::UI::Core::CoreWindow^ window);
        virtual void Load(Platform::String^ entryPoint);
        virtual void Run();
        virtual void Uninitialize();

    protected:
        ...
    };
```

### <a name="inspect-appcpp"></a><span data-ttu-id="e2c73-139">Überprüfen Sie **App.cpp**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-139">Inspect **App.cpp**</span></span>

<span data-ttu-id="e2c73-140">Die **main**-Methode befindet sich in der Quelldatei **App.cpp**:</span><span class="sxs-lookup"><span data-stu-id="e2c73-140">Here's the **main** method in the **App.cpp** source file:</span></span>

```cpp
//The main function is only used to initialize our IFrameworkView class.
[Platform::MTAThread]
int main(Platform::Array<Platform::String^>^)
{
    auto direct3DApplicationSource = ref new Direct3DApplicationSource();
    CoreApplication::Run(direct3DApplicationSource);
    return 0;
}
```

<span data-ttu-id="e2c73-141">Die Methode erstellt eine Instanz des Direct3D-Ansichtsanbieters aus der Ansichtsanbieterfactory (**Direct3DApplicationSource**, definiert in **App.h**) und übergibt sie zur Ausführung an das App-Singleton ([**CoreApplication::Run**](https://msdn.microsoft.com/library/windows/apps/hh700469)).</span><span class="sxs-lookup"><span data-stu-id="e2c73-141">In this method, it creates an instance of the Direct3D view provider from the view provider factory (**Direct3DApplicationSource**, defined in **App.h**), and passes it to the app singleton by calling ([**CoreApplication::Run**](https://msdn.microsoft.com/library/windows/apps/hh700469)).</span></span> <span data-ttu-id="e2c73-142">Das bedeutet, dass sich der Ausgangspunkt für Ihr Spiel im Implementierungscode der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode (in diesem Fall: **App::Run**) befindet.</span><span class="sxs-lookup"><span data-stu-id="e2c73-142">This means that the starting point for your game lives in the body of the implementation of the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method, and in this case, it's the **App::Run**.</span></span> 

<span data-ttu-id="e2c73-143">Suchen Sie die **App::Run**-Methode in **App.cpp**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-143">Scroll to find the **App::Run** method in **App.cpp**.</span></span> <span data-ttu-id="e2c73-144">Hier ist der Code:</span><span class="sxs-lookup"><span data-stu-id="e2c73-144">Here's the code:</span></span>

```cpp
//This method is called after the window becomes active.
void App::Run()
{
    while (!m_windowClosed)
    {
        if (m_windowVisible)
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            m_main->Update();

            if (m_main->Render())
            {
                m_deviceResources->Present();
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
}
```

<span data-ttu-id="e2c73-145">So funktioniert die Methode: Wenn das Fenster Ihres Spiels nicht geschlossen wird, werden hiermit alle Ereignisse gesendet, der Timer wird aktualisiert, und die Ergebnisse der Grafikpipeline werden gerendert und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2c73-145">What this method does: If the window for your game isn't closed, it dispatches all events, updates the timer, then renders and presents the results of your graphics pipeline.</span></span> <span data-ttu-id="e2c73-146">Wir befassen uns ausführlicher damit unter [Definieren der UWP-App-Framework](tutorial--building-the-games-uwp-app-framework.md), [Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md), und [Rendering-Framework II: Spiel-Rendering](tutorial-game-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e2c73-146">We'll talk about this in greater detail in [Define the UWP app framework](tutorial--building-the-games-uwp-app-framework.md), [Rendering framework I: Intro to rendering](tutorial--assembling-the-rendering-pipeline.md), and  [Rendering framework II: Game rendering](tutorial-game-rendering.md).</span></span> <span data-ttu-id="e2c73-147">Damit dürften Sie ein gewisses Gespür für die grundlegende Codestruktur eines UWP-DirectX-Spiels entwickelt haben.</span><span class="sxs-lookup"><span data-stu-id="e2c73-147">At this point, you should have a sense of the basic code structure of a UWP DirectX game.</span></span>

## <a name="review-and-update-the-packageappxmanifest-file"></a><span data-ttu-id="e2c73-148">Prüfen und Aktualisieren der Datei „package.appxmanifest“</span><span class="sxs-lookup"><span data-stu-id="e2c73-148">Review and update the package.appxmanifest file</span></span>


<span data-ttu-id="e2c73-149">Die Vorlage hat aber noch mehr zu bieten als nur Codedateien.</span><span class="sxs-lookup"><span data-stu-id="e2c73-149">The code files aren't all there is to the template.</span></span> <span data-ttu-id="e2c73-150">Die Datei **package.appxmanifest** enthält Metadaten für Ihr Projekt. Diese werden zum Packen und Starten des Spiels sowie zum Übermitteln des Spiels an den Microsoft Store verwendet.</span><span class="sxs-lookup"><span data-stu-id="e2c73-150">The **Package.appxmanifest** file contains metadata about your project that are used for packaging and launching your game and for submission to the Microsoft Store.</span></span> <span data-ttu-id="e2c73-151">Darüber hinaus enthält sie wichtige Infos, mit deren Hilfe das System des Spielers den Zugriff auf die zum Ausführen des Spiels benötigten Systemressourcen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e2c73-151">It also contains important info the player's system uses to provide access to the system resources the game needs to run.</span></span>

<span data-ttu-id="e2c73-152">Starten Sie den **Manifest-Designer**. Doppelklicken Sie hierzu im **Projektmappen-Explorer** auf die Datei **package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-152">Launch the **manifest designer** by double-clicking the **Package.appxmanifest** file in **Solution Explorer**.</span></span>

![Screenshot des Manifest-Editor „package.appx“](images/simple-dx-game-setup-app-manifest.png)

<span data-ttu-id="e2c73-154">Weitere Informationen zur Datei **package.appxmanifest** und zum Packen finden Sie unter [Manifest-Designer](https://msdn.microsoft.com/library/windows/apps/br230259.aspx).</span><span class="sxs-lookup"><span data-stu-id="e2c73-154">For more info about the **package.appxmanifest** file and packaging, see [Manifest Designer](https://msdn.microsoft.com/library/windows/apps/br230259.aspx).</span></span> <span data-ttu-id="e2c73-155">Nun widmen wir uns aber erst einmal der Registerkarte **Funktionen** und den dort zur Verfügung stehenden Optionen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-155">For now, take a look at the **Capabilities** tab and look at the options provided.</span></span>

![Screenshot der Standardfunktionen einer Direct3D-App](images/simple-dx-game-setup-capabilities.png)

<span data-ttu-id="e2c73-157">Wenn Sie die von Ihrem Spiel genutzten Funktionen (etwa den Zugriff auf das Internet\*\*\*\* für eine globale Bestenliste) nicht auswählen, können Sie nicht auf die entsprechenden Ressourcen oder Features zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-157">If you don't select the capabilities that your game uses, such as access to the **Internet** for global high score board, you won't be able to access the corresponding resources or features.</span></span> <span data-ttu-id="e2c73-158">Achten Sie beim Erstellen eines neuen Spiels darauf, die Funktionen auszuwählen, die Ihr Spiel für die Ausführung benötigt.</span><span class="sxs-lookup"><span data-stu-id="e2c73-158">When you create a new game, make sure that you select the capabilities that your game needs to run!</span></span>

<span data-ttu-id="e2c73-159">Kommen wir nun zu den restlichen Dateien der Vorlage **DirectX 11-App (Universelle Windows-App)**.</span><span class="sxs-lookup"><span data-stu-id="e2c73-159">Now, let's look at the rest of the files that come with the **DirectX 11 App (Universal Windows)** template.</span></span>

## <a name="review-the-included-libraries-and-headers"></a><span data-ttu-id="e2c73-160">Anzeigen der enthaltenen Bibliotheken und Header</span><span class="sxs-lookup"><span data-stu-id="e2c73-160">Review the included libraries and headers</span></span>

<span data-ttu-id="e2c73-161">Ein paar Dateien haben wir uns für den Schluss aufgehoben.</span><span class="sxs-lookup"><span data-stu-id="e2c73-161">There are a few files we haven't looked at yet.</span></span> <span data-ttu-id="e2c73-162">Diese Dateien bieten zusätzliche Tools und Unterstützung für die Entwicklung von Direct3D-Spielen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-162">These files provide additional tools and support common to Direct3D game development scenarios.</span></span> <span data-ttu-id="e2c73-163">Die vollständige Liste der Dateien, die im grundlegenden DirectX-Spieleprojekts enthalten ist, finden Sie unter [DirectX-Spielprojektvorlagen](user-interface.md#template-structure).</span><span class="sxs-lookup"><span data-stu-id="e2c73-163">For the full list of files that comes with the basic DirectX game project, see [DirectX game project templates](user-interface.md#template-structure).</span></span>

| <span data-ttu-id="e2c73-164">Quelldatei der Vorlage</span><span class="sxs-lookup"><span data-stu-id="e2c73-164">Template Source File</span></span>         | <span data-ttu-id="e2c73-165">Dateiordner</span><span class="sxs-lookup"><span data-stu-id="e2c73-165">File folder</span></span>            | <span data-ttu-id="e2c73-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e2c73-166">Description</span></span> |
|------------------------------|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e2c73-167">DeviceResources.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="e2c73-167">DeviceResources.h/.cpp</span></span>       | <span data-ttu-id="e2c73-168">Allgemein</span><span class="sxs-lookup"><span data-stu-id="e2c73-168">Common</span></span>                 | <span data-ttu-id="e2c73-169">Definiert ein Klassenobjekt, das [Geräteressourcen](tutorial--assembling-the-rendering-pipeline.md#resource) von DirectX steuert.</span><span class="sxs-lookup"><span data-stu-id="e2c73-169">Defines a class object that controls all DirectX [device resources](tutorial--assembling-the-rendering-pipeline.md#resource).</span></span> <span data-ttu-id="e2c73-170">Darüber hinaus enthält es eine Schnittstelle für die Anwendung, die DeviceResources besitzt, um benachrichtigt zu werden, wenn das Gerät verloren geht oder erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="e2c73-170">It also includes an interface for your application that owns DeviceResources to be notified  when the device is lost or created.</span></span>                                                |
| <span data-ttu-id="e2c73-171">DirectXHelper.h</span><span class="sxs-lookup"><span data-stu-id="e2c73-171">DirectXHelper.h</span></span>              | <span data-ttu-id="e2c73-172">Allgemein</span><span class="sxs-lookup"><span data-stu-id="e2c73-172">Common</span></span>                 | <span data-ttu-id="e2c73-173">Implementiert Methoden wie z.B. **DX::ThrowIfFailed**, **ReadDataAsync**, und \*\* ConvertDipsToPixels.</span><span class="sxs-lookup"><span data-stu-id="e2c73-173">Implements methods including **DX::ThrowIfFailed**, **ReadDataAsync**, and \*\*ConvertDipsToPixels.</span></span> <span data-ttu-id="e2c73-174">**DX::ThrowIfFailed**konvertiert die von DirectX Win32-APIs zurückgegebenen HRESULT-Fehlerwerte in Ausnahmen der Windows-Runtime konvertiert.</span><span class="sxs-lookup"><span data-stu-id="e2c73-174">**DX::ThrowIfFailed** converts the error HRESULT values returned by DirectX Win32 APIs into Windows Runtime exceptions.</span></span> <span data-ttu-id="e2c73-175">Verwenden Sie diese Methode, um einen Haltepunkt zum Debuggen von DirectX-Fehlern zu setzen.</span><span class="sxs-lookup"><span data-stu-id="e2c73-175">Use this method to put a break point for debugging DirectX errors.</span></span> <span data-ttu-id="e2c73-176">Weitere Informationen finden Sie unter [ThrowIfFailed](https://github.com/Microsoft/DirectXTK/wiki/ThrowIfFailed).</span><span class="sxs-lookup"><span data-stu-id="e2c73-176">For more information, see [ThrowIfFailed](https://github.com/Microsoft/DirectXTK/wiki/ThrowIfFailed).</span></span> <span data-ttu-id="e2c73-177">**ReadDataAsync** liest asynchron aus einer binären Datei.</span><span class="sxs-lookup"><span data-stu-id="e2c73-177">**ReadDataAsync** reads from a binary file asynchronously.</span></span> <span data-ttu-id="e2c73-178">**ConvertDipsToPixels** konvertiert eine Länge in geräteunabhängige Pixel (DIPs) auf eine Länge in physische Pixel.</span><span class="sxs-lookup"><span data-stu-id="e2c73-178">**ConvertDipsToPixels** converts a length in device-independent pixels (DIPs) to a length in physical pixels.</span></span> |
| <span data-ttu-id="e2c73-179">StepTimer.h</span><span class="sxs-lookup"><span data-stu-id="e2c73-179">StepTimer.h</span></span>                  | <span data-ttu-id="e2c73-180">Allgemein</span><span class="sxs-lookup"><span data-stu-id="e2c73-180">Common</span></span>                 | <span data-ttu-id="e2c73-181">Definiert einen Timer mit hoher Auflösung, der sich besonders für Spiele oder Apps mit interaktivem Rendering eignet.</span><span class="sxs-lookup"><span data-stu-id="e2c73-181">Defines a high-resolution timer useful for gaming or interactive rendering apps.</span></span>   |
| <span data-ttu-id="e2c73-182">Sample3DSceneRenderer.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="e2c73-182">Sample3DSceneRenderer.h/.cpp</span></span> | <span data-ttu-id="e2c73-183">Inhalt</span><span class="sxs-lookup"><span data-stu-id="e2c73-183">Content</span></span>                | <span data-ttu-id="e2c73-184">Definiert ein Klassenobjekt, um eine grundlegende Renderingpipeline zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="e2c73-184">Defines a class object to instantiate a basic rendering pipeline.</span></span> <span data-ttu-id="e2c73-185">Erstellt eine einfache Renderimplementierung, die eine Direct3D-Swapchain und einen Grafikadapter mit Ihrem UWP-DirectX-Spiel verbindet.</span><span class="sxs-lookup"><span data-stu-id="e2c73-185">It creates a basic renderer implementation that connects a Direct3D swap chain and graphics adapter to your UWP using DirectX.</span></span>   |
| <span data-ttu-id="e2c73-186">SampleFPSTextRenderer.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="e2c73-186">SampleFPSTextRenderer.h/.cpp</span></span> | <span data-ttu-id="e2c73-187">Inhalt</span><span class="sxs-lookup"><span data-stu-id="e2c73-187">Content</span></span>                | <span data-ttu-id="e2c73-188">Definiert ein Klassenobjekt, das den aktuellen FPS-Wert mit Direct2D und DirectWrite rechts unten auf dem Bildschirm rendert.</span><span class="sxs-lookup"><span data-stu-id="e2c73-188">Defines a class object to render the current frames per second (FPS) value in the bottom right corner of the screen using Direct2D and DirectWrite.</span></span>  |
| <span data-ttu-id="e2c73-189">SamplePixelShader.hlsl</span><span class="sxs-lookup"><span data-stu-id="e2c73-189">SamplePixelShader.hlsl</span></span>       | <span data-ttu-id="e2c73-190">Inhalt</span><span class="sxs-lookup"><span data-stu-id="e2c73-190">Content</span></span>                | <span data-ttu-id="e2c73-191">Enthält den Code der High-Level-Shader-Language (HLSL) für einen sehr einfachen Pixel-Shader.</span><span class="sxs-lookup"><span data-stu-id="e2c73-191">Contains the high-level shader language (HLSL) code for a very basic pixel shader.</span></span>                                            |
| <span data-ttu-id="e2c73-192">SampleVertexShader.hlsl</span><span class="sxs-lookup"><span data-stu-id="e2c73-192">SampleVertexShader.hlsl</span></span>      | <span data-ttu-id="e2c73-193">Inhalt</span><span class="sxs-lookup"><span data-stu-id="e2c73-193">Content</span></span>                | <span data-ttu-id="e2c73-194">Enthält den Code der High-Level Shader Language (HLSL) für einen sehr einfachen Vertex-Shader.</span><span class="sxs-lookup"><span data-stu-id="e2c73-194">Contains the high-level shader language (HLSL) code for a very basic vertex shader.</span></span>                                           |
| <span data-ttu-id="e2c73-195">ShaderStructures.h</span><span class="sxs-lookup"><span data-stu-id="e2c73-195">ShaderStructures.h</span></span>           | <span data-ttu-id="e2c73-196">Inhalt</span><span class="sxs-lookup"><span data-stu-id="e2c73-196">Content</span></span>                | <span data-ttu-id="e2c73-197">Enthält die Shader-Strukturen, die zum Senden von MVP-Matrizen und Vertex-Daten an den Vertexshader verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="e2c73-197">Contains shader structures that can be used to send MVP matrices and per-vertex data to the vertex shader.</span></span>  |
| <span data-ttu-id="e2c73-198">pch.h/.cpp</span><span class="sxs-lookup"><span data-stu-id="e2c73-198">pch.h/.cpp</span></span>                   | <span data-ttu-id="e2c73-199">Main</span><span class="sxs-lookup"><span data-stu-id="e2c73-199">Main</span></span>                   | <span data-ttu-id="e2c73-200">Enthält alles, was das Windows-System für die von einer Direct3D-App genutzten APIs (einschließlich DirectX11-APIs) enthält.</span><span class="sxs-lookup"><span data-stu-id="e2c73-200">Contains all the Windows system includes for the APIs used by a Direct3D app, including the DirectX 11 APIs.</span></span>| 

### <a name="next-steps"></a><span data-ttu-id="e2c73-201">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e2c73-201">Next steps</span></span>

<span data-ttu-id="e2c73-202">Hier haben Sie gelernt, wie Sie ein UWP-DirectX-Spieleprojekts mithilfe der **DirectX11-App (Universal Windows)**-Vorlage erstellen und haben einige Komponenten und Dateien eingeführt, die von diesem Projekt bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e2c73-202">At this point, you've learnt how to create a UWP DirectX game project using the **DirectX 11 App (Universal Windows)** template and have been introduced to a few components and files provided by this project.</span></span>

<span data-ttu-id="e2c73-203">Der nächste Abschnittist [Definieren des UWP-App-Frameworks für das Spiel](tutorial--building-the-games-uwp-app-framework.md).</span><span class="sxs-lookup"><span data-stu-id="e2c73-203">The next section is [Defining the game's UWP framework](tutorial--building-the-games-uwp-app-framework.md).</span></span> <span data-ttu-id="e2c73-204">Wir untersuchen, wie dieses Spiel viele der Konzepte und Komponenten verwendet und erweitert, die die Vorlage bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="e2c73-204">We'll examine how this game uses and extends many of the concepts and components that the template provides.</span></span>

 

 




