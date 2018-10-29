---
author: stevewhims
description: Code, der in das Gerät selbst integriert und auf dessen Sensoren abgestimmt ist, umfasst auch Eingaben vom und Ausgaben an den Benutzer.
title: Portieren von Windows-Runtime 8.x zu UWP für E/A, Gerät und App-Modell
ms.assetid: bb13fb8f-bdec-46f5-8640-57fb0dd2d85b
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8e15014e39ed6d980cbe80daa0a129ff83a021b9
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5751782"
---
# <a name="porting-windows-runtime-8x-to-uwp-for-io-device-and-app-model"></a><span data-ttu-id="9fac7-104">Portieren von Windows-Runtime 8.x zu UWP für E/A, Gerät und App-Modell</span><span class="sxs-lookup"><span data-stu-id="9fac7-104">Porting Windows Runtime 8.x to UWP for I/O, device, and app model</span></span>




<span data-ttu-id="9fac7-105">Im vorherigen Thema ging es um das [Portieren von XAML und UI](w8x-to-uwp-porting-xaml-and-ui.md).</span><span class="sxs-lookup"><span data-stu-id="9fac7-105">The previous topic was [Porting XAML and UI](w8x-to-uwp-porting-xaml-and-ui.md).</span></span>

<span data-ttu-id="9fac7-106">Code, der in das Gerät selbst integriert und auf dessen Sensoren abgestimmt ist, umfasst auch Eingaben vom und Ausgaben an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9fac7-106">Code that integrates with the device itself and its sensors involves input from, and output to, the user.</span></span> <span data-ttu-id="9fac7-107">Auch die Datenverarbeitung kann einbezogen werden.</span><span class="sxs-lookup"><span data-stu-id="9fac7-107">It can also involve processing data.</span></span> <span data-ttu-id="9fac7-108">Aber dieser Code wird in der Regel nicht als UI-Ebene *oder* Datenebene betrachtet.</span><span class="sxs-lookup"><span data-stu-id="9fac7-108">But, this code is not generally thought of as either the UI layer *or* the data layer.</span></span> <span data-ttu-id="9fac7-109">Dieser Code enthält die Integration in Vibrationscontroller, Beschleunigungsmesser, Gyroskop, Mikrofon und Lautsprecher (Überschneidungen mit Spracherkennung und Sprachsynthese), (geografischen) Standort und Eingabemodalitäten, z.B. Toucheingabe, Maus, Tastatur und Stift.</span><span class="sxs-lookup"><span data-stu-id="9fac7-109">This code includes integration with the vibration controller, accelerometer, gyroscope, microphone and speaker (which intersect with speech recognition and synthesis), (geo)location, and input modalities such as touch, mouse, keyboard, and pen.</span></span>

## <a name="application-lifecycle-process-lifetime-management"></a><span data-ttu-id="9fac7-110">App-Lebenszyklus (Prozesslebensdauer-Verwaltung)</span><span class="sxs-lookup"><span data-stu-id="9fac7-110">Application lifecycle (process lifetime management)</span></span>


<span data-ttu-id="9fac7-111">Bei universellen8.1-Apps ist zwischen der Deaktivierung der App und dem Auslösen des Anhalteereignisses durch das System eine „Entprellfenster“-Zeit von zwei Sekunden vorhanden.</span><span class="sxs-lookup"><span data-stu-id="9fac7-111">For a Universal 8.1 app, there is a two-second "debounce window" of time between the app becoming inactive and the system raising the suspending event.</span></span> <span data-ttu-id="9fac7-112">Die Verwendung dieses Entprellfensters als zusätzliche Zeit zum Anhaltezustand ist unsicher, und für eine UWP (Universelle Windows-Plattform)-App ist überhaupt kein Entprellfenster vorhanden; das Anhalteereignis wird ausgelöst, sobald eine App inaktiv wird.</span><span class="sxs-lookup"><span data-stu-id="9fac7-112">Using this debounce window as extra time to suspend state is unsafe, and for a Universal Windows Platform (UWP) app, there is no debounce window at all; the suspension event is raised as soon as an app becomes inactive.</span></span>

<span data-ttu-id="9fac7-113">Weitere Informationen finden Sie unter [App-Lebenszyklus](https://msdn.microsoft.com/library/windows/apps/mt243287).</span><span class="sxs-lookup"><span data-stu-id="9fac7-113">For more info, see [App lifecycle](https://msdn.microsoft.com/library/windows/apps/mt243287).</span></span>

## <a name="background-audio"></a><span data-ttu-id="9fac7-114">Hintergrundaudio</span><span class="sxs-lookup"><span data-stu-id="9fac7-114">Background audio</span></span>


<span data-ttu-id="9fac7-115">Für die Eigenschaft [**MediaElement.AudioCategory**](https://msdn.microsoft.com/library/windows/apps/br227352) sind **ForegroundOnlyMedia** und **BackgroundCapableMedia** für Windows 10-apps als veraltet.</span><span class="sxs-lookup"><span data-stu-id="9fac7-115">For the [**MediaElement.AudioCategory**](https://msdn.microsoft.com/library/windows/apps/br227352) property, **ForegroundOnlyMedia** and **BackgroundCapableMedia** are deprecated for Windows10 apps.</span></span> <span data-ttu-id="9fac7-116">Verwenden Sie stattdessen das Windows Phone Store-App-Modell.</span><span class="sxs-lookup"><span data-stu-id="9fac7-116">Use the Windows Phone Store app model instead.</span></span> <span data-ttu-id="9fac7-117">Weitere Informationen finden Sie unter [Hintergrundaudio](https://msdn.microsoft.com/library/windows/apps/mt282140).</span><span class="sxs-lookup"><span data-stu-id="9fac7-117">For more information, see [Background Audio](https://msdn.microsoft.com/library/windows/apps/mt282140).</span></span>

## <a name="detecting-the-platform-your-app-is-running-on"></a><span data-ttu-id="9fac7-118">Erkennen der Plattform, auf der Ihre App ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="9fac7-118">Detecting the platform your app is running on</span></span>


<span data-ttu-id="9fac7-119">Die Möglichkeit für die Herangehensweise Änderungen mit Windows 10-ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="9fac7-119">The way of thinking about app-targeting changes with Windows10.</span></span> <span data-ttu-id="9fac7-120">Das neue konzeptionelle Modell besteht darin, dass eine App auf die Universelle Windows-Plattform (UWP) ausgerichtet ist und auf allen Windows-Geräten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9fac7-120">The new conceptual model is that an app targets the Universal Windows Platform (UWP) and runs across all Windows devices.</span></span> <span data-ttu-id="9fac7-121">Dann besteht die Möglichkeit, Funktionen hervorzuheben, die exklusiv für bestimmte Gerätefamilien angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="9fac7-121">It can then opt to light up features that are exclusive to particular device families.</span></span> <span data-ttu-id="9fac7-122">Bei Bedarf besteht auch die Möglichkeit, die App auf eine oder mehrere bestimmte Gerätefamilien zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="9fac7-122">If needed, the app also has the option to limit itself to targeting one or more device families specifically.</span></span> <span data-ttu-id="9fac7-123">Weitere Informationen zu Gerätefamilien – und wie Sie entscheiden, auf welche Sie eine App ausrichten sollten – finden Sie unter [Anleitung für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631).</span><span class="sxs-lookup"><span data-stu-id="9fac7-123">For more info on what device families are—and how to decide which device family to target—see [Guide to UWP apps](https://msdn.microsoft.com/library/windows/apps/dn894631).</span></span>

<span data-ttu-id="9fac7-124">Wenn in Ihrer universellen8.1-App Code vorhanden ist, der erkennt, unter welchem Betriebssystem sie ausgeführt wird, müssen Sie diesen je nach dem Grund für die Logik möglicherweise ändern.</span><span class="sxs-lookup"><span data-stu-id="9fac7-124">If you have code in your Universal 8.1 app that detects what operating system it is running on, then you may need to change that depending on the reason for the logic.</span></span> <span data-ttu-id="9fac7-125">Wenn die App den Wert weitergibt und nicht verwendet, sollten Sie weiterhin die Betriebssysteminformationen sammeln.</span><span class="sxs-lookup"><span data-stu-id="9fac7-125">If the app is passing the value through, and not acting on it, then you may want to continue to collect the operating system info.</span></span>

<span data-ttu-id="9fac7-126">**Hinweis:**  empfohlen, dass Sie nicht Betriebssystem oder die Gerätefamilie zum Ermitteln des Vorhandenseins von Features zu.</span><span class="sxs-lookup"><span data-stu-id="9fac7-126">**Note** We recommend that you not use operating system or device family to detect the presence of features.</span></span> <span data-ttu-id="9fac7-127">Das Identifizieren des aktuellen Betriebssystems oder der Gerätefamilie ist in der Regel nicht die beste Möglichkeit, um festzustellen, ob ein bestimmtes Feature für das Betriebssystem oder die Gerätefamilie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="9fac7-127">Identifying the current operating system or device family is usually not the best way to determine whether a particular operating system or device family feature is present.</span></span> <span data-ttu-id="9fac7-128">Anstatt das Betriebssystem oder die Gerätefamilie (und Versionsnummer) zu ermitteln, sollten Sie das Vorhandensein des Features selbst überprüfen (siehe [Bedingte Kompilierung und adaptiver Code](w8x-to-uwp-porting-to-a-uwp-project.md)).</span><span class="sxs-lookup"><span data-stu-id="9fac7-128">Rather than detecting the operating system or device family (and version number), test for the presence of the feature itself (see [Conditional compilation, and adaptive code](w8x-to-uwp-porting-to-a-uwp-project.md)).</span></span> <span data-ttu-id="9fac7-129">Wenn ein bestimmtes Betriebssystem oder eine bestimmte Gerätefamilie erforderlich ist, sollten Sie darauf achten, es bzw. sie als unterstützte Mindestversion zu verwenden, anstatt den Test nur für diese Version zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="9fac7-129">If you must require a particular operating system or device family, be sure to use it as a minimum supported version, rather than design the test for that one version.</span></span>

 

<span data-ttu-id="9fac7-130">Zum Anpassen der Benutzeroberfläche Ihrer App für verschiedene Geräte gibt es mehrere empfohlene Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="9fac7-130">To tailor your app's UI to different devices, there are several techniques that we recommend.</span></span> <span data-ttu-id="9fac7-131">Verwenden Sie weiterhin Elemente mit automatischer Größenanpassung und dynamische Layoutbereiche.</span><span class="sxs-lookup"><span data-stu-id="9fac7-131">Continue to use auto-sized elements and dynamic layout panels as you always have.</span></span> <span data-ttu-id="9fac7-132">Verwenden Sie in Ihrem XAML-Markup weiterhin Größen in effektiven Pixeln (früher „Anzeigepixel“), damit sich die Benutzeroberfläche an verschiedene Auflösungen und Skalierungsfaktoren anpasst (siehe [Effektive Pixel, Abstand zum Bildschirm und Skalierungsfaktoren](w8x-to-uwp-porting-xaml-and-ui.md)).</span><span class="sxs-lookup"><span data-stu-id="9fac7-132">In your XAML markup, continue to use sizes in effective pixels (formerly view pixels) so that your UI adapts to different resolutions and scale factors (see [Effective pixels, viewing distance, and scale factors](w8x-to-uwp-porting-xaml-and-ui.md).).</span></span> <span data-ttu-id="9fac7-133">Verwenden Sie außerdem die adaptiven Auslöser und Setter des Visual State-Managers zum Anpassen der Benutzeroberfläche an die Fenstergröße (siehe [Anleitung für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631)).</span><span class="sxs-lookup"><span data-stu-id="9fac7-133">And use Visual State Manager's adaptive triggers and setters to adapt your UI to the window size (see [Guide to UWP apps](https://msdn.microsoft.com/library/windows/apps/dn894631).).</span></span>

<span data-ttu-id="9fac7-134">Bei einem Szenario, in dem das Erkennen der Gerätefamilie unvermeidbar ist, können Sie so vorgehen.</span><span class="sxs-lookup"><span data-stu-id="9fac7-134">However, if you have a scenario where it is unavoidable to detect the device family, then you can do that.</span></span> <span data-ttu-id="9fac7-135">In diesem Beispiel verwenden wir die [**AnalyticsVersionInfo**](https://msdn.microsoft.com/library/windows/apps/dn960165)-Klasse, um zu einer für die jeweilige Mobilgerätefamilie angepassten Seite zu navigieren – falls diese vorhanden ist – und wir stellen sicher, dass andernfalls eine Umleitung auf eine Standardseite erfolgt.</span><span class="sxs-lookup"><span data-stu-id="9fac7-135">In this example, we use the [**AnalyticsVersionInfo**](https://msdn.microsoft.com/library/windows/apps/dn960165) class to navigate to a page tailored for the mobile device family where appropriate, and we make sure to fall back to a default page otherwise.</span></span>

```csharp
   if (Windows.System.Profile.AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Mobile")
        rootFrame.Navigate(typeof(MainPageMobile), e.Arguments);
    else
        rootFrame.Navigate(typeof(MainPage), e.Arguments);
```

<span data-ttu-id="9fac7-136">Ihre App kann auch anhand der aktiven Ressourcenauswahlfaktoren die Gerätefamilie ermitteln, auf der sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9fac7-136">Your app can also determine the device family that it is running on from the resource selection factors that are in effect.</span></span> <span data-ttu-id="9fac7-137">Im folgenden Beispiel wird gezeigt, wie dies imperativ durchgeführt wird, und im Thema [**ResourceContext.QualifierValues**](https://msdn.microsoft.com/library/windows/apps/br206071) wird der gängigere Anwendungsfall für die Klasse beim Laden der gerätefamilienspezifischen Ressourcen basierend auf dem Gerätefamilienfaktor beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9fac7-137">The example below shows how to do this imperatively, and the [**ResourceContext.QualifierValues**](https://msdn.microsoft.com/library/windows/apps/br206071) topic describes the more typical use case for the class in loading device family-specific resources based on the device family factor.</span></span>

```csharp
var qualifiers = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues;
string deviceFamilyName;
bool isDeviceFamilyNameKnown = qualifiers.TryGetValue("DeviceFamily", out deviceFamilyName);
```

<span data-ttu-id="9fac7-138">Siehe auch [Bedingte Kompilierung und adaptiver Code](w8x-to-uwp-porting-to-a-uwp-project.md).</span><span class="sxs-lookup"><span data-stu-id="9fac7-138">Also, see [Conditional compilation, and adaptive code](w8x-to-uwp-porting-to-a-uwp-project.md).</span></span>

## <a name="location"></a><span data-ttu-id="9fac7-139">Position</span><span class="sxs-lookup"><span data-stu-id="9fac7-139">Location</span></span>


<span data-ttu-id="9fac7-140">Wenn eine app, die die Position in der app-Paketmanifest deklariert unter Windows 10 ausgeführt wird, fordert das System die Zustimmung des Endbenutzers.</span><span class="sxs-lookup"><span data-stu-id="9fac7-140">When an app that declares the Location capability in its app package manifest runs on Windows10, the system will prompt the end-user for consent.</span></span> <span data-ttu-id="9fac7-141">Dies gilt unabhängig davon, ob die app eine Windows Phone Store-app oder eine Windows 10-app ist.</span><span class="sxs-lookup"><span data-stu-id="9fac7-141">This is true whether the app is a Windows Phone Store app or a Windows10 app.</span></span> <span data-ttu-id="9fac7-142">Falls in Ihrer App eine eigene benutzerdefinierte Aufforderung zur Zustimmung oder eine Schaltfläche zum Aktivieren/Deaktivieren angezeigt wird, sollten Sie sie entfernen, damit Endbenutzer nur eine Aufforderung erhalten.</span><span class="sxs-lookup"><span data-stu-id="9fac7-142">So, if your app displays its own custom consent prompt, or if it provides an on-off toggle, then you will want to remove that so that the end-user is only prompted once.</span></span>

 

 




