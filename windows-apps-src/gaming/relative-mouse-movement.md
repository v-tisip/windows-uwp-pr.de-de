---
title: Relative Mausbewegung
description: Verwendung relativer Maussteuerungen, die nicht den Systemcursor verwenden und keine absoluten Bildschirmkoordinaten zurückgeben, um das Pixeldelta zwischen Mausebewegungen in Spielen nachzuverfolgen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Maus, Eingabe
ms.assetid: 08c35e05-2822-4a01-85b8-44edb9b6898f
ms.localizationpriority: medium
ms.openlocfilehash: 71985841e6c0fa764201c179fb12408581823e5e
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8208082"
---
# <a name="relative-mouse-movement-and-corewindow"></a><span data-ttu-id="74d2e-104">Relative Mausbewegung und CoreWindow</span><span class="sxs-lookup"><span data-stu-id="74d2e-104">Relative mouse movement and CoreWindow</span></span>

<span data-ttu-id="74d2e-105">In Spielen ist die Maus eine gängige Steuerungsoption, mit der viele Spieler vertraut sind. Sie ist ebenso für viele Spielgenres unentbehrlich, einschließlich der First-Person- und Third-Person-Shooter sowie der Echtzeitstrategiespiele.</span><span class="sxs-lookup"><span data-stu-id="74d2e-105">In games, the mouse is a common control option that is familiar to many players, and is likewise essential to many genres of games, including first- and third-person shooters, and real-time strategy games.</span></span> <span data-ttu-id="74d2e-106">In diesem Thema wird die Implementierung relativer Maussteuerungen erläutert, die nicht den Systemcursor verwenden und keine absoluten Bildschirmkoordinaten zurückgeben, sondern stattdessen das Pixeldelta zwischen Mausbewegungen nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="74d2e-106">Here we discuss the implementation of relative mouse controls, which don't use the system cursor and don't return absolute screen coordinates; instead, they track the pixel delta between mouse movements.</span></span>

<span data-ttu-id="74d2e-107">Einige Apps, z.B. Spiele, verwenden die Maus als ein eher allgemeineres Eingabegerät.</span><span class="sxs-lookup"><span data-stu-id="74d2e-107">Some apps, such as games, use the mouse as a more general input device.</span></span> <span data-ttu-id="74d2e-108">In einem 3D-Modellierer kann die Mauseingabe zum Ausrichten eines 3D-Objekts verwendet werden, indem ein virtueller Trackball simuliert wird. Oder in einem Spiel kann mit der Maus die Richtung der Kamera über Bewegungs-/Blicksteuerungen geändert werden.</span><span class="sxs-lookup"><span data-stu-id="74d2e-108">For example, a 3-D modeler might use mouse input to orient a 3-D object by simulating a virtual trackball; or a game might use the mouse to change the direction of the viewing camera via mouse-look controls.</span></span> 

<span data-ttu-id="74d2e-109">In diesen Szenarien benötigt die App relative Mausdaten.</span><span class="sxs-lookup"><span data-stu-id="74d2e-109">In these scenarios, the app requires relative mouse data.</span></span> <span data-ttu-id="74d2e-110">Relative Mauswerte geben an, welche Entfernung die Maus seit dem letzten Frame zurückgelegt hat, und stellen keine absoluten x- und y-Koordinaten in einem Fenster oder Bildschirm dar.</span><span class="sxs-lookup"><span data-stu-id="74d2e-110">Relative mouse values represent how far the mouse moved since the last frame, rather than the absolute x-y coordinate values within a window or screen.</span></span> <span data-ttu-id="74d2e-111">Zudem blenden Apps häufig den Mauszeiger aus, da die Position des Cursors in Bezug auf die Bildschirmkoordinaten beim Bearbeiten eines 3D-Objekts oder einer 3D-Szene nicht relevant ist.</span><span class="sxs-lookup"><span data-stu-id="74d2e-111">Also, apps often hide the mouse cursor since the position of the cursor with respect to the screen coordinates is not relevant when manipulating a 3-D object or scene.</span></span> 

<span data-ttu-id="74d2e-112">Wenn der Benutzer eine Aktion durchführt, die die App in einen Bearbeitungsmodus für relative 3D-Objekte/-Szenen versetzt, muss die App folgende Aufgaben ausführen:</span><span class="sxs-lookup"><span data-stu-id="74d2e-112">When the user takes an action that moves the app into a relative 3-D object/scene manipulation mode, the app must:</span></span> 
- <span data-ttu-id="74d2e-113">Ignorieren der standardmäßigen Mausbehandlung</span><span class="sxs-lookup"><span data-stu-id="74d2e-113">Ignore default mouse handling.</span></span>
- <span data-ttu-id="74d2e-114">Aktivieren der relativen Mausbehandlung</span><span class="sxs-lookup"><span data-stu-id="74d2e-114">Enable relative mouse handling.</span></span>
- <span data-ttu-id="74d2e-115">Ausblenden des Mauszeigers durch Festlegen eines NULL-Zeigers ("nullptr")</span><span class="sxs-lookup"><span data-stu-id="74d2e-115">Hide the mouse cursor by setting it a null pointer (nullptr).</span></span> 

<span data-ttu-id="74d2e-116">Wenn der Benutzer eine Aktion durchführt, die den App-Bearbeitungsmodus für relative 3D-Objekte/-Szenen beendet, muss die App folgende Aufgaben ausführen:</span><span class="sxs-lookup"><span data-stu-id="74d2e-116">When the user takes an action that moves the app out of a relative 3-D object/scene manipulation mode, the app must:</span></span> 
- <span data-ttu-id="74d2e-117">Aktivieren der standardmäßigen/absoluten Mausbehandlung</span><span class="sxs-lookup"><span data-stu-id="74d2e-117">Enable default/absolute mouse handling.</span></span>
- <span data-ttu-id="74d2e-118">Deaktivieren der relativen Mausbehandlung</span><span class="sxs-lookup"><span data-stu-id="74d2e-118">Turn off relative mouse handling.</span></span> 
- <span data-ttu-id="74d2e-119">Festlegen des Mauszeigers auf einen Wert ungleich NULL (so dass der Mauszeiger sichtbar wird)</span><span class="sxs-lookup"><span data-stu-id="74d2e-119">Set the mouse cursor to a non-null value (which makes it visible).</span></span>

> **<span data-ttu-id="74d2e-120">Hinweis</span><span class="sxs-lookup"><span data-stu-id="74d2e-120">Note</span></span>**  
<span data-ttu-id="74d2e-121">Bei diesem Muster wird die Position des absoluten Mauszeigers beim Wechsel in den relativen Modus ohne Cursor beibehalten.</span><span class="sxs-lookup"><span data-stu-id="74d2e-121">With this pattern, the location of the absolute mouse cursor is preserved on entering the cursorless relative mode.</span></span> <span data-ttu-id="74d2e-122">Der Mauszeiger erscheint erneut an einer Position mit den gleichen Bildschirmkoordinaten wie vor der Aktivierung des Modus für die relative Mausbewegung.</span><span class="sxs-lookup"><span data-stu-id="74d2e-122">The cursor re-appears in the same screen coordinate location as it was previous to enabling the relative mouse movement mode.</span></span>

 

## <a name="handling-relative-mouse-movement"></a><span data-ttu-id="74d2e-123">Behandeln der relativen Mausbewegung</span><span class="sxs-lookup"><span data-stu-id="74d2e-123">Handling relative mouse movement</span></span>


<span data-ttu-id="74d2e-124">Führen Sie die Registrierung für das [MouseDevice::MouseMoved](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.input.mousedevice.mousemoved.aspx)-Ereignis aus, um auf die relativen Mausdeltawerte zuzugreifen, so wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="74d2e-124">To access relative mouse delta values, register for the [MouseDevice::MouseMoved](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.input.mousedevice.mousemoved.aspx) event as shown here.</span></span>


```cpp


// register handler for relative mouse movement events
Windows::Devices::Input::MouseDevice::GetForCurrentView()->MouseMoved +=
        ref new TypedEventHandler<MouseDevice^, MouseEventArgs^>(this, &MoveLookController::OnMouseMoved);


```

```cpp


void MoveLookController::OnMouseMoved(
    _In_ Windows::Devices::Input::MouseDevice^ mouseDevice,
    _In_ Windows::Devices::Input::MouseEventArgs^ args
    )
{
    float2 pointerDelta;
    pointerDelta.x = static_cast<float>(args->MouseDelta.X);
    pointerDelta.y = static_cast<float>(args->MouseDelta.Y);

    float2 rotationDelta;
    rotationDelta = pointerDelta * ROTATION_GAIN;   // scale for control sensitivity

    // update our orientation based on the command
    m_pitch -= rotationDelta.y;                     // mouse y increases down, but pitch increases up
    m_yaw   -= rotationDelta.x;                     // yaw defined as CCW around y-axis

    // limit pitch to straight up or straight down
    float limit = (float)(M_PI/2) - 0.01f;
    m_pitch = (float) __max( -limit, m_pitch );
    m_pitch = (float) __min( +limit, m_pitch );

    // keep longitude in useful range by wrapping
    if ( m_yaw >  M_PI )
        m_yaw -= (float)M_PI*2;
    else if ( m_yaw < -M_PI )
        m_yaw += (float)M_PI*2;
}

```

<span data-ttu-id="74d2e-125">Der Ereignishandler in diesem Codebeispiel, **OnMouseMoved**, rendert die Ansicht basierend auf den Bewegungen der Maus.</span><span class="sxs-lookup"><span data-stu-id="74d2e-125">The event handler in this code example, **OnMouseMoved**, renders the view based on the movements of the mouse.</span></span> <span data-ttu-id="74d2e-126">Die Position des Mauszeigers wird als [MouseEventArgs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.input.mouseeventargs.aspx)-Objekt an den Handler übergeben.</span><span class="sxs-lookup"><span data-stu-id="74d2e-126">The position of the mouse pointer is passed to the handler as a [MouseEventArgs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.input.mouseeventargs.aspx) object.</span></span> 

<span data-ttu-id="74d2e-127">Überspringen Sie die Verarbeitung der absoluten Mausdaten aus dem [CoreWindow::PointerMoved](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointermoved.aspx)-Ereignis, wenn Ihre App in den Modus zur Behandlung relativer Mausbewegungswerte wechselt.</span><span class="sxs-lookup"><span data-stu-id="74d2e-127">Skip over processing of absolute mouse data from the [CoreWindow::PointerMoved](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointermoved.aspx) event when your app changes to handling relative mouse movement values.</span></span> <span data-ttu-id="74d2e-128">Überspringen Sie diese Eingabe jedoch nur, wenn das **CoreWindow::PointerMoved**-Ereignis als Ergebnis einer Mauseingabe (und nicht einer Fingereingabe) aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="74d2e-128">However, only skip this input if the **CoreWindow::PointerMoved** event occurred as the result of mouse input (as opposed to touch input).</span></span> <span data-ttu-id="74d2e-129">Der Cursor wird ausgeblendet, indem [CoreWindow::PointerCursor](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointercursor.aspx) auf **nullptr** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="74d2e-129">The cursor is hidden by setting the [CoreWindow::PointerCursor](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointercursor.aspx) to **nullptr**.</span></span> 

## <a name="returning-to-absolute-mouse-movement"></a><span data-ttu-id="74d2e-130">Zurückkehren zur absoluten Mausbewegung</span><span class="sxs-lookup"><span data-stu-id="74d2e-130">Returning to absolute mouse movement</span></span>

<span data-ttu-id="74d2e-131">Wenn die App den Bearbeitungsmodus für 3D-Objekte/-Szenen verlässt und die relative Mausbewegung nicht mehr verwendet (wenn sie z.B. einen Menübildschirm anzeigt), sollte die App zur normalen Verarbeitung der absoluten Mausbewegung zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="74d2e-131">When the app exits the 3-D object or scene manipulation mode and no longer uses relative mouse movement (such as when it returns to a menu screen), return to normal processing of absolute mouse movement.</span></span> <span data-ttu-id="74d2e-132">Beenden Sie zu diesem Zeitpunkt das Lesen der relativen Mausdaten, starten Sie die Verarbeitung der standardmäßigen Maus- und Zeigerereignisse neu, und setzen Sie [CoreWindow::PointerCursor](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointercursor.aspx) auf einen Wert ungleich NULL.</span><span class="sxs-lookup"><span data-stu-id="74d2e-132">At this time, stop reading relative mouse data, restart the processing of standard mouse (and pointer) events, and set [CoreWindow::PointerCursor](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.core.corewindow.pointercursor.aspx) to non-null value.</span></span> 

> **<span data-ttu-id="74d2e-133">Hinweis</span><span class="sxs-lookup"><span data-stu-id="74d2e-133">Note</span></span>**  
<span data-ttu-id="74d2e-134">Wenn sich Ihre App im Bearbeitungsmodus für 3D-Objekte/-Szenen befindet, in dem relative Mausbewegungen bei deaktiviertem Cursor verarbeitet werden, kann die Maus keine UI am Bildschirmrand aufrufen, z.B. Charms, Stapel für die Rückwärtsnavigation oder App-Leiste.</span><span class="sxs-lookup"><span data-stu-id="74d2e-134">When your app is in the 3-D object/scene manipulation mode (processing relative mouse movements with the cursor off), the mouse cannot invoke edge UI such as the charms, back stack, or app bar.</span></span> <span data-ttu-id="74d2e-135">Daher ist es wichtig, einen Mechanismus bereitzustellen, um diesen besonderen Modus zu beenden, z.B. die allgemein verwendete **Esc**-Taste.</span><span class="sxs-lookup"><span data-stu-id="74d2e-135">Therefore, it is important to provide a mechanism to exit this particular mode, such as the commonly used **Esc** key.</span></span>

## <a name="related-topics"></a><span data-ttu-id="74d2e-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="74d2e-136">Related topics</span></span>

* [<span data-ttu-id="74d2e-137">Bewegungs-/Blicksteuerungen für Spiele</span><span class="sxs-lookup"><span data-stu-id="74d2e-137">Move-look controls for games</span></span>](tutorial--adding-move-look-controls-to-your-directx-game.md) 
* [<span data-ttu-id="74d2e-138">Toucheingabesteuerelemente für Spiele</span><span class="sxs-lookup"><span data-stu-id="74d2e-138">Touch controls for games</span></span>](tutorial--adding-touch-controls-to-your-directx-game.md)