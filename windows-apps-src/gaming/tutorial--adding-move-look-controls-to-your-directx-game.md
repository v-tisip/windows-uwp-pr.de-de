---
author: mtoepke
title: Bewegungs-/Blicksteuerungen für Spiele
description: Hier erfahren Sie, wie Sie Ihrem DirectX-Spiel herkömmliche Bewegungs-/Blicksteuerungen für Maus und Tastatur (auch als Maussteuerungen bezeichnet) hinzufügen.
ms.assetid: 4b4d967c-3de9-8a97-ae68-0327f00cc933
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Bewegungs-/Blicksteuerungen, Steuerelemente
ms.localizationpriority: medium
ms.openlocfilehash: 219d014eb03803ace440dc1c1773043a9ecbc99f
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5597842"
---
# <a name="span-iddevgamingtutorialaddingmove-lookcontrolstoyourdirectxgamespanmove-look-controls-for-games"></a><span data-ttu-id="85a89-104"><span id="dev_gaming.tutorial__adding_move-look_controls_to_your_directx_game"></span>Bewegungs-/Blicksteuerungen für Spiele</span><span class="sxs-lookup"><span data-stu-id="85a89-104"><span id="dev_gaming.tutorial__adding_move-look_controls_to_your_directx_game"></span>Move-look controls for games</span></span>



<span data-ttu-id="85a89-105">Hier erfahren Sie, wie Sie Ihrem DirectX-Spiel herkömmliche Bewegungs-/Blicksteuerungen für Maus und Tastatur (auch als Maussteuerungen bezeichnet) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="85a89-105">Learn how to add traditional mouse and keyboard move-look controls (also known as mouselook controls) to your DirectX game.</span></span>

<span data-ttu-id="85a89-106">Außerdem erörtern wir die Bewegungs-/Blicksteuerungsunterstützung für Toucheingabegräte mit dem als linker unterer Bildschirmabschnitt definierten Bewegungscontroller, der als Richtungseingabe fungiert, und dem für den restlichen Bildschirm definierten Blickcontroller, dessen Kamera mittig auf die letzte Stelle ausgerichtet wird, die der Spieler in diesem Bereich berührt hat.</span><span class="sxs-lookup"><span data-stu-id="85a89-106">We also discuss move-look support for touch devices, with the move controller defined as the lower-left section of the screen that behaves like a directional input, and the look controller defined for the remainder of the screen, with the camera centering on the last place the player touched in that area.</span></span>

<span data-ttu-id="85a89-107">Falls Ihnen dieses Steuerungskonzept nicht vertraut ist, können Sie sich das wie folgt vorstellen: Die Tastatur (oder das auf Toucheingabe basierende Richtungseingabefeld) steuert Ihre Beine im 3D-Raum und verhält sich so als könnten sich Ihre Beine nur vorwärts oder rückwärts bzw. nur nach links und rechts bewegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-107">If this is an unfamiliar control concept to you, think of it this way: the keyboard (or the touch-based directional input box) controls your legs in this 3D space, and behaves as if your legs were only capable of moving forward or backward, or strafing left and right.</span></span> <span data-ttu-id="85a89-108">Die Maus (oder der Fingereingabezeiger) steuert Ihren Kopf.</span><span class="sxs-lookup"><span data-stu-id="85a89-108">The mouse (or touch pointer) controls your head.</span></span> <span data-ttu-id="85a89-109">Mit dem Kopf schauen Sie in eine Richtung – nach links oder rechts, nach oben oder unten oder zu einer Stelle in dieser Ebene.</span><span class="sxs-lookup"><span data-stu-id="85a89-109">You use your head to look in a direction -- left or right, up or down, or somewhere in that plane.</span></span> <span data-ttu-id="85a89-110">Befindet sich ein Ziel in Ihrer Sicht, richten Sie die Kameraansicht mit der Maus mittig auf dieses Ziel aus und drücken die Vorwärts-Taste, um sich zum Ziel hin zu bewegen, oder die Rückwärts-Taste, um sich vom Ziel weg zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-110">If there is a target in your view, you would use the mouse to center your camera view on that target, and then press the forward key to move towards it, or back to move away from it.</span></span> <span data-ttu-id="85a89-111">Um das Ziel einzukreisen, halten Sie die Kameraansicht auf das Ziel ausgerichtet und bewegen sich gleichzeitig nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="85a89-111">To circle the target, you would keep the camera view centered on the target, and move left or right at the same time.</span></span> <span data-ttu-id="85a89-112">Wie Sie sehen, ist dies eine sehr effektive Steuerungsmethode für die Navigation in 3D-Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="85a89-112">You can see how this is a very effective control method for navigating 3D environments!</span></span>

<span data-ttu-id="85a89-113">Diese Steuerungen werden bei Spielen im Allgemeinen als WASD-Steuerungen bezeichnet: Die Tasten W, A, S und D werden für die feste Kamerabewegung in der Z-Ebene verwendet, und die Maus wird zum Steuern der Kameradrehung um die X- und Y-Achsen verwendet.</span><span class="sxs-lookup"><span data-stu-id="85a89-113">These controls are commonly known as WASD controls in gaming, where the W, A, S, and D keys are used for x-z plane fixed camera movement, and the mouse is used to control camera rotation around the x and y axes.</span></span>

## <a name="objectives"></a><span data-ttu-id="85a89-114">Ziele</span><span class="sxs-lookup"><span data-stu-id="85a89-114">Objectives</span></span>


-   <span data-ttu-id="85a89-115">Hinzufügen einfacher Bewegungs-/Blicksteuerungen zum DirectX-Spiel für Maus und Tastatur sowie Touchscreens</span><span class="sxs-lookup"><span data-stu-id="85a89-115">Add basic move-look controls to your DirectX game for both mouse and keyboard, and touch screens.</span></span>
-   <span data-ttu-id="85a89-116">Implementieren einer First-Person-Kamera zum Navigieren in einer 3D-Umgebung</span><span class="sxs-lookup"><span data-stu-id="85a89-116">Implement a first-person camera used to navigate a 3D environment.</span></span>

## <a name="a-note-on-touch-control-implementations"></a><span data-ttu-id="85a89-117">Hinweis zur Implementierung der Fingereingabesteuerung</span><span class="sxs-lookup"><span data-stu-id="85a89-117">A note on touch control implementations</span></span>


<span data-ttu-id="85a89-118">Für die Toucheingabesteuerungen werden zwei Controller implementiert: der Bewegungscontroller, der die Bewegung in der Z-Ebene relativ zum Blickpunkt der Kamera behandelt, und der Blickcontroller, der den Blickpunkt der Kamera ausrichtet.</span><span class="sxs-lookup"><span data-stu-id="85a89-118">For touch controls, we implement two controllers: the move controller, which handles movement in the x-z plane relative to the camera's look point; and the look controller, which aims the camera's look point.</span></span> <span data-ttu-id="85a89-119">Der Bewegungscontroller ist den WASD-Tasten auf der Tastatur zugeordnet und der Blickcontroller der Maus.</span><span class="sxs-lookup"><span data-stu-id="85a89-119">Our move controller maps to the keyboard WASD buttons, and the look controller maps to the mouse.</span></span> <span data-ttu-id="85a89-120">Für die Fingereingabesteuerungen müssen wir aber einen Bereich des Bildschirms festlegen, der als Richtungseingabe bzw. als virtuelle WASD-Tasten dient, während der restliche Bildschirm den Eingabebereich für die Blicksteuerungen darstellt.</span><span class="sxs-lookup"><span data-stu-id="85a89-120">But for touch controls, we need to define a region of the screen that serves as the directional inputs, or the virtual WASD buttons, with the remainder of the screen serving as the input space for the look controls.</span></span>

<span data-ttu-id="85a89-121">Der Bildschirm sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="85a89-121">Our screen looks like this.</span></span>

![Layout des Bewegungs-/Blickrichtungscontrollers](images/movelook-touch.png)

<span data-ttu-id="85a89-123">Wenn Sie in der linken unteren Bildschirmecke den Toucheingabezeiger (nicht die Maus!) nach oben bewegen, bewegt sich die Kamera vorwärts.</span><span class="sxs-lookup"><span data-stu-id="85a89-123">When you move the touch pointer (not the mouse!) in the lower left of the screen, any movement upwards will make the camera move forward.</span></span> <span data-ttu-id="85a89-124">Bei allen Abwärtsbewegungen bewegt sich die Kamera rückwärts.</span><span class="sxs-lookup"><span data-stu-id="85a89-124">Any movement downwards will make the camera move backwards.</span></span> <span data-ttu-id="85a89-125">Das Gleiche gilt für Bewegungen nach links und rechts im Zeigerbereich des Bewegungscontrollers.</span><span class="sxs-lookup"><span data-stu-id="85a89-125">The same holds for left and right movement inside the move controller's pointer space.</span></span> <span data-ttu-id="85a89-126">Außerhalb dieses Bereichs wird der Zeiger zum Blickcontroller – Sie ziehen die Kamera einfach durch Berühren des Bildschirms in die gewünschte Blickrichtung.</span><span class="sxs-lookup"><span data-stu-id="85a89-126">Outside of that space, and it becomes a look controller -- you just touch or drag the camera to where you'd like it to face.</span></span>

## <a name="set-up-the-basic-input-event-infrastructure"></a><span data-ttu-id="85a89-127">Einrichten der grundlegenden Eingabeereignisinfrastruktur</span><span class="sxs-lookup"><span data-stu-id="85a89-127">Set up the basic input event infrastructure</span></span>


<span data-ttu-id="85a89-128">Zunächst müssen wir die Steuerungsklasse erstellen, mit der wir Eingabeereignisse von Maus und Tastatur behandeln, und die Kameraperspektive auf der Grundlage dieser Eingabe aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85a89-128">First, we must create our control class that we use to handle input events from the mouse and keyboard, and update the camera perspective based on that input.</span></span> <span data-ttu-id="85a89-129">Da wir Bewegungs-/Blicksteuerungen implementieren, nennen wir diese Klasse **MoveLookController**.</span><span class="sxs-lookup"><span data-stu-id="85a89-129">Because we're implementing move-look controls, we call it **MoveLookController**.</span></span>

```cpp
using namespace Windows::UI::Core;
using namespace Windows::System;
using namespace Windows::Foundation;
using namespace Windows::Devices::Input;
#include <DirectXMath.h>

// Methods to get input from the UI pointers
ref class MoveLookController
{
};  // class MoveLookController
```

<span data-ttu-id="85a89-130">Jetzt erstellen wir einen Header, der den Zustand des Bewegungs-/Blickcontrollers und der First-Person-Kamera definiert, sowie die grundlegenden Methoden und Ereignishandler, die die Steuerungen implementieren und den Zustand der Kamera aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85a89-130">Now, let's create a header that defines the state of the move-look controller and its first-person camera, plus the basic methods and event handlers that implement the controls and that update the state of the camera.</span></span>

```cpp
#define ROTATION_GAIN 0.004f    // Sensitivity adjustment for the look controller
#define MOVEMENT_GAIN 0.1f      // Sensitivity adjustment for the move controller

ref class MoveLookController
{
private:
    // Properties of the controller object
    DirectX::XMFLOAT3 m_position;               // The position of the controller
    float m_pitch, m_yaw;           // Orientation euler angles in radians

    // Properties of the Move control
    bool m_moveInUse;               // Specifies whether the move control is in use
    uint32 m_movePointerID;         // Id of the pointer in this control
    DirectX::XMFLOAT2 m_moveFirstDown;          // Point where initial contact occurred
    DirectX::XMFLOAT2 m_movePointerPosition;   // Point where the move pointer is currently located
    DirectX::XMFLOAT3 m_moveCommand;            // The net command from the move control

    // Properties of the Look control
    bool m_lookInUse;               // Specifies whether the look control is in use
    uint32 m_lookPointerID;         // Id of the pointer in this control
    DirectX::XMFLOAT2 m_lookLastPoint;          // Last point (from last frame)
    DirectX::XMFLOAT2 m_lookLastDelta;          // For smoothing

    bool m_forward, m_back;         // States for movement
    bool m_left, m_right;
    bool m_up, m_down;


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

    void OnKeyDown(
        _In_ Windows::UI::Core::CoreWindow^ sender,
        _In_ Windows::UI::Core::KeyEventArgs^ args
        );

    void OnKeyUp(
        _In_ Windows::UI::Core::CoreWindow^ sender,
        _In_ Windows::UI::Core::KeyEventArgs^ args
        );

    // Set up the Controls that this controller supports
    void Initialize( _In_ Windows::UI::Core::CoreWindow^ window );

    void Update( Windows::UI::Core::CoreWindow ^window );
    
internal:
    // Accessor to set position of controller
    void SetPosition( _In_ DirectX::XMFLOAT3 pos );

    // Accessor to set position of controller
    void SetOrientation( _In_ float pitch, _In_ float yaw );

    // Returns the position of the controller object
    DirectX::XMFLOAT3 get_Position();

    // Returns the point  which the controller is facing
    DirectX::XMFLOAT3 get_LookPoint();


};  // class MoveLookController
```

<span data-ttu-id="85a89-131">Unser Code enthält vier Gruppen privater Felder.</span><span class="sxs-lookup"><span data-stu-id="85a89-131">Our code contains 4 groups of private fields.</span></span> <span data-ttu-id="85a89-132">Im Folgenden klären wir, wofür die einzelnen Felder dienen.</span><span class="sxs-lookup"><span data-stu-id="85a89-132">Let's review the purpose of each one.</span></span>

<span data-ttu-id="85a89-133">Als Erstes definieren wir einige nützliche Felder, die die aktualisierten Informationen zur Kameraansicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="85a89-133">First, we define some useful fields that hold our updated info about our camera view.</span></span>

-   <span data-ttu-id="85a89-134">**m\_position** ist die Position der Kamera (und daher die Bildebene) in der 3D-Szene (in Szenenkoordinaten).</span><span class="sxs-lookup"><span data-stu-id="85a89-134">**m\_position** is the position of the camera (and therefore the viewplane) in the 3D scene, using scene coordinates.</span></span>
-   <span data-ttu-id="85a89-135">**m\_pitch** ist der Nickwinkel der Kamera bzw. ihre Drehung nach oben oder unten um die X-Achse der Bildebene (in Radianten).</span><span class="sxs-lookup"><span data-stu-id="85a89-135">**m\_pitch** is the pitch of the camera, or its up-down rotation around the viewplane's x-axis, in radians.</span></span>
-   <span data-ttu-id="85a89-136">**m\_yaw** ist der Gierwinkel der Kamera bzw. ihre Drehung nach links oder rechts um die Y-Achse der Bildebene (in Radianten).</span><span class="sxs-lookup"><span data-stu-id="85a89-136">**m\_yaw** is the yaw of the camera, or its left-right rotation around the viewplane's y-axis, in radians.</span></span>

<span data-ttu-id="85a89-137">Als Nächstes definieren wir die Felder, in denen Informationen zum Status und zur Position der Controller gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="85a89-137">Now, let's define the fields that we use to store info about the status and position of our controllers.</span></span> <span data-ttu-id="85a89-138">Die Felder, die wir für den fingereingabebasierten Bewegungscontroller benötigen, definieren wir zuerst.</span><span class="sxs-lookup"><span data-stu-id="85a89-138">First, we'll define the fields we need for our touch-based move controller.</span></span> <span data-ttu-id="85a89-139">(Für die Tastaturimplementierung des Bewegungscontrollers sind keine speziellen Felder erforderlich.</span><span class="sxs-lookup"><span data-stu-id="85a89-139">(There's nothing special needed for the keyboard implementation of the move controller.</span></span> <span data-ttu-id="85a89-140">Es werden nur Tastaturereignisse mit bestimmten Handlern gelesen.)</span><span class="sxs-lookup"><span data-stu-id="85a89-140">We just read keyboard events with specific handlers.)</span></span>

-   <span data-ttu-id="85a89-141">**m\_moveInUse** gibt an, ob der Bewegungscontroller verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="85a89-141">**m\_moveInUse** indicates whether the move controller is in use.</span></span>
-   <span data-ttu-id="85a89-142">**m\_movePointerID** ist die eindeutige ID für den aktuellen Bewegungszeiger.</span><span class="sxs-lookup"><span data-stu-id="85a89-142">**m\_movePointerID** is the unique ID for the current move pointer.</span></span> <span data-ttu-id="85a89-143">Damit wird beim Überprüfen der Zeiger-ID zwischen dem Blickzeiger und dem Bewegungszeiger unterschieden.</span><span class="sxs-lookup"><span data-stu-id="85a89-143">We use it to differentiate between the look pointer and the move pointer when we check the pointer ID value.</span></span>
-   <span data-ttu-id="85a89-144">**m\_moveFirstDown** ist der Punkt auf dem Bildschirm, an dem der Spieler den Zeigerbereich des Bewegungscontrollers zuerst berührt hat.</span><span class="sxs-lookup"><span data-stu-id="85a89-144">**m\_moveFirstDown** is the point on the screen where the player first touched the move controller pointer area.</span></span> <span data-ttu-id="85a89-145">Dieser Wert wird später verwendet, um einen inaktiven Bereich festzulegen, damit die Ansicht bei geringfügigen Bewegungen nicht zittert.</span><span class="sxs-lookup"><span data-stu-id="85a89-145">We use this value later to set a dead zone to keep tiny movements from jittering the view.</span></span>
-   <span data-ttu-id="85a89-146">**m\_movePointerPosition** ist der Punkt auf dem Bildschirm, an den der Spieler den Zeiger gerade bewegt hat.</span><span class="sxs-lookup"><span data-stu-id="85a89-146">**m\_movePointerPosition** is the point on the screen the player has currently moved the pointer to.</span></span> <span data-ttu-id="85a89-147">Dieser Wert wird mit **m\_moveFirstDown** verglichen, um die beabsichtigte Bewegungsrichtung des Spielers zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="85a89-147">We use it to determine what direction the player wanted to move by examining it relative to **m\_moveFirstDown**.</span></span>
-   <span data-ttu-id="85a89-148">**m\_moveCommand** ist der berechnete endgültige Befehl für den Bewegungscontroller: nach oben (vorwärts), nach unten (rückwärts), nach links oder nach rechts.</span><span class="sxs-lookup"><span data-stu-id="85a89-148">**m\_moveCommand** is the final computed command for the move controller: up (forward), down (back), left, or right.</span></span>

<span data-ttu-id="85a89-149">Jetzt definieren wir die Felder für den Blickcontroller (für Maus- und Toucheingabeimplementierungen).</span><span class="sxs-lookup"><span data-stu-id="85a89-149">Now, we define the fields we use for our look controller, both the mouse and touch implementations.</span></span>

-   <span data-ttu-id="85a89-150">**m\_lookInUse** gibt an, ob die Blicksteuerung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="85a89-150">**m\_lookInUse** indicates whether the look control is in use.</span></span>
-   <span data-ttu-id="85a89-151">**m\_lookPointerID** ist die eindeutige ID für den aktuellen Blickzeiger.</span><span class="sxs-lookup"><span data-stu-id="85a89-151">**m\_lookPointerID** is the unique ID for the current look pointer.</span></span> <span data-ttu-id="85a89-152">Damit wird beim Überprüfen der Zeiger-ID zwischen dem Blickzeiger und dem Bewegungszeiger unterschieden.</span><span class="sxs-lookup"><span data-stu-id="85a89-152">We use it to differentiate between the look pointer and the move pointer when we check the pointer ID value.</span></span>
-   <span data-ttu-id="85a89-153">**m\_lookLastPoint** ist der letzte Punkt, der im vorherigen Frame erfasst wurde (in Szenenkoordinaten).</span><span class="sxs-lookup"><span data-stu-id="85a89-153">**m\_lookLastPoint** is the last point, in scene coordinates, that was captured in the previous frame.</span></span>
-   <span data-ttu-id="85a89-154">**m\_lookLastDelta** ist die berechnete Differenz zwischen der aktuellen **m\_position** und **m\_lookLastPoint**.</span><span class="sxs-lookup"><span data-stu-id="85a89-154">**m\_lookLastDelta** is the computed difference between the current **m\_position** and **m\_lookLastPoint**.</span></span>

<span data-ttu-id="85a89-155">Zum Schluss definieren wir sechs boolesche Werte für die sechs Bewegungsgrade, mit denen der aktuelle Zustand der einzelnen Bewegungsaktionen angegeben wird (Ein oder Aus):</span><span class="sxs-lookup"><span data-stu-id="85a89-155">Finally, we define 6 Boolean values for the 6 degrees of movement, which we use to indicate the current state of each directional move action (on or off):</span></span>

-   <span data-ttu-id="85a89-156">**m\_forward**, **m\_back**, **m\_left**, **m\_right**, **m\_up** und **m\_down**.</span><span class="sxs-lookup"><span data-stu-id="85a89-156">**m\_forward**, **m\_back**, **m\_left**, **m\_right**, **m\_up** and **m\_down**.</span></span>

<span data-ttu-id="85a89-157">Die Eingabedaten zum Aktualisieren des Zustands der Controller werden mit sechs Ereignishandlern erfasst:</span><span class="sxs-lookup"><span data-stu-id="85a89-157">We use the 6 event handlers to capture the input data we use to update the state of our controllers:</span></span>

-   <span data-ttu-id="85a89-158">**OnPointerPressed**.</span><span class="sxs-lookup"><span data-stu-id="85a89-158">**OnPointerPressed**.</span></span> <span data-ttu-id="85a89-159">Der Spieler hat die linke Maustaste gedrückt oder den Bildschirm berührt, während sich der Zeiger im Spielbildschirm befand.</span><span class="sxs-lookup"><span data-stu-id="85a89-159">The player pressed the left mouse button with the pointer in our game screen, or touched the screen.</span></span>
-   <span data-ttu-id="85a89-160">**OnPointerMoved**.</span><span class="sxs-lookup"><span data-stu-id="85a89-160">**OnPointerMoved**.</span></span> <span data-ttu-id="85a89-161">Der Spieler hat die Maus oder den Toucheingabezeiger auf dem Bildschirm bewegt, während sich der Zeiger im Spielbildschirm befand.</span><span class="sxs-lookup"><span data-stu-id="85a89-161">The player moved the mouse with the pointer in our game screen, or dragged the touch pointer on the screen.</span></span>
-   <span data-ttu-id="85a89-162">**OnPointerReleased**.</span><span class="sxs-lookup"><span data-stu-id="85a89-162">**OnPointerReleased**.</span></span> <span data-ttu-id="85a89-163">Der Spieler hat die linke Maustaste losgelassen oder aufgehört, den Bildschirm zu berühren, während sich der Zeiger im Spielbildschirm befand.</span><span class="sxs-lookup"><span data-stu-id="85a89-163">The player released the left mouse button with the pointer in our game screen, or stopped touching the screen.</span></span>
-   <span data-ttu-id="85a89-164">**OnKeyDown**.</span><span class="sxs-lookup"><span data-stu-id="85a89-164">**OnKeyDown**.</span></span> <span data-ttu-id="85a89-165">Der Spieler hat eine Taste gedrückt.</span><span class="sxs-lookup"><span data-stu-id="85a89-165">The player pressed a key.</span></span>
-   <span data-ttu-id="85a89-166">**OnKeyUp**.</span><span class="sxs-lookup"><span data-stu-id="85a89-166">**OnKeyUp**.</span></span> <span data-ttu-id="85a89-167">Der Spieler hat eine Taste losgelassen.</span><span class="sxs-lookup"><span data-stu-id="85a89-167">The player released a key.</span></span>

<span data-ttu-id="85a89-168">Die folgenden Methoden und Eigenschaften verwenden wir, um die Zustandsinformationen der Controller zu initialisieren, auf sie zuzugreifen und sie zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85a89-168">And finally, we use these methods and properties to initialize, access, and update the controllers' state info.</span></span>

-   <span data-ttu-id="85a89-169">**Initialize**.</span><span class="sxs-lookup"><span data-stu-id="85a89-169">**Initialize**.</span></span> <span data-ttu-id="85a89-170">Die App ruft diesen Ereignishandler auf, um die Steuerungen zu initialisieren und an das [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Objekt anzufügen, das das Anzeigefenster beschreibt.</span><span class="sxs-lookup"><span data-stu-id="85a89-170">Our app calls this event handler to initialize the controls and attach them to the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) object that describes our display window.</span></span>
-   <span data-ttu-id="85a89-171">**SetPosition**.</span><span class="sxs-lookup"><span data-stu-id="85a89-171">**SetPosition**.</span></span> <span data-ttu-id="85a89-172">Die App ruft diese Methode auf, um die Koordinaten (X, Y und Z) der Steuerungen im Szenenbereich festzulegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-172">Our app calls this method to set the (x, y, and z) coordinates of our controls in the scene space.</span></span>
-   <span data-ttu-id="85a89-173">**SetOrientation**.</span><span class="sxs-lookup"><span data-stu-id="85a89-173">**SetOrientation**.</span></span> <span data-ttu-id="85a89-174">Die App ruft diese Methode auf, um den Nick- und Gierwinkel der Kamera festzulegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-174">Our app calls this method to set the pitch and yaw of the camera.</span></span>
-   <span data-ttu-id="85a89-175">**get\_Position**.</span><span class="sxs-lookup"><span data-stu-id="85a89-175">**get\_Position**.</span></span> <span data-ttu-id="85a89-176">Die App greift auf diese Eigenschaft zu, um die aktuelle Position der Kamera im Szenenbereich abzurufen.</span><span class="sxs-lookup"><span data-stu-id="85a89-176">Our app accesses this property to get the current position of the camera in the scene space.</span></span> <span data-ttu-id="85a89-177">Diese Eigenschaft wird verwendet, um der App die aktuelle Kameraposition mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="85a89-177">You use this property as the method of communicating the current camera position to the app.</span></span>
-   <span data-ttu-id="85a89-178">**get\_LookPoint**.</span><span class="sxs-lookup"><span data-stu-id="85a89-178">**get\_LookPoint**.</span></span> <span data-ttu-id="85a89-179">Die App greift auf diese Eigenschaft zu, um den aktuellen Punkt abzurufen, auf den die Kamera gerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="85a89-179">Our app accesses this property to get the current point toward which the controller camera is facing.</span></span>
-   <span data-ttu-id="85a89-180">**Update**.</span><span class="sxs-lookup"><span data-stu-id="85a89-180">**Update**.</span></span> <span data-ttu-id="85a89-181">Diese Methode liest den Zustand der Bewegungs- und Blickcontroller und aktualisiert die Kameraposition.</span><span class="sxs-lookup"><span data-stu-id="85a89-181">Reads the state of the move and look controllers and updates the camera position.</span></span> <span data-ttu-id="85a89-182">Diese Methode wird in der Hauptschleife der App kontinuierlich aufgerufen, um die Kameracontrollerdaten und die Kameraposition im Szenenbereich zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85a89-182">You continually call this method from the app's main loop to refresh the camera controller data and the camera position in the scene space.</span></span>

<span data-ttu-id="85a89-183">Jetzt haben Sie alle Komponenten, die Sie zum Implementieren der Bewegungs-/Blicksteuerungen benötigen.</span><span class="sxs-lookup"><span data-stu-id="85a89-183">Now, you have here all the components you need to implement your move-look controls.</span></span> <span data-ttu-id="85a89-184">Als Nächstes setzen wir diese Teile zusammen.</span><span class="sxs-lookup"><span data-stu-id="85a89-184">So, let's connect these pieces together.</span></span>

## <a name="create-the-basic-input-events"></a><span data-ttu-id="85a89-185">Erstellen der grundlegenden Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="85a89-185">Create the basic input events</span></span>


<span data-ttu-id="85a89-186">Der Ereignisverteiler der Windows-Runtime stellt fünfEreignisse bereit, die von Instanzen der **MoveLookController**-Klasse behandelt werden sollen:</span><span class="sxs-lookup"><span data-stu-id="85a89-186">The Windows Runtime event dispatcher provides 5 events we want instances of the **MoveLookController** class to handle:</span></span>

-   [**<span data-ttu-id="85a89-187">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="85a89-187">PointerPressed</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208278)
-   [**<span data-ttu-id="85a89-188">PointerMoved</span><span class="sxs-lookup"><span data-stu-id="85a89-188">PointerMoved</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208276)
-   [**<span data-ttu-id="85a89-189">PointerReleased</span><span class="sxs-lookup"><span data-stu-id="85a89-189">PointerReleased</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208279)
-   [**<span data-ttu-id="85a89-190">KeyUp</span><span class="sxs-lookup"><span data-stu-id="85a89-190">KeyUp</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208271)
-   [**<span data-ttu-id="85a89-191">KeyDown</span><span class="sxs-lookup"><span data-stu-id="85a89-191">KeyDown</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208270)

<span data-ttu-id="85a89-192">Diese Ereignisse sind im [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Typ implementiert.</span><span class="sxs-lookup"><span data-stu-id="85a89-192">These events are implemented on the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) type.</span></span> <span data-ttu-id="85a89-193">Es wird davon ausgegangen, dass Sie über ein **CoreWindow**-Objekt verfügen, mit dem Sie arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="85a89-193">We assume that you have a **CoreWindow** object to work with.</span></span> <span data-ttu-id="85a89-194">Informationen dazu, wie Sie ein solches Objekt erhalten, finden Sie bei Bedarf unter [Einrichten der UWP-C++-App (Universals Windows Plattform) zum Anzeigen einer DirectX-Ansicht](https://msdn.microsoft.com/library/windows/apps/hh465077).</span><span class="sxs-lookup"><span data-stu-id="85a89-194">If you don't know how to obtain one, see [How to set up your Universal Windows Platform (UWP) C++ app to display a DirectX view](https://msdn.microsoft.com/library/windows/apps/hh465077).</span></span>

<span data-ttu-id="85a89-195">Wenn diese Ereignisse während der Ausführung der App ausgelöst werden, aktualisieren die Handler die in den privaten Feldern definierten Zustandsinformationen der Controller.</span><span class="sxs-lookup"><span data-stu-id="85a89-195">As these events fire while our app is running, the handlers update the controllers' state info defined in our private fields.</span></span>

<span data-ttu-id="85a89-196">Als Erstes füllen wir die Ereignishandler für die Maus und den Toucheingabezeiger auf.</span><span class="sxs-lookup"><span data-stu-id="85a89-196">First, let's populate the mouse and touch pointer event handlers.</span></span> <span data-ttu-id="85a89-197">Im ersten Ereignishandler (**OnPointerPressed()**), rufen wir die X- und Y-Koordinaten des Zeigers vom [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Objekt ab, das die Anzeige verwaltet, wenn der Benutzer im Bereich des Blickcontrollers mit der Maus klickt oder den Bildschirm berührt.</span><span class="sxs-lookup"><span data-stu-id="85a89-197">In the first event handler, **OnPointerPressed()**, we get the x-y coordinates of the pointer from the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) that manages our display when the user clicks the mouse or touches the screen in the look controller region.</span></span>

**<span data-ttu-id="85a89-198">OnPointerPressed</span><span class="sxs-lookup"><span data-stu-id="85a89-198">OnPointerPressed</span></span>**

```cpp
void MoveLookController::OnPointerPressed(
_In_ CoreWindow^ sender,
_In_ PointerEventArgs^ args)
{
    // Get the current pointer position.
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2( args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y );

    auto device = args->CurrentPoint->PointerDevice;
    auto deviceType = device->PointerDeviceType;
    if ( deviceType == PointerDeviceType::Mouse )
    {
        // Action, Jump, or Fire
    }

    // Check  if this pointer is in the move control.
    // Change the values  to percentages of the preferred screen resolution.
    // You can set the x value to <preferred resolution> * <percentage of width>
    // for example, ( position.x < (screenResolution.x * 0.15) ).

    if (( position.x < 300 && position.y > 380 ) && ( deviceType != PointerDeviceType::Mouse ))
    {
        if ( !m_moveInUse ) // if no pointer is in this control yet
        {
            // Process a DPad touch down event.
            m_moveFirstDown = position;                 // Save the location of the initial contact.
            m_movePointerPosition = position;
            m_movePointerID = pointerID;                // Store the id of the pointer using this control.
            m_moveInUse = TRUE;
        }
    }
    else // This pointer must be in the look control.
    {
        if ( !m_lookInUse ) // If no pointer is in this control yet...
        {
            m_lookLastPoint = position;                         // save the point for later move
            m_lookPointerID = args->CurrentPoint->PointerId;  // store the id of pointer using this control
            m_lookLastDelta.x = m_lookLastDelta.y = 0;          // these are for smoothing
            m_lookInUse = TRUE;
        }
    }
}
```

<span data-ttu-id="85a89-199">Dieser Ereignishandler überprüft, ob es sich beim Zeiger um die Maus handelt (da in diesem Beispiel sowohl Maus als auch Toucheingabe unterstützt werden) und ob sich der Zeiger im Bereich des Bewegungscontrollers befindet.</span><span class="sxs-lookup"><span data-stu-id="85a89-199">This event handler checks whether the pointer is not the mouse (for the purposes of this sample, which supports both mouse and touch) and if it is in the move controller area.</span></span> <span data-ttu-id="85a89-200">Treffen beide Kriterien zu, überprüft er, ob der Zeiger gerade erst gedrückt wurde (d.h. ob dieses Click-Ereignis nicht mit einer vorherigen Bewegungs- oder Blickeingabe zusammenhängt), indem er testet, ob **m\_moveInUse** auf „false“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="85a89-200">If both criteria are true, it checks whether the pointer was just pressed, specifically, whether this click is unrelated to a previous move or look input, by testing if **m\_moveInUse** is false.</span></span> <span data-ttu-id="85a89-201">Ist dies der Fall, erfasst der Handler den entsprechenden Punkt im Bereich des Bewegungscontrollers und legt **m\_moveInUse** auf „true“ fest, damit er die Startposition der Eingabeinteraktion für den Bewegungscontroller bei einem erneuten Aufruf nicht überschreibt.</span><span class="sxs-lookup"><span data-stu-id="85a89-201">If so, the handler captures the point in the move controller area where the press happened and sets **m\_moveInUse** to true, so that when this handler is called again, it won't overwrite the start position of the move controller input interaction.</span></span> <span data-ttu-id="85a89-202">Außerdem aktualisiert er die Zeiger-ID des Bewegungscontrollers mit der ID des aktuellen Zeigers.</span><span class="sxs-lookup"><span data-stu-id="85a89-202">It also updates the move controller pointer ID to the current pointer's ID.</span></span>

<span data-ttu-id="85a89-203">Wenn es sich beim Zeiger um die Maus handelt oder der Toucheingabezeiger sich nicht im Bereich des Bewegungscontrollers befindet, muss er sich im Bereich des Blickcontrollers befinden.</span><span class="sxs-lookup"><span data-stu-id="85a89-203">If the pointer is the mouse or if the touch pointer isn't in the move controller area, it must be in the look controller area.</span></span> <span data-ttu-id="85a89-204">Der Handler legt **m\_lookLastPoint** auf die aktuelle Position fest, an der der Benutzer die Maustaste gedrückt oder den Bildschirm berührt und gedrückt hat, setzt die Differenz (Delta) zurück und aktualisiert die Zeiger-ID des Blickcontrollers mit der aktuellen Zeiger-ID.</span><span class="sxs-lookup"><span data-stu-id="85a89-204">It sets **m\_lookLastPoint** to the current position where the user pressed the mouse button or touched and pressed, resets the delta, and updates the look controller's pointer ID to the current pointer ID.</span></span> <span data-ttu-id="85a89-205">Außerdem legt er den Zustand des Blickcontrollers auf „Aktiv“ fest.</span><span class="sxs-lookup"><span data-stu-id="85a89-205">It also sets the state of the look controller to active.</span></span>

**<span data-ttu-id="85a89-206">OnPointerMoved</span><span class="sxs-lookup"><span data-stu-id="85a89-206">OnPointerMoved</span></span>**

```cpp
void MoveLookController::OnPointerMoved(
    _In_ CoreWindow ^sender,
    _In_ PointerEventArgs ^args)
{
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2(args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y);

    // Decide which control this pointer is operating.
    if (pointerID == m_movePointerID)           // This is the move pointer.
    {
        // Move control
        m_movePointerPosition = position;       // Save the current position.

    }
    else if (pointerID == m_lookPointerID)      // This is the look pointer.
    {
        // Look control

        DirectX::XMFLOAT2 pointerDelta;
        pointerDelta.x = position.x - m_lookLastPoint.x;        // How far did pointer move
        pointerDelta.y = position.y - m_lookLastPoint.y;

        DirectX::XMFLOAT2 rotationDelta;
        rotationDelta.x = pointerDelta.x * ROTATION_GAIN;   // Scale for control sensitivity.
        rotationDelta.y = pointerDelta.y * ROTATION_GAIN;

        m_lookLastPoint = position;                     // Save for the next time through.

                                                        // Update our orientation based on the command.
        m_pitch -= rotationDelta.y;                     // Mouse y increases down, but pitch increases up.
        m_yaw -= rotationDelta.x;                       // Yaw is defined as CCW around the y-axis.

                                                        // Limit the pitch to straight up or straight down.
        m_pitch = (float)__max(-DirectX::XM_PI / 2.0f, m_pitch);
        m_pitch = (float)__min(+DirectX::XM_PI / 2.0f, m_pitch);
    }
}
```

<span data-ttu-id="85a89-207">Der **OnPointerMoved**-Ereignishandler wird bei jeder Bewegung des Zeigers ausgelöst (in diesem Fall, wenn ein Toucheingabezeiger bewegt oder der Mauszeiger mit gedrückter linker Maustaste bewegt wird).</span><span class="sxs-lookup"><span data-stu-id="85a89-207">The **OnPointerMoved** event handler fires whenever the pointer moves (in this case, if a touch screen pointer is being dragged, or if the mouse pointer is being moved while the left button is pressed).</span></span> <span data-ttu-id="85a89-208">Ist die Zeiger-ID mit der Zeiger-ID des Bewegungscontrollers identisch, ist es der Bewegungszeiger. Andernfalls wird überprüft, ob es sich beim aktiven Zeiger um den Zeiger des Blickcontrollers handelt.</span><span class="sxs-lookup"><span data-stu-id="85a89-208">If the pointer ID is the same as the move controller pointer's ID, then it's the move pointer; otherwise, we check if it's the look controller that's the active pointer.</span></span>

<span data-ttu-id="85a89-209">Wenn es sich um den Zeiger des Bewegungscontrollers handelt, wird nur die Zeigerposition aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="85a89-209">If it's the move controller, we just update the pointer position.</span></span> <span data-ttu-id="85a89-210">Die Position wird weiter aktualisiert, solange das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276)-Ereignis ausgelöst wird, da die endgültige Position mit der ersten Position verglichen werden soll, die mit dem **OnPointerPressed**-Ereignishandler erfasst wurde.</span><span class="sxs-lookup"><span data-stu-id="85a89-210">We keep updating it as long the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276) event keeps firing, because we want to compare the final position with the first one we captured with the **OnPointerPressed** event handler.</span></span>

<span data-ttu-id="85a89-211">Wenn es sich um den Zeiger des Blickcontrollers handelt, wird es etwas komplizierter.</span><span class="sxs-lookup"><span data-stu-id="85a89-211">If it's the look controller, things are a little more complicated.</span></span> <span data-ttu-id="85a89-212">Wir müssen einen neuen Blickpunkt berechnen und die Kamera auf diesen Punkt ausrichten. Dazu berechnen wir die Differenz zwischen dem letzten Blickpunkt und der aktuellen Bildschirmposition und multiplizieren sie mit dem Skalierungsfaktor, den wir einstellen können, um die Blickbewegungen in Bezug zur Distanz der Bildschirmbewegung zu verkleinern oder zu vergrößern.</span><span class="sxs-lookup"><span data-stu-id="85a89-212">We need to calculate a new look point and center the camera on it, so we calculate the delta between the last look point and the current screen position, and then we multiply versus our scale factor, which we can tweak to make the look movements smaller or larger relative to the distance of the screen movement.</span></span> <span data-ttu-id="85a89-213">Anhand dieses Werts berechnen wir den Neigungswinkel und den Schwenkwinkel.</span><span class="sxs-lookup"><span data-stu-id="85a89-213">Using that value, we calculate the pitch and the yaw.</span></span>

<span data-ttu-id="85a89-214">Abschließend müssen wir die Bewegungs- oder Blickcontrollerverhalten deaktivieren, wenn der Spieler aufhört, die Maus zu bewegen oder den Bildschirm zu berühren.</span><span class="sxs-lookup"><span data-stu-id="85a89-214">Finally, we need to deactivate the move or look controller behaviors when the player stops moving the mouse or touching the screen.</span></span> <span data-ttu-id="85a89-215">Dazu wird der **OnPointerReleased**-Ereignishandler verwendet. Diesen Handler rufen wir auf, wenn [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) ausgelöst wird, um **m\_moveInUse** oder **m\_lookInUse** auf „false“ festzulegen, die Schwenkbewegung der Kamera zu deaktivieren und die Zeiger-ID auf Null festzulegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-215">We use **OnPointerReleased**, which we call when [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) is fired, to set **m\_moveInUse** or **m\_lookInUse** to FALSE and turn off the camera pan movement, and to zero out the pointer ID.</span></span>

**<span data-ttu-id="85a89-216">OnPointerReleased</span><span class="sxs-lookup"><span data-stu-id="85a89-216">OnPointerReleased</span></span>**

```cpp
void MoveLookController::OnPointerReleased(
_In_ CoreWindow ^sender,
_In_ PointerEventArgs ^args)
{
    uint32 pointerID = args->CurrentPoint->PointerId;
    DirectX::XMFLOAT2 position = DirectX::XMFLOAT2( args->CurrentPoint->Position.X, args->CurrentPoint->Position.Y );


    if ( pointerID == m_movePointerID )    // This was the move pointer.
    {
        m_moveInUse = FALSE;
        m_movePointerID = 0;
    }
    else if (pointerID == m_lookPointerID ) // This was the look pointer.
    {
        m_lookInUse = FALSE;
        m_lookPointerID = 0;
    }
}
```

<span data-ttu-id="85a89-217">Damit haben wir alle Touchscreenereignisse behandelt.</span><span class="sxs-lookup"><span data-stu-id="85a89-217">So far, we handled all the touch screen events.</span></span> <span data-ttu-id="85a89-218">Als Nächstes behandeln wir die Tasteneingabeereignisse für einen tastaturbasierten Bewegungscontroller.</span><span class="sxs-lookup"><span data-stu-id="85a89-218">Now, let's handle the key input events for a keyboard-based move controller.</span></span>

**<span data-ttu-id="85a89-219">OnKeyDown</span><span class="sxs-lookup"><span data-stu-id="85a89-219">OnKeyDown</span></span>**

```cpp
void MoveLookController::OnKeyDown(
                                   __in CoreWindow^ sender,
                                   __in KeyEventArgs^ args )
{
    Windows::System::VirtualKey Key;
    Key = args->VirtualKey;

    // Figure out the command from the keyboard.
    if ( Key == VirtualKey::W )     // Forward
        m_forward = true;
    if ( Key == VirtualKey::S )     // Back
        m_back = true;
    if ( Key == VirtualKey::A )     // Left
        m_left = true;
    if ( Key == VirtualKey::D )     // Right
        m_right = true;
}
```

<span data-ttu-id="85a89-220">Solange eine dieser Tasten gedrückt wird, legt der Ereignishandler den entsprechenden Bewegungszustand auf „true“ fest.</span><span class="sxs-lookup"><span data-stu-id="85a89-220">As long as one of these keys is pressed, this event handler sets the corresponding directional move state to true.</span></span>

**<span data-ttu-id="85a89-221">OnKeyUp</span><span class="sxs-lookup"><span data-stu-id="85a89-221">OnKeyUp</span></span>**

```cpp
void MoveLookController::OnKeyUp(
                                 __in CoreWindow^ sender,
                                 __in KeyEventArgs^ args)
{
    Windows::System::VirtualKey Key;
    Key = args->VirtualKey;

    // Figure out the command from the keyboard.
    if ( Key == VirtualKey::W )     // forward
        m_forward = false;
    if ( Key == VirtualKey::S )     // back
        m_back = false;
    if ( Key == VirtualKey::A )     // left
        m_left = false;
    if ( Key == VirtualKey::D )     // right
        m_right = false;
}
```

<span data-ttu-id="85a89-222">Wenn die Taste losgelassen wird, legt der Ereignishandler den Zustand wieder auf „false“ fest.</span><span class="sxs-lookup"><span data-stu-id="85a89-222">And when the key is released, this event handler sets it back to false.</span></span> <span data-ttu-id="85a89-223">Wenn **Update** aufgerufen wird, überprüft der Ereignishandler diese Bewegungszustände und bewegt die Kamera entsprechend.</span><span class="sxs-lookup"><span data-stu-id="85a89-223">When we call **Update**, it checks these directional move states, and move the camera accordingly.</span></span> <span data-ttu-id="85a89-224">Dies ist etwas einfacher als die Implementierung für Fingereingabe.</span><span class="sxs-lookup"><span data-stu-id="85a89-224">This is a bit simpler than the touch implementation!</span></span>

## <a name="initialize-the-touch-controls-and-the-controller-state"></a><span data-ttu-id="85a89-225">Initialisieren der Fingereingabesteuerungen und des Controllerzustands</span><span class="sxs-lookup"><span data-stu-id="85a89-225">Initialize the touch controls and the controller state</span></span>


<span data-ttu-id="85a89-226">Jetzt verbinden wir die Ereignisse und initialisieren alle Controllerzustandsfelder.</span><span class="sxs-lookup"><span data-stu-id="85a89-226">Let's hook up the events now, and initialize all the controller state fields.</span></span>

**<span data-ttu-id="85a89-227">Initialize</span><span class="sxs-lookup"><span data-stu-id="85a89-227">Initialize</span></span>**

```cpp
void MoveLookController::Initialize( _In_ CoreWindow^ window )
{

    // Opt in to recieve touch/mouse events.
    window->PointerPressed += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerPressed);

    window->PointerMoved += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerMoved);

    window->PointerReleased += 
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerReleased);

    window->CharacterReceived +=
    ref new TypedEventHandler<CoreWindow^, CharacterReceivedEventArgs^>(this, &MoveLookController::OnCharacterReceived);

    window->KeyDown += 
    ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &MoveLookController::OnKeyDown);

    window->KeyUp += 
    ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &MoveLookController::OnKeyUp);

    // Initialize the state of the controller.
    m_moveInUse = FALSE;                // No pointer is in the Move control.
    m_movePointerID = 0;

    m_lookInUse = FALSE;                // No pointer is in the Look control.
    m_lookPointerID = 0;

    //  Need to init this as it is reset every frame.
    m_moveCommand = DirectX::XMFLOAT3( 0.0f, 0.0f, 0.0f );

    SetOrientation( 0, 0 );             // Look straight ahead when the app starts.

}
```

<span data-ttu-id="85a89-228">Die **Initialize**-Methode akzeptiert als Parameter einen Verweis auf die [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Instanz der App und registriert die von uns entwickelten Ereignishandler für die entsprechenden Ereignisse in dieser **CoreWindow**-Instanz.</span><span class="sxs-lookup"><span data-stu-id="85a89-228">**Initialize** takes a reference to the app's [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) instance as a parameter and registers the event handlers we developed to the appropriate events on that **CoreWindow**.</span></span> <span data-ttu-id="85a89-229">Sie initialisiert die Bewegungs- und Blickzeiger-IDs, legt den Befehlsvektor für die Touchscreen-Bewegungscontrollerimplementierung auf Null fest und richtet die Kameraansicht gerade nach vorn aus, wenn die App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="85a89-229">It initializes the move and look pointer's IDs, sets the command vector for our touch screen move controller implementation to zero, and sets the camera looking straight ahead when the app starts.</span></span>

## <a name="getting-and-setting-the-position-and-orientation-of-the-camera"></a><span data-ttu-id="85a89-230">Abrufen und Festlegen der Position und Ausrichtung der Kamera</span><span class="sxs-lookup"><span data-stu-id="85a89-230">Getting and setting the position and orientation of the camera</span></span>


<span data-ttu-id="85a89-231">Als Nächstes definieren wir einige Methoden zum Abrufen und Festlegen der Kameraposition in Bezug zum Viewport.</span><span class="sxs-lookup"><span data-stu-id="85a89-231">Let's define some methods to get and set the position of the camera with respect to the viewport.</span></span>

```cpp
void MoveLookController::SetPosition( _In_ DirectX::XMFLOAT3 pos )
{
    m_position = pos;
}

// Accessor to set the position of the controller.
void MoveLookController::SetOrientation( _In_ float pitch, _In_ float yaw )
{
    m_pitch = pitch;
    m_yaw = yaw;
}

// Returns the position of the controller object.
DirectX::XMFLOAT3 MoveLookController::get_Position()
{
    return m_position;
}

// Returns the point at which the camera controller is facing.
DirectX::XMFLOAT3 MoveLookController::get_LookPoint()
{
    float y = sinf(m_pitch);        // Vertical
    float r = cosf(m_pitch);        // In the plane
    float z = r*cosf(m_yaw);        // Fwd-back
    float x = r*sinf(m_yaw);        // Left-right
    DirectX::XMFLOAT3 result(x,y,z);
    result.x += m_position.x;
    result.y += m_position.y;
    result.z += m_position.z;

    // Return m_position + DirectX::XMFLOAT3(x, y, z);
    return result;
}
```

## <a name="updating-the-controller-state-info"></a><span data-ttu-id="85a89-232">Aktualisieren der Zustandsinformationen der Controller</span><span class="sxs-lookup"><span data-stu-id="85a89-232">Updating the controller state info</span></span>


<span data-ttu-id="85a89-233">Jetzt führen wir die Berechnungen aus, mit denen die in **m\_movePointerPosition** erfassten Zeigerkoordinaten in neue Koordinaten für das Spielwelt-Koordinatensystem konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="85a89-233">Now, we perform our calculations that convert the pointer coordinate info tracked in **m\_movePointerPosition** into new coordinate information respective of our world coordinate system.</span></span> <span data-ttu-id="85a89-234">Die App ruft diese Methode bei jeder Aktualisierung der Hauptschleife auf.</span><span class="sxs-lookup"><span data-stu-id="85a89-234">Our app calls this method every time we refresh the main app loop.</span></span> <span data-ttu-id="85a89-235">Daher berechnen wir an dieser Stelle die neuen Informationen zur Blickpunktposition, die an die App übergeben werden sollen, um die Ansichtsmatrix vor der Projektion in den Viewport zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="85a89-235">So, it is here that we compute the new look point position info we want to pass to the app for updating the view matrix before projection into the viewport.</span></span>

```cpp
void MoveLookController::Update(CoreWindow ^window)
{
    // Check for input from the Move control.
    if (m_moveInUse)
    {
        DirectX::XMFLOAT2 pointerDelta(m_movePointerPosition);
        pointerDelta.x -= m_moveFirstDown.x;
        pointerDelta.y -= m_moveFirstDown.y;

        // Figure out the command from the touch-based virtual joystick.
        if (pointerDelta.x > 16.0f)      // Leave 32 pixel-wide dead spot for being still.
            m_moveCommand.x = 1.0f;
        else
            if (pointerDelta.x < -16.0f)
            m_moveCommand.x = -1.0f;

        if (pointerDelta.y > 16.0f)      // Joystick y is up, so change sign.
            m_moveCommand.y = -1.0f;
        else
            if (pointerDelta.y < -16.0f)
            m_moveCommand.y = 1.0f;
    }

    // Poll our state bits that are set by the keyboard input events.
    if (m_forward)
        m_moveCommand.y += 1.0f;
    if (m_back)
        m_moveCommand.y -= 1.0f;

    if (m_left)
        m_moveCommand.x -= 1.0f;
    if (m_right)
        m_moveCommand.x += 1.0f;

    if (m_up)
        m_moveCommand.z += 1.0f;
    if (m_down)
        m_moveCommand.z -= 1.0f;

    // Make sure that 45 degree cases are not faster.
    DirectX::XMFLOAT3 command = m_moveCommand;
    DirectX::XMVECTOR vector;
    vector = DirectX::XMLoadFloat3(&command);

    if (fabsf(command.x) > 0.1f || fabsf(command.y) > 0.1f || fabsf(command.z) > 0.1f)
    {
        vector = DirectX::XMVector3Normalize(vector);
        DirectX::XMStoreFloat3(&command, vector);
    }
    

    // Rotate command to align with our direction (world coordinates).
    DirectX::XMFLOAT3 wCommand;
    wCommand.x = command.x*cosf(m_yaw) - command.y*sinf(m_yaw);
    wCommand.y = command.x*sinf(m_yaw) + command.y*cosf(m_yaw);
    wCommand.z = command.z;

    // Scale for sensitivity adjustment.
    wCommand.x = wCommand.x * MOVEMENT_GAIN;
    wCommand.y = wCommand.y * MOVEMENT_GAIN;
    wCommand.z = wCommand.z * MOVEMENT_GAIN;

    // Our velocity is based on the command.
    // Also note that y is the up-down axis. 
    DirectX::XMFLOAT3 Velocity;
    Velocity.x = -wCommand.x;
    Velocity.z = wCommand.y;
    Velocity.y = wCommand.z;

    // Integrate
    m_position.x += Velocity.x;
    m_position.y += Velocity.y;
    m_position.z += Velocity.z;

    // Clear movement input accumulator for use during the next frame.
    m_moveCommand = DirectX::XMFLOAT3(0.0f, 0.0f, 0.0f);

}
```

<span data-ttu-id="85a89-236">Damit die Bewegung nicht "zittert", wenn der Spieler den fingereingabebasierten Bewegungscontroller verwendet, legen wir einen virtuellen inaktiven Bereich mit einem Durchmesser von 32Pixel um den Zeiger fest.</span><span class="sxs-lookup"><span data-stu-id="85a89-236">Because we don't want jittery movement when the player uses our touch-based move controller, we set a virtual dead zone around the pointer with a diameter of 32 pixels.</span></span> <span data-ttu-id="85a89-237">Außerdem fügen wir die Geschwindigkeit hinzu, die sich aus dem Befehlswert plus einer Bewegungsrate berechnet.</span><span class="sxs-lookup"><span data-stu-id="85a89-237">We also add velocity, which is the command value plus a movement gain rate.</span></span> <span data-ttu-id="85a89-238">(Sie können dieses Verhalten wie gewünscht anpassen, um die Bewegungsrate basierend auf der Distanz, um die der Zeiger im Bereich des Bewegungscontrollers bewegt wird, zu erhöhen oder zu verringern.)</span><span class="sxs-lookup"><span data-stu-id="85a89-238">(You can adjust this behavior to your liking, to slow down or speed up the rate of movement based on the distance the pointer moves in the move controller area.)</span></span>

<span data-ttu-id="85a89-239">Beim Berechnen der Geschwindigkeit setzen wir außerdem die von den Bewegungs- und Blickcontrollern empfangenen Koordinaten in die Bewegung des tatsächlichen Blickpunkts um, die wir an die Methode zum Berechnen der Ansichtsmatrix für die Szene senden.</span><span class="sxs-lookup"><span data-stu-id="85a89-239">When we compute the velocity, we also translate the coordinates received from the move and look controllers into the movement of the actual look point we send to the method that computes our view matrix for the scene.</span></span> <span data-ttu-id="85a89-240">Als Erstes invertieren wir die X-Koordinate, da sich der Blickpunkt in der Szene in entgegengesetzter Richtung dreht (was die Drehung einer Kamera um ihre Mittelachse simuliert), wenn wir den Blickcontroller per Mausklick oder Toucheingabe nach links oder rechts bewegen.</span><span class="sxs-lookup"><span data-stu-id="85a89-240">First, we invert the x coordinate, because if we click-move or drag left or right with the look controller, the look point rotates in the opposite direction in the scene, as a camera might swing about its central axis.</span></span> <span data-ttu-id="85a89-241">Anschließend vertauschen wir die Y- und Z-Achse, da eine Aufwärts-/Abwärtsbewegung mittels Taste oder Toucheingabe (interpretiert als Y-Achsenverhalten) mit dem Bewegungscontroller in eine Kameraaktion umgesetzt werden soll, durch die der Blickpunkt in den oder aus dem Bildschirm (Z-Achse) bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="85a89-241">Then, we swap the y and z axes, because an up/down key press or touch drag motion (read as a y-axis behavior) on the move controller should translate into a camera action that moves the look point into or out of the screen (the z-axis).</span></span>

<span data-ttu-id="85a89-242">Die endgültige Position des Blickpunkts für den Spieler ist die letzte Position plus die berechnete Geschwindigkeit. Dies ist die Position, die der Renderer liest, wenn er die **get\_Position**-Methode aufruft (wahrscheinlich während der Einrichtung für die einzelnen Frames).</span><span class="sxs-lookup"><span data-stu-id="85a89-242">The final position of the look point for the player is the last position plus the calculated velocity, and this is what is read by the renderer when it calls the **get\_Position** method (most likely during the setup for each frame).</span></span> <span data-ttu-id="85a89-243">Danach setzen wir den Bewegungsbefehl auf Null zurück.</span><span class="sxs-lookup"><span data-stu-id="85a89-243">After that, we reset the move command to zero.</span></span>

## <a name="updating-the-view-matrix-with-the-new-camera-position"></a><span data-ttu-id="85a89-244">Aktualisieren der Ansichtsmatrix mit der neuen Kameraposition</span><span class="sxs-lookup"><span data-stu-id="85a89-244">Updating the view matrix with the new camera position</span></span>


<span data-ttu-id="85a89-245">Wir können eine Koordinate des Szenenbereichs abrufen, auf die die Kamera ausgerichtet ist und die jedes Mal aktualisiert wird, wenn die App dazu angewiesen wird (z.B. alle 60Sekunden in der Hauptschleife der App).</span><span class="sxs-lookup"><span data-stu-id="85a89-245">We can obtain a scene space coordinate that our camera is focused on, and which is updated whenever you tell your app to do so (every 60 seconds in the main app loop, for example).</span></span> <span data-ttu-id="85a89-246">Dieser Pseudocode zeigt das Aufrufverhalten, das Sie implementieren können:</span><span class="sxs-lookup"><span data-stu-id="85a89-246">This pseudocode suggests the calling behavior you can implement:</span></span>

```cpp
myMoveLookController->Update( m_window );   

// Update the view matrix based on the camera position.
myFirstPersonCamera->SetViewParameters(
                 myMoveLookController->get_Position(),       // Point we are at
                 myMoveLookController->get_LookPoint(),      // Point to look towards
                 DirectX::XMFLOAT3( 0, 1, 0 )                   // Up-vector
                 ); 
```

<span data-ttu-id="85a89-247">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="85a89-247">Congratulations!</span></span> <span data-ttu-id="85a89-248">Sie haben einfache Bewegungs-/Blicksteuerungen für Touchscreens und Tastatur-/Mauseingabe in Ihrem Spiel implementiert.</span><span class="sxs-lookup"><span data-stu-id="85a89-248">You've implemented basic move-look controls for both touch screens and keyboard/mouse input touch controls in your game!</span></span>



 

 




