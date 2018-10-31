---
author: eliotcowley
title: Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel
description: Lernen Sie mehr über bewährte Methoden, die bei der Arbeit mit Eingabegeräten beachtet werden sollten.
ms.assetid: b946bf62-c0ca-f9ec-1a87-8195b89a5ab4
ms.author: elcowle
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Eingabe, Beispiel
ms.localizationpriority: medium
ms.openlocfilehash: 0b7e9a3f655b8be1b93334ed8decf9fe6fa8bbf2
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5827518"
---
# <a name="adding-input-and-interactivity-to-the-marble-maze-sample"></a><span data-ttu-id="11bb3-104">Hinzufügen von Eingaben und Interaktivität zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="11bb3-104">Adding input and interactivity to the Marble Maze sample</span></span>




<span data-ttu-id="11bb3-105">UWP-Spiele können auf den verschiedensten Geräten ausgeführt werden, beispielsweise auf Desktopcomputern, Laptops und Tablets.</span><span class="sxs-lookup"><span data-stu-id="11bb3-105">Universal Windows Platform (UWP) games run on a wide variety of devices, such as desktop computers, laptops, and tablets.</span></span> <span data-ttu-id="11bb3-106">Für ein Gerät sind viele verschiedene Eingabe- und Steuerungsmechanismen möglich.</span><span class="sxs-lookup"><span data-stu-id="11bb3-106">A device can have a plethora of input and control mechanisms.</span></span> <span data-ttu-id="11bb3-107">In diesem Dokument werden die wichtigsten Methoden beschrieben, die Sie berücksichtigen sollten, wenn Sie mit Eingabegeräten arbeiten. Außerdem erfahren Sie, wie diese Methoden in Marble Maze angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-107">This document describes the key practices to keep in mind when you work with input devices and shows how Marble Maze applies these practices.</span></span>

> [!NOTE]
> <span data-ttu-id="11bb3-108">Den Beispielcode für dieses Dokument finden Sie im [DirectX-Beispielspiel Marble Maze](http://go.microsoft.com/fwlink/?LinkId=624011).</span><span class="sxs-lookup"><span data-stu-id="11bb3-108">The sample code that corresponds to this document is found in the [DirectX Marble Maze game sample](http://go.microsoft.com/fwlink/?LinkId=624011).</span></span>

 
<span data-ttu-id="11bb3-109">Hier sind einige der wichtigsten in diesem Dokument erörterten Punkte für das Arbeiten mit Eingaben in Ihrem Spiel:</span><span class="sxs-lookup"><span data-stu-id="11bb3-109">Here are some of the key points that this document discusses for when you work with input in your game:</span></span>

-   <span data-ttu-id="11bb3-110">Unterstützen Sie nach Möglichkeit mehrere Eingabegeräte, damit die Kunden Ihr Spiel ganz nach ihren persönlichen Vorlieben und Fähigkeiten spielen können.</span><span class="sxs-lookup"><span data-stu-id="11bb3-110">When possible, support multiple input devices to enable your game to accommodate a wider range of preferences and abilities among your customers.</span></span> <span data-ttu-id="11bb3-111">Die Verwendung eines Gamecontrollers und Sensors ist zwar optional, wird aber dringend empfohlen, um die Benutzerfreundlichkeit für die Spieler zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-111">Although game controller and sensor usage is optional, we strongly recommend it to enhance the player experience.</span></span> <span data-ttu-id="11bb3-112">Die APIs für Gamecontroller und Sensoren soll Ihnen die Integration dieser Eingabegeräte erleichtern.</span><span class="sxs-lookup"><span data-stu-id="11bb3-112">We designed the game controller and sensor APIs to help you more easily integrate these input devices.</span></span>

-   <span data-ttu-id="11bb3-113">Zum Initialisieren der Toucheingabe müssen Sie sich für Windows-Ereignisse registrieren, beispielsweise für das Aktivieren, Freigeben und Verschieben des Zeigers.</span><span class="sxs-lookup"><span data-stu-id="11bb3-113">To initialize touch, you must register for window events such as when the pointer is activated, released, and moved.</span></span> <span data-ttu-id="11bb3-114">Zum Initialisieren des Beschleunigungsmessers erstellen Sie ein [Windows::Devices::Sensors::Accelerometer](https://msdn.microsoft.com/library/windows/apps/br225687)-Objekt, wenn Sie die Anwendung initialisieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-114">To initialize the accelerometer, create a [Windows::Devices::Sensors::Accelerometer](https://msdn.microsoft.com/library/windows/apps/br225687) object when you initialize the application.</span></span> <span data-ttu-id="11bb3-115">Der Xbox-Controller muss nicht initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-115">The Xbox controller doesn't require initialization.</span></span>

-   <span data-ttu-id="11bb3-116">Überlegen Sie bei Spielen für einen Spieler, ob Sie die Eingaben aller möglichen Xbox-Controller kombinieren möchten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-116">For single-player games, consider whether to combine input from all possible Xbox controllers.</span></span> <span data-ttu-id="11bb3-117">Auf diese Weise müssen Sie nicht nachverfolgen, welche Eingabe von welchem Controller kommt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-117">This way, you don’t have to track what input comes from which controller.</span></span> <span data-ttu-id="11bb3-118">Oder verfolgen Sie einfach die Eingaben vom zuletzt hinzugefügten Controller nach, wie in diesem Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-118">Or, simply track input only from the most recently added controller, as we do in this sample.</span></span>

-   <span data-ttu-id="11bb3-119">Verarbeiten Sie erst Windows-Ereignisse und dann Eingabegeräte.</span><span class="sxs-lookup"><span data-stu-id="11bb3-119">Process Windows events before you process input devices.</span></span>

-   <span data-ttu-id="11bb3-120">Der Xbox-Controller und der Beschleunigungsmesser unterstützen Abrufe.</span><span class="sxs-lookup"><span data-stu-id="11bb3-120">The Xbox controller and the accelerometer support polling.</span></span> <span data-ttu-id="11bb3-121">Das heißt, Sie können Daten abrufen, wenn Sie sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-121">That is, you can poll for data when you need it.</span></span> <span data-ttu-id="11bb3-122">Für die Toucheingabe sollten Sie Touchereignisse in Datenstrukturen aufzeichnen, die für Ihren Eingabeverarbeitungscode verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="11bb3-122">For touch, record touch events in data structures that are available to your input processing code.</span></span>

-   <span data-ttu-id="11bb3-123">Überlegen Sie, ob Sie Eingabewerte in ein gemeinsames Format normalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-123">Consider whether to normalize input values to a common format.</span></span> <span data-ttu-id="11bb3-124">Auf diese Weise können Sie die Interpretation der Eingabe durch andere Komponenten des Spiels wie beispielsweise die Simulation von Physikeffekten vereinfachen und leichter Spiele schreiben, die sich für unterschiedliche Bildschirmauflösungen eignen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-124">Doing so can simplify how input is interpreted by other components of your game, such as physics simulation, and can make it easier to write games that work on different screen resolutions.</span></span>

## <a name="input-devices-supported-by-marble-maze"></a><span data-ttu-id="11bb3-125">Von Marble Maze unterstützte Eingabegeräte</span><span class="sxs-lookup"><span data-stu-id="11bb3-125">Input devices supported by Marble Maze</span></span>


<span data-ttu-id="11bb3-126">Marble Maze unterstützt Xbox-Controller, Maus und Toucheingabe zum Auswählen von Menüelementen und Xbox-Controller, Maus, Toucheingabe und Beschleunigungsmesser zum Steuern des Spielverlaufs.</span><span class="sxs-lookup"><span data-stu-id="11bb3-126">Marble Maze supports the Xbox controller, mouse, and touch to select menu items, and the Xbox controller, mouse, touch, and the accelerometer to control game play.</span></span> <span data-ttu-id="11bb3-127">Marble Maze ruft die Eingaben vom Controller mithilfe der [Windows::Gaming::Input](https://docs.microsoft.com/uwp/api/windows.gaming.input)-API ab.</span><span class="sxs-lookup"><span data-stu-id="11bb3-127">Marble Maze uses the [Windows::Gaming::Input](https://docs.microsoft.com/uwp/api/windows.gaming.input) APIs to poll the controller for input.</span></span> <span data-ttu-id="11bb3-128">Bei der Toucheingabe können Anwendungen Eingaben mit der Fingerspitze nachverfolgen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-128">Touch enables applications to track and respond to fingertip input.</span></span> <span data-ttu-id="11bb3-129">Ein Beschleunigungsmesser ist ein Sensor, der die Kraft misst, die entlang der X-, Y- und Z-Achsen angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-129">An accelerometer is a sensor that measures the force that is applied along the X, Y, and Z axes.</span></span> <span data-ttu-id="11bb3-130">Mit der Windows-Runtime können Sie den aktuellen Zustand des Beschleunigungsmessers abrufen und Touchereignisse über den Ereignisbehandlungsmechanismus der Windows-Runtime empfangen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-130">By using the Windows Runtime, you can poll the current state of the accelerometer device, as well as receive touch events through the Windows Runtime event-handling mechanism.</span></span>

> [!NOTE]
> <span data-ttu-id="11bb3-131">In diesem Dokument wird der Begriff Toucheingabe für Touch- und Mauseingabe und sowie Zeigereingabe verwendet. Damit sind alle Geräte gemeint, die Zeigerereignisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-131">This document uses touch to refer to both touch and mouse input and pointer to refer to any device that uses pointer events.</span></span> <span data-ttu-id="11bb3-132">Da bei der Touch- und Mauseingabe Standardzeigerereignisse verwendet werden, können Sie jedes der Geräte verwenden, um Menüelemente auszuwählen und den Spielverlauf zu steuern.</span><span class="sxs-lookup"><span data-stu-id="11bb3-132">Because touch and the mouse use standard pointer events, you can use either device to select menu items and control game play.</span></span>

 

> [!NOTE]
> <span data-ttu-id="11bb3-133">Das Paketmanifest legt das **Querformat** als unterstützte Drehung für das Spiel fest. Damit wird verhindert, dass sich die Ausrichtung ändert, wenn Sie das Gerät drehen, um die Murmel zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-133">The package manifest sets **Landscape** as the only supported rotation for the game to prevent the orientation from changing when you rotate the device to roll the marble.</span></span> <span data-ttu-id="11bb3-134">Um das Paketmanifest zu sehen, öffnen Sie **Package.appxmanifest** unter **Solution Explorer** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11bb3-134">To view the package manifest, open **Package.appxmanifest** in the **Solution Explorer** in Visual Studio.</span></span>

 

## <a name="initializing-input-devices"></a><span data-ttu-id="11bb3-135">Initialisieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="11bb3-135">Initializing input devices</span></span>


<span data-ttu-id="11bb3-136">Der Xbox-Controller muss nicht initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-136">The Xbox controller does not require initialization.</span></span> <span data-ttu-id="11bb3-137">Zum Initialisieren der Toucheingabe müssen Sie sich für Windows-Ereignisse registrieren, beispielsweise für das Aktivieren (z. B. wenn der Benutzer die Maustaste drückt oder den Bildschirm berührt), Freigeben und Verschieben des Zeigers.</span><span class="sxs-lookup"><span data-stu-id="11bb3-137">To initialize touch, you must register for windowing events such as when the pointer is activated (for example, the player presses the mouse button or touches the screen), released, and moved.</span></span> <span data-ttu-id="11bb3-138">Zum Initialisieren des Beschleunigungsmessers müssen Sie ein [Windows::Devices::Sensors::Accelerometer](https://msdn.microsoft.com/library/windows/apps/br225687)-Objekt erstellen, wenn Sie die Anwendung initialisieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-138">To initialize the accelerometer, you have to create a [Windows::Devices::Sensors::Accelerometer](https://msdn.microsoft.com/library/windows/apps/br225687) object when you initialize the application.</span></span>

<span data-ttu-id="11bb3-139">Im folgenden Beispiel wird dargestellt, wie die **App::SetWindow**-Methode für die Zeigerereignisse [Windows::UI::Core::CoreWindow::PointerPressed](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerPressed) und [Windows::UI::Core::CoreWindow::PointerReleased](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerReleased) des [Windows::UI::Core::CoreWindow::PointerMoved](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerMoved)-Elements registriert wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-139">The following example shows how the **App::SetWindow** method registers for the [Windows::UI::Core::CoreWindow::PointerPressed](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerPressed), [Windows::UI::Core::CoreWindow::PointerReleased](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerReleased), and [Windows::UI::Core::CoreWindow::PointerMoved](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow.PointerMoved) pointer events.</span></span> <span data-ttu-id="11bb3-140">Diese Ereignisse werden bei der Initialisierung der App und vor der Spielschleife registriert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-140">These events are registered during application initialization and before the game loop.</span></span>

<span data-ttu-id="11bb3-141">Die Ereignisse werden in einem separaten Thread behandelt, über den die Ereignishandler aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-141">These events are handled in a separate thread that invokes the event handlers.</span></span>

<span data-ttu-id="11bb3-142">Weitere Informationen zum Initialisieren der Anwendung finden Sie unter [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md).</span><span class="sxs-lookup"><span data-stu-id="11bb3-142">For more information about how the application is initialized, see [Marble Maze application structure](marble-maze-application-structure.md).</span></span>

```cpp
window->PointerPressed += ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(
    this, 
    &App::OnPointerPressed);

window->PointerReleased += ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(
    this, 
    &App::OnPointerReleased);

window->PointerMoved += ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(
    this, 
    &App::OnPointerMoved);
```

<span data-ttu-id="11bb3-143">Die **MarbleMazeMain**-Klasse erstellt außerdem ein **std::map**-Objekt für Touchereignisse.</span><span class="sxs-lookup"><span data-stu-id="11bb3-143">The **MarbleMazeMain** class also creates a **std::map** object to hold touch events.</span></span> <span data-ttu-id="11bb3-144">Der Schlüssel für dieses Zuordnungsobjekt ist ein Wert, der den Eingabezeiger eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-144">The key for this map object is a value that uniquely identifies the input pointer.</span></span> <span data-ttu-id="11bb3-145">Jeder Schlüssel ist der Entfernung zwischen jedem Touchpunkt und der Mitte des Bildschirms zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="11bb3-145">Each key maps to the distance between every touch point and the center of the screen.</span></span> <span data-ttu-id="11bb3-146">Diese Werte verwendet Marble Maze später, um die Neigung des Labyrinths zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-146">Marble Maze later uses these values to calculate the amount by which the maze is tilted.</span></span>

```cpp
typedef std::map<int, XMFLOAT2> TouchMap;
TouchMap        m_touches;
```

<span data-ttu-id="11bb3-147">Die **MarbleMazeMain**-Klasse enthält ein [Beschleunigungsmesserobjekt](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer).</span><span class="sxs-lookup"><span data-stu-id="11bb3-147">The **MarbleMazeMain** class also holds an [Accelerometer](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer) object.</span></span>

```cpp
Windows::Devices::Sensors::Accelerometer^           m_accelerometer;
```

<span data-ttu-id="11bb3-148">Das **Beschleunigungsmesserobjekt** wird wie im folgenden Beispiel in der **MarbleMazeMain**-Konstruktor initialisiert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-148">The **Accelerometer** object is initialized in the **MarbleMazeMain** constructor, as shown in the following example.</span></span> <span data-ttu-id="11bb3-149">Die [Windows::Devices::Sensors::Accelerometer::GetDefault](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer.GetDefault)-Methode gibt eine Instanz des Standardbeschleunigungsmessers zurück.</span><span class="sxs-lookup"><span data-stu-id="11bb3-149">The [Windows::Devices::Sensors::Accelerometer::GetDefault](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer.GetDefault) method returns an instance of the default accelerometer.</span></span> <span data-ttu-id="11bb3-150">Wenn kein Standardbeschleunigungsmesser vorhanden ist, bleibt der **Accelerometer::GetDefault**-Wert **nullptr**.</span><span class="sxs-lookup"><span data-stu-id="11bb3-150">If there is no default accelerometer, **Accelerometer::GetDefault** returns **nullptr**.</span></span>

```cpp
// Returns accelerometer ref if there is one; nullptr otherwise.
m_accelerometer = Windows::Devices::Sensors::Accelerometer::GetDefault();
```

##  <a name="navigating-the-menus"></a><span data-ttu-id="11bb3-151">Navigieren in den Menüs</span><span class="sxs-lookup"><span data-stu-id="11bb3-151">Navigating the menus</span></span>

<span data-ttu-id="11bb3-152">Sie haben folgende Möglichkeiten, mit der Maus, mit Toucheingabe oder mit dem Xbox-Controller in den Menüs zu navigieren:</span><span class="sxs-lookup"><span data-stu-id="11bb3-152">You can use the mouse, touch, or the Xbox controller to navigate the menus, as follows:</span></span>

-   <span data-ttu-id="11bb3-153">Verwenden Sie das Steuerkreuz, um das aktive Menüelement zu ändern.</span><span class="sxs-lookup"><span data-stu-id="11bb3-153">Use the directional pad to change the active menu item.</span></span>
-   <span data-ttu-id="11bb3-154">Verwenden Sie Toucheingabe, die A-Taste oder die Menütaste, um ein Menüelement auszuwählen oder das aktuelle Menü zu schließen, beispielsweise die Highscoretabelle.</span><span class="sxs-lookup"><span data-stu-id="11bb3-154">Use touch, the A button, or the Menu button to pick a menu item or close the current menu, such as the high-score table.</span></span>
-   <span data-ttu-id="11bb3-155">Verwenden Sie die Menütaste, um das Spiel anzuhalten oder fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-155">Use the Menu button to pause or resume the game.</span></span>
-   <span data-ttu-id="11bb3-156">Klicken Sie mit der Maus auf ein Menüelement, um die jeweilige Aktion auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-156">Click on a menu item with the mouse to choose that action.</span></span>

###  <a name="tracking-xbox-controller-input"></a><span data-ttu-id="11bb3-157">Nachverfolgen von Xbox-Controllereingaben</span><span class="sxs-lookup"><span data-stu-id="11bb3-157">Tracking Xbox controller input</span></span>

<span data-ttu-id="11bb3-158">Um die derzeit verbundenen Gamepads nachzuverfolgen, definiert **MarbleMazeMain** eine Membervariable **M_myGamepads**, die eine Sammlung von [Windows::Gaming::Input::Gamepad](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad)-Objekten ist.</span><span class="sxs-lookup"><span data-stu-id="11bb3-158">To keep track of the gamepads currently connected to the device, **MarbleMazeMain** defines a member variable, **m_myGamepads**, which is a collection of [Windows::Gaming::Input::Gamepad](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad) objects.</span></span> <span data-ttu-id="11bb3-159">Dies wird im Konstruktor wie folgt initialisiert:</span><span class="sxs-lookup"><span data-stu-id="11bb3-159">This is initialized in the constructor like so:</span></span>

```cpp
m_myGamepads = ref new Vector<Gamepad^>();

for (auto gamepad : Gamepad::Gamepads)
{
    m_myGamepads->Append(gamepad);
}
```

<span data-ttu-id="11bb3-160">Darüber hinaus registriert der **MarbleMazeMain**-Konstruktor Ereignisse, wenn Gamepads hinzugefügt oder entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="11bb3-160">Additionally, the **MarbleMazeMain** constructor registers events for when gamepads are added or removed:</span></span>

```cpp
Gamepad::GamepadAdded += 
    ref new EventHandler<Gamepad^>([=](Platform::Object^, Gamepad^ args)
{
    m_myGamepads->Append(args);
    m_currentGamepadNeedsRefresh = true;
});

Gamepad::GamepadRemoved += 
    ref new EventHandler<Gamepad ^>([=](Platform::Object^, Gamepad^ args)
{
    unsigned int indexRemoved;

    if (m_myGamepads->IndexOf(args, &indexRemoved))
    {
        m_myGamepads->RemoveAt(indexRemoved);
        m_currentGamepadNeedsRefresh = true;
    }
});
```

<span data-ttu-id="11bb3-161">Wenn ein Gamepad hinzugefügt wird, wird dieser **M_myGamepads** hinzugefügt; wenn ein Gamepad entfernt wird, wird überprüft, ob das Gamepad **M_myGamepads** ist, und wenn dies der Fall ist, entfernen wir diesen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-161">When a gamepad is added, it is added to **m_myGamepads**; when a gamepad is removed, we check if the gamepad is in **m_myGamepads**, and if it is, we remove it.</span></span> <span data-ttu-id="11bb3-162">In beiden Fällen legen wir **M_currentGamepadNeedsRefresh** auf **true** fest, was angibt, das wir **M_gamepad** erneut zuweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-162">In both cases, we set **m_currentGamepadNeedsRefresh** to **true**, indicating that we need to reassign **m_gamepad**.</span></span>

<span data-ttu-id="11bb3-163">Schließlich legen wir ein Gamepad, **M_gamepad** und **M_currentGamepadNeedsRefresh** auf **false** fest:</span><span class="sxs-lookup"><span data-stu-id="11bb3-163">Finally, we assign a gamepad to **m_gamepad** and set **m_currentGamepadNeedsRefresh** to **false**:</span></span>

```cpp
m_gamepad = GetLastGamepad();
m_currentGamepadNeedsRefresh = false;
```

<span data-ttu-id="11bb3-164">In der **Update** -Methode wird überprüft, ob **M_gamepad** neu zugewiesen werden muss:</span><span class="sxs-lookup"><span data-stu-id="11bb3-164">In the **Update** method, we check if **m_gamepad** needs to be reassigned:</span></span>

```cpp
if (m_currentGamepadNeedsRefresh)
{
    auto mostRecentGamepad = GetLastGamepad();

    if (m_gamepad != mostRecentGamepad)
    {
        m_gamepad = mostRecentGamepad;
    }

    m_currentGamepadNeedsRefresh = false;
}
```

<span data-ttu-id="11bb3-165">Wenn **M_gamepad** neu zugeordnet werden muss, müssen wir ihm den zuletzt hinzugefügten Gamepads mit **GetLastGamepad** zuweisen, der wie folgt definiert wird:</span><span class="sxs-lookup"><span data-stu-id="11bb3-165">If **m_gamepad** does need to be reassigned, we assign to it the most recently added gamepad, using **GetLastGamepad**, which is defined like so:</span></span>

```cpp
Gamepad^ MarbleMaze::MarbleMazeMain::GetLastGamepad()
{
    Gamepad^ gamepad = nullptr;

    if (m_myGamepads->Size > 0)
    {
        gamepad = m_myGamepads->GetAt(m_myGamepads->Size - 1);
    }

    return gamepad;
}
```

<span data-ttu-id="11bb3-166">Diese Methode gibt einfach den letzten Gamepad **M_myGamepads** zurück.</span><span class="sxs-lookup"><span data-stu-id="11bb3-166">This method simply returns the last gamepad in **m_myGamepads**.</span></span>

<span data-ttu-id="11bb3-167">Sie können an ein Windows 10-Gerät bis zu vier Xbox-Controller anschließen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-167">You can connect up to four Xbox controllers to a Windows 10 device.</span></span> <span data-ttu-id="11bb3-168">Um zu vermeiden, dass Sie herausfinden müssen, welcher Controller aktiv ist, verfolgen wir einfach nur Titel des zuletzt hinzugefügten Gamepads.</span><span class="sxs-lookup"><span data-stu-id="11bb3-168">To avoid having to figure out which controller is the active one, we simply only track the most recently added gamepad.</span></span> <span data-ttu-id="11bb3-169">Wenn Ihr Spiel mehrere Spieler unterstützt, müssen Sie die Eingabe für jeden Spieler getrennt nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-169">If your game supports more than one player, you have to track input for each player separately.</span></span>

<span data-ttu-id="11bb3-170">Die **MarbleMazeMain::Update**-Methode fragt das Gamepad für die Eingabe ab:</span><span class="sxs-lookup"><span data-stu-id="11bb3-170">The **MarbleMazeMain::Update** method polls the gamepad for input:</span></span>

```cpp
if (m_gamepad != nullptr)
{
    m_oldReading = m_newReading;
    m_newReading = m_gamepad->GetCurrentReading();
}
```

<span data-ttu-id="11bb3-171">Wir behalten Sie den Überblick über die Eingabe durch den letzten Frame mit **m_oldReading** und die letzte Eingabe mit **m_newReading**, die wir durch Aufrufen von [Gamepad::GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.GetCurrentReading) erhalten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-171">We keep track of the input reading we got in the last frame with **m_oldReading**, and the latest input reading with **m_newReading**, which we get by calling [Gamepad::GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.GetCurrentReading).</span></span> <span data-ttu-id="11bb3-172">Dies gibt ein [GamepadReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadreading)-Objekt zurück, das Informationen über den aktuellen Zustand des Gamepads enthält.</span><span class="sxs-lookup"><span data-stu-id="11bb3-172">This returns a [GamepadReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadreading) object, which contains information about the current state of the gamepad.</span></span>

<span data-ttu-id="11bb3-173">Um zu überprüfen, ob eine Schaltfläche einfach gedrückt oder losgelassen wurde, definieren wir **MarbleMazeMain::ButtonJustPressed** und **MarbleMazeMain::ButtonJustReleased**, was die Tasteneingabe aus diesem und dem letzten Frame vergleicht.</span><span class="sxs-lookup"><span data-stu-id="11bb3-173">To check if a button was just pressed or released, we define **MarbleMazeMain::ButtonJustPressed** and **MarbleMazeMain::ButtonJustReleased**, which compare button readings from this frame and the last frame.</span></span> <span data-ttu-id="11bb3-174">So kann eine Aktion nur beim ersten Drücken einer Taste ausgeführt werden und nicht, wenn die Taste gedrückt gehalten oder losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-174">This way, we can perform an action only at the time when a button is initially pressed or released, and not when it's held:</span></span>

```cpp
bool MarbleMaze::MarbleMazeMain::ButtonJustPressed(GamepadButtons selection)
{
    bool newSelectionPressed = (selection == (m_newReading.Buttons & selection));
    bool oldSelectionPressed = (selection == (m_oldReading.Buttons & selection));
    return newSelectionPressed && !oldSelectionPressed;
}

bool MarbleMaze::MarbleMazeMain::ButtonJustReleased(GamepadButtons selection)
{
    bool newSelectionReleased = 
        (GamepadButtons::None == (m_newReading.Buttons & selection));

    bool oldSelectionReleased = 
        (GamepadButtons::None == (m_oldReading.Buttons & selection));

    return newSelectionReleased && !oldSelectionReleased;
}
```

<span data-ttu-id="11bb3-175">[GamepadButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadbuttons)-Messwerte werden mit bitweisen Operationen&mdash;verglichen und es wird überprüft, ob eine Schaltfläche mit *bitweise und* (&) geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-175">[GamepadButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadbuttons) readings are compared using bitwise operations&mdash;we check if a button is pressed using *bitwise and* (&).</span></span> <span data-ttu-id="11bb3-176">Wir ermitteln, ob eine Schaltfläche einfach gedrückt oder losgelassen wurde, indem der alte Messwert und der neue Messwert verglichen werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-176">We determine whether a button was just pressed or released by comparing the old reading and the new reading.</span></span>

<span data-ttu-id="11bb3-177">Mithilfe der oben aufgeführten Methoden, überprüfen wir, ob bestimmte Schaltflächen gedrückt wurden und führen die entsprechenden Aktionen aus.</span><span class="sxs-lookup"><span data-stu-id="11bb3-177">Using the above methods, we check if certain buttons have been pressed and perform any corresponding actions that must happen.</span></span> <span data-ttu-id="11bb3-178">Wenn beispielsweise die Menütaste (**GamepadButtons::Menu**) gedrückt wird, ändert sich der Spielzustand von aktiv in angehalten oder von angehalten in aktiv.</span><span class="sxs-lookup"><span data-stu-id="11bb3-178">For example, when the Menu button (**GamepadButtons::Menu**) is pressed, the game state changes from active to paused or paused to active.</span></span>

```cpp
if (ButtonJustPressed(GamepadButtons::Menu) || m_pauseKeyPressed)
{
    m_pauseKeyPressed = false;

    if (m_gameState == GameState::InGameActive)
    {
        SetGameState(GameState::InGamePaused);
    }  
    else if (m_gameState == GameState::InGamePaused)
    {
        SetGameState(GameState::InGameActive);
    }
}
```

<span data-ttu-id="11bb3-179">Es wird auch überprüft, ob der Spieler die Ansicht-Taste drückt. In diesem Fall starten wir das Spiel erneut oder löschen die hohe Highscore-Tabelle:</span><span class="sxs-lookup"><span data-stu-id="11bb3-179">We also check if the player presses the View button, in which case we restart the game or clear the high score table:</span></span>

```cpp
if (ButtonJustPressed(GamepadButtons::View) || m_homeKeyPressed)
{
    m_homeKeyPressed = false;

    if (m_gameState == GameState::InGameActive ||
        m_gameState == GameState::InGamePaused ||
        m_gameState == GameState::PreGameCountdown)
    {
        SetGameState(GameState::MainMenu);
        m_inGameStopwatchTimer.SetVisible(false);
        m_preGameCountdownTimer.SetVisible(false);
    }
    else if (m_gameState == GameState::HighScoreDisplay)
    {
        m_highScoreTable.Reset();
    }
}
```

<span data-ttu-id="11bb3-180">Wenn das Hauptmenü aktiv ist, ändert sich das aktive Menüelement, sobald das Steuerkreuz nach oben oder nach unten gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-180">If the main menu is active, the active menu item changes when the directional pad is pressed up or down.</span></span> <span data-ttu-id="11bb3-181">Wenn der Benutzer die aktuelle Auswahl auswählt, wird das entsprechende UI-Element als ausgewählt markiert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-181">If the user chooses the current selection, the appropriate UI element is marked as being chosen.</span></span>

```cpp
// Handle menu navigation.
bool chooseSelection = 
    (ButtonJustPressed(GamepadButtons::A) 
    || ButtonJustPressed(GamepadButtons::Menu));

bool moveUp = ButtonJustPressed(GamepadButtons::DPadUp);
bool moveDown = ButtonJustPressed(GamepadButtons::DPadDown);

switch (m_gameState)
{
case GameState::MainMenu:
    if (chooseSelection)
    {
        m_audio.PlaySoundEffect(MenuSelectedEvent);
        if (m_startGameButton.GetSelected())
        {
            m_startGameButton.SetPressed(true);
        }
        if (m_highScoreButton.GetSelected())
        {
            m_highScoreButton.SetPressed(true);
        }
    }
    if (moveUp || moveDown)
    {
        m_startGameButton.SetSelected(!m_startGameButton.GetSelected());
        m_highScoreButton.SetSelected(!m_startGameButton.GetSelected());
        m_audio.PlaySoundEffect(MenuChangeEvent);
    }
    break;

case GameState::HighScoreDisplay:
    if (chooseSelection || anyPoints)
    {
        SetGameState(GameState::MainMenu);
    }
    break;

case GameState::PostGameResults:
    if (chooseSelection || anyPoints)
    {
        SetGameState(GameState::HighScoreDisplay);
    }
    break;

case GameState::InGamePaused:
    if (m_pausedText.IsPressed())
    {
        m_pausedText.SetPressed(false);
        SetGameState(GameState::InGameActive);
    }
    break;
}
```

### <a name="tracking-touch-and-mouse-input"></a><span data-ttu-id="11bb3-182">Nachverfolgen von Touch- und Mauseingaben</span><span class="sxs-lookup"><span data-stu-id="11bb3-182">Tracking touch and mouse input</span></span>

<span data-ttu-id="11bb3-183">Bei der Touch- und Mauseingabe wird ein Menüelement ausgewählt, wenn der Benutzer das Element berührt oder darauf klickt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-183">For touch and mouse input, a menu item is chosen when the user touches or clicks it.</span></span> <span data-ttu-id="11bb3-184">Das folgende Beispiel zeigt, wie die **MarbleMazeMain::Update**-Methode die Zeigereingabe verarbeitet, um Menüelemente auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-184">The following example shows how the **MarbleMazeMain::Update** method processes pointer input to select menu items.</span></span> <span data-ttu-id="11bb3-185">Die **m\_pointQueue**-Membervariable verfolgt die Stellen auf dem Bildschirm nach, die der Benutzer berührt hat oder auf die er geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="11bb3-185">The **m\_pointQueue** member variable tracks the locations where the user touched or clicked on the screen.</span></span> <span data-ttu-id="11bb3-186">Im Abschnitt [Verarbeiten von Zeigereingaben](#processing-pointer-input) wird ausführlicher beschrieben, wie Marble Maze die Zeigereingaben erfasst.</span><span class="sxs-lookup"><span data-stu-id="11bb3-186">The way in which Marble Maze collects pointer input is described in greater detail later in this document in the section [Processing pointer input](#processing-pointer-input).</span></span>

```cpp
// Check whether the user chose a button from the UI. 
bool anyPoints = !m_pointQueue.empty();
while (!m_pointQueue.empty())
{
    UserInterface::GetInstance().HitTest(m_pointQueue.front());
    m_pointQueue.pop();
}
```

<span data-ttu-id="11bb3-187">Die **UserInterface::HitTest**-Methode ermittelt, ob sich der angegebene Punkt innerhalb der Grenzen eines UI-Elements befindet.</span><span class="sxs-lookup"><span data-stu-id="11bb3-187">The **UserInterface::HitTest** method determines whether the provided point is located in the bounds of any UI element.</span></span> <span data-ttu-id="11bb3-188">Alle UI-Elemente, die diesen Test bestanden haben, werden als berührt markiert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-188">Any UI elements that pass this test are marked as being touched.</span></span> <span data-ttu-id="11bb3-189">Diese Methode ermittelt mit der **PointInRect**-Hilfsfunktion, ob sich der angegebene Punkt innerhalb der Grenzen der einzelnen UI-Elemente befindet.</span><span class="sxs-lookup"><span data-stu-id="11bb3-189">This method uses the **PointInRect** helper function to determine whether the provided point is located in the bounds of each UI element.</span></span>

```cpp
void UserInterface::HitTest(D2D1_POINT_2F point)
{
    for (auto iter = m_elements.begin(); iter != m_elements.end(); ++iter)
    {
        if (!(*iter)->IsVisible())
            continue;

        TextButton* textButton = dynamic_cast<TextButton*>(*iter);
        if (textButton != nullptr)
        {
            D2D1_RECT_F bounds = (*iter)->GetBounds();
            textButton->SetPressed(PointInRect(point, bounds));
        }
    }
}
```

### <a name="updating-the-game-state"></a><span data-ttu-id="11bb3-190">Upgrade des Spielzustands</span><span class="sxs-lookup"><span data-stu-id="11bb3-190">Updating the game state</span></span>

<span data-ttu-id="11bb3-191">Wenn die **MarbleMazeMain::Update**-Methode die Controller- und Toucheingabe verarbeitet hat und eine Taste gedrückt wurde, aktualisiert sie den Spielzustand.</span><span class="sxs-lookup"><span data-stu-id="11bb3-191">After the **MarbleMazeMain::Update** method processes controller and touch input, it updates the game state if any button was pressed.</span></span>

```cpp
// Update the game state if the user chose a menu option. 
if (m_startGameButton.IsPressed())
{
    SetGameState(GameState::PreGameCountdown);
    m_startGameButton.SetPressed(false);
}
if (m_highScoreButton.IsPressed())
{
    SetGameState(GameState::HighScoreDisplay);
    m_highScoreButton.SetPressed(false);
}
```

##  <a name="controlling-game-play"></a><span data-ttu-id="11bb3-192">Steuern des Spielverlaufs</span><span class="sxs-lookup"><span data-stu-id="11bb3-192">Controlling game play</span></span>


<span data-ttu-id="11bb3-193">Die Spielschleife und die **MarbleMazeMain::Update**-Methode aktualisieren gemeinsam den Zustand der Spielobjekte.</span><span class="sxs-lookup"><span data-stu-id="11bb3-193">The game loop and the **MarbleMazeMain::Update** method work together to update the state of game objects.</span></span> <span data-ttu-id="11bb3-194">Wenn Ihr Spiel Eingaben von mehreren Geräten akzeptiert, können Sie die Eingaben aller Geräte in einem Satz von Variablen sammeln. Auf diese Weise können Sie Code schreiben, der sich leichter verwalten lässt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-194">If your game accepts input from multiple devices, you can accumulate the input from all devices into one set of variables so that you can write code that's easier to maintain.</span></span> <span data-ttu-id="11bb3-195">Die **MarbleMazeMain::Update**-Methode definiert einen Variablensatz, mit dem Bewegungen von allen Geräten gesammelt werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-195">The **MarbleMazeMain::Update** method defines one set of variables that accumulates movement from all devices.</span></span>

```cpp
float combinedTiltX = 0.0f;
float combinedTiltY = 0.0f;
```

<span data-ttu-id="11bb3-196">Die Eingabemechanismen der einzelnen Eingabegeräte können dabei unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="11bb3-196">The input mechanism can vary from one input device to another.</span></span> <span data-ttu-id="11bb3-197">Beispielsweise werden Zeigereingaben mit dem Ereignisbehandlungsmodell der Windows-Runtime behandelt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-197">For example, pointer input is handled by using the Windows Runtime event-handling model.</span></span> <span data-ttu-id="11bb3-198">Die Eingabedaten des Xbox-Controllers dagegen rufen Sie bei Bedarf ab.</span><span class="sxs-lookup"><span data-stu-id="11bb3-198">Conversely, you poll for input data from the Xbox controller when you need it.</span></span> <span data-ttu-id="11bb3-199">Am besten halten Sie sich immer an die Eingabemechanismen, die für ein bestimmtes Gerät vorgeschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="11bb3-199">We recommend that you always follow the input mechanism that is prescribed for a given device.</span></span> <span data-ttu-id="11bb3-200">In diesem Abschnitt wird beschrieben, wie Marble Maze die Eingaben von den einzelnen Geräten liest, die kombinierten Eingabewerte aktualisiert und sie verwendet, um den Spielzustand zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-200">This section describes how Marble Maze reads input from each device, how it updates the combined input values, and how it uses the combined input values to update the state of the game.</span></span>

###  <a name="processing-pointer-input"></a><span data-ttu-id="11bb3-201">Verarbeiten von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="11bb3-201">Processing pointer input</span></span>

<span data-ttu-id="11bb3-202">Wenn Sie mit Zeigereingaben arbeiten, rufen Sie die [Windows::UI::Core::CoreDispatcher::ProcessEvents](https://docs.microsoft.com/uwp/api/windows.ui.core.coredispatcher.processevents)-Methode auf, um Windows-Ereignisse zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-202">When you work with pointer input, call the [Windows::UI::Core::CoreDispatcher::ProcessEvents](https://docs.microsoft.com/uwp/api/windows.ui.core.coredispatcher.processevents) method to process window events.</span></span> <span data-ttu-id="11bb3-203">Rufen Sie diese Methode in Ihrer Spielschleife auf, bevor Sie die Szene aktualisieren oder rendern.</span><span class="sxs-lookup"><span data-stu-id="11bb3-203">Call this method in your game loop before you update or render the scene.</span></span> <span data-ttu-id="11bb3-204">Marble Maze ruft dies in der **Implementierungscode**-Methode auf:</span><span class="sxs-lookup"><span data-stu-id="11bb3-204">Marble Maze calls this in the **App::Run** method:</span></span> 

```cpp
while (!m_windowClosed)
{
    if (m_windowVisible)
    {
        CoreWindow::GetForCurrentThread()->
            Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

        m_main->Update();

        if (m_main->Render())
        {
            m_deviceResources->Present();
        }
    }
    else
    {
        CoreWindow::GetForCurrentThread()->
            Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
    }
}
```

<span data-ttu-id="11bb3-205">Wenn das Fenster sichtbar ist, übergeben wir **CoreProcessEventsOption::ProcessAllIfPresent** an **ProcessEvents**, um alle Ereignisse in der Warteschlange sofort zu verarbeiten. Andernfalls übergeben wir **CoreProcessEventsOption::ProcessOneAndAllPending**, um alle Ereignisse in der Warteschlange zu verarbeiten und warten auf das das nächste neue Ereignis.</span><span class="sxs-lookup"><span data-stu-id="11bb3-205">If the window is visible, we pass **CoreProcessEventsOption::ProcessAllIfPresent** to **ProcessEvents** to process all queued events and return immediately; otherwise, we pass **CoreProcessEventsOption::ProcessOneAndAllPending** to process all queued events and wait for the next new event.</span></span> <span data-ttu-id="11bb3-206">Nach der Verarbeitung der Ereignisse rendert Marble Maze den nächsten Frame und zeigt ihn an.</span><span class="sxs-lookup"><span data-stu-id="11bb3-206">After events are processed, Marble Maze renders and presents the next frame.</span></span>

<span data-ttu-id="11bb3-207">Die Windows-Runtime ruft den registrierten Handler für jedes aufgetretene Ereignis auf.</span><span class="sxs-lookup"><span data-stu-id="11bb3-207">The Windows Runtime calls the registered handler for each event that occurred.</span></span> <span data-ttu-id="11bb3-208">Die **App::SetWindow**-Methode registriert sich für Ereignisse und leitet Zeigerinformationen an die **MarbleMazeMain**-Klasse weiter.</span><span class="sxs-lookup"><span data-stu-id="11bb3-208">The **App::SetWindow** method registers for events and forwards pointer information to the **MarbleMazeMain** class.</span></span>

```cpp
void App::OnPointerPressed(
    Windows::UI::Core::CoreWindow^ sender, 
    Windows::UI::Core::PointerEventArgs^ args)
{
    m_main->AddTouch(args->CurrentPoint->PointerId, args->CurrentPoint->Position);
}

void App::OnPointerReleased(
    Windows::UI::Core::CoreWindow^ sender, 
    Windows::UI::Core::PointerEventArgs^ args)
{
    m_main->RemoveTouch(args->CurrentPoint->PointerId);
}

void App::OnPointerMoved(
    Windows::UI::Core::CoreWindow^ sender, 
    Windows::UI::Core::PointerEventArgs^ args)
{
    m_main->UpdateTouch(args->CurrentPoint->PointerId, args->CurrentPoint->Position);
}
```

<span data-ttu-id="11bb3-209">Die **MarbleMazeMain**-Klasse reagiert auf Zeigerereignisse, indem sie das Zuordnungsobjekt aktualisiert, das Touchereignisse enthält.</span><span class="sxs-lookup"><span data-stu-id="11bb3-209">The **MarbleMazeMain** class reacts to pointer events by updating the map object that holds touch events.</span></span> <span data-ttu-id="11bb3-210">Die **MarbleMazeMain::AddTouch**-Methode wird aufgerufen, wenn der Zeiger zum ersten Mal gedrückt wird. Dies ist beispielsweise der Fall, wenn der Benutzer zum ersten Mal den Bildschirm eines touchfähigen Geräts berührt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-210">The **MarbleMazeMain::AddTouch** method is called when the pointer is first pressed, for example, when the user initially touches the screen on a touch-enabled device.</span></span> <span data-ttu-id="11bb3-211">Die **MarbleMazeMain::UpdateTouch**-Methode wird aufgerufen, wenn die Zeigerposition verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-211">The **MarbleMazeMain::UpdateTouch** method is called when the pointer position moves.</span></span> <span data-ttu-id="11bb3-212">Die **MarbleMazeMain::RemoveTouch**-Methode wird aufgerufen, wenn der Zeiger losgelassen wird. Dies ist beispielsweise der Fall, wenn der Benutzer den Bildschirm nicht mehr berührt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-212">The **MarbleMazeMain::RemoveTouch** method is called when the pointer is released, for example, when the user stops touching the screen.</span></span>

```cpp
void MarbleMazeMain::AddTouch(int id, Windows::Foundation::Point point)
{
    m_touches[id] = PointToTouch(point, m_deviceResources->GetLogicalSize());

    m_pointQueue.push(D2D1::Point2F(point.X, point.Y));
}

void MarbleMazeMain::UpdateTouch(int id, Windows::Foundation::Point point)
{
    if (m_touches.find(id) != m_touches.end())
        m_touches[id] = PointToTouch(point, m_deviceResources->GetLogicalSize());
}

void MarbleMazeMain::RemoveTouch(int id)
{
    m_touches.erase(id);
}
```

<span data-ttu-id="11bb3-213">Die **PointToTouch**-Funktion verschiebt die aktuelle Zeigerposition, sodass sich der Ursprung in der Mitte des Bildschirms befindet. Dann skaliert sie die Koordinaten so, dass sie ungefähr zwischen -1,0 und +1,0 liegen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-213">The **PointToTouch** function translates the current pointer position so that the origin is in the center of the screen, and then scales the coordinates so that they range approximately between -1.0 and +1.0.</span></span> <span data-ttu-id="11bb3-214">Dadurch kann die einheitliche Neigung des Labyrinths für verschiedene Eingabemethoden leichter berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="11bb3-214">This makes it easier to calculate the tilt of the maze in a consistent way across different input methods.</span></span>

```cpp
inline XMFLOAT2 PointToTouch(Windows::Foundation::Point point, Windows::Foundation::Size bounds)
{
    float touchRadius = min(bounds.Width, bounds.Height);
    float dx = (point.X - (bounds.Width / 2.0f)) / touchRadius;
    float dy = ((bounds.Height / 2.0f) - point.Y) / touchRadius;

    return XMFLOAT2(dx, dy);
}
```

<span data-ttu-id="11bb3-215">Die **MarbleMazeMain::Update**-Methode aktualisiert die kombinierten Eingabewerte, indem sie den Neigungsfaktor um einen konstanten Skalierungswert erhöht.</span><span class="sxs-lookup"><span data-stu-id="11bb3-215">The **MarbleMazeMain::Update** method updates the combined input values by incrementing the tilt factor by a constant scaling value.</span></span> <span data-ttu-id="11bb3-216">Dieser Skalierungswert wurde durch Experimentieren mit verschiedenen Werten ermittelt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-216">This scaling value was determined by experimenting with several different values.</span></span>

```cpp
// Account for touch input.
for (TouchMap::const_iterator iter = m_touches.cbegin(); 
    iter != m_touches.cend(); 
    ++iter)
{
    combinedTiltX += iter->second.x * m_touchScaleFactor;
    combinedTiltY += iter->second.y * m_touchScaleFactor;
}
```

### <a name="processing-accelerometer-input"></a><span data-ttu-id="11bb3-217">Verarbeiten von Beschleunigungsmessereingaben</span><span class="sxs-lookup"><span data-stu-id="11bb3-217">Processing accelerometer input</span></span>

<span data-ttu-id="11bb3-218">Zur Verarbeitung von Beschleunigungsmessereingaben ruft die **MarbleMazeMain::Update**-Methode die [Windows::Devices::Sensors::Accelerometer::GetCurrentReading](https://msdn.microsoft.com/library/windows/apps/br225699)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="11bb3-218">To process accelerometer input, the **MarbleMazeMain::Update** method calls the [Windows::Devices::Sensors::Accelerometer::GetCurrentReading](https://msdn.microsoft.com/library/windows/apps/br225699) method.</span></span> <span data-ttu-id="11bb3-219">Diese Methode gibt ein [Windows::Devices::Sensors::AccelerometerReading](https://msdn.microsoft.com/library/windows/apps/br225688)-Objekt zurück, das die Ablesung eines Beschleunigungsmessers darstellt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-219">This method returns a [Windows::Devices::Sensors::AccelerometerReading](https://msdn.microsoft.com/library/windows/apps/br225688) object, which represents an accelerometer reading.</span></span> <span data-ttu-id="11bb3-220">Die Eigenschaften **Windows::Devices::Sensors::AccelerometerReading::AccelerationX** und **Windows::Devices::Sensors::AccelerometerReading::AccelerationY** enthalten die Schwerkraftbeschleunigung entlang der X-Achse bzw. der Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="11bb3-220">The **Windows::Devices::Sensors::AccelerometerReading::AccelerationX** and **Windows::Devices::Sensors::AccelerometerReading::AccelerationY** properties hold the g-force acceleration along the X and Y axes, respectively.</span></span>

<span data-ttu-id="11bb3-221">Das folgende Beispiel zeigt, wie die **MarbleMazeMain::Update**-Methode den Beschleunigungsmesser abruft und die kombinierten Eingabewerte aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-221">The following example shows how the **MarbleMazeMain::Update** method polls the accelerometer and updates the combined input values.</span></span> <span data-ttu-id="11bb3-222">Wenn Sie das Gerät neigen, bewegt sich die Murmel aufgrund der Schwerkraft schneller.</span><span class="sxs-lookup"><span data-stu-id="11bb3-222">As you tilt the device, gravity causes the marble to move faster.</span></span>

```cpp
// Account for sensors.
if (m_accelerometer != nullptr)
{
    Windows::Devices::Sensors::AccelerometerReading^ reading =
        m_accelerometer->GetCurrentReading();

    if (reading != nullptr)
    {
        combinedTiltX += 
            static_cast<float>(reading->AccelerationX) * m_accelerometerScaleFactor;

        combinedTiltY += 
            static_cast<float>(reading->AccelerationY) * m_accelerometerScaleFactor;
    }
}
```

<span data-ttu-id="11bb3-223">Da Sie nicht sicher sein können, dass der Computer des Benutzers über einen [Beschleunigungsmesser](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer) verfügt, müssen Sie immer sicherstellen, dass Sie ein gültiges Beschleunigungsmesserobjekt haben, und erst dann die Werte vom Beschleunigungsmesser abrufen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-223">Because you can't be sure that an accelerometer is present on the user’s computer, always ensure that you have a valid [Accelerometer](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Accelerometer) object before you poll the accelerometer.</span></span>

### <a name="processing-xbox-controller-input"></a><span data-ttu-id="11bb3-224">Verarbeiten von Xbox-Controllereingaben</span><span class="sxs-lookup"><span data-stu-id="11bb3-224">Processing Xbox controller input</span></span>

<span data-ttu-id="11bb3-225">In der **MarbleMazeMain::Update**-Methode verwenden wir **m_newReading**-Eingaben vom linken Analogstick:</span><span class="sxs-lookup"><span data-stu-id="11bb3-225">In the **MarbleMazeMain::Update** method, we use **m_newReading** to process input from the left analog stick:</span></span>

```cpp
float leftStickX = static_cast<float>(m_newReading.LeftThumbstickX);
float leftStickY = static_cast<float>(m_newReading.LeftThumbstickY);

auto oppositeSquared = leftStickY * leftStickY;
auto adjacentSquared = leftStickX * leftStickX;

if ((oppositeSquared + adjacentSquared) > m_deadzoneSquared)
{
    combinedTiltX += leftStickX * m_controllerScaleFactor;
    combinedTiltY += leftStickY * m_controllerScaleFactor;
}
```

<span data-ttu-id="11bb3-226">Wir überprüfen, ob die Eingabe vom linken Analogstick außerhalb des inaktiven Bereichs liegt, und wenn dies der Fall ist, fügen wir **combinedTiltX** und **combinedTiltY** hinzu (multipliziert mit dem Skalierungsfaktor), um die Phase zu verändern.</span><span class="sxs-lookup"><span data-stu-id="11bb3-226">We check if the input from the left analog stick is outside of the dead zone, and if it is, we add it to **combinedTiltX** and **combinedTiltY** (multiplied by a scale factor) to tilt the stage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11bb3-227">Berücksichtigen Sie immer den inaktiven Bereich, wenn Sie mit dem Xbox-Controller arbeiten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-227">When you work with the Xbox controller, always account for the dead zone.</span></span> <span data-ttu-id="11bb3-228">Der inaktive Bereich bezieht sich auf die unterschiedliche Empfindlichkeit von Gamepads für die ersten Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-228">The dead zone refers to the variance among gamepads in their sensitivity to initial movement.</span></span> <span data-ttu-id="11bb3-229">Bei manchen Controllern ergibt eine kleine Bewegung keinen Messwert, während sie bei anderen zu einem messbaren Ergebnis führt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-229">In some controllers, a small movement may generate no reading, but in others it may generate a measurable reading.</span></span> <span data-ttu-id="11bb3-230">Berücksichtigen Sie dies in Ihrem Spiel, indem Sie für die ersten Bewegungen des Ministicks einen Bereich für Nichtbewegungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-230">To account for this in your game, create a zone of non-movement for initial thumbstick movement.</span></span> <span data-ttu-id="11bb3-231">Weitere Informationen finden über den inaktiven Bereich finden Sie unter [Lesen der Ministicks](gamepad-and-vibration.md#reading-the-thumbsticks).</span><span class="sxs-lookup"><span data-stu-id="11bb3-231">For more information about the dead zone, see [Reading the thumbsticks](gamepad-and-vibration.md#reading-the-thumbsticks).</span></span>

 

###  <a name="applying-input-to-the-game-state"></a><span data-ttu-id="11bb3-232">Anwenden von Eingaben auf den Spielzustand</span><span class="sxs-lookup"><span data-stu-id="11bb3-232">Applying input to the game state</span></span>

<span data-ttu-id="11bb3-233">Geräte melden Eingabewerte auf unterschiedliche Weise.</span><span class="sxs-lookup"><span data-stu-id="11bb3-233">Devices report input values in different ways.</span></span> <span data-ttu-id="11bb3-234">So wird eine Zeigereingabe möglicherweise in Bildschirmkoordinaten angegeben, eine Controllereingabe aber in einem völlig anderen Format.</span><span class="sxs-lookup"><span data-stu-id="11bb3-234">For example, pointer input might be in screen coordinates, and controller input might be in a completely different format.</span></span> <span data-ttu-id="11bb3-235">Beim Kombinieren der Eingaben von mehreren Geräten in einem Satz von Eingabewerten besteht eine Herausforderung darin, die Werte in ein gemeinsames Format zu normalisieren oder konvertieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-235">One challenge with combining input from multiple devices into one set of input values is normalization, or converting values to a common format.</span></span> <span data-ttu-id="11bb3-236">Marble Maze normalisiert Werte durch Skalieren auf einen Bereich \[-1,0, 1,0\].</span><span class="sxs-lookup"><span data-stu-id="11bb3-236">Marble Maze normalizes values by scaling them to the range \[-1.0, 1.0\].</span></span> <span data-ttu-id="11bb3-237">Mit der weiter oben in diesem Abschnitt beschriebenen **PointToTouch**-Funktion werden Bildschirmkoordinaten in normalisierte Werte konvertiert. Diese Werte liegen ungefähr zwischen -1,0 und +1,0.</span><span class="sxs-lookup"><span data-stu-id="11bb3-237">The **PointToTouch** function, which is previously described in this section, converts screen coordinates to normalized values that range approximately between -1.0 and +1.0.</span></span>

> [!TIP]
> <span data-ttu-id="11bb3-238">Auch wenn Ihre Anwendung eine einzige Eingabemethode verwendet, sollten Sie die Eingabewerte immer normalisieren.</span><span class="sxs-lookup"><span data-stu-id="11bb3-238">Even if your application uses one input method, we recommend that you always normalize input values.</span></span> <span data-ttu-id="11bb3-239">Auf diese Weise können Sie die Interpretation der Eingabe durch andere Komponenten des Spiels wie beispielsweise die Simulation von Physikeffekten vereinfachen und leichter Spiele schreiben, die sich für unterschiedliche Bildschirmauflösungen eignen.</span><span class="sxs-lookup"><span data-stu-id="11bb3-239">Doing so can simplify how input is interpreted by other components of your game, such as physics simulation, and makes it easier to write games that work on different screen resolutions.</span></span>

 

<span data-ttu-id="11bb3-240">Nachdem die **MarbleMazeMain::Update**-Methode die Eingabe verarbeitet hat, erstellt sie einen Vektor, der die Auswirkung der Neigung des Labyrinths auf die Murmel darstellt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-240">After the **MarbleMazeMain::Update** method processes input, it creates a vector that represents the effect of the tilt of the maze on the marble.</span></span> <span data-ttu-id="11bb3-241">Das folgende Beispiel zeigt, wie Marble Maze mit der [XMVector3Normalize](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.geometric.xmvector3normalize)-Funktion einen normalisierten Schwerkraftvektor erstellt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-241">The following example shows how Marble Maze uses the [XMVector3Normalize](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.geometric.xmvector3normalize) function to create a normalized gravity vector.</span></span> <span data-ttu-id="11bb3-242">Die **maxTilt**-Variable schränkt die Neigung des Labyrinths ein und verhindert, dass das Labyrinth auf die Seite gekippt wird.</span><span class="sxs-lookup"><span data-stu-id="11bb3-242">The **maxTilt** variable constrains the amount by which the maze tilts and prevents the maze from tilting on its side.</span></span>

```cpp
const float maxTilt = 1.0f / 8.0f;

XMVECTOR gravity = XMVectorSet(
    combinedTiltX * maxTilt, 
    combinedTiltY * maxTilt, 
    1.0f, 
    0.0f);

gravity = XMVector3Normalize(gravity);
```

<span data-ttu-id="11bb3-243">Als letzten Schritt beim Aktualisieren der Szenenobjekte übergibt Marble Maze den aktualisierten Schwerkraftvektor der Simulation für Physikeffekte, aktualisiert diese Simulation für den seit dem vorherigen Frame verstrichenen Zeitraum und aktualisiert die Position und Ausrichtung der Murmel.</span><span class="sxs-lookup"><span data-stu-id="11bb3-243">To complete the update of scene objects, Marble Maze passes the updated gravity vector to the physics simulation, updates the physics simulation for the time that has elapsed since the previous frame, and updates the position and orientation of the marble.</span></span> <span data-ttu-id="11bb3-244">Wenn die Murmel durch das Labyrinth gefallen ist, platziert die **MarbleMazeMain::Update**-Methode die Murmel wieder am letzten Prüfpunkt, den die Murmel berührt hat, und setzt den Zustand der Simulation für Physikeffekte zurück.</span><span class="sxs-lookup"><span data-stu-id="11bb3-244">If the marble has fallen through the maze, the **MarbleMazeMain::Update** method places the marble back at the last checkpoint that the marble touched and resets the state of the physics simulation.</span></span>

```cpp
XMFLOAT3A g;
XMStoreFloat3(&g, gravity);
m_physics.SetGravity(g);

if (m_gameState == GameState::InGameActive)
{
    // Only update physics when gameplay is active.
    m_physics.UpdatePhysicsSimulation(static_cast<float>(m_timer.GetElapsedSeconds()));

    // ...Code omitted for simplicity...

}

// ...Code omitted for simplicity...

// Check whether the marble fell off of the maze. 
const float fadeOutDepth = 0.0f;
const float resetDepth = 80.0f;
if (marblePosition.z >= fadeOutDepth)
{
    m_targetLightStrength = 0.0f;
}
if (marblePosition.z >= resetDepth)
{
    // Reset marble.
    memcpy(&marblePosition, &m_checkpoints[m_currentCheckpoint], sizeof(XMFLOAT3));
    oldMarblePosition = marblePosition;
    m_physics.SetPosition((const XMFLOAT3&)marblePosition);
    m_physics.SetVelocity(XMFLOAT3(0, 0, 0));
    m_lightStrength = 0.0f;
    m_targetLightStrength = 1.0f;

    m_resetCamera = true;
    m_resetMarbleRotation = true;
    m_audio.PlaySoundEffect(FallingEvent);
}
```

<span data-ttu-id="11bb3-245">In diesem Abschnitt wird nicht beschrieben, wie die Simulation für Physikeffekte funktioniert.</span><span class="sxs-lookup"><span data-stu-id="11bb3-245">This section does not describe how the physics simulation works.</span></span> <span data-ttu-id="11bb3-246">Details hierzu finden Sie in den Quellen für Marble Maze in **Physics.h** und **Physics.cpp**.</span><span class="sxs-lookup"><span data-stu-id="11bb3-246">For details about that, see **Physics.h** and **Physics.cpp** in the Marble Maze sources.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11bb3-247">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="11bb3-247">Next steps</span></span>


<span data-ttu-id="11bb3-248">Lesen Sie [Hinzufügen von Audio zum Marble Maze-Beispiel](adding-audio-to-the-marble-maze-sample.md). Dort finden Sie Informationen zu einigen der wichtigen Methoden, die Sie beim Arbeiten mit Audio berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="11bb3-248">Read [Adding audio to the Marble Maze sample](adding-audio-to-the-marble-maze-sample.md) for information about some of the key practices to keep in mind when you work with audio.</span></span> <span data-ttu-id="11bb3-249">In diesem Dokument wird erörtert, wie Marble Maze mithilfe von Microsoft Media Foundation und XAudio2 Audioressourcen lädt, mischt und wiedergibt.</span><span class="sxs-lookup"><span data-stu-id="11bb3-249">The document discusses how Marble Maze uses Microsoft Media Foundation and XAudio2 to load, mix, and play audio resources.</span></span>

## <a name="related-topics"></a><span data-ttu-id="11bb3-250">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11bb3-250">Related topics</span></span>


* [<span data-ttu-id="11bb3-251">Hinzufügen von Audiodaten zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="11bb3-251">Adding audio to the Marble Maze sample</span></span>](adding-audio-to-the-marble-maze-sample.md)
* [<span data-ttu-id="11bb3-252">Hinzufügen von visuellen Inhalten zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="11bb3-252">Adding visual content to the Marble Maze sample</span></span>](adding-visual-content-to-the-marble-maze-sample.md)
* [<span data-ttu-id="11bb3-253">Entwickeln von Marble Maze, einem UWP-Spiel in C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="11bb3-253">Developing Marble Maze, a UWP game in C++ and DirectX</span></span>](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)

 

 




