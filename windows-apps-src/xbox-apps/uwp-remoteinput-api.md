---
author: WilliamsJason
title: Geräteportal-Remoteeingabe– API-Referenz
description: Hier erfahren Sie, wie Sie remote Controller-, Tastatur- und Mauseingaben auf einer Xbox senden.
ms.localizationpriority: medium
ms.openlocfilehash: a2217b87d840bc95010e2e1ce47ea72e991e8fa3
ms.sourcegitcommit: c104b653601d9b81cfc8bb6032ca434cff8fe9b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "1921248"
---
# <a name="remote-input-api-reference"></a><span data-ttu-id="c85d9-103">API-Referenz für die Remoteeingabe</span><span class="sxs-lookup"><span data-stu-id="c85d9-103">Remote Input API reference</span></span>   
<span data-ttu-id="c85d9-104">Über diese API können Sie in Echtzeit per Fernzugriff Controller-, Tastatur- und Mauseingaben senden.</span><span class="sxs-lookup"><span data-stu-id="c85d9-104">You can send controller, keyboard, and mouse input in real time remotely via this API.</span></span>

**<span data-ttu-id="c85d9-105">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c85d9-105">Request</span></span>**

<span data-ttu-id="c85d9-106">Methode</span><span class="sxs-lookup"><span data-stu-id="c85d9-106">Method</span></span>      | <span data-ttu-id="c85d9-107">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c85d9-107">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c85d9-108">Websocket</span><span class="sxs-lookup"><span data-stu-id="c85d9-108">Websocket</span></span> | <span data-ttu-id="c85d9-109">/ext/remoteinput</span><span class="sxs-lookup"><span data-stu-id="c85d9-109">/ext/remoteinput</span></span>
<br />
**<span data-ttu-id="c85d9-110">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c85d9-110">URI parameters</span></span>**

- <span data-ttu-id="c85d9-111">Keine</span><span class="sxs-lookup"><span data-stu-id="c85d9-111">None</span></span>

**<span data-ttu-id="c85d9-112">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c85d9-112">Request headers</span></span>**

- <span data-ttu-id="c85d9-113">Keiner</span><span class="sxs-lookup"><span data-stu-id="c85d9-113">None</span></span>

**<span data-ttu-id="c85d9-114">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c85d9-114">Request</span></span>**

<span data-ttu-id="c85d9-115">Der Websocket, eine Reihe von Byte-Array-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="c85d9-115">The websocket a series of byte array messages.</span></span> <span data-ttu-id="c85d9-116">Für jede Nachricht ist das Format wie folgt.</span><span class="sxs-lookup"><span data-stu-id="c85d9-116">For each message the format is as follows.</span></span>

<span data-ttu-id="c85d9-117">Das erste Byte gibt den Eingabetyp an.</span><span class="sxs-lookup"><span data-stu-id="c85d9-117">The first byte indicates the input type.</span></span> <span data-ttu-id="c85d9-118">Die folgenden Eingabetypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="c85d9-118">The following input types are supported:</span></span>

| <span data-ttu-id="c85d9-119">Eingabetyp</span><span class="sxs-lookup"><span data-stu-id="c85d9-119">Input Type</span></span>        | <span data-ttu-id="c85d9-120">Byte-Wert</span><span class="sxs-lookup"><span data-stu-id="c85d9-120">Byte Value</span></span> |
|------------|-------------|
<span data-ttu-id="c85d9-121">Tastencodes der Tastatur</span><span class="sxs-lookup"><span data-stu-id="c85d9-121">Keyboard KeyCodes</span></span> | <span data-ttu-id="c85d9-122">0x01</span><span class="sxs-lookup"><span data-stu-id="c85d9-122">0x01</span></span>
<span data-ttu-id="c85d9-123">ScanCodes der Tastatur</span><span class="sxs-lookup"><span data-stu-id="c85d9-123">Keyboard ScanCodes</span></span> | <span data-ttu-id="c85d9-124">0x02</span><span class="sxs-lookup"><span data-stu-id="c85d9-124">0x02</span></span>
<span data-ttu-id="c85d9-125">Maus</span><span class="sxs-lookup"><span data-stu-id="c85d9-125">Mouse</span></span> | <span data-ttu-id="c85d9-126">0x03</span><span class="sxs-lookup"><span data-stu-id="c85d9-126">0x03</span></span>
<span data-ttu-id="c85d9-127">Alle aufheben</span><span class="sxs-lookup"><span data-stu-id="c85d9-127">Clear All</span></span> | <span data-ttu-id="c85d9-128">0x04</span><span class="sxs-lookup"><span data-stu-id="c85d9-128">0x04</span></span>

<span data-ttu-id="c85d9-129">Für KeyboardKeyCodes und KeyboardScanCodes ist das zweite Byte der Wert des Tastencodes oder Scancodes und das dritte Byte ist 0x01 für das Drücken der Taste und 0x00 für das Loslassen der Taste.</span><span class="sxs-lookup"><span data-stu-id="c85d9-129">For KeyboardKeyCodes and KeyboardScanCodes, the second byte is the value of the keycode or scancode and the third byte is 0x01 for a down press and 0x00 for a release.</span></span>

<span data-ttu-id="c85d9-130">Für eine Mausmeldung ist der nächste Wert ein UINT16 in der Netzwerkreihenfolge (2 Byte), der den Typ des Mausereignisses angibt:</span><span class="sxs-lookup"><span data-stu-id="c85d9-130">For a Mouse message, the next value is a UINT16 in network order (2 bytes) indicating the type of mouse event:</span></span>

| <span data-ttu-id="c85d9-131">Aktionstyp</span><span class="sxs-lookup"><span data-stu-id="c85d9-131">Action Type</span></span>        | <span data-ttu-id="c85d9-132">UINT16-Wert</span><span class="sxs-lookup"><span data-stu-id="c85d9-132">UINT16 Value</span></span> |
|------------|-------------|
<span data-ttu-id="c85d9-133">Move</span><span class="sxs-lookup"><span data-stu-id="c85d9-133">Move</span></span> | <span data-ttu-id="c85d9-134">0x0001</span><span class="sxs-lookup"><span data-stu-id="c85d9-134">0x0001</span></span>
<span data-ttu-id="c85d9-135">LeftDown</span><span class="sxs-lookup"><span data-stu-id="c85d9-135">LeftDown</span></span> | <span data-ttu-id="c85d9-136">0x0002</span><span class="sxs-lookup"><span data-stu-id="c85d9-136">0x0002</span></span>
<span data-ttu-id="c85d9-137">LeftUp</span><span class="sxs-lookup"><span data-stu-id="c85d9-137">LeftUp</span></span> | <span data-ttu-id="c85d9-138">0x0004</span><span class="sxs-lookup"><span data-stu-id="c85d9-138">0x0004</span></span>
<span data-ttu-id="c85d9-139">RightDown</span><span class="sxs-lookup"><span data-stu-id="c85d9-139">RightDown</span></span> | <span data-ttu-id="c85d9-140">0x0008</span><span class="sxs-lookup"><span data-stu-id="c85d9-140">0x0008</span></span>
<span data-ttu-id="c85d9-141">RightUp</span><span class="sxs-lookup"><span data-stu-id="c85d9-141">RightUp</span></span> | <span data-ttu-id="c85d9-142">0x0010</span><span class="sxs-lookup"><span data-stu-id="c85d9-142">0x0010</span></span>
<span data-ttu-id="c85d9-143">MiddleDown</span><span class="sxs-lookup"><span data-stu-id="c85d9-143">MiddleDown</span></span> | <span data-ttu-id="c85d9-144">0x0020</span><span class="sxs-lookup"><span data-stu-id="c85d9-144">0x0020</span></span>
<span data-ttu-id="c85d9-145">MiddleUp</span><span class="sxs-lookup"><span data-stu-id="c85d9-145">MiddleUp</span></span> | <span data-ttu-id="c85d9-146">0x0040</span><span class="sxs-lookup"><span data-stu-id="c85d9-146">0x0040</span></span>
<span data-ttu-id="c85d9-147">X1Down</span><span class="sxs-lookup"><span data-stu-id="c85d9-147">X1Down</span></span> | <span data-ttu-id="c85d9-148">0x0080</span><span class="sxs-lookup"><span data-stu-id="c85d9-148">0x0080</span></span>
<span data-ttu-id="c85d9-149">X1Up</span><span class="sxs-lookup"><span data-stu-id="c85d9-149">X1Up</span></span> | <span data-ttu-id="c85d9-150">0x0100</span><span class="sxs-lookup"><span data-stu-id="c85d9-150">0x0100</span></span>
<span data-ttu-id="c85d9-151">X2Down</span><span class="sxs-lookup"><span data-stu-id="c85d9-151">X2Down</span></span> | <span data-ttu-id="c85d9-152">0x0200</span><span class="sxs-lookup"><span data-stu-id="c85d9-152">0x0200</span></span>
<span data-ttu-id="c85d9-153">X2Up</span><span class="sxs-lookup"><span data-stu-id="c85d9-153">X2Up</span></span> | <span data-ttu-id="c85d9-154">0x0400</span><span class="sxs-lookup"><span data-stu-id="c85d9-154">0x0400</span></span>
<span data-ttu-id="c85d9-155">VerticalWheelMoved</span><span class="sxs-lookup"><span data-stu-id="c85d9-155">VerticalWheelMoved</span></span> | <span data-ttu-id="c85d9-156">0x0800</span><span class="sxs-lookup"><span data-stu-id="c85d9-156">0x0800</span></span>
<span data-ttu-id="c85d9-157">HorizontalWheelMoved</span><span class="sxs-lookup"><span data-stu-id="c85d9-157">HorizontalWheelMoved</span></span> | <span data-ttu-id="c85d9-158">0x1000</span><span class="sxs-lookup"><span data-stu-id="c85d9-158">0x1000</span></span>

<span data-ttu-id="c85d9-159">Nach diesem Byte folgen zwei UINT32-Werte in der Netzwerkreihenfolge und ein optionaler dritter UINT32 für Radaktionen.</span><span class="sxs-lookup"><span data-stu-id="c85d9-159">This byte is followed by two UINT32 values in network order, and an optional third UINT32 for wheel actions.</span></span> <span data-ttu-id="c85d9-160">Die ersten beiden Werte sind die X- und Y-Koordinaten und der dritte ist der Deltawert für das Mausrad.</span><span class="sxs-lookup"><span data-stu-id="c85d9-160">The first two values are the X and Y coordinate and the third is the wheel delta.</span></span> <span data-ttu-id="c85d9-161">Die X- und Y-Koordinaten sollten erwartungsgemäß einen Wert zwischen 0 und 65535 haben, der jeweils die relative Position der Maus auf der horizontalen und vertikalen Ebene angibt.</span><span class="sxs-lookup"><span data-stu-id="c85d9-161">The X and Y coordinates are expected to be a value between 0 and 65535 indicating the relative position of the mouse in the horizontal and vertical planes.</span></span>

<span data-ttu-id="c85d9-162">ClearAll gibt an, dass alle derzeit gedrückten Tasten losgelassen werden sollten.</span><span class="sxs-lookup"><span data-stu-id="c85d9-162">ClearAll indicates any currently held down keys should be released.</span></span> <span data-ttu-id="c85d9-163">Es werden keine anderen Bytes erwartet.</span><span class="sxs-lookup"><span data-stu-id="c85d9-163">No other bytes are expected.</span></span>

<span data-ttu-id="c85d9-164">Um Gamepad-Eingaben zu senden, können die Tastencodewerte, die Gamepad-Tastendrücke darstellen, mit KeyboardKeyCodes verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c85d9-164">For sending Gamepad input, the keycode values which represent Gamepad button presses can be used with KeyboardKeyCodes.</span></span> <span data-ttu-id="c85d9-165">Diese Werte sind:</span><span class="sxs-lookup"><span data-stu-id="c85d9-165">Those values are as follows:</span></span>

| <span data-ttu-id="c85d9-166">Gamepad-Typ</span><span class="sxs-lookup"><span data-stu-id="c85d9-166">Gamepad Type</span></span>        | <span data-ttu-id="c85d9-167">Byte-Wert</span><span class="sxs-lookup"><span data-stu-id="c85d9-167">Byte Value</span></span> |
|------------|-------------|
<span data-ttu-id="c85d9-168">VK_GAMEPAD_A</span><span class="sxs-lookup"><span data-stu-id="c85d9-168">VK_GAMEPAD_A</span></span>                       |  <span data-ttu-id="c85d9-169">0xC3</span><span class="sxs-lookup"><span data-stu-id="c85d9-169">0xC3</span></span>
<span data-ttu-id="c85d9-170">VK_GAMEPAD_B</span><span class="sxs-lookup"><span data-stu-id="c85d9-170">VK_GAMEPAD_B</span></span>                       |  <span data-ttu-id="c85d9-171">0xC4</span><span class="sxs-lookup"><span data-stu-id="c85d9-171">0xC4</span></span>
<span data-ttu-id="c85d9-172">VK_GAMEPAD_X</span><span class="sxs-lookup"><span data-stu-id="c85d9-172">VK_GAMEPAD_X</span></span>                       |  <span data-ttu-id="c85d9-173">0xC5</span><span class="sxs-lookup"><span data-stu-id="c85d9-173">0xC5</span></span>
<span data-ttu-id="c85d9-174">VK_GAMEPAD_Y</span><span class="sxs-lookup"><span data-stu-id="c85d9-174">VK_GAMEPAD_Y</span></span>                       |  <span data-ttu-id="c85d9-175">0xC6</span><span class="sxs-lookup"><span data-stu-id="c85d9-175">0xC6</span></span>
<span data-ttu-id="c85d9-176">VK_GAMEPAD_RIGHT_SHOULDER</span><span class="sxs-lookup"><span data-stu-id="c85d9-176">VK_GAMEPAD_RIGHT_SHOULDER</span></span>          |  <span data-ttu-id="c85d9-177">0xC7</span><span class="sxs-lookup"><span data-stu-id="c85d9-177">0xC7</span></span>
<span data-ttu-id="c85d9-178">VK_GAMEPAD_LEFT_SHOULDER</span><span class="sxs-lookup"><span data-stu-id="c85d9-178">VK_GAMEPAD_LEFT_SHOULDER</span></span>           |  <span data-ttu-id="c85d9-179">0xC8</span><span class="sxs-lookup"><span data-stu-id="c85d9-179">0xC8</span></span>
<span data-ttu-id="c85d9-180">VK_GAMEPAD_LEFT_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="c85d9-180">VK_GAMEPAD_LEFT_TRIGGER</span></span>            |  <span data-ttu-id="c85d9-181">0xC9</span><span class="sxs-lookup"><span data-stu-id="c85d9-181">0xC9</span></span>
<span data-ttu-id="c85d9-182">VK_GAMEPAD_RIGHT_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="c85d9-182">VK_GAMEPAD_RIGHT_TRIGGER</span></span>           |  <span data-ttu-id="c85d9-183">0xCA</span><span class="sxs-lookup"><span data-stu-id="c85d9-183">0xCA</span></span>
<span data-ttu-id="c85d9-184">VK_GAMEPAD_DPAD_UP</span><span class="sxs-lookup"><span data-stu-id="c85d9-184">VK_GAMEPAD_DPAD_UP</span></span>                 |  <span data-ttu-id="c85d9-185">0xCB</span><span class="sxs-lookup"><span data-stu-id="c85d9-185">0xCB</span></span>
<span data-ttu-id="c85d9-186">VK_GAMEPAD_DPAD_DOWN</span><span class="sxs-lookup"><span data-stu-id="c85d9-186">VK_GAMEPAD_DPAD_DOWN</span></span>               |  <span data-ttu-id="c85d9-187">0xCC</span><span class="sxs-lookup"><span data-stu-id="c85d9-187">0xCC</span></span>
<span data-ttu-id="c85d9-188">VK_GAMEPAD_DPAD_LEFT</span><span class="sxs-lookup"><span data-stu-id="c85d9-188">VK_GAMEPAD_DPAD_LEFT</span></span>               |  <span data-ttu-id="c85d9-189">0xCD</span><span class="sxs-lookup"><span data-stu-id="c85d9-189">0xCD</span></span>
<span data-ttu-id="c85d9-190">VK_GAMEPAD_DPAD_RIGHT</span><span class="sxs-lookup"><span data-stu-id="c85d9-190">VK_GAMEPAD_DPAD_RIGHT</span></span>              |  <span data-ttu-id="c85d9-191">0xCE</span><span class="sxs-lookup"><span data-stu-id="c85d9-191">0xCE</span></span>
<span data-ttu-id="c85d9-192">VK_GAMEPAD_MENU</span><span class="sxs-lookup"><span data-stu-id="c85d9-192">VK_GAMEPAD_MENU</span></span>                    |  <span data-ttu-id="c85d9-193">0xCF</span><span class="sxs-lookup"><span data-stu-id="c85d9-193">0xCF</span></span>
<span data-ttu-id="c85d9-194">VK_GAMEPAD_VIEW</span><span class="sxs-lookup"><span data-stu-id="c85d9-194">VK_GAMEPAD_VIEW</span></span>                    |  <span data-ttu-id="c85d9-195">0xD0</span><span class="sxs-lookup"><span data-stu-id="c85d9-195">0xD0</span></span>
<span data-ttu-id="c85d9-196">VK_GAMEPAD_LEFT_THUMBSTICK_BUTTON</span><span class="sxs-lookup"><span data-stu-id="c85d9-196">VK_GAMEPAD_LEFT_THUMBSTICK_BUTTON</span></span>  |  <span data-ttu-id="c85d9-197">0xD1</span><span class="sxs-lookup"><span data-stu-id="c85d9-197">0xD1</span></span>
<span data-ttu-id="c85d9-198">VK_GAMEPAD_RIGHT_THUMBSTICK_BUTTON</span><span class="sxs-lookup"><span data-stu-id="c85d9-198">VK_GAMEPAD_RIGHT_THUMBSTICK_BUTTON</span></span> |  <span data-ttu-id="c85d9-199">0xD2</span><span class="sxs-lookup"><span data-stu-id="c85d9-199">0xD2</span></span>
<span data-ttu-id="c85d9-200">VK_GAMEPAD_LEFT_THUMBSTICK_UP</span><span class="sxs-lookup"><span data-stu-id="c85d9-200">VK_GAMEPAD_LEFT_THUMBSTICK_UP</span></span>      |  <span data-ttu-id="c85d9-201">0xD3</span><span class="sxs-lookup"><span data-stu-id="c85d9-201">0xD3</span></span>
<span data-ttu-id="c85d9-202">VK_GAMEPAD_LEFT_THUMBSTICK_DOWN</span><span class="sxs-lookup"><span data-stu-id="c85d9-202">VK_GAMEPAD_LEFT_THUMBSTICK_DOWN</span></span>    |  <span data-ttu-id="c85d9-203">0xD4</span><span class="sxs-lookup"><span data-stu-id="c85d9-203">0xD4</span></span>
<span data-ttu-id="c85d9-204">VK_GAMEPAD_LEFT_THUMBSTICK_RIGHT</span><span class="sxs-lookup"><span data-stu-id="c85d9-204">VK_GAMEPAD_LEFT_THUMBSTICK_RIGHT</span></span>   |  <span data-ttu-id="c85d9-205">0xD5</span><span class="sxs-lookup"><span data-stu-id="c85d9-205">0xD5</span></span>
<span data-ttu-id="c85d9-206">VK_GAMEPAD_LEFT_THUMBSTICK_LEFT</span><span class="sxs-lookup"><span data-stu-id="c85d9-206">VK_GAMEPAD_LEFT_THUMBSTICK_LEFT</span></span>    |  <span data-ttu-id="c85d9-207">0xD6</span><span class="sxs-lookup"><span data-stu-id="c85d9-207">0xD6</span></span>
<span data-ttu-id="c85d9-208">VK_GAMEPAD_RIGHT_THUMBSTICK_UP</span><span class="sxs-lookup"><span data-stu-id="c85d9-208">VK_GAMEPAD_RIGHT_THUMBSTICK_UP</span></span>     |  <span data-ttu-id="c85d9-209">0xD7</span><span class="sxs-lookup"><span data-stu-id="c85d9-209">0xD7</span></span>
<span data-ttu-id="c85d9-210">VK_GAMEPAD_RIGHT_THUMBSTICK_DOWN</span><span class="sxs-lookup"><span data-stu-id="c85d9-210">VK_GAMEPAD_RIGHT_THUMBSTICK_DOWN</span></span>   |  <span data-ttu-id="c85d9-211">0xD8</span><span class="sxs-lookup"><span data-stu-id="c85d9-211">0xD8</span></span>
<span data-ttu-id="c85d9-212">VK_GAMEPAD_RIGHT_THUMBSTICK_RIGHT</span><span class="sxs-lookup"><span data-stu-id="c85d9-212">VK_GAMEPAD_RIGHT_THUMBSTICK_RIGHT</span></span>  |  <span data-ttu-id="c85d9-213">0xD9</span><span class="sxs-lookup"><span data-stu-id="c85d9-213">0xD9</span></span>
<span data-ttu-id="c85d9-214">VK_GAMEPAD_RIGHT_THUMBSTICK_LEFT</span><span class="sxs-lookup"><span data-stu-id="c85d9-214">VK_GAMEPAD_RIGHT_THUMBSTICK_LEFT</span></span>   |  <span data-ttu-id="c85d9-215">0xDA</span><span class="sxs-lookup"><span data-stu-id="c85d9-215">0xDA</span></span>


**<span data-ttu-id="c85d9-216">Antwort</span><span class="sxs-lookup"><span data-stu-id="c85d9-216">Response</span></span>**   

- <span data-ttu-id="c85d9-217">Keine</span><span class="sxs-lookup"><span data-stu-id="c85d9-217">None</span></span>

**<span data-ttu-id="c85d9-218">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c85d9-218">Status code</span></span>**

<span data-ttu-id="c85d9-219">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c85d9-219">This API has the following expected status codes.</span></span>

<span data-ttu-id="c85d9-220">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c85d9-220">HTTP status code</span></span>      | <span data-ttu-id="c85d9-221">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c85d9-221">Description</span></span>
:------     | :-----
<span data-ttu-id="c85d9-222">200</span><span class="sxs-lookup"><span data-stu-id="c85d9-222">200</span></span> | <span data-ttu-id="c85d9-223">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c85d9-223">Request was successful</span></span>
<span data-ttu-id="c85d9-224">4XX</span><span class="sxs-lookup"><span data-stu-id="c85d9-224">4XX</span></span> | <span data-ttu-id="c85d9-225">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c85d9-225">Error codes</span></span>
<span data-ttu-id="c85d9-226">5XX</span><span class="sxs-lookup"><span data-stu-id="c85d9-226">5XX</span></span> | <span data-ttu-id="c85d9-227">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c85d9-227">Error codes</span></span>

<br />
**<span data-ttu-id="c85d9-228">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="c85d9-228">Available device families</span></span>**

* <span data-ttu-id="c85d9-229">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="c85d9-229">Windows Xbox</span></span>