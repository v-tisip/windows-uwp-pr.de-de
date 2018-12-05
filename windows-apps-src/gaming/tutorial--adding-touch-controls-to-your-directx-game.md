---
title: Toucheingabesteuerelemente für Spiele
description: Hier erfahren Sie, wie Sie Ihrem C++-Spiel für die universelle Windows-Plattform (UWP) mit DirectX einfache touchbasierte Steuerelemente hinzufügen.
ms.assetid: 9d40e6e4-46a9-97e9-b848-522d61e8e109
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Touch, Steuerelemente, Directx, Eingabe
ms.localizationpriority: medium
ms.openlocfilehash: e8892219b485d320bb77f90ac0d172e8e2403392
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8685520"
---
# <a name="touch-controls-for-games"></a><span data-ttu-id="6d839-104">Toucheingabesteuerelemente für Spiele</span><span class="sxs-lookup"><span data-stu-id="6d839-104">Touch controls for games</span></span>



<span data-ttu-id="6d839-105">Hier erfahren Sie, wie Sie Ihrem C++-Spiel für die universelle Windows-Plattform (UWP) mit DirectX einfache touchbasierte Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6d839-105">Learn how to add basic touch controls to your Universal Windows Platform (UWP) C++ game with DirectX.</span></span> <span data-ttu-id="6d839-106">Wir zeigen Ihnen, wie Sie touchbasierte Steuerelemente hinzufügen, um eine Kamera mit fester Ebene in einer Direct3D-Umgebung zu bewegen, indem die Kameraperspektive durch Bewegen des Fingers oder Eingabestifts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="6d839-106">We show you how to add touch-based controls to move a fixed-plane camera in a Direct3D environment, where dragging with a finger or stylus shifts the camera perspective.</span></span>

<span data-ttu-id="6d839-107">Sie können diese Steuerungen in Spiele integrieren, bei denen der Spieler in einer 3D-Umgebung (z.B. einer Karte oder einem Spielfeld) einen Bildlauf ausführen oder die Ansicht schwenken soll.</span><span class="sxs-lookup"><span data-stu-id="6d839-107">You can incorporate these controls in games where you want the player to drag to scroll or pan over a 3D environment, such as a map or playfield.</span></span> <span data-ttu-id="6d839-108">Bei einem Strategie- oder Puzzlespiel kann der Spieler mit diesen Steuerungen z.B. durch Schwenken nach links oder rechts eine Spielumgebung anzeigen, die größer als der Bildschirm ist.</span><span class="sxs-lookup"><span data-stu-id="6d839-108">For example, in a strategy or puzzle game, you can use these controls to let the player view a game environment that is larger than the screen by panning left or right.</span></span>

> <span data-ttu-id="6d839-109">**Hinweis:** unser Code eignet sich auch schwenksteuerungen mausbasierte.</span><span class="sxs-lookup"><span data-stu-id="6d839-109">**Note**Our code also works with mouse-based panning controls.</span></span> <span data-ttu-id="6d839-110">Die zeigerbezogenen Ereignisse werden von den Windows-Runtime-APIs abstrahiert, sodass sie toucheingabe- oder mausbasierte Zeigerereignisse behandeln können.</span><span class="sxs-lookup"><span data-stu-id="6d839-110">The pointer related events are abstracted by the Windows Runtime APIs, so they can handle either touch- or mouse-based pointer events.</span></span>

 

## <a name="objectives"></a><span data-ttu-id="6d839-111">Ziele</span><span class="sxs-lookup"><span data-stu-id="6d839-111">Objectives</span></span>


-   <span data-ttu-id="6d839-112">Erstellen einer einfachen Fingereingabesteuerung, um eine Kamera mit fester Ebene in einem DirectX-Spiel zu schwenken</span><span class="sxs-lookup"><span data-stu-id="6d839-112">Create a simple touch drag control for panning a fixed-plane camera in a DirectX game.</span></span>

## <a name="set-up-the-basic-touch-event-infrastructure"></a><span data-ttu-id="6d839-113">Einrichten der grundlegenden Infrastruktur für Toucheingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="6d839-113">Set up the basic touch event infrastructure</span></span>


<span data-ttu-id="6d839-114">Als Erstes definieren wir den grundlegenden Controllertyp – in diesem Fall: **CameraPanController**.</span><span class="sxs-lookup"><span data-stu-id="6d839-114">First, we define our basic controller type, the **CameraPanController**, in this case.</span></span> <span data-ttu-id="6d839-115">Der Controller wird hier als abstrakte Idee definiert, d.h. als Satz von Verhaltensweisen, die der Benutzer ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="6d839-115">Here, we define a controller as an abstract idea, the set of behaviors the user can perform.</span></span>

<span data-ttu-id="6d839-116">Die **CameraPanController**-Klasse ist eine regelmäßig aktualisierte Sammlung von Informationen zum Zustand des Kameracontrollers und bietet der App die Möglichkeit, diese Informationen aus ihrer Aktualisierungsschleife abzurufen.</span><span class="sxs-lookup"><span data-stu-id="6d839-116">The **CameraPanController** class is a regularly refreshed collection of information about the camera controller state, and provides a way for our app to obtain that information from its update loop.</span></span>

```cpp
using namespace Windows::UI::Core;
using namespace Windows::System;
using namespace Windows::Foundation;
using namespace Windows::Devices::Input;
#include <directxmath.h>

// Methods to get input from the UI pointers
ref class CameraPanController
{
}
```

<span data-ttu-id="6d839-117">Jetzt erstellen wir einen Header, der den Zustand des Kameracontrollers definiert, sowie die grundlegenden Methoden und Ereignishandler, die die Interaktionen des Kameracontrollers implementieren.</span><span class="sxs-lookup"><span data-stu-id="6d839-117">Now, let's create a header that defines the state of the camera controller, and the basic methods and event handlers that implement the camera controller interactions.</span></span>

```cpp
ref class CameraPanController
{
private:
    // Properties of the controller object
    DirectX::XMFLOAT3 m_position;               // the position of the camera

    // Properties of the camera pan control
    bool m_panInUse;                
    uint32 m_panPointerID;          
    DirectX::XMFLOAT2 m_panFirstDown;           
    DirectX::XMFLOAT2 m_panPointerPosition;   
    DirectX::XMFLOAT3 m_panCommand;         
    
internal:
    // Accessor to set the position of the controller
    void SetPosition( _In_ DirectX::XMFLOAT3 pos );

       // Accessor to set the fixed "look point" of the controller
       DirectX::XMFLOAT3 get_FixedLookPoint();

    // Returns the position of the controller object
    DirectX::XMFLOAT3 get_Position();

public:

    // Methods to get input from the UI pointers
    void OnPointerPressed(
        _In_ Windows::UI::Core::CoreWindow^ sender,
        _In_ Windows::UI::Core::PointerEventArgs^ args
        );

    void OnPointerMoved(
        _In_ Windows::UI::Core::CoreWindow^ sender,
        _In_ Windows::UI::Core::PointerEventArgs^ args
        );

    void OnPointerReleased(
        _In_ Windows::UI::Core::CoreWindow^ sender,
        _In_ Windows::UI::Core::PointerEventArgs^ args
        );

    // Set up the Controls supported by this controller
    void Initialize( _In_ Windows::UI::Core::CoreWindow^ window );

    void Update( Windows::UI::Core::CoreWindow ^window );

};  // Class CameraPanController
```

<span data-ttu-id="6d839-118">Die privaten Felder enthalten den aktuellen Zustand des Kameracontrollers.</span><span class="sxs-lookup"><span data-stu-id="6d839-118">The private fields contain the current state of the camera controller.</span></span> <span data-ttu-id="6d839-119">Ihre Funktion wird im Folgenden erläutert.</span><span class="sxs-lookup"><span data-stu-id="6d839-119">Let's review them.</span></span>

-   <span data-ttu-id="6d839-120">**m\_position** ist die Position der Kamera im Szenenbereich.</span><span class="sxs-lookup"><span data-stu-id="6d839-120">**m\_position** is the position of the camera in the scene space.</span></span> <span data-ttu-id="6d839-121">In diesem Beispiel ist der Wert der Z-Koordinate unveränderlich auf„0“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6d839-121">In this example, the z-coordinate value is fixed at 0.</span></span> <span data-ttu-id="6d839-122">Dieser Wert könnte mit „DirectX::XMFLOAT2“ dargestellt werden, für dieses Beispiel – und um zukünftige Erweiterungen zu ermöglichen – verwenden wir hier aber „DirectX::XMFLOAT3“.</span><span class="sxs-lookup"><span data-stu-id="6d839-122">We could use a DirectX::XMFLOAT2 to represent this value, but for the purposes of this sample and future extensibility, we use a DirectX::XMFLOAT3.</span></span> <span data-ttu-id="6d839-123">Diesen Wert übergeben wir mit der **get\_Position**-Eigenschaft an die App, damit sie den Viewport entsprechend aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="6d839-123">We pass this value through the **get\_Position** property to the app itself so it can update the viewport accordingly.</span></span>
-   <span data-ttu-id="6d839-124">**m\_panInUse** ist ein boolescher Wert, der angibt, ob ein Schwenkvorgang aktiv ist (also ob der Spieler den Bildschirm berührt und die Kamera bewegt).</span><span class="sxs-lookup"><span data-stu-id="6d839-124">**m\_panInUse** is a Boolean value that indicates whether a pan operation is active; or, more specifically, whether the player is touching the screen and moving the camera.</span></span>
-   <span data-ttu-id="6d839-125">**m\_panPointerID** ist eine eindeutige ID für den Zeiger.</span><span class="sxs-lookup"><span data-stu-id="6d839-125">**m\_panPointerID** is a unique ID for the pointer.</span></span> <span data-ttu-id="6d839-126">Obwohl die ID im Beispiel nicht verwendet wird, empfiehlt es sich, der Controllerzustandsklasse immer einen bestimmten Zeiger zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="6d839-126">We won't use this in the sample, but it's a good practice to associate your controller state class with a specific pointer.</span></span>
-   <span data-ttu-id="6d839-127">**m\_panFirstDown** ist der Punkt, an dem der Spieler während des Kameraschwenks erstmals den Bildschirm berührt oder mit der Maus geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="6d839-127">**m\_panFirstDown** is the point on the screen where the player first touched the screen or clicked the mouse during the camera pan action.</span></span> <span data-ttu-id="6d839-128">Dieser Wert wird später verwendet, um einen inaktiven Bereich festzulegen, damit die Ansicht nicht flimmert, wenn der Bildschirm berührt oder die Maus leicht bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="6d839-128">We use this value later to set a dead zone to prevent jitter when the screen is touched, or if the mouse shakes a little.</span></span>
-   <span data-ttu-id="6d839-129">**m\_panPointerPosition** ist der Punkt auf dem Bildschirm, an den der Spieler den Zeiger gerade bewegt hat.</span><span class="sxs-lookup"><span data-stu-id="6d839-129">**m\_panPointerPosition** is the point on the screen where the player has currently moved the pointer.</span></span> <span data-ttu-id="6d839-130">Dieser Wert wird mit **m\_panFirstDown** verglichen, um die beabsichtigte Bewegungsrichtung des Spielers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="6d839-130">We use it to determine what direction the player wanted to move by examining it relative to **m\_panFirstDown**.</span></span>
-   <span data-ttu-id="6d839-131">**m\_panCommand** ist der berechnete endgültige Befehl für den Kameracontroller: nach oben, nach unten, nach links oder nach rechts.</span><span class="sxs-lookup"><span data-stu-id="6d839-131">**m\_panCommand** is the final computed command for the camera controller: up, down, left, or right.</span></span> <span data-ttu-id="6d839-132">Da die Kamerabewegung hier auf die X-Y-Ebene beschränkt ist, könnte stattdessen ein DirectX::XMFLOAT2-Wert verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6d839-132">Because we are working with a camera fixed to the x-y plane, this could be a DirectX::XMFLOAT2 value instead.</span></span>

<span data-ttu-id="6d839-133">Mit den folgenden drei Ereignishandlern aktualisieren wir die Informationen zum Zustand des Kameracontrollers.</span><span class="sxs-lookup"><span data-stu-id="6d839-133">We use these 3 event handlers to update the camera controller state info.</span></span>

-   <span data-ttu-id="6d839-134">**OnPointerPressed** ist ein Ereignishandler, der von der App aufgerufen wird, wenn der Spieler den Touchscreen mit dem Finger berührt und der Zeiger zu den Koordinaten des Berührungspunkts bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="6d839-134">**OnPointerPressed** is an event handler that our app calls when the players presses a finger onto the touch surface and the pointer is moved to the coordinates of the press.</span></span>
-   <span data-ttu-id="6d839-135">**OnPointerMoved** ist ein Ereignishandler, der von der App aufgerufen wird, wenn der Spieler mit einem Finger eine Wischbewegung über den Touchscreen ausführt.</span><span class="sxs-lookup"><span data-stu-id="6d839-135">**OnPointerMoved** is an event handler that our app calls when the player swipes a finger across the touch surface.</span></span> <span data-ttu-id="6d839-136">Er aktualisiert den Wert mit den neuen Koordinaten der Bewegung.</span><span class="sxs-lookup"><span data-stu-id="6d839-136">It updates with the new coordinates of the drag path.</span></span>
-   <span data-ttu-id="6d839-137">**OnPointerReleased** ist ein Ereignishandler, der von der App aufgerufen wird, wenn der Spieler den Finger vom Touchscreen nimmt.</span><span class="sxs-lookup"><span data-stu-id="6d839-137">**OnPointerReleased** is an event handler that our app calls when the player removes the pressing finger from the touch surface.</span></span>

<span data-ttu-id="6d839-138">Die folgenden Methoden und Eigenschaften verwenden wir, um die Zustandsinformationen des Kameracontrollers zu initialisieren, auf sie zuzugreifen und sie zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="6d839-138">Finally, we use these methods and properties to initialize, access, and update the camera controller state information.</span></span>

-   <span data-ttu-id="6d839-139">**Initialize** ist ein Ereignishandler, den die App aufruft, um die Steuerelemente zu initialisieren und an das [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Objekt anzufügen, das das Anzeigefenster beschreibt.</span><span class="sxs-lookup"><span data-stu-id="6d839-139">**Initialize** is an event handler that our app calls to initialize the controls and attach them to the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) object that describes your display window.</span></span>
-   <span data-ttu-id="6d839-140">**SetPosition** ist eine Methode, die die App aufruft, um die Koordinaten (X, Y und Z) der Steuerungen im Szenenbereich festzulegen.</span><span class="sxs-lookup"><span data-stu-id="6d839-140">**SetPosition** is a method that our app calls to set the (x, y, and z) coordinates of your controls in the scene space.</span></span> <span data-ttu-id="6d839-141">Beachten Sie, dass die Z-Koordinate in diesem Lernprogramm immer Null ist.</span><span class="sxs-lookup"><span data-stu-id="6d839-141">Note that our z-coordinate is 0 throughout this tutorial.</span></span>
-   <span data-ttu-id="6d839-142">**get\_Position** ist eine Eigenschaft, auf die die App zugreift, um die aktuelle Position der Kamera im Szenenbereich abzurufen.</span><span class="sxs-lookup"><span data-stu-id="6d839-142">**get\_Position** is a property that our app accesses to get the current position of the camera in the scene space.</span></span> <span data-ttu-id="6d839-143">Diese Eigenschaft wird verwendet, um der App die aktuelle Kameraposition mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="6d839-143">You use this property as the way of communicating the current camera position to the app.</span></span>
-   <span data-ttu-id="6d839-144">**get\_FixedLookPoint** ist eine Eigenschaft, auf die die App zugreift, um den aktuellen Punkt abzurufen, auf den die Kamera gerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="6d839-144">**get\_FixedLookPoint** is a property that our app accesses to get the current point toward which the controller camera is facing.</span></span> <span data-ttu-id="6d839-145">In diesem Beispiel ist der Punkt auf die Normale der X-Y-Ebene beschränkt.</span><span class="sxs-lookup"><span data-stu-id="6d839-145">In this example, it is locked normal to the x-y plane.</span></span>
-   <span data-ttu-id="6d839-146">**Update** ist eine Methode, die den Controllerzustand liest und die Kameraposition aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="6d839-146">**Update** is a method that reads the controller state and updates the camera position.</span></span> <span data-ttu-id="6d839-147">&lt;Etwas&gt; wird in der Hauptschleife der App kontinuierlich aufgerufen, um die Kameracontrollerdaten und die Kameraposition im Szenenbereich zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="6d839-147">You continually call this &lt;something&gt; from the app's main loop to refresh the camera controller data and the camera position in the scene space.</span></span>

<span data-ttu-id="6d839-148">Jetzt haben Sie alle Komponenten, die Sie zum Implementieren von Toucheingabesteuerungen benötigen.</span><span class="sxs-lookup"><span data-stu-id="6d839-148">Now, you have here all the components you need to implement touch controls.</span></span> <span data-ttu-id="6d839-149">Sie können feststellen, wann und wo die Fingereingabe- oder Mauszeigerereignisse stattgefunden haben und um welche Aktion es sich dabei handelt.</span><span class="sxs-lookup"><span data-stu-id="6d839-149">You can detect when and where the touch or mouse pointer events have occurred, and what the action is.</span></span> <span data-ttu-id="6d839-150">Sie können die Position und Ausrichtung der Kamera in Bezug zum Szenenbereich festlegen und die Änderungen nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="6d839-150">You can set the position and orientation of the camera relative to the scene space, and track the changes.</span></span> <span data-ttu-id="6d839-151">Und schließlich können Sie die neue Kameraposition der aufrufenden App mitteilen.</span><span class="sxs-lookup"><span data-stu-id="6d839-151">Finally, you can communicate the new camera position to the calling app.</span></span>

<span data-ttu-id="6d839-152">Als Nächstes setzen wir diese Teile zusammen.</span><span class="sxs-lookup"><span data-stu-id="6d839-152">Now, let's connect these pieces together.</span></span>

## <a name="create-the-basic-touch-events"></a><span data-ttu-id="6d839-153">Erstellen der grundlegenden Fingereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="6d839-153">Create the basic touch events</span></span>


<span data-ttu-id="6d839-154">Der Ereignisverteiler der Windows-Runtime stellt dreiEreignisse bereit, die von der App behandelt werden sollen:</span><span class="sxs-lookup"><span data-stu-id="6d839-154">The Windows Runtime event dispatcher provides 3 events we want our app to handle:</span></span>

-   [**<span data-ttu-id="6d839-155">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="6d839-155">PointerPressed</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208278)
-   [**<span data-ttu-id="6d839-156">PointerMoved</span><span class="sxs-lookup"><span data-stu-id="6d839-156">PointerMoved</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208276)
-   [**<span data-ttu-id="6d839-157">PointerReleased</span><span class="sxs-lookup"><span data-stu-id="6d839-157">PointerReleased</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208279)

<span data-ttu-id="6d839-158">Diese Ereignisse sind im [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Typ implementiert.</span><span class="sxs-lookup"><span data-stu-id="6d839-158">These events are implemented on the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) type.</span></span> <span data-ttu-id="6d839-159">Es wird davon ausgegangen, dass Sie über ein **CoreWindow**-Objekt verfügen, mit dem Sie arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="6d839-159">We assume that you have a **CoreWindow** object to work with.</span></span> <span data-ttu-id="6d839-160">Weitere Informationen finden Sie unter [Einrichten der UWP-C++-App zum Anzeigen einer DirectX-Ansicht](https://msdn.microsoft.com/library/windows/apps/hh465077).</span><span class="sxs-lookup"><span data-stu-id="6d839-160">For more info, see [How to set up your UWP C++ app to display a DirectX view](https://msdn.microsoft.com/library/windows/apps/hh465077).</span></span>

<span data-ttu-id="6d839-161">Wenn diese Ereignisse während der Ausführung der App ausgelöst werden, aktualisieren die Handler die in den privaten Feldern definierten Zustandsinformationen des Kameracontrollers.</span><span class="sxs-lookup"><span data-stu-id="6d839-161">As these events fire while our app is running, the handlers update the camera controller state info defined in our private fields.</span></span>

<span data-ttu-id="6d839-162">Als Erstes füllen wir die Ereignishandler für den Toucheingabezeiger auf.</span><span class="sxs-lookup"><span data-stu-id="6d839-162">First, let's populate the touch pointer event handlers.</span></span> <span data-ttu-id="6d839-163">Im ersten Ereignishandler (**OnPointerPressed**) rufen wir die X- und Y-Koordinaten des Zeigers aus dem [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Objekt ab, das die Anzeige verwaltet, wenn der Benutzer den Bildschirm berührt oder mit der Maus klickt.</span><span class="sxs-lookup"><span data-stu-id="6d839-163">In the first event handler, **OnPointerPressed**, we get the x-y coordinates of the pointer from the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) that manages our display when the user touches the screen or clicks the mouse.</span></span>

**<span data-ttu-id="6d839-164">OnPointerPressed</span><span class="sxs-lookup"><span data-stu-id="6d839-164">OnPointerPressed</span></span>**

```cpp
void CameraPanController::OnPointerPressed(
                                           _In_ CoreWindow^ sender,
                                           _In_ PointerEventArgs^ args)
{
    // Get the current pointer position.
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2( args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y );

    auto device = args->CurrentPoint->PointerDevice;
    auto deviceType = device->PointerDeviceType;
    

       if ( !m_panInUse )   // If no pointer is in this control yet.
    {
       m_panFirstDown = position;                   // Save the location of the initial contact.
       m_panPointerPosition = position;
       m_panPointerID = pointerID;              // Store the id of the pointer using this control.
       m_panInUse = TRUE;
    }
    
}
```

<span data-ttu-id="6d839-165">Mit diesem Handler teilen wir der aktuellen **CameraPanController**-Instanz mit, dass der Kameracontroller als aktiv behandelt werden soll. Hierzu wird **m\_panInUse** auf „true“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6d839-165">We use this handler to let the current **CameraPanController** instance know that camera controller should be treated as active by setting **m\_panInUse** to TRUE.</span></span> <span data-ttu-id="6d839-166">Auf diese Weise verwendet die App die aktuellen Positionsdaten zum Aktualisieren des Viewports, wenn sie **Update** aufruft.</span><span class="sxs-lookup"><span data-stu-id="6d839-166">That way, when the app calls **Update** , it will use the current position data to update the viewport.</span></span>

<span data-ttu-id="6d839-167">Nachdem wir die Basiswerte für die Kamerabewegung beim Berühren des Bildschirms oder Klicken im Anzeigefenster eingerichtet haben, müssen wir bestimmen, was passieren soll, wenn der Benutzer den Finger auf dem Bildschirm bewegt oder die Maus mit gedrückter Maustaste bewegt.</span><span class="sxs-lookup"><span data-stu-id="6d839-167">Now that we've established the base values for the camera movement when the user touches the screen or click-presses in the display window, we must determine what to do when the user either drags the screen press or moves the mouse with button pressed.</span></span>

<span data-ttu-id="6d839-168">Der **OnPointerMoved**-Ereignishandler wird bei jeder Bewegung des Zeigers ausgelöst – bei jedem Teilstrich, um den der Spieler den Zeiger auf dem Bildschirm bewegt.</span><span class="sxs-lookup"><span data-stu-id="6d839-168">The **OnPointerMoved** event handler fires whenever the pointer moves, at every tick that the player drags it on the screen.</span></span> <span data-ttu-id="6d839-169">Wir müssen die App über die aktuelle Position des Zeigers auf dem Laufenden halten. Dazu gehen wir wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="6d839-169">We need to keep the app aware of the current location of the pointer, and this is how we do it.</span></span>

**<span data-ttu-id="6d839-170">OnPointerMoved</span><span class="sxs-lookup"><span data-stu-id="6d839-170">OnPointerMoved</span></span>**

```cpp
void CameraPanController::OnPointerMoved(
                                        _In_ CoreWindow ^sender,
                                        _In_ PointerEventArgs ^args)
{
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2( args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y );

    m_panPointerPosition = position;
}
```

<span data-ttu-id="6d839-171">Abschließend müssen wir den Kameraschwenk deaktivieren, wenn der Spieler aufhört, den Bildschirm zu berühren.</span><span class="sxs-lookup"><span data-stu-id="6d839-171">Finally, we need to deactivate the camera pan behavior when the player stops touching the screen.</span></span> <span data-ttu-id="6d839-172">Dazu verwenden wir **OnPointerReleased**. Dieser Ereignishandler wird aufgerufen, wenn [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) ausgelöst wird, um **m\_panInUse** auf „false“ festzulegen, den Kameraschwenk zu deaktivieren und die Zeiger-ID auf Null zu festzulegen.</span><span class="sxs-lookup"><span data-stu-id="6d839-172">We use **OnPointerReleased**, which is called when [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) is fired, to set **m\_panInUse** to FALSE and turn off the camera pan movement, and set the pointer ID to 0.</span></span>

**<span data-ttu-id="6d839-173">OnPointerReleased</span><span class="sxs-lookup"><span data-stu-id="6d839-173">OnPointerReleased</span></span>**

```cpp
void CameraPanController::OnPointerReleased(
                                             _In_ CoreWindow ^sender,
                                             _In_ PointerEventArgs ^args)
{
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2( args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y );

    m_panInUse = FALSE;
    m_panPointerID = 0;
}
```

## <a name="initialize-the-touch-controls-and-the-controller-state"></a><span data-ttu-id="6d839-174">Initialisieren der Toucheingabesteuerungen und des Controllerzustands</span><span class="sxs-lookup"><span data-stu-id="6d839-174">Initialize the touch controls and the controller state</span></span>


<span data-ttu-id="6d839-175">Jetzt verbinden wir die Ereignisse und initialisieren alle grundlegenden Zustandsfelder des Kameracontrollers.</span><span class="sxs-lookup"><span data-stu-id="6d839-175">Let's hook the events and initialize all the basic state fields of the camera controller.</span></span>

**<span data-ttu-id="6d839-176">Initialize</span><span class="sxs-lookup"><span data-stu-id="6d839-176">Initialize</span></span>**

```cpp
void CameraPanController::Initialize( _In_ CoreWindow^ window )
{

    // Start recieving touch/mouse events.
    window->PointerPressed += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &CameraPanController::OnPointerPressed);

    window->PointerMoved += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &CameraPanController::OnPointerMoved);

    window->PointerReleased += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &CameraPanController::OnPointerReleased);


    // Initialize the state of the controller.
    m_panInUse = FALSE;             
    m_panPointerID = 0;

    //  Initialize this as it is reset on every frame.
    m_panCommand = DirectX::XMFLOAT3( 0.0f, 0.0f, 0.0f );

}
```

<span data-ttu-id="6d839-177">Die **Initialize**-Methode akzeptiert als Parameter einen Verweis auf die [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Instanz der App und registriert die von uns entwickelten Ereignishandler für die entsprechenden Ereignisse in dieser **CoreWindow**-Instanz.</span><span class="sxs-lookup"><span data-stu-id="6d839-177">**Initialize** takes a reference to the app's [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) instance as a parameter and registers the event handlers we developed to the appropriate events on that **CoreWindow**.</span></span>

## <a name="getting-and-setting-the-position-of-the-camera-controller"></a><span data-ttu-id="6d839-178">Abrufen und Festlegen der Position des Kameracontrollers</span><span class="sxs-lookup"><span data-stu-id="6d839-178">Getting and setting the position of the camera controller</span></span>


<span data-ttu-id="6d839-179">Als Nächstes definieren wir einige Methoden zum Abrufen und Festlegen der Position des Kameracontrollers im Szenenbereich.</span><span class="sxs-lookup"><span data-stu-id="6d839-179">Let's define some methods to get and set the position of the camera controller in the scene space.</span></span>

```cpp
void CameraPanController::SetPosition( _In_ DirectX::XMFLOAT3 pos )
{
    m_position = pos;
}

// Returns the position of the controller object
DirectX::XMFLOAT3 CameraPanController::get_Position()
{
    return m_position;
}

DirectX::XMFLOAT3 CameraPanController::get_FixedLookPoint()
{
    // For this sample, we don't need to use the trig functions because our
    // look point is fixed. 
    DirectX::XMFLOAT3 result= m_position;
    result.z += 1.0f;
    return result;    

}
```

<span data-ttu-id="6d839-180">**SetPosition** ist eine öffentliche Methode, die wir in der App aufrufen können, wenn wir die Position des Kameracontrollers auf einen bestimmten Punkt festlegen müssen.</span><span class="sxs-lookup"><span data-stu-id="6d839-180">**SetPosition** is a public method that we can call from our app if we need to set the camera controller position to a specific point.</span></span>

<span data-ttu-id="6d839-181">**get\_Position** ist die wichtigste öffentliche Eigenschaft: Mit dieser Eigenschaft ruft die App die aktuelle Position des Kameracontrollers im Szenenbereich ab, damit sie den Viewport entsprechend aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="6d839-181">**get\_Position** is our most important public property: it's the way our app gets the current position of the camera controller in the scene space so it can update the viewport accordingly.</span></span>

<span data-ttu-id="6d839-182">**get\_FixedLookPoint** ist eine öffentliche Eigenschaft, die in diesem Beispiel einen Blickpunkt senkrecht zur X-Y-Ebene abruft.</span><span class="sxs-lookup"><span data-stu-id="6d839-182">**get\_FixedLookPoint** is a public property that, in this example, obtains a look point that is normal to the x-y plane.</span></span> <span data-ttu-id="6d839-183">Sie können diese Methode ändern, um die Berechnung der X-, Y- und Z-Koordinatenwerte mit den trigonometrischen Funktionen Sinus und Kosinus durchzuführen, wenn Sie schrägere Winkel für die feste Kamera verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="6d839-183">You can change this method to use the trigonometric functions, sin and cos, when calculating the x, y, and z coordinate values if you want to create more oblique angles for the fixed camera.</span></span>

## <a name="updating-the-camera-controller-state-information"></a><span data-ttu-id="6d839-184">Aktualisieren der Zustandsinformationen des Kameracontrollers</span><span class="sxs-lookup"><span data-stu-id="6d839-184">Updating the camera controller state information</span></span>


<span data-ttu-id="6d839-185">Jetzt führen wir die Berechnungen aus, mit denen die in **m\_panPointerPosition** erfassten Zeigerkoordinaten in neue Koordinaten für den 3D-Szenenbereich konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="6d839-185">Now, we perform our calculations that convert the pointer coordinate info tracked in **m\_panPointerPosition** into new coordinate info respective of our 3D scene space.</span></span> <span data-ttu-id="6d839-186">Die App ruft diese Methode bei jeder Aktualisierung der Hauptschleife auf.</span><span class="sxs-lookup"><span data-stu-id="6d839-186">Our app calls this method every time we refresh the main app loop.</span></span> <span data-ttu-id="6d839-187">Dabei werden die neuen, an die App zu übergebenden Positionsinformationen berechnet, die zum Aktualisieren der Ansichtsmatrix vor der Projektion in den Viewport verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6d839-187">In it we compute the new position information we want to pass to the app which is used to update the view matrix before projection into the viewport.</span></span>

```cpp

void CameraPanController::Update( CoreWindow ^window )
{
    if ( m_panInUse )
    {
        pointerDelta.x = m_panPointerPosition.x - m_panFirstDown.x;
        pointerDelta.y = m_panPointerPosition.y - m_panFirstDown.y;

        if ( pointerDelta.x > 16.0f )        // Leave 32 pixel-wide dead spot for being still.
            m_panCommand.x += 1.0f;
        else
            if ( pointerDelta.x < -16.0f )
                m_panCommand.x += -1.0f;

        if ( pointerDelta.y > 16.0f )        
            m_panCommand.y += 1.0f;
        else
            if (pointerDelta.y < -16.0f )
                m_panCommand.y += -1.0f;
    }

       DirectX::XMFLOAT3 command = m_panCommand;
   
    // Our velocity is based on the command.
    DirectX::XMFLOAT3 Velocity;
    Velocity.x =  command.x;
    Velocity.y =  command.y;
    Velocity.z =  0.0f;

    // Integrate
    m_position.x = m_position.x + Velocity.x;
    m_position.y = m_position.y + Velocity.y;
    m_position.z = m_position.z + Velocity.z;

    // Clear the movement input accumulator for use during the next frame.
    m_panCommand = DirectX::XMFLOAT3( 0.0f, 0.0f, 0.0f );

}
```

<span data-ttu-id="6d839-188">Damit die Bewegung bei Verwendung der Finger- oder Mauseingabe nicht "zittert" und die Schwenkbewegung der Kamera dadurch ruckartig wird, legen wir einen inaktiven Bereich mit einem Durchmesser von 32Pixel um den Zeiger fest.</span><span class="sxs-lookup"><span data-stu-id="6d839-188">Because we don't want touch or mouse jitter to make our camera panning jerky, we set a dead zone around the pointer with a diameter of 32 pixels.</span></span> <span data-ttu-id="6d839-189">Außerdem haben wir einen Geschwindigkeitswert – in diesem Fall 1:1 – für die Zeigerbewegung außerhalb des inaktiven Bereichs.</span><span class="sxs-lookup"><span data-stu-id="6d839-189">We also have a velocity value, which in this case is 1:1 with the pixel traversal of the pointer past the dead zone.</span></span> <span data-ttu-id="6d839-190">Sie können dieses Verhalten anpassen, um die Geschwindigkeitsrate zu erhöhen oder zu verringern.</span><span class="sxs-lookup"><span data-stu-id="6d839-190">You can adjust this behavior to slow down or speed up the rate of movement.</span></span>

## <a name="updating-the-view-matrix-with-the-new-camera-position"></a><span data-ttu-id="6d839-191">Aktualisieren der Ansichtsmatrix mit der neuen Kameraposition</span><span class="sxs-lookup"><span data-stu-id="6d839-191">Updating the view matrix with the new camera position</span></span>


<span data-ttu-id="6d839-192">Jetzt können wir eine Koordinate des Szenenbereichs abrufen, auf die die Kamera ausgerichtet ist und die jedes Mal aktualisiert wird, wenn die App dazu angewiesen wird (z.B. alle 60Sekunden in der Hauptschleife der App).</span><span class="sxs-lookup"><span data-stu-id="6d839-192">We can now obtain a scene space coordinate that our camera is focused on, and which is updated whenever you tell your app to do so (every 60 seconds in the main app loop, for example).</span></span> <span data-ttu-id="6d839-193">Dieser Pseudocode zeigt das Aufrufverhalten, das Sie implementieren können:</span><span class="sxs-lookup"><span data-stu-id="6d839-193">This pseudocode suggests the calling behavior you can implement:</span></span>

```cpp
 myCameraPanController->Update( m_window ); 

 // Update the view matrix based on the camera position.
 myCamera->MyMethodToComputeViewMatrix(
        myController->get_Position(),        // The position in the 3D scene space.
        myController->get_FixedLookPoint(),      // The point in the space we are looking at.
        DirectX::XMFLOAT3( 0, 1, 0 )                    // The axis that is "up" in our space.
        );  
```

<span data-ttu-id="6d839-194">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="6d839-194">Congratulations!</span></span> <span data-ttu-id="6d839-195">Sie haben in Ihrem Spiel einen einfachen Satz mit Toucheingabesteuerungen zum Schwenken einer Kamera implementiert.</span><span class="sxs-lookup"><span data-stu-id="6d839-195">You've implemented a simple set of camera panning touch controls in your game.</span></span>


 

 

 




