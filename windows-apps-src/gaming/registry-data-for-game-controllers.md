---
author: eliotcowley
title: Registrierungsdaten für Spielecontroller
description: Enthält Informationen zu den Daten, die Sie der Registrierung Ihres PCs hinzufügen können, damit der Controller UWP-Spielen verwenden kann.
ms.assetid: 2DD0B384-8776-4599-9E52-4FC0AA682735
ms.author: wdg-dev-content
ms.date: 06/25/2018
ms.topic: article
keywords: Windows10, UWP, Spiele, Eingabe, Registrierung, benutzerdefiniert
ms.localizationpriority: medium
ms.openlocfilehash: 4bbd4074c52514b9cb66fd6f2dd189421f61d5ee
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6032060"
---
# <a name="registry-data-for-game-controllers"></a><span data-ttu-id="ad0c3-104">Registrierungsdaten für Spielecontroller</span><span class="sxs-lookup"><span data-stu-id="ad0c3-104">Registry data for game controllers</span></span>

> [!NOTE]
> <span data-ttu-id="ad0c3-105">Dieses Thema für Hersteller von Windows10-kompatiblen Spielecontroller vorgesehen und gilt nicht für die meisten Entwickler.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-105">This topic is meant for manufacturers of Windows 10-compatible game controllers, and doesn't apply to the majority of developers.</span></span>

<span data-ttu-id="ad0c3-106">Der [Windows.Gaming.Input-Namespace](https://docs.microsoft.com/uwp/api/windows.gaming.input) ermöglicht unabhängigen Hardwareanbietern (IHVs) das Hinzufügen von Daten an die PC-Registrierung, damit ihre Geräte als [Gamepads](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad), [RacingWheels](https://docs.microsoft.com/uwp/api/windows.gaming.input.racingwheel), [ArcadeSticks](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightSticks](https://docs.microsoft.com/en-us/uwp/api/windows.gaming.input.flightstick) und [UINavigationControllers](https://docs.microsoft.com/uwp/api/windows.gaming.input.uinavigationcontroller) entsprechend angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-106">The [Windows.Gaming.Input namespace](https://docs.microsoft.com/uwp/api/windows.gaming.input) allows independent hardware vendors (IHVs) to add data to the PC's registry, enabling their devices to appear as [Gamepads](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad), [RacingWheels](https://docs.microsoft.com/uwp/api/windows.gaming.input.racingwheel), [ArcadeSticks](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightSticks](https://docs.microsoft.com/en-us/uwp/api/windows.gaming.input.flightstick), and [UINavigationControllers](https://docs.microsoft.com/uwp/api/windows.gaming.input.uinavigationcontroller) as appropriate.</span></span> <span data-ttu-id="ad0c3-107">Alle IHVs sollten diese Daten für ihre kompatiblen Controller hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-107">All IHVs should add this data for their compatible controllers.</span></span> <span data-ttu-id="ad0c3-108">Auf diese Weise können alle UWP-Spiele (und alle Desktop-Spiele, die WinRT-API verwenden) Ihren Spielecontroller unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-108">By doing this, all UWP games (and any desktop games that use the WinRT API) will be able to support your game controller.</span></span>

## <a name="mapping-scheme"></a><span data-ttu-id="ad0c3-109">Zuordnungsschema</span><span class="sxs-lookup"><span data-stu-id="ad0c3-109">Mapping scheme</span></span>

<span data-ttu-id="ad0c3-110">Zuordnungen für ein Gerät mit Hersteller-ID (VID) **VVVV**, Produkt-ID (PID) **PPPP**, Verwendungsseite **UUUU** und Nutzungs-ID **XXXX** werden von diesem Speicherort in der Registrierung gelesen:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-110">Mappings for a device with Vendor ID (VID) **VVVV**, Product ID (PID) **PPPP**, Usage Page **UUUU**, and Usage ID **XXXX**, will be read out from this location in the registry:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\VVVVPPPPUUUUXXXX`

<span data-ttu-id="ad0c3-111">In der folgenden Tabelle wird der erwartete Werte im Stammverzeichnis des Geräts erläutert:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-111">The table below explains the expected values under the device root location:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-112">Name</span><span class="sxs-lookup"><span data-stu-id="ad0c3-112">Name</span></span></th>
        <th><span data-ttu-id="ad0c3-113">Typ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-113">Type</span></span></th>
        <th><span data-ttu-id="ad0c3-114">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-114">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-115">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-115">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-116">Deaktiviert</span><span class="sxs-lookup"><span data-stu-id="ad0c3-116">Disabled</span></span></td>
        <td><span data-ttu-id="ad0c3-117">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-117">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-118">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-118">No</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-119">Gibt an, dass dieses Gerät deaktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-119">Indicates that this particular device should be disabled.</span></span></p>
            <ul>
                <li><span data-ttu-id="ad0c3-120"><b>0</b>: Das Gerät ist nicht deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-120"><b>0</b>: Device is not disabled.</span></span></li>
                <li><span data-ttu-id="ad0c3-121"><b>1</b>: Das Gerät ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-121"><b>1</b>: Device is disabled.</span></span></li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-122">Description</span></span></td>
        <td><span data-ttu-id="ad0c3-123">REG_SZ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-123">REG_SZ</span></span> <td><span data-ttu-id="ad0c3-124">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-124">No</span></span></td>
        <td><span data-ttu-id="ad0c3-125">Eine kurze Beschreibung des Geräts</span><span class="sxs-lookup"><span data-stu-id="ad0c3-125">A short description of the device.</span></span></td>
    </tr>
</table>

<span data-ttu-id="ad0c3-126">Das Geräteinstallationsprogramm sollte diese Daten der Registrierung hinzufügen (entweder über das Setup oder eine [INF-Datei](https://docs.microsoft.com/windows-hardware/drivers/install/inf-files)).</span><span class="sxs-lookup"><span data-stu-id="ad0c3-126">Your device installer should add this data to the registry (either via setup or an [INF file](https://docs.microsoft.com/windows-hardware/drivers/install/inf-files)).</span></span>

<span data-ttu-id="ad0c3-127">Unterschlüssel im Stammverzeichnis des Geräts werden in den folgenden Abschnitten detailliert beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-127">Subkeys under the device root location are detailed in the following sections.</span></span>

### <a name="gamepad"></a><span data-ttu-id="ad0c3-128">Gamepad</span><span class="sxs-lookup"><span data-stu-id="ad0c3-128">Gamepad</span></span>

<span data-ttu-id="ad0c3-129">Die folgende Tabelle enthält die erforderlichen und optionalen Unterschlüssel unter dem **Gamepad**-Unterschlüssel:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-129">The table below lists the required and optional subkeys under the **Gamepad** subkey:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-130">Unterschlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-130">Subkey</span></span></th>
        <th><span data-ttu-id="ad0c3-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-131">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-132">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-132">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-133">Menü</span><span class="sxs-lookup"><span data-stu-id="ad0c3-133">Menu</span></span></td>
        <td><span data-ttu-id="ad0c3-134">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-134">Yes</span></span></td>
        <td rowspan="18" style="vertical-align: middle;"><span data-ttu-id="ad0c3-135">Siehe <a href="#button-mapping">Tastenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-135">See <a href="#button-mapping">Button mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-136">Ansicht</span><span class="sxs-lookup"><span data-stu-id="ad0c3-136">View</span></span></td>
        <td><span data-ttu-id="ad0c3-137">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-137">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-138">A</span><span class="sxs-lookup"><span data-stu-id="ad0c3-138">A</span></span></td>
        <td><span data-ttu-id="ad0c3-139">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-139">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-140">B</span><span class="sxs-lookup"><span data-stu-id="ad0c3-140">B</span></span></td>
        <td><span data-ttu-id="ad0c3-141">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-141">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-142">X</span><span class="sxs-lookup"><span data-stu-id="ad0c3-142">X</span></span></td>
        <td><span data-ttu-id="ad0c3-143">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-143">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-144">Y</span><span class="sxs-lookup"><span data-stu-id="ad0c3-144">Y</span></span></td>
        <td><span data-ttu-id="ad0c3-145">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-145">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-146">LeftShoulder</span><span class="sxs-lookup"><span data-stu-id="ad0c3-146">LeftShoulder</span></span></td>
        <td><span data-ttu-id="ad0c3-147">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-147">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-148">RightShoulder</span><span class="sxs-lookup"><span data-stu-id="ad0c3-148">RightShoulder</span></span></td>
        <td><span data-ttu-id="ad0c3-149">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-149">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-150">LeftThumbstickButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-150">LeftThumbstickButton</span></span></td>
        <td><span data-ttu-id="ad0c3-151">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-151">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-152">RightThumbstickButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-152">RightThumbstickButton</span></span></td>
        <td><span data-ttu-id="ad0c3-153">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-153">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-154">DPadUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-154">DPadUp</span></span></td>
        <td><span data-ttu-id="ad0c3-155">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-155">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-156">DPadDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-156">DPadDown</span></span></td>
        <td><span data-ttu-id="ad0c3-157">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-157">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-158">DPadLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-158">DPadLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-159">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-159">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-160">DPadRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-160">DPadRight</span></span></td>
        <td><span data-ttu-id="ad0c3-161">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-161">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-162">Paddle1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-162">Paddle1</span></span></td>
        <td><span data-ttu-id="ad0c3-163">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-163">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-164">Paddle2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-164">Paddle2</span></span></td>
        <td><span data-ttu-id="ad0c3-165">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-165">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-166">Paddle3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-166">Paddle3</span></span></td>
        <td><span data-ttu-id="ad0c3-167">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-167">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-168">Paddle4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-168">Paddle4</span></span></td>
        <td><span data-ttu-id="ad0c3-169">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-169">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-170">LeftTrigger</span><span class="sxs-lookup"><span data-stu-id="ad0c3-170">LeftTrigger</span></span></td>
        <td><span data-ttu-id="ad0c3-171">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-171">Yes</span></span></td>
        <td rowspan="6" style="vertical-align: middle;"><span data-ttu-id="ad0c3-172">Siehe <a href="#axis-mapping">Achsenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-172">See <a href="#axis-mapping">Axis mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-173">RightTrigger</span><span class="sxs-lookup"><span data-stu-id="ad0c3-173">RightTrigger</span></span></td>
        <td><span data-ttu-id="ad0c3-174">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-174">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-175">LeftThumbstickX</span><span class="sxs-lookup"><span data-stu-id="ad0c3-175">LeftThumbstickX</span></span></td>
        <td><span data-ttu-id="ad0c3-176">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-176">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-177">LeftThumbstickY</span><span class="sxs-lookup"><span data-stu-id="ad0c3-177">LeftThumbstickY</span></span></td>
        <td><span data-ttu-id="ad0c3-178">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-178">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-179">RightThumbstickX</span><span class="sxs-lookup"><span data-stu-id="ad0c3-179">RightThumbstickX</span></span></td>
        <td><span data-ttu-id="ad0c3-180">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-180">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-181">RightThumbstickY</span><span class="sxs-lookup"><span data-stu-id="ad0c3-181">RightThumbstickY</span></span></td>
        <td><span data-ttu-id="ad0c3-182">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-182">Yes</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="ad0c3-183">Wenn Sie Ihren Spielecontroller als einen unterstützten **Gamepad** hinzufügen, wird dringend empfohlen, dass Sie ihn auch als unterstützten **UINavigationController** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-183">If you add your game controller as a supported **Gamepad**, we highly recommend that you also add it as a supported **UINavigationController**.</span></span>

### <a name="racingwheel"></a><span data-ttu-id="ad0c3-184">RacingWheel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-184">RacingWheel</span></span>

<span data-ttu-id="ad0c3-185">Die folgende Tabelle enthält die erforderlichen und optionalen Unterschlüssel unter dem **RacingWheel**-Unterschlüssel:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-185">The table below lists the required and optional subkeys under the **RacingWheel** subkey:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-186">Unterschlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-186">Subkey</span></span></th>
        <th><span data-ttu-id="ad0c3-187">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-187">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-188">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-188">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-189">PreviousGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-189">PreviousGear</span></span></td>
        <td><span data-ttu-id="ad0c3-190">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-190">Yes</span></span></td>
        <td rowspan="30" style="vertical-align: middle;"><span data-ttu-id="ad0c3-191">Siehe <a href="#button-mapping">Tastenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-191">See <a href="#button-mapping">Button mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-192">NextGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-192">NextGear</span></span></td>
        <td><span data-ttu-id="ad0c3-193">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-193">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-194">DPadUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-194">DPadUp</span></span></td>
        <td><span data-ttu-id="ad0c3-195">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-195">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-196">DPadDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-196">DPadDown</span></span></td>
        <td><span data-ttu-id="ad0c3-197">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-197">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-198">DPadLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-198">DPadLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-199">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-199">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-200">DPadRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-200">DPadRight</span></span></td>
        <td><span data-ttu-id="ad0c3-201">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-201">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-202">Button1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-202">Button1</span></span></td>
        <td><span data-ttu-id="ad0c3-203">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-203">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-204">Button2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-204">Button2</span></span></td>
        <td><span data-ttu-id="ad0c3-205">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-205">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-206">Button3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-206">Button3</span></span></td>
        <td><span data-ttu-id="ad0c3-207">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-207">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-208">Button4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-208">Button4</span></span></td>
        <td><span data-ttu-id="ad0c3-209">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-209">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-210">Button5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-210">Button5</span></span></td>
        <td><span data-ttu-id="ad0c3-211">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-211">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-212">Button6</span><span class="sxs-lookup"><span data-stu-id="ad0c3-212">Button6</span></span></td>
        <td><span data-ttu-id="ad0c3-213">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-213">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-214">Button7</span><span class="sxs-lookup"><span data-stu-id="ad0c3-214">Button7</span></span></td>
        <td><span data-ttu-id="ad0c3-215">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-215">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-216">Button8</span><span class="sxs-lookup"><span data-stu-id="ad0c3-216">Button8</span></span></td>
        <td><span data-ttu-id="ad0c3-217">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-217">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-218">Button9</span><span class="sxs-lookup"><span data-stu-id="ad0c3-218">Button9</span></span></td>
        <td><span data-ttu-id="ad0c3-219">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-219">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-220">Button10</span><span class="sxs-lookup"><span data-stu-id="ad0c3-220">Button10</span></span></td>
        <td><span data-ttu-id="ad0c3-221">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-221">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-222">Button11</span><span class="sxs-lookup"><span data-stu-id="ad0c3-222">Button11</span></span></td>
        <td><span data-ttu-id="ad0c3-223">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-223">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-224">Button12</span><span class="sxs-lookup"><span data-stu-id="ad0c3-224">Button12</span></span></td>
        <td><span data-ttu-id="ad0c3-225">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-225">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-226">Button13</span><span class="sxs-lookup"><span data-stu-id="ad0c3-226">Button13</span></span></td>
        <td><span data-ttu-id="ad0c3-227">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-227">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-228">Button14</span><span class="sxs-lookup"><span data-stu-id="ad0c3-228">Button14</span></span></td>
        <td><span data-ttu-id="ad0c3-229">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-229">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-230">Button15</span><span class="sxs-lookup"><span data-stu-id="ad0c3-230">Button15</span></span></td>
        <td><span data-ttu-id="ad0c3-231">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-231">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-232">Button16</span><span class="sxs-lookup"><span data-stu-id="ad0c3-232">Button16</span></span></td>
        <td><span data-ttu-id="ad0c3-233">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-233">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-234">FirstGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-234">FirstGear</span></span></td>
        <td><span data-ttu-id="ad0c3-235">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-235">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-236">SecondGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-236">SecondGear</span></span></td>
        <td><span data-ttu-id="ad0c3-237">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-237">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-238">ThirdGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-238">ThirdGear</span></span></td>
        <td><span data-ttu-id="ad0c3-239">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-239">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-240">FourthGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-240">FourthGear</span></span></td>
        <td><span data-ttu-id="ad0c3-241">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-241">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-242">FifthGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-242">FifthGear</span></span></td>
        <td><span data-ttu-id="ad0c3-243">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-243">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-244">SixthGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-244">SixthGear</span></span></td>
        <td><span data-ttu-id="ad0c3-245">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-245">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-246">SeventhGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-246">SeventhGear</span></span></td>
        <td><span data-ttu-id="ad0c3-247">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-247">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-248">ReverseGear</span><span class="sxs-lookup"><span data-stu-id="ad0c3-248">ReverseGear</span></span></td>
        <td><span data-ttu-id="ad0c3-249">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-249">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-250">Wheel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-250">Wheel</span></span></td>
        <td><span data-ttu-id="ad0c3-251">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-251">Yes</span></span></td>
        <td rowspan="5" style="vertical-align: middle;"><span data-ttu-id="ad0c3-252">Siehe <a href="#axis-mapping">Achsenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-252">See <a href="#axis-mapping">Axis mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-253">Drosselung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-253">Throttle</span></span></td>
        <td><span data-ttu-id="ad0c3-254">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-254">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-255">Bremse</span><span class="sxs-lookup"><span data-stu-id="ad0c3-255">Brake</span></span></td>
        <td><span data-ttu-id="ad0c3-256">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-256">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-257">Kupplung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-257">Clutch</span></span></td>
        <td><span data-ttu-id="ad0c3-258">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-258">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-259">Handbremse</span><span class="sxs-lookup"><span data-stu-id="ad0c3-259">Handbrake</span></span></td>
        <td><span data-ttu-id="ad0c3-260">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-260">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-261">MaxWheelAngle</span><span class="sxs-lookup"><span data-stu-id="ad0c3-261">MaxWheelAngle</span></span></td>
        <td><span data-ttu-id="ad0c3-262">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-262">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-263">Siehe <a href="#properties-mapping">Eigenschaften zuordnen</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-263">See <a href="#properties-mapping">Properties mapping</a></span></span></td>
    </tr>
</table>

### <a name="arcadestick"></a><span data-ttu-id="ad0c3-264">ArcadeStick</span><span class="sxs-lookup"><span data-stu-id="ad0c3-264">ArcadeStick</span></span>

<span data-ttu-id="ad0c3-265">Die folgende Tabelle enthält die erforderlichen und optionalen Unterschlüssel unter dem **ArcadeStick**-Unterschlüssel:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-265">The table below lists the required and optional subkeys under the **ArcadeStick** subkey:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-266">Unterschlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-266">Subkey</span></span></th>
        <th><span data-ttu-id="ad0c3-267">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-267">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-268">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-268">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-269">Action1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-269">Action 1</span></span></td>
        <td><span data-ttu-id="ad0c3-270">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-270">Yes</span></span></td>
        <td rowspan="12" style="vertical-align: middle;"><span data-ttu-id="ad0c3-271">Siehe <a href="#button-mapping">Tastenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-271">See <a href="#button-mapping">Button mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-272">Action2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-272">Action2</span></span></td>
        <td><span data-ttu-id="ad0c3-273">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-273">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-274">Action3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-274">Action3</span></span></td>
        <td><span data-ttu-id="ad0c3-275">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-275">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-276">Action4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-276">Action4</span></span></td>
        <td><span data-ttu-id="ad0c3-277">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-277">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-278">Action5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-278">Action5</span></span></td>
        <td><span data-ttu-id="ad0c3-279">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-279">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-280">Action6</span><span class="sxs-lookup"><span data-stu-id="ad0c3-280">Action6</span></span></td>
        <td><span data-ttu-id="ad0c3-281">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-281">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-282">Special1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-282">Special1</span></span></td>
        <td><span data-ttu-id="ad0c3-283">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-283">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-284">Special2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-284">Special2</span></span></td>
        <td><span data-ttu-id="ad0c3-285">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-285">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-286">StickUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-286">StickUp</span></span></td>
        <td><span data-ttu-id="ad0c3-287">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-287">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-288">StickDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-288">StickDown</span></span></td>
        <td><span data-ttu-id="ad0c3-289">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-289">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-290">StickLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-290">StickLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-291">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-291">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-292">StickRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-292">StickRight</span></span></td>
        <td><span data-ttu-id="ad0c3-293">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-293">Yes</span></span></td>
    </tr>
</table>

### <a name="flightstick"></a><span data-ttu-id="ad0c3-294">FlightStick</span><span class="sxs-lookup"><span data-stu-id="ad0c3-294">FlightStick</span></span>

<span data-ttu-id="ad0c3-295">Die folgende Tabelle enthält die erforderlichen und optionalen Unterschlüssel unter dem **FlightStick**-Unterschlüssel:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-295">The table below lists the required and optional subkeys under the **FlightStick** subkey:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-296">Unterschlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-296">Subkey</span></span></th>
        <th><span data-ttu-id="ad0c3-297">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-297">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-298">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-298">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-299">FirePrimary</span><span class="sxs-lookup"><span data-stu-id="ad0c3-299">FirePrimary</span></span></td>
        <td><span data-ttu-id="ad0c3-300">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-300">Yes</span></span></td>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-301">Siehe <a href="#button-mapping">Tastenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-301">See <a href="#button-mapping">Button mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-302">FireSecondary</span><span class="sxs-lookup"><span data-stu-id="ad0c3-302">FireSecondary</span></span></td>
        <td><span data-ttu-id="ad0c3-303">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-303">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-304">Roll</span><span class="sxs-lookup"><span data-stu-id="ad0c3-304">Roll</span></span></td>
        <td><span data-ttu-id="ad0c3-305">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-305">Yes</span></span></td>
        <td rowspan="4" style="vertical-align: middle;"><span data-ttu-id="ad0c3-306">Siehe <a href="#axis-mapping">Achsenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-306">See <a href="#axis-mapping">Axis mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-307">Nickwinkel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-307">Pitch</span></span></td>
        <td><span data-ttu-id="ad0c3-308">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-308">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-309">Schwenken</span><span class="sxs-lookup"><span data-stu-id="ad0c3-309">Yaw</span></span></td>
        <td><span data-ttu-id="ad0c3-310">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-310">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-311">Drosselung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-311">Throttle</span></span></td>
        <td><span data-ttu-id="ad0c3-312">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-312">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-313">HatSwitch</span><span class="sxs-lookup"><span data-stu-id="ad0c3-313">HatSwitch</span></span></td>
        <td><span data-ttu-id="ad0c3-314">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-314">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-315">Siehe <a href="#switch-mapping">Switch-Zuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-315">See <a href="#switch-mapping">Switch mapping</a></span></span></td>
    </tr>
</table>

### <a name="uinavigation"></a><span data-ttu-id="ad0c3-316">UINavigation</span><span class="sxs-lookup"><span data-stu-id="ad0c3-316">UINavigation</span></span>

<span data-ttu-id="ad0c3-317">Die folgende Tabelle enthält die erforderlichen und optionalen Unterschlüssel unter dem **UINavigation**-Unterschlüssel:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-317">The table below lists the required and optional subkeys under **UINavigation** subkey:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-318">Unterschlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-318">Subkey</span></span></th>
        <th><span data-ttu-id="ad0c3-319">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-319">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-320">Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-320">Info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-321">Menü</span><span class="sxs-lookup"><span data-stu-id="ad0c3-321">Menu</span></span></td>
        <td><span data-ttu-id="ad0c3-322">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-322">Yes</span></span></td>
        <td rowspan="24" style="vertical-align: middle;"><span data-ttu-id="ad0c3-323">Siehe <a href="#button-mapping">Tastenzuordnung</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-323">See <a href="#button-mapping">Button mapping</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-324">Ansicht</span><span class="sxs-lookup"><span data-stu-id="ad0c3-324">View</span></span></td>
        <td><span data-ttu-id="ad0c3-325">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-325">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-326">Annehmen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-326">Accept</span></span></td>
        <td><span data-ttu-id="ad0c3-327">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-327">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-328">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-328">Cancel</span></span></td>
        <td><span data-ttu-id="ad0c3-329">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-329">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-330">PrimaryUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-330">PrimaryUp</span></span></td>
        <td><span data-ttu-id="ad0c3-331">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-331">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-332">PrimaryDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-332">PrimaryDown</span></span></td>
        <td><span data-ttu-id="ad0c3-333">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-333">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-334">PrimaryLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-334">PrimaryLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-335">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-335">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-336">PrimaryRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-336">PrimaryRight</span></span></td>
        <td><span data-ttu-id="ad0c3-337">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-337">Yes</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-338">Context1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-338">Context1</span></span></td>
        <td><span data-ttu-id="ad0c3-339">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-339">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-340">Context2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-340">Context2</span></span></td>
        <td><span data-ttu-id="ad0c3-341">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-341">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-342">Context3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-342">Context3</span></span></td>
        <td><span data-ttu-id="ad0c3-343">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-343">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-344">Context4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-344">Context4</span></span></td>
        <td><span data-ttu-id="ad0c3-345">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-345">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-346">BildAuf</span><span class="sxs-lookup"><span data-stu-id="ad0c3-346">PageUp</span></span></td>
        <td><span data-ttu-id="ad0c3-347">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-347">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-348">BildAb</span><span class="sxs-lookup"><span data-stu-id="ad0c3-348">PageDown</span></span></td>
        <td><span data-ttu-id="ad0c3-349">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-349">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-350">PageLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-350">PageLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-351">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-351">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-352">PageRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-352">PageRight</span></span></td>
        <td><span data-ttu-id="ad0c3-353">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-353">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-354">ScrollUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-354">ScrollUp</span></span></td>
        <td><span data-ttu-id="ad0c3-355">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-355">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-356">ScrollDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-356">ScrollDown</span></span></td>
        <td><span data-ttu-id="ad0c3-357">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-357">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-358">ScrollLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-358">ScrollLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-359">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-359">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-360">ScrollRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-360">ScrollRight</span></span></td>
        <td><span data-ttu-id="ad0c3-361">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-361">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-362">SecondaryUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-362">SecondaryUp</span></span></td>
        <td><span data-ttu-id="ad0c3-363">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-363">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-364">SecondaryDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-364">SecondaryDown</span></span></td>
        <td><span data-ttu-id="ad0c3-365">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-365">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-366">SecondaryLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-366">SecondaryLeft</span></span></td>
        <td><span data-ttu-id="ad0c3-367">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-367">No</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-368">SecondaryRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-368">SecondaryRight</span></span></td>
        <td><span data-ttu-id="ad0c3-369">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-369">No</span></span></td>
    </tr>
</table>

<span data-ttu-id="ad0c3-370">Weitere Informationen zu den Benutzeroberflächen-Navigationscontrollern und den oben aufgeführten Befehlen finden Sie unter [Benutzeroberflächen-Navigationscontroller](https://docs.microsoft.com/windows/uwp/gaming/ui-navigation-controller).</span><span class="sxs-lookup"><span data-stu-id="ad0c3-370">For more information about UI navigation controllers and the above commands, see [UI navigation controller](https://docs.microsoft.com/windows/uwp/gaming/ui-navigation-controller).</span></span>

## <a name="keys"></a><span data-ttu-id="ad0c3-371">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-371">Keys</span></span>

<span data-ttu-id="ad0c3-372">In den folgenden Abschnitten wird der Inhalt aller Unterschlüssel des Schlüssels für **Gamepad**, **RacingWheel**, **ArcadeStick**, **FlightStick** und **UINavigation** erläutert.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-372">The following sections explain the contents of each of the subkeys under the **Gamepad**, **RacingWheel**, **ArcadeStick**, **FlightStick**, and **UINavigation** keys.</span></span>

### <a name="button-mapping"></a><span data-ttu-id="ad0c3-373">Tastenzuordnung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-373">Button mapping</span></span>

<span data-ttu-id="ad0c3-374">Die folgende Tabelle listet die Werte, die benötigt werden, um eine Taste zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-374">The table below lists the values that are needed to map a button.</span></span> <span data-ttu-id="ad0c3-375">Beim Drücken von **DPadUp** auf dem Gamecontroller sollte die Zuordnung für **DPadUp** die Werte **ButtonIndex** enthalten (**Quelle** ist **Taste**).</span><span class="sxs-lookup"><span data-stu-id="ad0c3-375">For example, if pressing **DPadUp** on the game controller, the mapping for **DPadUp** should contain the **ButtonIndex** value (**Source** is **Button**).</span></span> <span data-ttu-id="ad0c3-376">Wenn **DPadUp** von einer Switchposition zugeordnet werden soll, muss die **DPadUp**-Zuordnung die Werte **SwitchIndex** und **SwitchPosition** enthalten (**Quelle** ist **Switch**).</span><span class="sxs-lookup"><span data-stu-id="ad0c3-376">If **DPadUp** needs to be mapped from a switch position, then the **DPadUp** mapping should contain the values **SwitchIndex** and **SwitchPosition** (**Source** is **Switch**).</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-377">Quelle</span><span class="sxs-lookup"><span data-stu-id="ad0c3-377">Source</span></span></th>
        <th><span data-ttu-id="ad0c3-378">Wertname</span><span class="sxs-lookup"><span data-stu-id="ad0c3-378">Value name</span></span></th>
        <th><span data-ttu-id="ad0c3-379">Werttyp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-379">Value type</span></span></th>
        <th><span data-ttu-id="ad0c3-380">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-380">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-381">Wert-Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-381">Value info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-382">Taste</span><span class="sxs-lookup"><span data-stu-id="ad0c3-382">Button</span></span></td>
        <td><span data-ttu-id="ad0c3-383">ButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-383">ButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-384">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-384">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-385">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-385">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-386">Index in der <b>RawGameController</b>-Tastenarray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-386">Index in the <b>RawGameController</b> button array.</span></span></td>
    </tr>
    <tr>
        <td rowspan="4" style="vertical-align: middle;"><span data-ttu-id="ad0c3-387">Achse</span><span class="sxs-lookup"><span data-stu-id="ad0c3-387">Axis</span></span></td>
        <td><span data-ttu-id="ad0c3-388">AxisIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-388">AxisIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-389">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-389">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-390">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-390">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-391">Index in der <b>RawGameController</b>-Achsenarray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-391">Index in the <b>RawGameController</b> axis array.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-392">Invertierung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-392">Invert</span></span></td>
        <td><span data-ttu-id="ad0c3-393">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-393">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-394">Nein</span><span class="sxs-lookup"><span data-stu-id="ad0c3-394">No</span></span></td>
        <td><span data-ttu-id="ad0c3-395">Gibt an, dass der Achsenwert umgekehrt werden soll, bevor Sie <b>ThresholdPercent</b> und <b>DebouncePercent</b> als Faktoren anwenden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-395">Indicates that the axis value should be inverted before the <b>Threshold Percent</b> and <b>DebouncePercent</b> factors are applied.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-396">ThresholdPercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-396">ThresholdPercent</span></span></td>
        <td><span data-ttu-id="ad0c3-397">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-397">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-398">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-398">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-399">Gibt die Achsenposition an, von der der zugeordnete Wert der Taste zwischen dem gedrückten und losgelassenen Zustand wechselt.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-399">Indicates the axis position at which the mapped button value transitions between the pressed and released states.</span></span> <span data-ttu-id="ad0c3-400">Der gültige Wertebereich liegt zwischen 0 bis 100.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-400">The valid range of values is 0 to 100.</span></span> <span data-ttu-id="ad0c3-401">Die Taste gilt als gedrückt, wenn der Achsenwert größer als oder gleich diesem Wert ist.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-401">The button is considered pressed if the axis value is greater than or equal to this value.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-402">DebouncePercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-402">DebouncePercent</span></span></td>
        <td><span data-ttu-id="ad0c3-403">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-403">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-404">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-404">Yes</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-405">Definiert die Größe eines Fensters um den <b>ThresholdPercent</b>-Wert, der verwendet wird, um den Zustand der gemeldeten Taste zu entprellen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-405">Defines the size of a window around the <b>ThresholdPercent</b> value, which is used to debounce the reported button state.</span></span> <span data-ttu-id="ad0c3-406">Der gültige Wertebereich liegt zwischen 0 bis 100.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-406">The valid range of values is 0 to 100.</span></span> <span data-ttu-id="ad0c3-407">Statusübergänge der Tasten können nur auftreten, wenn der Achsenwert den oberen oder unteren Rand der Entprellfenster überschreitet.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-407">Button state transitions can only occur when the axis value crosses the upper or lower boundaries of the debounce window.</span></span> <span data-ttu-id="ad0c3-408">Ist beispielsweise der <b>ThresholdPercent</b>-Wert 50 und der <b>DebouncePercent</b>-Wert 10, liegt die Entprellgrenze bei 45% und 55% für den gesamten Achsenwert.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-408">For example, a <b>ThresholdPercent</b> of 50 and <b>DebouncePercent</b> of 10 results in debounce boundaries at 45% and 55% of the full-range axis values.</span></span> <span data-ttu-id="ad0c3-409">Die Taste kann nicht zum gedrückten Zustand übergehen, bis der Achsenwert 55% oder höher erreicht, und es kann nicht in den endgültigen Zustand übergehen, bis der Achsenwert 45% oder darunter erreicht.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-409">The button can't transition to the pressed state until the axis value reaches 55% or above, and it can't transition back to the released state until the axis value reaches 45% or below.</span></span></p>
            <p><span data-ttu-id="ad0c3-410">Die berechneten Entprellfenstergrenzen liegen zwischen 0% und 100%.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-410">The computed debounce window boundaries are clamped between 0% and 100%.</span></span> <span data-ttu-id="ad0c3-411">Z.B. ergibt eine Schwellenwert von 5% und ein Entprellfenster von 20% eine Entprellfenstergrenze von 0% und 15%.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-411">For example, a threshold of 5% and a debounce window of 20% would result in the debounce window boundaries falling at 0% and 15%.</span></span> <span data-ttu-id="ad0c3-412">Der Zustand der Taste für einen Achsenwerte von 0% und 100% ist immer als gedrückt oder losgelassen gemeldet, unabhängig von den Schwellen- und Entprellwerten.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-412">The button state for axis values of 0% and 100% are always reported as released and pressed, respectively, regardless of the threshold and debounce values.</span></span></p>
        </td>
    </tr>
    <tr>
        <td rowspan="3" style="vertical-align: middle;"><span data-ttu-id="ad0c3-413">Switch</span><span class="sxs-lookup"><span data-stu-id="ad0c3-413">Switch</span></span></td>
        <td><span data-ttu-id="ad0c3-414">SwitchIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-414">SwitchIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-415">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-415">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-416">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-416">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-417">Index im <b>RawGameController</b>-Switcharray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-417">Index in the <b>RawGameController</b> switch array.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-418">SwitchPosition</span><span class="sxs-lookup"><span data-stu-id="ad0c3-418">SwitchPosition</span></span></td>
        <td><span data-ttu-id="ad0c3-419">REG_SZ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-419">REG_SZ</span></span></td>
        <td><span data-ttu-id="ad0c3-420">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-420">Yes</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-421">Gibt die Switchposition an, die bewirkt, dass die zugeordnete Schaltfläche meldet, dass darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-421">Indicates the switch position that will cause the mapped button to report that it's being pressed.</span></span> <span data-ttu-id="ad0c3-422">Die Positionswerte können eine der folgenden Zeichenfolgen sein:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-422">The position values can be one of these strings:</span></span></p>
            <ul>
                <li><span data-ttu-id="ad0c3-423">Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-423">Up</span></span></li> 
                <li><span data-ttu-id="ad0c3-424">UpRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-424">UpRight</span></span></li>
                <li><span data-ttu-id="ad0c3-425">Right</span><span class="sxs-lookup"><span data-stu-id="ad0c3-425">Right</span></span></li>
                <li><span data-ttu-id="ad0c3-426">DownRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-426">DownRight</span></span></li>
                <li><span data-ttu-id="ad0c3-427">Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-427">Down</span></span></li>
                <li><span data-ttu-id="ad0c3-428">DownLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-428">DownLeft</span></span></li>
                <li><span data-ttu-id="ad0c3-429">Left</span><span class="sxs-lookup"><span data-stu-id="ad0c3-429">Left</span></span></li>
                <li><span data-ttu-id="ad0c3-430">UpLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-430">UpLeft</span></span></li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-431">IncludeAdjacent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-431">IncludeAdjacent</span></span></td>
        <td><span data-ttu-id="ad0c3-432">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-432">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-433">Nein.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-433">No</span></span></td>
        <td><span data-ttu-id="ad0c3-434">Gibt die Switchposition daneben an, die ebenfalls bewirkt, dass die zugeordnete Schaltfläche meldet, dass darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-434">Indicates that adjacent switch positions will also cause the mapped button to report that it's being pressed.</span></span></td>
    </tr>
</table>

### <a name="axis-mapping"></a><span data-ttu-id="ad0c3-435">Achsenzuordnung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-435">Axis mapping</span></span>

<span data-ttu-id="ad0c3-436">Die folgende Tabelle listet die Werte, die benötigt werden, um eine Achse zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-436">The table below lists the values that are needed to map an axis:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-437">Quelle</span><span class="sxs-lookup"><span data-stu-id="ad0c3-437">Source</span></span></th>
        <th><span data-ttu-id="ad0c3-438">Wertname</span><span class="sxs-lookup"><span data-stu-id="ad0c3-438">Value name</span></span></th>
        <th><span data-ttu-id="ad0c3-439">Werttyp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-439">Value type</span></span></th>
        <th><span data-ttu-id="ad0c3-440">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ad0c3-440">Required?</span></span></th>
        <th><span data-ttu-id="ad0c3-441">Wert-Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-441">Value info</span></span></th>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-442">Taste</span><span class="sxs-lookup"><span data-stu-id="ad0c3-442">Button</span></span></td>
        <td><span data-ttu-id="ad0c3-443">MaxValueButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-443">MaxValueButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-444">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-444">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-445">Ja.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-445">Yes</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-446">Index des <b>RawGameController</b>-Tastenarrays, das als zugeordneter unidirektionaler Achsenwert übersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-446">Index in the <b>RawGameController</b> button array which gets translated to the mapped unidirectional axis value.</span></span></p>
            <table>
                <tr>
                    <th><span data-ttu-id="ad0c3-447">MaxButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-447">MaxButton</span></span></th>
                    <th><span data-ttu-id="ad0c3-448">AxisValue</span><span class="sxs-lookup"><span data-stu-id="ad0c3-448">AxisValue</span></span></th>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-449">FALSE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-449">FALSE</span></span></td>
                    <td><span data-ttu-id="ad0c3-450">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-450">0.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-451">TRUE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-451">TRUE</span></span></td>
                    <td><span data-ttu-id="ad0c3-452">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-452">1.0</span></span></td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-453">MinValueButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-453">MinValueButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-454">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-454">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-455">Nein.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-455">No</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-456">Gibt an, dass die zugeordnete Achse bidirektional ist.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-456">Indicates that the mapped axis is bidirectional.</span></span> <span data-ttu-id="ad0c3-457">Werte von <b>MaxButton</b> und <b>MinButton</b> werden in einer einzelnen bidirektionalen Achse kombiniert, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-457">Values of <b>MaxButton</b> and <b>MinButton</b> are combined into a single bidirectional axis as shown below.</span></span></p>
            <table>
                <tr>
                    <th><span data-ttu-id="ad0c3-458">MinButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-458">MinButton</span></span></th>
                    <th><span data-ttu-id="ad0c3-459">MaxButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-459">MaxButton</span></span></th>
                    <th><span data-ttu-id="ad0c3-460">AxisValue</span><span class="sxs-lookup"><span data-stu-id="ad0c3-460">AxisValue</span></span></th>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-461">FALSE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-461">FALSE</span></span></td>
                    <td><span data-ttu-id="ad0c3-462">FALSE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-462">FALSE</span></span></td>
                    <td><span data-ttu-id="ad0c3-463">0.5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-463">0.5</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-464">FALSE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-464">FALSE</span></span></td>
                    <td><span data-ttu-id="ad0c3-465">TRUE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-465">TRUE</span></span></td>
                    <td><span data-ttu-id="ad0c3-466">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-466">1.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-467">TRUE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-467">TRUE</span></span></td>
                    <td><span data-ttu-id="ad0c3-468">FALSE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-468">FALSE</span></span></td>
                    <td><span data-ttu-id="ad0c3-469">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-469">0.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-470">TRUE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-470">TRUE</span></span></td>
                    <td><span data-ttu-id="ad0c3-471">TRUE</span><span class="sxs-lookup"><span data-stu-id="ad0c3-471">TRUE</span></span></td>
                    <td><span data-ttu-id="ad0c3-472">0.5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-472">0.5</span></span></td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-473">Achse</span><span class="sxs-lookup"><span data-stu-id="ad0c3-473">Axis</span></span></td>
        <td><span data-ttu-id="ad0c3-474">AxisIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-474">AxisIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-475">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-475">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-476">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-476">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-477">Index in der <b>RawGameController</b>-Achsenarray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-477">Index in the <b>RawGameController</b> axis array.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-478">Invertierung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-478">Invert</span></span></td>
        <td><span data-ttu-id="ad0c3-479">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-479">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-480">Nein.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-480">No</span></span></td>
        <td><span data-ttu-id="ad0c3-481">Gibt an, dass der zugeordnete Achsenwert umgekehrt werden soll, bevor es zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-481">Indicates that the mapped axis value should be inverted before it's returned.</span></span></td>
    </tr>
    <tr>
        <td rowspan="3" style="vertical-align: middle;"><span data-ttu-id="ad0c3-482">Switch</span><span class="sxs-lookup"><span data-stu-id="ad0c3-482">Switch</span></span></td>
        <td><span data-ttu-id="ad0c3-483">SwitchIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-483">SwitchIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-484">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-484">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-485">Ja</span><span class="sxs-lookup"><span data-stu-id="ad0c3-485">Yes</span></span></td>
        <td><span data-ttu-id="ad0c3-486">Index im <b>RawGameController</b>-Switcharray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-486">Index in the <b>RawGameController</b> switch array.</span></span>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-487">MaxValueSwitchPosition</span><span class="sxs-lookup"><span data-stu-id="ad0c3-487">MaxValueSwitchPosition</span></span></td>
        <td><span data-ttu-id="ad0c3-488">REG_SZ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-488">REG_SZ</span></span></td>
        <td><span data-ttu-id="ad0c3-489">Ja.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-489">Yes</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-490">Eine der folgenden Zeichenfolgen:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-490">One of the following strings:</span></span></p>
            <ul>
                <li><span data-ttu-id="ad0c3-491">Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-491">Up</span></span></li>
                <li><span data-ttu-id="ad0c3-492">UpRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-492">UpRight</span></span></li>
                <li><span data-ttu-id="ad0c3-493">Right</span><span class="sxs-lookup"><span data-stu-id="ad0c3-493">Right</span></span></li>
                <li><span data-ttu-id="ad0c3-494">DownRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-494">DownRight</span></span></li>
                <li><span data-ttu-id="ad0c3-495">Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-495">Down</span></span></li>
                <li><span data-ttu-id="ad0c3-496">DownLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-496">DownLeft</span></span></li>
                <li><span data-ttu-id="ad0c3-497">Left</span><span class="sxs-lookup"><span data-stu-id="ad0c3-497">Left</span></span></li>
                <li><span data-ttu-id="ad0c3-498">UpLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-498">UpLeft</span></span></li>
            </ul>
            <p><span data-ttu-id="ad0c3-499">Es gibt die Position des Switchs an, bei dem der zugeordnete Achsenwert als 1,0 gemeldet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-499">It indicates the position of the switch that causes the mapped axis value to be reported as 1.0.</span></span> <span data-ttu-id="ad0c3-500">Die entgegengesetzte Richtung der <b>MaxValueSwitchPosition</b> wird als 0,0 behandelt.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-500">The opposing direction of <b>MaxValueSwitchPosition</b> is treated as 0.0.</span></span> <span data-ttu-id="ad0c3-501">Wenn beispielsweise <b>MaxValueSwitchPosition</b> auf <b>Up</b> festgelegt ist, ist die Achsenwert-Übersetzung wie unten gezeigt:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-501">For example, if <b>MaxValueSwitchPosition</b> is <b>Up</b>, the axis value translation is shown below:</span></span></p>
            <table>
                <tr>
                    <th><span data-ttu-id="ad0c3-502">Switchposition</span><span class="sxs-lookup"><span data-stu-id="ad0c3-502">Switch position</span></span></th>
                    <th><span data-ttu-id="ad0c3-503">AxisValue</span><span class="sxs-lookup"><span data-stu-id="ad0c3-503">AxisValue</span></span></th>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-504">Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-504">Up</span></span></td>
                    <td><span data-ttu-id="ad0c3-505">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-505">1.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-506">Center</span><span class="sxs-lookup"><span data-stu-id="ad0c3-506">Center</span></span></td>
                    <td><span data-ttu-id="ad0c3-507">0.5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-507">0.5</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-508">Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-508">Down</span></span></td>
                    <td><span data-ttu-id="ad0c3-509">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-509">0.0</span></span></td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-510">IncludeAdjacent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-510">IncludeAdjacent</span></span></td>
        <td><span data-ttu-id="ad0c3-511">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-511">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-512">Nein.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-512">No</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-513">Gibt die Schalterposition daneben an, die ebenfalls bewirkt, dass die zugeordnete Achse 1,0 meldet.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-513">Indicates that adjacent switch positions will also cause the mapped axis to report 1.0.</span></span> <span data-ttu-id="ad0c3-514">Wenn im obigen Beispiel <b>IncludeAdjacent</b> festgelegt ist, wird die Achsen-Übersetzung wie folgt durchgeführt:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-514">In the above example, if <b>IncludeAdjacent</b> is set, then the axis translation is done as follows:</span></span></p>
            <table>
                <tr>
                    <th><span data-ttu-id="ad0c3-515">Switchposition</span><span class="sxs-lookup"><span data-stu-id="ad0c3-515">Switch position</span></span></th>
                    <th><span data-ttu-id="ad0c3-516">AxisValue</span><span class="sxs-lookup"><span data-stu-id="ad0c3-516">AxisValue</span></span></th>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-517">Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-517">Up</span></span></td>
                    <td><span data-ttu-id="ad0c3-518">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-518">1.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-519">UpRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-519">UpRight</span></span></td>
                    <td><span data-ttu-id="ad0c3-520">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-520">1.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-521">UpLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-521">UpLeft</span></span></td>
                    <td><span data-ttu-id="ad0c3-522">1.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-522">1.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-523">Center</span><span class="sxs-lookup"><span data-stu-id="ad0c3-523">Center</span></span></td>
                    <td><span data-ttu-id="ad0c3-524">0.5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-524">0.5</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-525">Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-525">Down</span></span></td>
                    <td><span data-ttu-id="ad0c3-526">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-526">0.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-527">DownRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-527">DownRight</span></span></td>
                    <td><span data-ttu-id="ad0c3-528">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-528">0.0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-529">DownLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-529">DownLeft</span></span></td>
                    <td><span data-ttu-id="ad0c3-530">0.0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-530">0.0</span></span></td>
                </tr>
            </table>
        </td>
    </tr>
</table>

### <a name="switch-mapping"></a><span data-ttu-id="ad0c3-531">Switch-Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-531">Switch mapping</span></span>

<span data-ttu-id="ad0c3-532">Switchpositionen können entweder aus einer Reihe von Tasten im Array der Tasten von **RawGameController** oder von einem Index im Array der Switches zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-532">Switch positions can be mapped either from a set of buttons in the buttons array of the **RawGameController** or from an index in the switches array.</span></span> <span data-ttu-id="ad0c3-533">Switchpositionen können nicht von Achsen aus zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-533">Switch positions can't be mapped from axes.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-534">Quelle</span><span class="sxs-lookup"><span data-stu-id="ad0c3-534">Source</span></span></th>
        <th><span data-ttu-id="ad0c3-535">Wertname</span><span class="sxs-lookup"><span data-stu-id="ad0c3-535">Value name</span></span></th>
        <th><span data-ttu-id="ad0c3-536">Werttyp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-536">Value type</span></span></th>
        <th><span data-ttu-id="ad0c3-537">Wert-Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-537">Value info</span></span></th>
    </tr>
    <tr>
        <td rowspan="10" style="vertical-align: middle;"><span data-ttu-id="ad0c3-538">Taste</span><span class="sxs-lookup"><span data-stu-id="ad0c3-538">Button</span></span></td>
        <td><span data-ttu-id="ad0c3-539">ButtonCount</span><span class="sxs-lookup"><span data-stu-id="ad0c3-539">ButtonCount</span></span></td>
        <td><span data-ttu-id="ad0c3-540">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-540">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-541">2, 4 oder 8</span><span class="sxs-lookup"><span data-stu-id="ad0c3-541">2, 4, or 8</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-542">SwitchKind</span><span class="sxs-lookup"><span data-stu-id="ad0c3-542">SwitchKind</span></span></td>
        <td><span data-ttu-id="ad0c3-543">REG_SZ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-543">REG_SZ</span></span></td>
        <td><span data-ttu-id="ad0c3-544"><b>TwoWay</b>, <b>FourWay</b> oder <b>EightWay</b></span><span class="sxs-lookup"><span data-stu-id="ad0c3-544"><b>TwoWay</b>, <b>FourWay</b>, or <b>EightWay</b></span></span>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-545">UpButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-545">UpButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-546">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-546">DWORD</span></span></td>
        <td rowspan="8" style="vertical-align: middle;"><span data-ttu-id="ad0c3-547">Siehe <a href="#buttonindex-values">\*ButtonIndex-Werte</a></span><span class="sxs-lookup"><span data-stu-id="ad0c3-547">See <a href="#buttonindex-values">\*ButtonIndex values</a></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-548">DownButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-548">DownButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-549">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-549">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-550">LeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-550">LeftButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-551">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-551">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-552">RightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-552">RightButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-553">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-553">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-554">UpRightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-554">UpRightButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-555">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-555">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-556">DownRightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-556">DownRightButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-557">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-557">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-558">DownLeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-558">DownLeftButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-559">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-559">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-560">UpLeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-560">UpLeftButtonIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-561">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-561">DWORD</span></span></td>
    </tr>
    <tr>
        <td rowspan="9" style="vertical-align: middle;"><span data-ttu-id="ad0c3-562">Achse</span><span class="sxs-lookup"><span data-stu-id="ad0c3-562">Axis</span></span></td>
        <td><span data-ttu-id="ad0c3-563">SwitchKind</span><span class="sxs-lookup"><span data-stu-id="ad0c3-563">SwitchKind</span></span></td>
        <td><span data-ttu-id="ad0c3-564">REG_SZ</span><span class="sxs-lookup"><span data-stu-id="ad0c3-564">REG_SZ</span></span></td>
        <td><span data-ttu-id="ad0c3-565"><b>TwoWay</b>, <b>FourWay</b> oder <b>EightWay</b></span><span class="sxs-lookup"><span data-stu-id="ad0c3-565"><b>TwoWay</b>, <b>FourWay</b>, or <b>EightWay</b></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-566">XAxisIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-566">XAxisIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-567">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-567">DWORD</span></span></td>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-568"><b>YAxisIndex</b> ist immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-568"><b>YAxisIndex</b> is always present.</span></span> <span data-ttu-id="ad0c3-569"><b>XAxisIndex</b> ist nur verfügbar wenn <b>SwitchKind</b> entweder <b>FourWay</b> oder <b>EightWay</b> ist.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-569"><b>XAxisIndex</b> is only present when <b>SwitchKind</b> is <b>FourWay</b> or <b>EightWay</b>.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-570">YAxisIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-570">YAxisIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-571">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-571">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-572">XDeadZonePercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-572">XDeadZonePercent</span></span></td>
        <td><span data-ttu-id="ad0c3-573">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-573">DWORD</span></span></td>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-574">Gibt die Größe des inaktiven Bereichs um die Mittelposition der Achsen an.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-574">Indicate the size of the dead zone around the center position of the axes.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-575">YDeadZonePercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-575">YDeadZonePercent</span></span></td>
        <td><span data-ttu-id="ad0c3-576">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-576">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-577">XDebouncePercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-577">XDebouncePercent</span></span></td>
        <td><span data-ttu-id="ad0c3-578">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-578">DWORD</span></span></td>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-579">Legen Sie die Größe der Fenster um die Grenzen des oberen und unteren inaktiven Bereichs fest, die verwendet werden, um den entprellten Switchzustand zu melden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-579">Define the size of the windows around the upper and lower dead zone limits, which are used to de-bounce the reported switch state.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-580">YDebouncePercent</span><span class="sxs-lookup"><span data-stu-id="ad0c3-580">YDebouncePercent</span></span></td>
        <td><span data-ttu-id="ad0c3-581">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-581">DWORD</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-582">XInvert</span><span class="sxs-lookup"><span data-stu-id="ad0c3-582">XInvert</span></span></td>
        <td><span data-ttu-id="ad0c3-583">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-583">DWORD</span></span></td>
        <td rowspan="2" style="vertical-align: middle;"><span data-ttu-id="ad0c3-584">Geben Sie an, dass die entsprechenden Achsenwerte umgekehrt werden sollen, bevor die Kalkulation für den inaktiven Bereich und das Entprellfenster angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-584">Indicate that the corresponding axis values should be inverted before the dead zone and debounce window calculations are applied.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-585">YInvert</span><span class="sxs-lookup"><span data-stu-id="ad0c3-585">YInvert</span></span></td>
        <td><span data-ttu-id="ad0c3-586">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-586">DWORD</span></span></td>
    </tr>
    <tr>
        <td rowspan="3" style="vertical-align: middle;"><span data-ttu-id="ad0c3-587">Switch</span><span class="sxs-lookup"><span data-stu-id="ad0c3-587">Switch</span></span></td>
        <td><span data-ttu-id="ad0c3-588">SwitchIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-588">SwitchIndex</span></span></td>
        <td><span data-ttu-id="ad0c3-589">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-589">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-590">Index im <b>RawGameController</b>-Schalterarray.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-590">Index in the <b>RawGameController</b> switch array.</span></span>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-591">Invertierung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-591">Invert</span></span></td>
        <td><span data-ttu-id="ad0c3-592">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-592">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-593">Gibt an, dass der Switch ihre Position in einer Reihenfolge gegen den Uhrzeigersinn anstelle der Reihenfolge im Uhrzeigersinn meldet.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-593">Indicates that the switch reports its positions in a counter-clockwise order, rather than the default clockwise order.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-594">PositionBias</span><span class="sxs-lookup"><span data-stu-id="ad0c3-594">PositionBias</span></span></td>
        <td><span data-ttu-id="ad0c3-595">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-595">DWORD</span></span></td>
        <td>
            <p><span data-ttu-id="ad0c3-596">Verschiebt den Ausgangspunkt, wie Positionen um den angegebenen Wert gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-596">Shifts the starting point of how positions are reported by the specified amount.</span></span> <span data-ttu-id="ad0c3-597"><b>PositionBias</b> wird immer im Uhrzeigersinn vom ursprünglichen Ausgangspunkt gezählt und wird angewendet, bevor die Reihenfolge der Werte zurückgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-597"><b>PositionBias</b> is always counted clockwise from the original starting point, and is applied before the order of values is reversed.</span></span></p>
            <p><span data-ttu-id="ad0c3-598">Ein Switch, der beispielsweise die Positionen ab <b>DownRight</b> gegen den Uhrzeigersinn meldet kann durch Festlegen der Kennzeichen <b>Invert</b> und angeben eines <b>PositionBias</b> von 5 normalisiert werden:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-598">For example, a switch that reports positions starting with <b>DownRight</b> in counter-clockwise order can be normalized by setting the <b>Invert</b> flag and specifying a <b>PositionBias</b> of 5:</span></span></p>
            <table>
                <tr>
                    <th><span data-ttu-id="ad0c3-599">Position</span><span class="sxs-lookup"><span data-stu-id="ad0c3-599">Position</span></span></th>
                    <th><span data-ttu-id="ad0c3-600">Gemeldeter Wert</span><span class="sxs-lookup"><span data-stu-id="ad0c3-600">Reported value</span></span></th>
                    <th><span data-ttu-id="ad0c3-601">Nach PositionBias and Invert-Flags</span><span class="sxs-lookup"><span data-stu-id="ad0c3-601">After PositionBias and Invert flags</span></span></th>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-602">DownRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-602">DownRight</span></span></td>
                    <td><span data-ttu-id="ad0c3-603">0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-603">0</span></span></td>
                    <td><span data-ttu-id="ad0c3-604">3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-604">3</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-605">Right</span><span class="sxs-lookup"><span data-stu-id="ad0c3-605">Right</span></span></td>
                    <td><span data-ttu-id="ad0c3-606">1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-606">1</span></span></td>
                    <td><span data-ttu-id="ad0c3-607">2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-607">2</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-608">UpRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-608">UpRight</span></span></td>
                    <td><span data-ttu-id="ad0c3-609">2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-609">2</span></span></td>
                    <td><span data-ttu-id="ad0c3-610">1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-610">1</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-611">Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-611">Up</span></span></td>
                    <td><span data-ttu-id="ad0c3-612">3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-612">3</span></span></td>
                    <td><span data-ttu-id="ad0c3-613">0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-613">0</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-614">UpLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-614">UpLeft</span></span></td>
                    <td><span data-ttu-id="ad0c3-615">4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-615">4</span></span></td>
                    <td><span data-ttu-id="ad0c3-616">7</span><span class="sxs-lookup"><span data-stu-id="ad0c3-616">7</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-617">Left</span><span class="sxs-lookup"><span data-stu-id="ad0c3-617">Left</span></span></td>
                    <td><span data-ttu-id="ad0c3-618">5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-618">5</span></span></td>
                    <td><span data-ttu-id="ad0c3-619">6</span><span class="sxs-lookup"><span data-stu-id="ad0c3-619">6</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-620">DownLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-620">DownLeft</span></span></td>
                    <td><span data-ttu-id="ad0c3-621">6</span><span class="sxs-lookup"><span data-stu-id="ad0c3-621">6</span></span></td>
                    <td><span data-ttu-id="ad0c3-622">5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-622">5</span></span></td>
                </tr>
                <tr>
                    <td><span data-ttu-id="ad0c3-623">Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-623">Down</span></span></td>
                    <td><span data-ttu-id="ad0c3-624">7</span><span class="sxs-lookup"><span data-stu-id="ad0c3-624">7</span></span></td>
                    <td><span data-ttu-id="ad0c3-625">4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-625">4</span></span></td>
                </tr>
            </table>
    </tr>
</table>

#### <a name="buttonindex-values"></a><span data-ttu-id="ad0c3-626">\*ButtonIndex values</span><span class="sxs-lookup"><span data-stu-id="ad0c3-626">\*ButtonIndex values</span></span>

<span data-ttu-id="ad0c3-627">\*ButtonIndex-Werte legt Index auf den Tastenarray **RawGameController** fest:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-627">\*ButtonIndex values index into the **RawGameController**'s button array:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-628">ButtonCount</span><span class="sxs-lookup"><span data-stu-id="ad0c3-628">ButtonCount</span></span></th>
        <th><span data-ttu-id="ad0c3-629">SwitchKind</span><span class="sxs-lookup"><span data-stu-id="ad0c3-629">SwitchKind</span></span></th>
        <th><span data-ttu-id="ad0c3-630">RequiredMappings</span><span class="sxs-lookup"><span data-stu-id="ad0c3-630">RequiredMappings</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-631">2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-631">2</span></span></td>
        <td><span data-ttu-id="ad0c3-632">TwoWay</span><span class="sxs-lookup"><span data-stu-id="ad0c3-632">TwoWay</span></span></td>
        <td>
            <ul>
                <li><span data-ttu-id="ad0c3-633">UpButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-633">UpButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-634">DownButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-634">DownButtonIndex</span></span></li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-635">4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-635">4</span></span></td>
        <td><span data-ttu-id="ad0c3-636">FourWay</span><span class="sxs-lookup"><span data-stu-id="ad0c3-636">FourWay</span></span></td>
        <td>
            <ul>
                <li><span data-ttu-id="ad0c3-637">UpButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-637">UpButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-638">DownButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-638">DownButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-639">LeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-639">LeftButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-640">RightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-640">RightButtonIndex</span></span></li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-641">4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-641">4</span></span></td>
        <td><span data-ttu-id="ad0c3-642">EightWay</span><span class="sxs-lookup"><span data-stu-id="ad0c3-642">EightWay</span></span></td>
        <td>
            <ul>
                <li><span data-ttu-id="ad0c3-643">UpButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-643">UpButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-644">DownButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-644">DownButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-645">LeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-645">LeftButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-646">RightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-646">RightButtonIndex</span></span></li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-647">8</span><span class="sxs-lookup"><span data-stu-id="ad0c3-647">8</span></span></td>
        <td><span data-ttu-id="ad0c3-648">EightWay</span><span class="sxs-lookup"><span data-stu-id="ad0c3-648">EightWay</span></span></td>
        <td>
            <ul>
                <li><span data-ttu-id="ad0c3-649">UpButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-649">UpButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-650">DownButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-650">DownButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-651">LeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-651">LeftButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-652">RightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-652">RightButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-653">UpRightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-653">UpRightButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-654">DownRightButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-654">DownRightButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-655">DownLeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-655">DownLeftButtonIndex</span></span></li>
                <li><span data-ttu-id="ad0c3-656">UpLeftButtonIndex</span><span class="sxs-lookup"><span data-stu-id="ad0c3-656">UpLeftButtonIndex</span></span></li>
            </ul>
        </td>
    </tr>
</table>

### <a name="properties-mapping"></a><span data-ttu-id="ad0c3-657">Eigenschaften zuordnen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-657">Properties mapping</span></span>

<span data-ttu-id="ad0c3-658">Hierbei handelt es sich um statische Zuordnungswerte für verschiedene Zuordnungstypen.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-658">These are static mapping values for different mapping types.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-659">Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-659">Mapping</span></span></th>
        <th><span data-ttu-id="ad0c3-660">Wertname</span><span class="sxs-lookup"><span data-stu-id="ad0c3-660">Value name</span></span></th>
        <th><span data-ttu-id="ad0c3-661">Werttyp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-661">Value type</span></span></th>
        <th><span data-ttu-id="ad0c3-662">Wert-Info</span><span class="sxs-lookup"><span data-stu-id="ad0c3-662">Value info</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-663">RacingWheel</span><span class="sxs-lookup"><span data-stu-id="ad0c3-663">RacingWheel</span></span></td>
        <td><span data-ttu-id="ad0c3-664">MaxWheelAngle</span><span class="sxs-lookup"><span data-stu-id="ad0c3-664">MaxWheelAngle</span></span></td>
        <td><span data-ttu-id="ad0c3-665">DWORD</span><span class="sxs-lookup"><span data-stu-id="ad0c3-665">DWORD</span></span></td>
        <td><span data-ttu-id="ad0c3-666">Gibt den maximalen physischen Winkel des Lenkrads an, der vom Lenkrad in einer Richtung unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-666">Indicates the maximum physical wheel angle supported by the wheel in a single direction.</span></span> <span data-ttu-id="ad0c3-667">Beispielsweise würde ein Lenkrad mit einer mögliche Drehung von -90Grad bis 90Grad 90Grad angeben.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-667">For example, a wheel with a possible rotation of -90 degrees to 90 degrees would specify 90.</span></span></td>
    </tr>
</table>

## <a name="labels"></a><span data-ttu-id="ad0c3-668">Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-668">Labels</span></span>

<span data-ttu-id="ad0c3-669">Beschriftungen sollten unter dem **Beschriftungen**-Schlüssel unter dem Stammverzeichnis des Geräts vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-669">Labels should be present under the **Labels** key under the device root.</span></span> <span data-ttu-id="ad0c3-670">**Beschriftungen** können 3 Unterschlüssel enthalten: **Tasten**, **Achsen**, und **Switches**.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-670">**Labels** can have 3 subkeys: **Buttons**, **Axes**, and **Switches**.</span></span>

### <a name="button-labels"></a><span data-ttu-id="ad0c3-671">Schaltflächenbeschriftungen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-671">Button labels</span></span>

<span data-ttu-id="ad0c3-672">Der **Schaltflächen**-Schlüssel ordnet jeder Tastenposition im **RawGameController**-Tastenarray eine Zeichenfolge zu.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-672">The **Buttons** key maps each of the button positions in the **RawGameController**'s buttons array to a string.</span></span> <span data-ttu-id="ad0c3-673">Jede Zeichenfolge wird intern dem entsprechenden [GameControllerButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel)-Enumerationswert zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-673">Each string is mapped internally to the corresponding [GameControllerButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel) enum value.</span></span> <span data-ttu-id="ad0c3-674">Wenn ein Gamepad beispielsweise zehn Tasten enthält, ist die Reihenfolge, in der der **RawGameController** die Tasten analysiert und anbringt wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-674">For example, if a gamepad has ten buttons and the order in which the **RawGameController** parses out the buttons and presents them in the buttons report is like this:</span></span>

```cpp
Menu,               // Index 0
View,               // Index 1
LeftStickButton,    // Index 2
RightStickButton,   // Index 3
LetterA,            // Index 4
LetterB,            // Index 5
LetterX,            // Index 6
LetterY,            // Index 7
LeftBumper,         // Index 8
RightBumper         // Index 9
```

<span data-ttu-id="ad0c3-675">Die Bezeichnungen sollten in folgender Reihenfolge unter dem **Schaltflächen**-Schlüssel angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-675">The labels should appear in this order under the **Buttons** key:</span></span>

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-676">Name</span><span class="sxs-lookup"><span data-stu-id="ad0c3-676">Name</span></span></th>
        <th><span data-ttu-id="ad0c3-677">Wert (Typ: REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="ad0c3-677">Value (type: REG_SZ)</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-678">Button0</span><span class="sxs-lookup"><span data-stu-id="ad0c3-678">Button0</span></span></td>
        <td><span data-ttu-id="ad0c3-679">Menü</span><span class="sxs-lookup"><span data-stu-id="ad0c3-679">Menu</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-680">Button1</span><span class="sxs-lookup"><span data-stu-id="ad0c3-680">Button1</span></span></td>
        <td><span data-ttu-id="ad0c3-681">Ansicht</span><span class="sxs-lookup"><span data-stu-id="ad0c3-681">View</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-682">Button2</span><span class="sxs-lookup"><span data-stu-id="ad0c3-682">Button2</span></span></td>
        <td><span data-ttu-id="ad0c3-683">LeftStickButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-683">LeftStickButton</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-684">Button3</span><span class="sxs-lookup"><span data-stu-id="ad0c3-684">Button3</span></span></td>
        <td><span data-ttu-id="ad0c3-685">RightStickButton</span><span class="sxs-lookup"><span data-stu-id="ad0c3-685">RightStickButton</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-686">Button4</span><span class="sxs-lookup"><span data-stu-id="ad0c3-686">Button4</span></span></td>
        <td><span data-ttu-id="ad0c3-687">LetterA</span><span class="sxs-lookup"><span data-stu-id="ad0c3-687">LetterA</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-688">Button5</span><span class="sxs-lookup"><span data-stu-id="ad0c3-688">Button5</span></span></td>
        <td><span data-ttu-id="ad0c3-689">LetterB</span><span class="sxs-lookup"><span data-stu-id="ad0c3-689">LetterB</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-690">Button6</span><span class="sxs-lookup"><span data-stu-id="ad0c3-690">Button6</span></span></td>
        <td><span data-ttu-id="ad0c3-691">LetterX</span><span class="sxs-lookup"><span data-stu-id="ad0c3-691">LetterX</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-692">Button7</span><span class="sxs-lookup"><span data-stu-id="ad0c3-692">Button7</span></span></td>
        <td><span data-ttu-id="ad0c3-693">LetterY</span><span class="sxs-lookup"><span data-stu-id="ad0c3-693">LetterY</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-694">Button8</span><span class="sxs-lookup"><span data-stu-id="ad0c3-694">Button8</span></span></td>
        <td><span data-ttu-id="ad0c3-695">LeftBumper</span><span class="sxs-lookup"><span data-stu-id="ad0c3-695">LeftBumper</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-696">Button9</span><span class="sxs-lookup"><span data-stu-id="ad0c3-696">Button9</span></span></td>
        <td><span data-ttu-id="ad0c3-697">RightBumper</span><span class="sxs-lookup"><span data-stu-id="ad0c3-697">RightBumper</span></span></td>
    </tr>
</table>

### <a name="axis-labels"></a><span data-ttu-id="ad0c3-698">Achsenbeschriftung</span><span class="sxs-lookup"><span data-stu-id="ad0c3-698">Axis labels</span></span>

<span data-ttu-id="ad0c3-699">Der **Achsen**-Schlüssel ordnet jeder der Achsenpositionen des **RawGameControllers** -Achsenarrays zu einer der aufgeführten Beschriftungen der [GameControllerButtonLabel-Enumeration](https://docs.microsoft.com/en-us/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel) hinzu, genau wie die Beschriftungen der Tasten.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-699">The **Axes** key will map each of the axis positions in the **RawGameController**'s axis array to one of the labels listed in [GameControllerButtonLabel Enum](https://docs.microsoft.com/en-us/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel) just like the button labels.</span></span> <span data-ttu-id="ad0c3-700">Sehen Sie das Beispiel unter [Schaltflächenbeschriftungen](#button-labels).</span><span class="sxs-lookup"><span data-stu-id="ad0c3-700">See the example in [Button labels](#button-labels).</span></span>

### <a name="switch-labels"></a><span data-ttu-id="ad0c3-701">Switch-Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="ad0c3-701">Switch labels</span></span>

<span data-ttu-id="ad0c3-702">Der **Switches**-Schlüssel ordnet Switchpositionen Beschriftungen zu.</span><span class="sxs-lookup"><span data-stu-id="ad0c3-702">The **Switches** key maps switch positions to labels.</span></span> <span data-ttu-id="ad0c3-703">Die Werte dieser Namenskonvention sind folgendermaßen: um eine Position eines Switches zu bezeichnen, dessen Index *x* im **RawGameController**-Switcharray ist, fügen Sie folgende Werte unter dem **Switch**-Unterschlüssel hinzu:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-703">The values follow this naming convention: to label a position of a switch, whose index is *x* in the **RawGameController**'s switch array, add these values under the **Switches** subkey:</span></span> 

* <span data-ttu-id="ad0c3-704">SwitchxUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-704">SwitchxUp</span></span> 
* <span data-ttu-id="ad0c3-705">SwitchxUpRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-705">SwitchxUpRight</span></span> 
* <span data-ttu-id="ad0c3-706">SwitchxRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-706">SwitchxRight</span></span>
* <span data-ttu-id="ad0c3-707">SwitchxDownRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-707">SwitchxDownRight</span></span>
* <span data-ttu-id="ad0c3-708">SwitchxDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-708">SwitchxDown</span></span>
* <span data-ttu-id="ad0c3-709">SwitchxDownLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-709">SwitchxDownLeft</span></span>
* <span data-ttu-id="ad0c3-710">SwitchxUpLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-710">SwitchxUpLeft</span></span>
* <span data-ttu-id="ad0c3-711">SwitchxLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-711">SwitchxLeft</span></span>

<span data-ttu-id="ad0c3-712">Die folgende Tabelle zeigt einen Beispielsatz an Bezeichnungen für Switchpositionen eines 4-Weg-Switches an, der auf dem Index 0 im **RawGameController** erscheint:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-712">The following table shows an example set of labels for switch positions of a 4-way switch which shows up at index 0 in the **RawGameController**:</span></span> 

<table>
    <tr>
        <th><span data-ttu-id="ad0c3-713">Name</span><span class="sxs-lookup"><span data-stu-id="ad0c3-713">Name</span></span></th>
        <th><span data-ttu-id="ad0c3-714">Wert (Typ: REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="ad0c3-714">Value (type: REG_SZ)</span></span></th>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-715">Switch0Up</span><span class="sxs-lookup"><span data-stu-id="ad0c3-715">Switch0Up</span></span></td>
        <td><span data-ttu-id="ad0c3-716">XboxUp</span><span class="sxs-lookup"><span data-stu-id="ad0c3-716">XboxUp</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-717">Switch0Right</span><span class="sxs-lookup"><span data-stu-id="ad0c3-717">Switch0Right</span></span></td>
        <td><span data-ttu-id="ad0c3-718">XboxRight</span><span class="sxs-lookup"><span data-stu-id="ad0c3-718">XboxRight</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-719">Switch0Down</span><span class="sxs-lookup"><span data-stu-id="ad0c3-719">Switch0Down</span></span></td>
        <td><span data-ttu-id="ad0c3-720">XboxDown</span><span class="sxs-lookup"><span data-stu-id="ad0c3-720">XboxDown</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ad0c3-721">Switch0Left</span><span class="sxs-lookup"><span data-stu-id="ad0c3-721">Switch0Left</span></span></td>
        <td><span data-ttu-id="ad0c3-722">XboxLeft</span><span class="sxs-lookup"><span data-stu-id="ad0c3-722">XboxLeft</span></span></td>
    </tr>
</table>

<!--### Label strings

* XboxBack
* XboxStart
* XboxMenu
* XboxView
* XboxUp
* XboxDown
* XboxLeft
* XboxRight
* XboxA
* XboxB
* XboxX
* XboxY
* XboxLeftBumper
* XboxLeftTrigger
* XboxLeftStickButton
* XboxRightBumper
* XboxRightTrigger
* XboxRightStickButton
* XboxPaddle1
* XboxPaddle2
* XboxPaddle3
* XboxPaddle4
* Mode
* Select
* Menu
* View
* Back
* Start
* Options
* Share
* Up
* Down
* Left
* Right
* LetterA
* LetterB
* LetterC
* LetterL
* LetterR
* LetterX
* LetterY
* LetterZ
* Cross
* Circle
* Square
* Triangle
* LeftBumper
* LeftTrigger
* LeftStickButton
* Left1
* Left2
* Left3
* RightBumper
* RightTrigger
* RightStickButton
* Right1
* Right2
* Right3
* Paddle1
* Paddle2
* Paddle3
* Paddle4
* Plus
* Minus
* DownLeftArrow
* DialLeft
* DialRight
* Suspension-->

## <a name="example-registry-file"></a><span data-ttu-id="ad0c3-723">Beispiel einer Registrierungsdatei</span><span class="sxs-lookup"><span data-stu-id="ad0c3-723">Example registry file</span></span>

<span data-ttu-id="ad0c3-724">Zur Veranschaulichung, wie diese Zuordnungen und Werte gemeinsam eingesetzt werden, sehen Sie hier eine Registrierung für ein allgemeines **RacingWheel**:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-724">To show how all of these mappings and values come together, here is an example registry file for a generic **RacingWheel**:</span></span>

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004]
"Description" = "Example Wheel Device"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\Labels\Buttons]
"Button0" = "LetterA"
"Button1" = "LetterB"
"Button2" = "LetterX"
"Button3" = "LetterY"
"Button6" = "Menu"
"Button7" = "View"
"Button8" = "RightStickButton"
"Button9" = "LeftStickButton"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\Labels\Switches]
"Switch0Down" = "Down"
"Switch0Left" = "Left"
"Switch0Right" = "Right"
"Switch0Up" = "Up"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel]
"MaxWheelAngle" = dword:000001c2

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Brake]
"AxisIndex" = dword:00000002
"Invert" = dword:00000001

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button1]
"ButtonIndex" = dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button2]
"ButtonIndex" = dword:00000001

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button3]
"ButtonIndex" = dword:00000002

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button4]
"ButtonIndex" = dword:00000003

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button5]
"ButtonIndex" = dword:00000009

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button6]
"ButtonIndex" = dword:00000008

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button7]
"ButtonIndex" = dword:00000007

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Button8]
"ButtonIndex" = dword:00000006

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Clutch]
"AxisIndex" = dword:00000003
"Invert" = dword:00000001

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\DPadDown]
"IncludeAdjacent" = dword:00000001
"SwitchIndex" = dword:00000000
"SwitchPosition" = "Down"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\DPadLeft]
"IncludeAdjacent" = dword:00000001
"SwitchIndex" = dword:00000000
"SwitchPosition" = "Left"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\DPadRight]
"IncludeAdjacent" = dword:00000001
"SwitchIndex" = dword:00000000
"SwitchPosition" = "Right"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\DPadUp]
"IncludeAdjacent" = dword:00000001
"SwitchIndex" = dword:00000000
"SwitchPosition" = "Up"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\FifthGear]
"ButtonIndex" = dword:00000010

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\FirstGear]
"ButtonIndex" = dword:0000000c

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\FourthGear]
"ButtonIndex" = dword:0000000f

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\NextGear]
"ButtonIndex" = dword:00000004

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\PreviousGear]
"ButtonIndex" = dword:00000005

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\ReverseGear]
"ButtonIndex" = dword:0000000b

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\SecondGear]
"ButtonIndex" = dword:0000000d

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\SixthGear]
"ButtonIndex" = dword:00000011

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\ThirdGear]
"ButtonIndex" = dword:0000000e

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Throttle]
"AxisIndex" = dword:00000001
"Invert" = dword:00000001

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GameInput\Devices\1234567800010004\RacingWheel\Wheel]
"AxisIndex" = dword:00000000
"Invert" = dword:00000000
```

## <a name="see-also"></a><span data-ttu-id="ad0c3-725">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="ad0c3-725">See also</span></span>

* [<span data-ttu-id="ad0c3-726">Windows.Gaming.Input Namespace</span><span class="sxs-lookup"><span data-stu-id="ad0c3-726">Windows.Gaming.Input Namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input)
* [<span data-ttu-id="ad0c3-727">Windows.Gaming.Input.Custom Namespace</span><span class="sxs-lookup"><span data-stu-id="ad0c3-727">Windows.Gaming.Input.Custom Namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.custom)
* [<span data-ttu-id="ad0c3-728">INF-Dateien</span><span class="sxs-lookup"><span data-stu-id="ad0c3-728">INF Files</span></span>](https://docs.microsoft.com/windows-hardware/drivers/install/inf-files)