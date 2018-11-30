---
title: Texturadressierungsmodi
description: Die Direct3D-Anwendung kann jedem Scheitelpunkt jedes Grundtyps Texturkoordinaten zuweisen.
ms.assetid: 925E8F2E-43EC-404E-8870-03E39155F697
keywords:
- Texturadressierungsmodi
- Umbruch-Texturadressierungsmodus
- Spiegel-Texturadressiermodus
- Anklemmen-Texturadressierungsmodus
- Rand-Texturadressierungsmodus
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 5e263876f414e5683ffc8a5645a12e5031b3d6fb
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8325437"
---
# <a name="texture-addressing-modes"></a><span data-ttu-id="2649b-108">Texturadressierungsmodi</span><span class="sxs-lookup"><span data-stu-id="2649b-108">Texture addressing modes</span></span>


<span data-ttu-id="2649b-109">Die Direct3D-Anwendung kann jedem Scheitelpunkt jedes Grundtyps Texturkoordinaten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="2649b-109">Your Direct3D application can assign texture coordinates to any vertex of any primitive.</span></span> <span data-ttu-id="2649b-110">In der Regel liegen die u- und v-Texturkoordinaten, die Sie einem Scheitelpunkt zuweisen, im Bereich zwischen einschließlich 0,0 und 1,0.</span><span class="sxs-lookup"><span data-stu-id="2649b-110">Typically, the u- and v-texture coordinates that you assign to a vertex are in the range of 0.0 to 1.0 inclusive.</span></span> <span data-ttu-id="2649b-111">Durch die Zuweisung von Texturkoordinaten außerhalb dieses Bereichs können Sie jedoch bestimmte Textur-Spezialeffekte erzielen.</span><span class="sxs-lookup"><span data-stu-id="2649b-111">However, by assigning texture coordinates outside that range, you can create certain special texturing effects.</span></span> <span data-ttu-id="2649b-112">.</span><span class="sxs-lookup"><span data-stu-id="2649b-112">.</span></span>

<span data-ttu-id="2649b-113">Sie steuern, was Direct3D mit Texturkoordinaten außerhalb des Bereichs \[0,0, 1,0\] tut, indem Sie den Texturadressierungsmodus einstellen.</span><span class="sxs-lookup"><span data-stu-id="2649b-113">You control what Direct3D does with texture coordinates that are outside the \[0.0, 1.0\] range by setting the texture addressing mode.</span></span> <span data-ttu-id="2649b-114">So können Sie etwa dafür sorgen, dass Ihre Anwendung den Texturadressierungsmodus so einstellt, dass eine Textur als Kachel über einen Grundtyp gelegt wird.</span><span class="sxs-lookup"><span data-stu-id="2649b-114">For instance, you can have your application set the texture addressing mode so that a texture is tiled across a primitive.</span></span>

<span data-ttu-id="2649b-115">Direct3D ermöglicht Anwendungen die Durchführung eines Texturumbruchs.</span><span class="sxs-lookup"><span data-stu-id="2649b-115">Direct3D enables applications to perform texture wrapping.</span></span> <span data-ttu-id="2649b-116">Vgl. [Texturumbruch](texture-wrapping.md).</span><span class="sxs-lookup"><span data-stu-id="2649b-116">See [Texture wrapping](texture-wrapping.md).</span></span>

<span data-ttu-id="2649b-117">Die Aktivierung des Texturumbruchs macht Texturkoordinaten außerhalb des Bereichs \[0,0, 1,0\] ungültig, und das Verhalten für das Rastern solcher ungültiger Texturkoordinaten ist in diesem Fall nicht definiert.</span><span class="sxs-lookup"><span data-stu-id="2649b-117">Enabling texture wrapping effectively makes texture coordinates outside the \[0.0, 1.0\] range invalid, and the behavior for rasterizing such delinquent texture coordinates is undefined in this case.</span></span> <span data-ttu-id="2649b-118">Wenn der Texturumbruch aktiviert ist, werden keine Texturadressierungsmodi verwendet.</span><span class="sxs-lookup"><span data-stu-id="2649b-118">When texture wrapping is enabled, texture addressing modes are not used.</span></span> <span data-ttu-id="2649b-119">Achten Sie darauf, dass Ihre Anwendung keine Texturkoordinaten unter 0,0 oder über 1,0 angibt, wenn der Texturumbruch aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2649b-119">Take care that your application does not specify texture coordinates lower than 0.0 or higher than 1.0 when texture wrapping is enabled.</span></span>

## <a name="span-idsummaryofthetextureaddressingmodesspanspan-idsummaryofthetextureaddressingmodesspanspan-idsummaryofthetextureaddressingmodesspansummary-of-the-texture-addressing-modes"></a><span data-ttu-id="2649b-120"><span id="Summary_of_the_texture_addressing_modes"></span><span id="summary_of_the_texture_addressing_modes"></span><span id="SUMMARY_OF_THE_TEXTURE_ADDRESSING_MODES"></span>Zusammenfassung der Texturadressierungsmodi</span><span class="sxs-lookup"><span data-stu-id="2649b-120"><span id="Summary_of_the_texture_addressing_modes"></span><span id="summary_of_the_texture_addressing_modes"></span><span id="SUMMARY_OF_THE_TEXTURE_ADDRESSING_MODES"></span>Summary of the texture addressing modes</span></span>


| <span data-ttu-id="2649b-121">Texturadressierungsmodus</span><span class="sxs-lookup"><span data-stu-id="2649b-121">Texture addressing mode</span></span> | <span data-ttu-id="2649b-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2649b-122">Description</span></span>                                                                                                                           |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2649b-123">Umbruch</span><span class="sxs-lookup"><span data-stu-id="2649b-123">Wrap</span></span>                    | <span data-ttu-id="2649b-124">Wiederholt die Textur an jedem ganzzahligen Schnittpunkt</span><span class="sxs-lookup"><span data-stu-id="2649b-124">Repeats the texture on every integer junction.</span></span>                                                                                        |
| <span data-ttu-id="2649b-125">Spiegel</span><span class="sxs-lookup"><span data-stu-id="2649b-125">Mirror</span></span>                  | <span data-ttu-id="2649b-126">Spiegelt die Textur an jeder ganzzahligen Grenze</span><span class="sxs-lookup"><span data-stu-id="2649b-126">Mirrors the texture at every integer boundary.</span></span>                                                                                        |
| <span data-ttu-id="2649b-127">Anklemmen</span><span class="sxs-lookup"><span data-stu-id="2649b-127">Clamp</span></span>                   | <span data-ttu-id="2649b-128">Klemmt Ihre Texturkoordinaten an den Bereich \[0,0, 1,0\]. Dabei wird die Textur einmal angewendet, und die Farbe der Kantenpixel wird verstrichen.</span><span class="sxs-lookup"><span data-stu-id="2649b-128">Clamps your texture coordinates to the \[0.0, 1.0\] range; Clamp mode applies the texture once, then smears the color of edge pixels.</span></span> |
| <span data-ttu-id="2649b-129">Randfarbe</span><span class="sxs-lookup"><span data-stu-id="2649b-129">Border Color</span></span>            | <span data-ttu-id="2649b-130">Verwende eine beliebige *Randfarbe* für alle Texturkoordinaten außerhalb des Bereichs von 0,0 bis 1,0 (einschließlich).</span><span class="sxs-lookup"><span data-stu-id="2649b-130">Uses an arbitrary *border color* for any texture coordinates outside the range of 0.0 through 1.0, inclusive.</span></span>                         |

 

## <a name="span-idwraptextureaddressmodespanspan-idwraptextureaddressmodespanspan-idwraptextureaddressmodespanwrap-texture-address-mode"></a><span data-ttu-id="2649b-131"><span id="Wrap_texture_address_mode"></span><span id="wrap_texture_address_mode"></span><span id="WRAP_TEXTURE_ADDRESS_MODE"></span>Texturadressierungsmodus Umbruch</span><span class="sxs-lookup"><span data-stu-id="2649b-131"><span id="Wrap_texture_address_mode"></span><span id="wrap_texture_address_mode"></span><span id="WRAP_TEXTURE_ADDRESS_MODE"></span>Wrap texture address mode</span></span>


<span data-ttu-id="2649b-132">Der Umbruch-Texturadressierungsmodus sorgt dafür, dass Direct3D die Textur auf jedem ganzzahligen Schnittpunkt wiederholt.</span><span class="sxs-lookup"><span data-stu-id="2649b-132">The Wrap texture address mode makes Direct3D repeat the texture on every integer junction.</span></span>

<span data-ttu-id="2649b-133">Nehmen wir beispielsweise an, Ihre Anwendung erstellt einen quadratischen Grundtyp und gibt die Texturkoordinaten (0,0, 0,0), (0,0, 3,0), (3,0, 3,0) und (3,0, 0,0) an.</span><span class="sxs-lookup"><span data-stu-id="2649b-133">Suppose, for example, your application creates a square primitive and specifies texture coordinates of (0.0,0.0), (0.0,3.0), (3.0,3.0), and (3.0,0.0).</span></span> <span data-ttu-id="2649b-134">Das Festlegen des Texturadressiermodus auf „Umbruch“ führt dazu, dass die Textur dreimal in u- und v-Richtung angewendet wird, wie in der folgenden Abbildung illustriert.</span><span class="sxs-lookup"><span data-stu-id="2649b-134">Setting the texture addressing mode to "Wrap" results in the texture being applied three times in both the u-and v-directions, as shown in the following illustration.</span></span>

![Illustration einer Flächentextur mit Umbruch in u- und v-Richtung](images/wrap.png)

<span data-ttu-id="2649b-136">Vergleichen Sie dies mit dem folgenden **Spiegel-Texturadressiermodus**.</span><span class="sxs-lookup"><span data-stu-id="2649b-136">Contrast this with the following **Mirror texture address mode**.</span></span>

## <a name="span-idmirrortextureaddressmodespanspan-idmirrortextureaddressmodespanspan-idmirrortextureaddressmodespanmirror-texture-address-mode"></a><span data-ttu-id="2649b-137"><span id="Mirror_texture_address_mode"></span><span id="mirror_texture_address_mode"></span><span id="MIRROR_TEXTURE_ADDRESS_MODE"></span>Spiegel-Texturadressiermodus</span><span class="sxs-lookup"><span data-stu-id="2649b-137"><span id="Mirror_texture_address_mode"></span><span id="mirror_texture_address_mode"></span><span id="MIRROR_TEXTURE_ADDRESS_MODE"></span>Mirror texture address mode</span></span>


<span data-ttu-id="2649b-138">Der Spiegel-Texturadressiermodus sorgt dafür, dass Direct3D die Textur an jeder ganzzahligen Grenze spiegelt.</span><span class="sxs-lookup"><span data-stu-id="2649b-138">The Mirror texture address mode causes Direct3D to mirror the texture at every integer boundary.</span></span>

<span data-ttu-id="2649b-139">Nehmen wir beispielsweise an, Ihre Anwendung erstellt einen quadratischen Grundtyp und gibt die Texturkoordinaten (0,0, 0,0), (0,0, 3,0), (3,0, 3,0) und (3,0, 0,0) an.</span><span class="sxs-lookup"><span data-stu-id="2649b-139">Suppose, for example, your application creates a square primitive and specifies texture coordinates of (0.0,0.0), (0.0,3.0), (3.0,3.0), and (3.0,0.0).</span></span> <span data-ttu-id="2649b-140">Der Texturadressiermodus „Spiegel“ führt dazu, dass die Textur dreimal in u- und v-Richtung angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="2649b-140">Setting the texture addressing mode to "Mirror" results in the texture being applied three times in both the u- and v-directions.</span></span> <span data-ttu-id="2649b-141">Jede zweite Zeile und Spalte, auf die die Textur angewendet wird, ist ein Spiegelbild der jeweils vorhergehenden Zeile oder Spalte, wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2649b-141">Every other row and column that it is applied to is a mirror image of the preceding row or column, as shown in the following illustration.</span></span>

![Illustration von Spiegel-Images in einem 3 x 3-Raster](images/mirror.png)

<span data-ttu-id="2649b-143">Vergleichen Sie dies mit der vorherigen **Umbruch-Texturadressierungsmodus**.</span><span class="sxs-lookup"><span data-stu-id="2649b-143">Contrast this with the previous **Wrap texture address mode**.</span></span>

## <a name="span-idclamptextureaddressmodespanspan-idclamptextureaddressmodespanspan-idclamptextureaddressmodespanclamp-texture-address-mode"></a><span data-ttu-id="2649b-144"><span id="Clamp_texture_address_mode"></span><span id="clamp_texture_address_mode"></span><span id="CLAMP_TEXTURE_ADDRESS_MODE"></span>Anklemmen-Texturadressierungsmodus</span><span class="sxs-lookup"><span data-stu-id="2649b-144"><span id="Clamp_texture_address_mode"></span><span id="clamp_texture_address_mode"></span><span id="CLAMP_TEXTURE_ADDRESS_MODE"></span>Clamp texture address mode</span></span>


<span data-ttu-id="2649b-145">Der Anklemmen-Texturadressierungsmodus bewirkt, dass Direct3D Ihre Texturkoordinaten an den Bereich \[0,0, 1,0\] anklemmt. Dabei wird die Textur einmal angewendet und die Farbe der Randpixel wird verstrichen.</span><span class="sxs-lookup"><span data-stu-id="2649b-145">The Clamp texture address mode causes Direct3D to clamp your texture coordinates to the \[0.0, 1.0\] range; Clamp mode applies the texture once, then smears the color of edge pixels.</span></span>

<span data-ttu-id="2649b-146">Angenommen die Anwendung erstellt ein Grundquadrat und weist die Texturkoordinaten (0,0, 0,0), (0,0, 3,0), (3,0, 3,0) und (3,0, 0,0) den Ecken dieses Grundelements zu.</span><span class="sxs-lookup"><span data-stu-id="2649b-146">Suppose that your application creates a square primitive and assigns texture coordinates of (0.0,0.0), (0.0,3.0), (3.0,3.0), and (3.0,0.0) to the primitive's vertices.</span></span> <span data-ttu-id="2649b-147">Der Texturadressiermodus „Anklemmen“ führt dazu, dass die Textur einmal angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="2649b-147">Setting the texture addressing mode to "Clamp" results in the texture being applied once.</span></span> <span data-ttu-id="2649b-148">Die Pixelfarben am oberen Spaltenrand und am Ende der Zeilen werden nach oben und rechts von dem Grundelement ausgedehnt.</span><span class="sxs-lookup"><span data-stu-id="2649b-148">The pixel colors at the top of the columns and the end of the rows are extended to the top and right of the primitive respectively.</span></span>

<span data-ttu-id="2649b-149">Die folgende Abbildung zeigt eine angeklemmte Textur:</span><span class="sxs-lookup"><span data-stu-id="2649b-149">The following illustration shows a clamped texture.</span></span>

![Illustration einer Textur und einer angeklemmten Textur](images/clamp.png)

## <a name="span-idbordercolortextureaddressmodespanspan-idbordercolortextureaddressmodespanspan-idbordercolortextureaddressmodespanborder-color-texture-address-mode"></a><span data-ttu-id="2649b-151"><span id="Border_Color_texture_address_mode"></span><span id="border_color_texture_address_mode"></span><span id="BORDER_COLOR_TEXTURE_ADDRESS_MODE"></span>Rand-Texturadressierungsmodus</span><span class="sxs-lookup"><span data-stu-id="2649b-151"><span id="Border_Color_texture_address_mode"></span><span id="border_color_texture_address_mode"></span><span id="BORDER_COLOR_TEXTURE_ADDRESS_MODE"></span>Border Color texture address mode</span></span>


<span data-ttu-id="2649b-152">Der Rand-Texturadressiermodus verursacht, dass Direct3D eine beliebige Farbe, die *Randfarbe*, für alle Texturkoordinaten außerhalb des Bereichs von 0,0 bis 1,0 (einschließlich) verwendet.</span><span class="sxs-lookup"><span data-stu-id="2649b-152">The Border Color texture address mode causes Direct3D to use an arbitrary color, known as the *border color*, for any texture coordinates outside the range of 0.0 through 1.0, inclusive.</span></span>

<span data-ttu-id="2649b-153">In der folgenden Abbildunggibt die Anwendung an, dass die Textur für den Grundtyp mit einem roten Rahmen angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="2649b-153">In the following illustration, the application specifies that the texture be applied to the primitive using a red border.</span></span>

![Illustration einer Textur und einer Textur mit rotem Rand](images/border.png)

## <a name="span-iddevicelimitationsspanspan-iddevicelimitationsspanspan-iddevicelimitationsspandevice-limitations"></a><span data-ttu-id="2649b-155"><span id="Device_Limitations"></span><span id="device_limitations"></span><span id="DEVICE_LIMITATIONS"></span>Geräteeinschränkungen</span><span class="sxs-lookup"><span data-stu-id="2649b-155"><span id="Device_Limitations"></span><span id="device_limitations"></span><span id="DEVICE_LIMITATIONS"></span>Device limitations</span></span>


<span data-ttu-id="2649b-156">Obwohl das System in der Regel Texturkoordinaten außerhalb des Bereichs von 0,0 bis 1,0 (einschließlich) zulässt, wirken sich Hardwareeinschränkungen oft darauf aus, wie weit außerhalb dieses Bereichs Texturkoordinaten reichen können.</span><span class="sxs-lookup"><span data-stu-id="2649b-156">Although the system generally allows texture coordinates outside the range of 0.0 and 1.0, inclusive, hardware limitations often affect how far outside that range texture coordinates can be.</span></span> <span data-ttu-id="2649b-157">Ein Renderinggerät teilt den Grenzwert für den gesamten von diesem Gerät zugelassenen Texturkoordinatengerät mit, wenn Sie die Fähigkeiten des Geräts abrufen.</span><span class="sxs-lookup"><span data-stu-id="2649b-157">A rendering device communicates the limit for the full range of texture coordinates allowed by the device, when you retrieve the device's capabilities.</span></span>

<span data-ttu-id="2649b-158">Wenn beispielsweise dieser Wert 128 ist, müssen die Eingabe-Texturkoordinaten im Bereich zwischen -128,0 und +128,0 gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="2649b-158">For instance, if this value is 128, then the input texture coordinates must be kept in the range -128.0 to +128.0.</span></span> <span data-ttu-id="2649b-159">Die Übergabe von Scheitelpunkten mit Texturkoordinaten außerhalb dieses Bereichs ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="2649b-159">Passing vertices with texture coordinates outside this range is invalid.</span></span> <span data-ttu-id="2649b-160">Diese Beschränkung gilt auch für Texturkoordinaten, die automatisch erzeugt oder durch Texturkoordinatentransformationen generiert wurden.</span><span class="sxs-lookup"><span data-stu-id="2649b-160">The same restriction applies to the texture coordinates generated as a result of automatic texture coordinate generation and texture coordinate transformations.</span></span>

<span data-ttu-id="2649b-161">Die Einschränkungen für Texturwiederholungen können von der Größe der Textur wie durch die Texturkoordinaten angegeben abhängen.</span><span class="sxs-lookup"><span data-stu-id="2649b-161">Texture repeating limitations can depend on the size of the texture indexed by the texture coordinates.</span></span> <span data-ttu-id="2649b-162">In diesem Fall gilt bei einer angenommenen Texturgröße von 32 und einem vom Gerät zugelassenen Texturkoordinatenbereich von 512, dass der tatsächlich gültige Texturkoordinatenbereich 512/32 = 16 wäre. Die Texturkoordinaten für dieses Gerät müssen daher zwischen -16,0 und +16,0 liegen.</span><span class="sxs-lookup"><span data-stu-id="2649b-162">In that case, supposing the texture dimension is 32, and the range of texture coordinates allowed by the device is 512, the actual valid texture coordinate range would therefore be 512/32 = 16, so the texture coordinates for this device must be within the range of -16.0 to +16.0.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="2649b-163"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2649b-163"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="2649b-164">Texturen</span><span class="sxs-lookup"><span data-stu-id="2649b-164">Textures</span></span>](textures.md)

 

 




