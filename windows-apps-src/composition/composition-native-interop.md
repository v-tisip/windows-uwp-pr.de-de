---
author: jwmsft
ms.assetid: 16ad97eb-23f1-0264-23a9-a1791b4a5b95
title: "Systemeigene Interoperabilität"
description: "Die Windows.UI.Composition-API bietet systemeigene Interoperabilitätsschnittstellen, mit deren Hilfe Inhalte direkt in den Kompositor verschoben werden können."
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 96af2b92ec301a93cbae9eb14422af9e1ec8554c
ms.sourcegitcommit: b42d14c775efbf449a544ddb881abd1c65c1ee86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2017
---
# <a name="composition-native-interoperation-with-directx-and-direct2d"></a><span data-ttu-id="d10e0-104">Systemeigene Interoperabilität mit „DirectX“ und „Direct2D“</span><span class="sxs-lookup"><span data-stu-id="d10e0-104">Composition native interoperation with DirectX and Direct2D</span></span>

<span data-ttu-id="d10e0-105">Die Windows.UI.Composition-API bietet die systemeigenen Interoperabilitätsschnittstellen [**ICompositorInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620068), [**ICompositionDrawingSurfaceInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620058) und [**ICompositionGraphicsDeviceInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620065), mit deren Hilfe Inhalte direkt in den Kompositor verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="d10e0-105">The Windows.UI.Composition API provides the [**ICompositorInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620068), [**ICompositionDrawingSurfaceInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620058), and [**ICompositionGraphicsDeviceInterop**](https://msdn.microsoft.com/library/windows/apps/Mt620065) native interoperation interfaces allowing content to be moved directly into the compositor.</span></span>

<span data-ttu-id="d10e0-106">Systemeigene Interoperabilität ist um Oberflächenelemente herum strukturiert, die von DirectX-Texturen unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-106">Native interoperation is structured around surface objects that are backed by DirectX textures.</span></span> <span data-ttu-id="d10e0-107">Die Oberflächen werden aus einem Factoryobjekt mit der Bezeichnung [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749) erstellt.</span><span class="sxs-lookup"><span data-stu-id="d10e0-107">The surfaces are created from a factory object called [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749).</span></span> <span data-ttu-id="d10e0-108">Dieses Objekt wird durch ein zugrunde liegendes Direct2D- oder Direct3D-Geräteobjekt unterstützt, mit dem Videospeicher für Oberflächen zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d10e0-108">This object is backed by an underlying Direct2D or Direct3D device object, which it uses to allocate video memory for surfaces.</span></span> <span data-ttu-id="d10e0-109">Die Composition-API erstellt niemals das zugrunde liegende DirectX-Gerät.</span><span class="sxs-lookup"><span data-stu-id="d10e0-109">The composition API never creates the underlying DirectX device.</span></span> <span data-ttu-id="d10e0-110">Es wird von der Anwendung erstellt und an das **CompositionGraphicsDevice**-Objekt übergeben.</span><span class="sxs-lookup"><span data-stu-id="d10e0-110">It is the responsibility of the application to create one and pass it to the **CompositionGraphicsDevice** object.</span></span> <span data-ttu-id="d10e0-111">Eine Anwendung kann gleichzeitig mehrere **CompositionGraphicsDevice**-Objekte erstellen und das gleiche DirectX-Gerät als Renderinggerät für mehrere **CompositionGraphicsDevice**-Objekte verwenden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-111">An application may create more than one **CompositionGraphicsDevice** object at a time, and it may use the same DirectX device as the rendering device for multiple **CompositionGraphicsDevice** objects.</span></span>

## <a name="creating-a-surface"></a><span data-ttu-id="d10e0-112">Erstellen einer Oberfläche</span><span class="sxs-lookup"><span data-stu-id="d10e0-112">Creating a surface</span></span>

<span data-ttu-id="d10e0-113">Jedes [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749)-Objekt dient als Oberflächen-Factory.</span><span class="sxs-lookup"><span data-stu-id="d10e0-113">Each [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749) serves as a surface factory.</span></span> <span data-ttu-id="d10e0-114">Jede Oberfläche wird mit einer vorgegebenen Größe (z.B. 0,0), aber ohne gültige Pixel erstellt.</span><span class="sxs-lookup"><span data-stu-id="d10e0-114">Each surface is created with an initial size (which may be 0,0), but no valid pixels.</span></span> <span data-ttu-id="d10e0-115">Eine Oberfläche kann in ihrem ursprünglichen Zustand sofort in einer visuellen Struktur verwendet werden, z. B. über ein [**CompositionSurfaceBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589415)- und ein [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433)-Element. Sie hat jedoch in ihrem ursprünglichen Zustand keine Auswirkung auf die Bildschirmausgabe.</span><span class="sxs-lookup"><span data-stu-id="d10e0-115">A surface in its initial state may be immediately consumed in a visual tree, for example, via a [**CompositionSurfaceBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589415) and a [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433), but in its initial state the surface has no effect on screen output.</span></span> <span data-ttu-id="d10e0-116">Sie wird immer vollständig transparent angezeigt, auch wenn der Alphamodus als „undurchsichtig“ angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="d10e0-116">It is, for all purposes, entirely transparent, even if the specified alpha mode is “opaque”.</span></span>

<span data-ttu-id="d10e0-117">Gelegentlich können DirectX-Geräte unbrauchbar werden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-117">Occasionally, DirectX devices may be rendered unusable.</span></span> <span data-ttu-id="d10e0-118">Dies geschieht beispielsweise, wenn die Anwendung bestimmten DirectX-APIs ungültige Argumente übergibt, der Grafikadapter vom System zurückgesetzt wird oder der Treiber aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="d10e0-118">This may happen, amongst other reasons, if the application passes invalid arguments to certain DirectX APIs, or if the graphics adapter is reset by the system, or if the driver is updated.</span></span> <span data-ttu-id="d10e0-119">Direct3D verfügt über eine API, die von einer Anwendung asynchron zur Erkennung verwendet werden kann, wenn das Gerät aus irgendeinem Grund verloren geht.</span><span class="sxs-lookup"><span data-stu-id="d10e0-119">Direct3D has an API that an application may use to discover, asynchronously, if the device is lost for any reason.</span></span> <span data-ttu-id="d10e0-120">Wenn ein DirectX-Gerät verloren gegangen ist, muss die Anwendung es verwerfen, ein neues erstellen und es an ein beliebiges [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749)-Objekt übergeben, das zuvor dem unbrauchbaren DirectX-Gerät zugeordnet war.</span><span class="sxs-lookup"><span data-stu-id="d10e0-120">When a DirectX device is lost, the application must discard it, create a new one, and pass it to any [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749) objects previously associated with the bad DirectX device.</span></span>

## <a name="loading-pixels-into-a-surface"></a><span data-ttu-id="d10e0-121">Laden von Pixeln in eine Oberfläche</span><span class="sxs-lookup"><span data-stu-id="d10e0-121">Loading pixels into a surface</span></span>

<span data-ttu-id="d10e0-122">Um Pixel in eine Oberfläche zu laden, muss die Anwendung die [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx)-Methode aufrufen, die eine DirectX-Oberfläche zurückgibt. Abhängig von der Anforderung der Anwendung handelt es sich hierbei um eine Textur oder einen Direct2D-Kontext.</span><span class="sxs-lookup"><span data-stu-id="d10e0-122">To load pixels into the surface, the application must call the [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) method, which returns a DirectX interface representing a texture or Direct2D context, depending on what the application requests.</span></span> <span data-ttu-id="d10e0-123">Die Anwendung muss dann Pixel in die Textur rendern oder laden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-123">The application must then render or upload pixels into that texture.</span></span> <span data-ttu-id="d10e0-124">Anschließend ruft sie die [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="d10e0-124">When the application is done, it must call the [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) method.</span></span> <span data-ttu-id="d10e0-125">Erst dann stehen die neuen Pixel für die Komposition zur Verfügung. Sie werden allerdings erst auf dem Bildschirm angezeigt, wenn alle Änderungen an der visuellen Struktur gespeichert wurden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-125">Only at that point are the new pixels available for composition, but they still don't show up on screen until the next time all changes to the visual tree are committed.</span></span> <span data-ttu-id="d10e0-126">Falls die visuelle Struktur vor dem Aufrufen von **EndDraw** gespeichert wird, ist das gerade ausgeführte Update nicht auf dem Bildschirm sichtbar. Auf der Benutzeroberfläche werden stattdessen die Inhalte angezeigt, die vor dem Aufruf von **BeginDraw** vorhanden waren.</span><span class="sxs-lookup"><span data-stu-id="d10e0-126">If the visual tree is committed before **EndDraw** is called, then the update that is in progress is not visible on screen and the surface continues to display the contents it had prior to **BeginDraw**.</span></span> <span data-ttu-id="d10e0-127">Wenn **EndDraw** aufgerufen wird, wird die von „BeginDraw“ zurückgegebene Textur oder der Direct2D-Kontextzeiger ungültig.</span><span class="sxs-lookup"><span data-stu-id="d10e0-127">When **EndDraw** is called, the texture or Direct2D context pointer returned by BeginDraw is invalidated.</span></span> <span data-ttu-id="d10e0-128">Eine Anwendung sollte diesen Zeiger niemals über den Aufruf von **EndDraw** hinaus zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="d10e0-128">An application should never cache that pointer beyond the **EndDraw** call.</span></span>

<span data-ttu-id="d10e0-129">Die Anwendung kann „BeginDraw“ nur jeweils auf einer Oberfläche für ein bestimmtes [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749)-Element aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d10e0-129">The application may only call BeginDraw on one surface at a time, for any given [**CompositionGraphicsDevice**](https://msdn.microsoft.com/library/windows/apps/Dn706749).</span></span> <span data-ttu-id="d10e0-130">Nach dem Aufruf von [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) muss die Anwendung [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) auf dieser Oberfläche aufrufen, bevor sie auf einer anderen **BeginDraw** aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="d10e0-130">After calling [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx), the application must call [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) on that surface before calling **BeginDraw** on another.</span></span> <span data-ttu-id="d10e0-131">Da die API agil ist, muss die Anwendung diese Aufrufe synchronisiert durchführen, wenn das Rendering aus mehreren Workerthreads ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d10e0-131">As the API is agile, the application is responsible for synchronizing these calls if it wishes to perform rendering from multiple worker threads.</span></span> <span data-ttu-id="d10e0-132">Mit der [**SuspendDraw**](https://msdn.microsoft.com/library/windows/apps/mt620064.aspx) kann die Anwendung das Rendern einer Oberfläche unterbrechen und vorübergehend zu einer anderen wechseln.</span><span class="sxs-lookup"><span data-stu-id="d10e0-132">If an application wants to interrupt rendering one surface and switch to another temporarily, the application may use the [**SuspendDraw**](https://msdn.microsoft.com/library/windows/apps/mt620064.aspx) method.</span></span> <span data-ttu-id="d10e0-133">Dadurch kann eine weitere **BeginDraw**-Methode erfolgreich ausgeführt werden, während das erste Update der Oberfläche nicht für die Komposition auf dem Bildschirm bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d10e0-133">This allows another **BeginDraw** to succeed, but does not make the first surface update available for on-screen composition.</span></span> <span data-ttu-id="d10e0-134">So kann die Anwendung mehrere Transaktionsupdates ausführen.</span><span class="sxs-lookup"><span data-stu-id="d10e0-134">This allows the application to perform multiple updates in a transactional manner.</span></span> <span data-ttu-id="d10e0-135">Sobald eine Oberfläche angehalten wird, kann die Anwendung das Update fortführen, indem sie die [**ResumeDraw**](https://msdn.microsoft.com/library/windows/apps/mt620062)-Methode aufruft. Alternativ kann das Update durch Aufrufen von **EndDraw** als beendet erklärt werden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-135">Once a surface is suspended, the application may continue the update by calling the [**ResumeDraw**](https://msdn.microsoft.com/library/windows/apps/mt620062) method, or it may declare that the update is done by calling **EndDraw**.</span></span> <span data-ttu-id="d10e0-136">Dies bedeutet, dass für ein bestimmtes **CompositionGraphicsDevice**-Element jeweils nur eine Oberfläche gleichzeitig aktiv aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="d10e0-136">This means only one surface can be actively updated at a time for any given **CompositionGraphicsDevice**.</span></span> <span data-ttu-id="d10e0-137">Jedes Grafikgerät behält diesen Zustand unabhängig von den anderen bei, damit eine Anwendung zwei Oberflächen gleichzeitig rendern kann, wenn sie zu unterschiedlichen Grafikgeräten gehören.</span><span class="sxs-lookup"><span data-stu-id="d10e0-137">Each graphics device keeps this state independently of the others, so an application may render to two surfaces simultaneously if they belong to different graphics devices.</span></span> <span data-ttu-id="d10e0-138">Allerdings kann der Videospeicher für diese beiden Oberflächen unter diesen Umständen nicht zusammengelegt werden, was eine weniger effiziente Speichernutzung zur Folge hat.</span><span class="sxs-lookup"><span data-stu-id="d10e0-138">However, this precludes the video memory for those two surfaces from being pooled together and, as such, is less memory efficient.</span></span>

<span data-ttu-id="d10e0-139">Die Methoden [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx), [**SuspendDraw**](https://msdn.microsoft.com/library/windows/apps/mt620064.aspx), [**ResumeDraw**](https://msdn.microsoft.com/library/windows/apps/mt620062) und [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) geben Fehler zurück, wenn die Anwendung einen falschen Vorgang ausführt (z.B. das Übergeben ungültiger Argumente oder das Aufrufen von **BeginDraw** auf einer Oberfläche, bevor auf einer anderen **EndDraw** aufgerufen wurde).</span><span class="sxs-lookup"><span data-stu-id="d10e0-139">The [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx), [**SuspendDraw**](https://msdn.microsoft.com/library/windows/apps/mt620064.aspx), [**ResumeDraw**](https://msdn.microsoft.com/library/windows/apps/mt620062) and [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) methods return failures if the application performs an incorrect operation (such as passing invalid arguments, or calling **BeginDraw** on a surface before calling **EndDraw** on another).</span></span> <span data-ttu-id="d10e0-140">Bei diesen Arten von Fehlern handelt es sich um Anwendungsfehler. Daher wird erwartet, dass sie mit der Fail-Fast-Funktion verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="d10e0-140">These types of failures represent application bugs and, as such, the expectation is that they are handled with a fail fast.</span></span> <span data-ttu-id="d10e0-141">**BeginDraw** gibt möglicherweise auch einen Fehler zurück, wenn das zugrunde liegende DirectX-Gerät verloren geht.</span><span class="sxs-lookup"><span data-stu-id="d10e0-141">**BeginDraw** may also return a failure if the underlying DirectX device is lost.</span></span> <span data-ttu-id="d10e0-142">Dieser Fehler ist nicht schwerwiegend, da die Anwendung das DirectX-Gerät neu erstellen und den Vorgang wiederholen kann.</span><span class="sxs-lookup"><span data-stu-id="d10e0-142">This failure is not fatal as the application can recreate its DirectX device and try again.</span></span> <span data-ttu-id="d10e0-143">Es wird also erwartet, dass die Anwendung verloren gegangene Geräte behandelt, indem Sie das Rendering einfach überspringt.</span><span class="sxs-lookup"><span data-stu-id="d10e0-143">As such, the application is expected to handle device loss by simply skipping rendering.</span></span> <span data-ttu-id="d10e0-144">Falls **BeginDraw** aus irgendeinem Grund fehlschlägt, sollte die Anwendung nicht **EndDraw** aufrufen, da „BeginDraw“ gar nicht erst erfolgreich ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="d10e0-144">If **BeginDraw** fails for any reason, the application should also not call **EndDraw**, as the begin never succeeded in the first place.</span></span>

## <a name="scrolling"></a><span data-ttu-id="d10e0-145">Bildlauf</span><span class="sxs-lookup"><span data-stu-id="d10e0-145">Scrolling</span></span>

<span data-ttu-id="d10e0-146">Wenn eine Anwendung [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) aufruft, entsprechen die Inhalte der zurückgegebenen Textur infolge der Leistungsoptimierung nicht zwangsläufig den vorherigen Inhalten der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="d10e0-146">For performance reasons, when an application calls [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) the contents of the returned texture are not guaranteed to be the previous contents of the surface.</span></span> <span data-ttu-id="d10e0-147">Die Anwendung muss davon ausgehen, dass die Inhalte zufällig sind, und daher sicherstellen, dass alle Pixel berührt wurden. Löschen Sie zu diesem Zweck die Oberfläche vor dem Rendern, oder zeichnen Sie genügend undurchsichtigen Inhalt, um das gesamte aktualisierte Rechteck abzudecken.</span><span class="sxs-lookup"><span data-stu-id="d10e0-147">The application must assume that the contents are random and, as such, the application must ensure that all pixels are touched, either by clearing the surface before rendering or by drawing enough opaque contents to cover the entire updated rectangle.</span></span> <span data-ttu-id="d10e0-148">Aufgrund dessen und der Tatsache, dass der Texturzeiger nur zwischen **BeginDraw**- and [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060)-Aufrufen gültig ist, kann die Anwendung bereits vorhandenen Inhalt nicht aus der Oberfläche kopieren.</span><span class="sxs-lookup"><span data-stu-id="d10e0-148">This, combined with the fact that the texture pointer is only valid between **BeginDraw** and [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) calls, makes it impossible for the application to copy previous contents out of the surface.</span></span> <span data-ttu-id="d10e0-149">Aus diesem steht eine [**Scroll**](https://msdn.microsoft.com/library/windows/apps/mt620063)-Methode zur Verfügung, mit der die Anwendung eine Kopie der Pixel der gleichen Oberfläche erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="d10e0-149">For this reason, we offer a [**Scroll**](https://msdn.microsoft.com/library/windows/apps/mt620063) method, which allows the application to perform a same-surface pixel copy.</span></span>

## <a name="usage-example"></a><span data-ttu-id="d10e0-150">Anwendungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="d10e0-150">Usage Example</span></span>

<span data-ttu-id="d10e0-151">Das folgende Beispiel zeigt ein sehr einfaches Szenario, in dem eine Anwendung Zeichenoberflächen erstellt und [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) sowie [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) verwendet, um die Oberflächen mit Text zu füllen.</span><span class="sxs-lookup"><span data-stu-id="d10e0-151">The following sample illustrates a very simple scenario where an application creates drawing surfaces, and uses [**BeginDraw**](https://msdn.microsoft.com/library/windows/apps/mt620059.aspx) and [**EndDraw**](https://msdn.microsoft.com/library/windows/apps/mt620060) to populate the surfaces with text.</span></span> <span data-ttu-id="d10e0-152">Die Anwendung verwendet DirectWrite für das Layout des Texts (Details nicht dargestellt) und dann Direct2D zum Rendern.</span><span class="sxs-lookup"><span data-stu-id="d10e0-152">The application uses DirectWrite to layout the text (details not shown) and then uses Direct2D to render it.</span></span> <span data-ttu-id="d10e0-153">Das Grafikgerät für die Komposition akzeptiert das Direct2D-Gerät direkt zum Zeitpunkt der Initialisierung.</span><span class="sxs-lookup"><span data-stu-id="d10e0-153">The composition graphics device accepts the Direct2D device directly at initialization time.</span></span> <span data-ttu-id="d10e0-154">Dadurch kann **BeginDraw** einen ID2D1DeviceContext-Schnittstellenzeiger zurückzugeben. Dies ist wesentlich effizienter, als die Anwendung bei jedem Zeichenvorgang einen Direct2D-Kontext erstellen zu lassen, um eine zurückgegebene ID3D11Texture2D-Schnittstelle zu umschließen.</span><span class="sxs-lookup"><span data-stu-id="d10e0-154">This allows **BeginDraw** to return an ID2D1DeviceContext interface pointer, which is considerably more efficient than having the application create a Direct2D context to wrap a returned ID3D11Texture2D interface at each drawing operation.</span></span>

```cpp
//------------------------------------------------------------------------------
//
// Copyright (C) Microsoft. All rights reserved.
//
//------------------------------------------------------------------------------

#include "stdafx.h"

using namespace Microsoft::WRL;
using namespace Windows::Foundation;
using namespace Windows::Graphics::DirectX;
using namespace Windows::UI::Composition;

// This is an app-provided helper to render lines of text
class SampleText
{
private:
    // The text to draw
    ComPtr<IDWriteTextLayout> _text;

    // The composition surface that we use in the visual tree
    ComPtr<ICompositionDrawingSurfaceInterop> _drawingSurfaceInterop;

    // The device that owns the surface
    ComPtr<ICompositionGraphicsDevice> _compositionGraphicsDevice;

    // For managing our event notifier
    EventRegistrationToken _deviceReplacedEventToken;

public:
    SampleText(IDWriteTextLayout* text, ICompositionGraphicsDevice* compositionGraphicsDevice) :
        _text(text),
        _compositionGraphicsDevice(compositionGraphicsDevice)
    {
        // Create the surface just big enough to hold the formatted text block.
        DWRITE_TEXT_METRICS metrics;
        FailFastOnFailure(text->GetMetrics(&metrics));
        Windows::Foundation::Size surfaceSize = { metrics.width, metrics.height };
        ComPtr<ICompositionDrawingSurface> drawingSurface;
        FailFastOnFailure(_compositionGraphicsDevice->CreateDrawingSurface(
            surfaceSize,
            DirectXPixelFormat::DirectXPixelFormat_B8G8R8A8UIntNormalized,
            DirectXAlphaMode::DirectXAlphaMode_Ignore,
            &drawingSurface));

        // Cache the interop pointer, since that's what we always use.
        FailFastOnFailure(drawingSurface.As(&_drawingSurfaceInterop));

        // Draw the text
        DrawText();

        // If the rendering device is lost, the application will recreate and replace it. We then
        // own redrawing our pixels.
        FailFastOnFailure(_compositionGraphicsDevice->add_RenderingDeviceReplaced(
            Callback<RenderingDeviceReplacedEventHandler>([this](
                ICompositionGraphicsDevice* source, IRenderingDeviceReplacedEventArgs* args)
                -> HRESULT
            {
                // Draw the text again
                DrawText();
                return S_OK;
            }).Get(),
            &_deviceReplacedEventToken));
    }

    ~SampleText()
    {
        FailFastOnFailure(_compositionGraphicsDevice->remove_RenderingDeviceReplaced(
            _deviceReplacedEventToken));
    }

    // Return the underlying surface to the caller
    ComPtr<ICompositionSurface> get_Surface()
    {
        // To the caller, the fact that we have a drawing surface is an implementation detail.
        // Return the base interface instead
        ComPtr<ICompositionSurface> surface;
        FailFastOnFailure(_drawingSurfaceInterop.As(&surface));
        return surface;
    }

private:
    // We may detect device loss on BeginDraw calls. This helper handles this condition or other
    // errors.
    bool CheckForDeviceRemoved(HRESULT hr)
    {
        if (SUCCEEDED(hr))
        {
            // Everything is fine -- go ahead and draw
            return true;
        }
        else if (hr == DXGI_ERROR_DEVICE_REMOVED)
        {
            // We can't draw at this time, but this failure is recoverable. Just skip drawing for
            // now. We will be asked to draw again once the Direct3D device is recreated
            return false;
        }
        else
        {
            // Any other error is unexpected and, therefore, fatal
            FailFast();
        }
    }

    // Renders the text into our composition surface
    void DrawText()
    {
        // Begin our update of the surface pixels. If this is our first update, we are required
        // to specify the entire surface, which nullptr is shorthand for (but, as it works out,
        // any time we make an update we touch the entire surface, so we always pass nullptr).
        ComPtr<ID2D1DeviceContext> d2dDeviceContext;
        POINT offset;
        if (CheckForDeviceRemoved(_drawingSurfaceInterop->BeginDraw(nullptr,
            __uuidof(ID2D1DeviceContext), &d2dDeviceContext, &offset)))
        {
            // Create a solid color brush for the text. A more sophisticated application might want
            // to cache and reuse a brush across all text elements instead, taking care to recreate
            // it in the event of device removed.
            ComPtr<ID2D1SolidColorBrush> brush;
            FailFastOnFailure(d2dDeviceContext->CreateSolidColorBrush(
                D2D1::ColorF(D2D1::ColorF::Black, 1.0f), &brush));

            // Draw the line of text at the specified offset, which corresponds to the top-left
            // corner of our drawing surface. Notice we don't call BeginDraw on the D2D device
            // context; this has already been done for us by the composition API.
            d2dDeviceContext->DrawTextLayout(D2D1::Point2F(offset.x, offset.y), _text.Get(),
                brush.Get());

            // Our update is done. EndDraw never indicates rendering device removed, so any
            // failure here is unexpected and, therefore, fatal.
            FailFastOnFailure(_drawingSurfaceInterop->EndDraw());
        }
    }
};

class SampleApp
{
    ComPtr<ICompositor> _compositor;
    ComPtr<ID2D1Device> _d2dDevice;
    ComPtr<ICompositionGraphicsDevice> _compositionGraphicsDevice;
    std::vector<ComPtr<SampleText>> _textSurfaces;

public:
    // Run once when the application starts up
    void Initialize(ICompositor* compositor)
    {
        // Cache the compositor (created outside of this method)
        _compositor = compositor;

        // Create a Direct2D device (helper implementation not shown here)
        FailFastOnFailure(CreateDirect2DDevice(&_d2dDevice));

        // To create a composition graphics device, we need to QI for another interface
        ComPtr<ICompositorInterop> compositorInterop;
        FailFastOnFailure(_compositor.As(&compositorInterop));

        // Create a graphics device backed by our D3D device
        FailFastOnFailure(compositorInterop->CreateGraphicsDevice(
            _d2dDevice.Get(),
            &_compositionGraphicsDevice));
    }

    // Called when Direct3D signals the device lost event
    void OnDirect3DDeviceLost()
    {
        // Create a new device
        FailFastOnFailure(CreateDirect2DDevice(_d2dDevice.ReleaseAndGetAddressOf()));

        // Restore our composition graphics device to good health
        ComPtr<ICompositionGraphicsDeviceInterop> compositionGraphicsDeviceInterop;
        FailFastOnFailure(_compositionGraphicsDevice.As(&compositionGraphicsDeviceInterop));
        FailFastOnFailure(compositionGraphicsDeviceInterop->SetRenderingDevice(_d2dDevice.Get()));
    }

    // Create a surface that is asynchronously filled with an image
    ComPtr<ICompositionSurface> CreateSurfaceFromTextLayout(IDWriteTextLayout* text)
    {
        // Create our wrapper object that will handle downloading and decoding the image (assume
        // throwing new here)
        SampleText* textSurface = new SampleText(text, _compositionGraphicsDevice.Get());

        // Keep our image alive
        _textSurfaces.push_back(textSurface);

        // The caller is only interested in the underlying surface
        return textSurface->get_Surface();
    }

    // Create a visual that holds an image
    ComPtr<IVisual> CreateVisualFromTextLayout(IDWriteTextLayout* text)
    {
        // Create a sprite visual
        ComPtr<ISpriteVisual> spriteVisual;
        FailFastOnFailure(_compositor->CreateSpriteVisual(&spriteVisual));

        // The sprite visual needs a brush to hold the image
        ComPtr<ICompositionSurfaceBrush> surfaceBrush;
        FailFastOnFailure(_compositor->CreateSurfaceBrushWithSurface(
            CreateSurfaceFromTextLayout(text).Get(),
            &surfaceBrush));

        // Associate the brush with the visual
        ComPtr<ICompositionBrush> brush;
        FailFastOnFailure(surfaceBrush.As(&brush));
        FailFastOnFailure(spriteVisual->put_Brush(brush.Get()));

        // Return the visual to the caller as the base class
        ComPtr<IVisual> visual;
        FailFastOnFailure(spriteVisual.As(&visual));

        return visual;
    }

private:
    // This helper (implementation not shown here) creates a Direct2D device and registers
    // for a device loss notification on the underlying Direct3D device. When that notification is
    // raised, assume the OnDirect3DDeviceLost method is called.
    HRESULT CreateDirect2DDevice(ID2D1Device** ppDevice);
};
```

 

 




