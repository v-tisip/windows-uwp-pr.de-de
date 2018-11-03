---
author: JordanRh1
title: Aktivieren des Benutzermoduszugriffs auf GPIO, I2C und SPI
description: In diesem Lernprogramm wird der Benutzermoduszugriff auf GPIO, I2C, SPI und UART auf Windows10 beschrieben.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, ACPI, GPIO, I2C, SPI, UEFI
ms.assetid: 2fbdfc78-3a43-4828-ae55-fd3789da7b34
ms.localizationpriority: medium
ms.openlocfilehash: 09957c19414f586a49a1a2cb9186aa027dc1de07
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5989035"
---
# <a name="enable-usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="6e450-104">Aktivieren des Benutzermoduszugriffs auf GPIO, I2C und SPI</span><span class="sxs-lookup"><span data-stu-id="6e450-104">Enable usermode access to GPIO, I2C, and SPI</span></span>



<span data-ttu-id="6e450-105">Windows 10 enthält neue APIs für den Zugriff auf GPIO, I2C, SPI und UART direkt aus Benutzermodus.</span><span class="sxs-lookup"><span data-stu-id="6e450-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="6e450-106">Platinen für die Entwicklung, z.B. Raspberry Pi 2, zeigen eine Teilmenge dieser Verbindungen, mit denen Benutzer ein grundlegendes Berechnungsmodell mit benutzerdefiniertem Schaltkreis auf eine bestimmte Anwendung erweitern können.</span><span class="sxs-lookup"><span data-stu-id="6e450-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="6e450-107">Diese Low-Level Busse werden in der Regel mit nur einer Teilmenge der GPIO-Pins und -Busse in den Headern für andere wichtige integrierte Funktionen freigegeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-107">These low level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="6e450-108">Um die Systemstabilität zu erhalten, ist es erforderlich, anzugeben, welche Pins und Busse zur Änderung durch Benutzermodusanwendungen sicher sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span> 

<span data-ttu-id="6e450-109">In diesem Dokument wird beschrieben, wie diese Konfiguration in ACPI angegeben wird, und es enthält Tools, um zu überprüfen, dass die Konfiguration richtig angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="6e450-109">This document describes how to specify this configuration in ACPI and provides tools to validate that the configuration was specified correctly.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6e450-110">Die Zielgruppe für dieses Dokument sind UEFI- und ACPI-Entwickler.</span><span class="sxs-lookup"><span data-stu-id="6e450-110">The audience for this document is UEFI and ACPI developers.</span></span> <span data-ttu-id="6e450-111">Grundkenntnisse mit ACPI, dem Erstellen von ASL und SpbCx/GpioClx werden angenommen.</span><span class="sxs-lookup"><span data-stu-id="6e450-111">Some familiarity with ACPI, ASL authoring, and SpbCx/GpioClx is assumed.</span></span>

<span data-ttu-id="6e450-112">Benutzermoduszugriff auf Low-Level-Busse unter Windows wird über die vorhandenen `GpioClx`- und `SpbCx`-Frameworks konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="6e450-112">Usermode access to low level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="6e450-113">Ein neuer Treiber namens *RhProxy*, für Windows IoT Core und Windows Enterprise verfügbar, macht die `GpioClx`- und `SpbCx`-Ressourcen für den Benutzermodus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6e450-113">A new driver called *RhProxy*, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="6e450-114">Um die APIs zu aktivieren, muss ein Geräteknoten für rhproxy in Ihren ACPI-Tabellen für die einzelnen GPIO- und SPB-Ressourcen deklariert werden, die für den Benutzermodus verfügbar gemacht werden soll.</span><span class="sxs-lookup"><span data-stu-id="6e450-114">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span> <span data-ttu-id="6e450-115">Dieses Dokument führt Sie durch die Erstellung und Überprüfung von ASL.</span><span class="sxs-lookup"><span data-stu-id="6e450-115">This document walks through authoring and verifying the ASL.</span></span> 


## <a name="asl-by-example"></a><span data-ttu-id="6e450-116">ASL anhand eines Beispiels</span><span class="sxs-lookup"><span data-stu-id="6e450-116">ASL by example</span></span>

<span data-ttu-id="6e450-117">Betrachten wir die rhproxy-Geräteknotendeklaration auf Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="6e450-117">Let’s walk through the rhproxy device node declaration on Raspberry Pi 2.</span></span> <span data-ttu-id="6e450-118">Erstellen Sie zunächst die ACPI-Gerätedeklaration im Bereich \\_SB.</span><span class="sxs-lookup"><span data-stu-id="6e450-118">First, create the ACPI device declaration in the \\_SB scope.</span></span>  

```cpp
Device(RHPX) 
{ 
    Name(_HID, "MSFT8000") 
    Name(_CID, "MSFT8000") 
    Name(_UID, 1) 
    
```

* <span data-ttu-id="6e450-119">_HID – Hardware Id. Legen Sie hier eine herstellerspezifische Hardware-ID fest.</span><span class="sxs-lookup"><span data-stu-id="6e450-119">_HID – Hardware Id. Set this to a vendor-specific hardware ID.</span></span> 
* <span data-ttu-id="6e450-120">_CID – Compatible Id. Muss “MSFT8000” sein.</span><span class="sxs-lookup"><span data-stu-id="6e450-120">_CID – Compatible Id. Must be “MSFT8000”.</span></span>  
* <span data-ttu-id="6e450-121">_UID – Eindeutige ID. Auf 1 festlegen.</span><span class="sxs-lookup"><span data-stu-id="6e450-121">_UID – Unique Id. Set to 1.</span></span>  

<span data-ttu-id="6e450-122">Als Nächstes deklarieren wir alle GPIO- und SPB-Ressourcen, die für den Benutzermodus verfügbar gemacht werden soll.</span><span class="sxs-lookup"><span data-stu-id="6e450-122">Next we declare each of the GPIO and SPB resources that should be exposed to usermode.</span></span> <span data-ttu-id="6e450-123">Die Reihenfolge, in der Ressourcen deklariert werden, ist wichtig, da Ressourcenindizes verwendet werden, um Ressourcen Eigenschaften zuordnen.</span><span class="sxs-lookup"><span data-stu-id="6e450-123">The order in which resources are declared is important because resource indexes are used to associate properties with resources.</span></span> <span data-ttu-id="6e450-124">Sind mehrere I2C- oder SPI-Busse verfügbar gemacht, gilt der erste deklarierte Bus als „Standard“-Bus für diesen Typ und ist die Instanz, die durch die `GetDefaultAsync()`-Methoden der [Windows.Devices.I2c.I2cController](https://msdn.microsoft.com/library/windows/apps/windows.devices.i2c.i2ccontroller.aspx) und [Windows.Devices.Spi.SpiController](https://msdn.microsoft.com/library/windows/apps/windows.devices.spi.spicontroller.aspx) zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-124">If there are multiple I2C or SPI busses exposed, the first declared bus is considered the ‘default’ bus for that type, and will be the instance returned by the `GetDefaultAsync()` methods of [Windows.Devices.I2c.I2cController](https://msdn.microsoft.com/library/windows/apps/windows.devices.i2c.i2ccontroller.aspx) and [Windows.Devices.Spi.SpiController](https://msdn.microsoft.com/library/windows/apps/windows.devices.spi.spicontroller.aspx).</span></span> 

### <a name="spi"></a><span data-ttu-id="6e450-125">SPI</span><span class="sxs-lookup"><span data-stu-id="6e450-125">SPI</span></span> 

<span data-ttu-id="6e450-126">Raspberry Pi verfügt über zwei verfügbar gemachte SPI-Busse.</span><span class="sxs-lookup"><span data-stu-id="6e450-126">Raspberry Pi has two exposed SPI buses.</span></span> <span data-ttu-id="6e450-127">SPI0 hat zwei Hardware-Chip-Auswahlzeilen und SPI1 verfügt über eine Hardware-Chip-Auswahlzeile.</span><span class="sxs-lookup"><span data-stu-id="6e450-127">SPI0 has two hardware chip select lines and SPI1 has one hardware chip select line.</span></span> <span data-ttu-id="6e450-128">Eine SPISerialBus()-Ressourcendeklaration ist für jede Chip-Auswahlzeile für jeden Bus erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6e450-128">One SPISerialBus() resource declaration is required for each chip select line for each bus.</span></span> <span data-ttu-id="6e450-129">Die folgenden zwei SPISerialBus-Ressourcendeklarationen beziehen sich auf die zwei Chip-Auswahlzeilen in SPI0.</span><span class="sxs-lookup"><span data-stu-id="6e450-129">The following two SPISerialBus resource declarations are for the two chip select lines on SPI0.</span></span> <span data-ttu-id="6e450-130">Das DeviceSelection-Feld enthält einen eindeutigen Wert, das der Treiber als Hardware-Chip-Auswahlzeilenidentifikator interpretiert.</span><span class="sxs-lookup"><span data-stu-id="6e450-130">The DeviceSelection field contains a unique value which the driver interprets as a hardware chip select line identifier.</span></span> <span data-ttu-id="6e450-131">Der genaue Wert, den Sie im DeviceSelection-Feld eingeben, hängt davon ab, wie Ihr Treiber dieses Feld des ACPI-Verbindungsdeskriptors interpretiert.</span><span class="sxs-lookup"><span data-stu-id="6e450-131">The exact value that you put in the DeviceSelection field depends on how your driver interprets this field of the ACPI connection descriptor.</span></span>  

```cpp
// Index 0 
SPISerialBus(              // SCKL - GPIO 11 - Pin 23 
                           // MOSI - GPIO 10 - Pin 19 
                           // MISO - GPIO 9  - Pin 21 
                           // CE0  - GPIO 8  - Pin 24 
    0,                     // Device selection (CE0) 
    PolarityLow,           // Device selection polarity 
    FourWireMode,          // wiremode 
    0,                     // databit len: placeholder 
    ControllerInitiated,   // slave mode 
    0,                     // connection speed: placeholder 
    ClockPolarityLow,      // clock polarity: placeholder 
    ClockPhaseFirst,       // clock phase: placeholder 
    "\\_SB.SPI0",          // ResourceSource: SPI bus controller name 
    0,                     // ResourceSourceIndex 
                           // Resource usage 
    )                      // Vendor Data 

// Index 1 
SPISerialBus(              // SCKL - GPIO 11 - Pin 23 
                           // MOSI - GPIO 10 - Pin 19 
                           // MISO - GPIO 9  - Pin 21 
                           // CE1  - GPIO 7  - Pin 26 
    1,                     // Device selection (CE1) 
    PolarityLow,           // Device selection polarity 
    FourWireMode,          // wiremode 
    0,                     // databit len: placeholder 
    ControllerInitiated,   // slave mode 
    0,                     // connection speed: placeholder 
    ClockPolarityLow,      // clock polarity: placeholder 
    ClockPhaseFirst,       // clock phase: placeholder 
    "\\_SB.SPI0",          // ResourceSource: SPI bus controller name 
    0,                     // ResourceSourceIndex 
                           // Resource usage 
    )                      // Vendor Data 

```

<span data-ttu-id="6e450-132">Woher weiß Software, dass diese beiden Ressourcen demselben Bus zugeordnet werden sollen?</span><span class="sxs-lookup"><span data-stu-id="6e450-132">How does software know that these two resources should be associated with the same bus?</span></span> <span data-ttu-id="6e450-133">Die Zuordnung zwischen Bus-Anzeigenamen und Ressourcenindex wird in der DSD angegeben:</span><span class="sxs-lookup"><span data-stu-id="6e450-133">The mapping between bus friendly name and resource index is specified in the DSD:</span></span>  

```cpp
Package(2) { "bus-SPI-SPI0", Package() { 0, 1 }}, 
```

<span data-ttu-id="6e450-134">Dadurch wird einen Bus mit dem Namen „SPI0“ und zwei Chip-Auswahlzeilen erstellt – Ressourcenindizes 0 und 1.</span><span class="sxs-lookup"><span data-stu-id="6e450-134">This creates a bus named “SPI0” with two chip select lines – resource indexes 0 and 1.</span></span> <span data-ttu-id="6e450-135">Einige weitere Eigenschaften sind erforderlich, um die SPI-Bus-Funktionen zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-135">Several more properties are required to declare the capabilities of the SPI bus.</span></span>  

```cpp
Package(2) { "SPI0-MinClockInHz", 7629 }, 
Package(2) { "SPI0-MaxClockInHz", 125000000 },
```

<span data-ttu-id="6e450-136">Die **MinClockInHz**- und **MaxClockInHz**-Eigenschaften geben die minimalen und maximalen Taktfrequenzen an, die vom Controller unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-136">The **MinClockInHz** and **MaxClockInHz** properties specify the minimum and maximum clock speeds that are supported by the controller.</span></span> <span data-ttu-id="6e450-137">Die API verhindert, dass Benutzer Werte außerhalb dieses Bereichs angeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-137">The API will prevent users from specifying values outside this range.</span></span> <span data-ttu-id="6e450-138">Die Taktfrequenz wird an Ihren SPB-Treiber im _SPE-Feld der Verbindungsbeschreibung (ACPI-Abschnitt 6.4.3.8.2.2) übergeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-138">The clock speed is passed to your SPB driver in the _SPE field of the connection descriptor (ACPI section 6.4.3.8.2.2).</span></span>  

```cpp
Package(2) { "SPI0-SupportedDataBitLengths", Package() { 8 }}, 
```

<span data-ttu-id="6e450-139">Die **SupportedDataBitLengths**-Eigenschaft listet die Datenbitlängen auf, die vom Controller unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-139">The **SupportedDataBitLengths** property lists the data bit lengths supported by the controller.</span></span> <span data-ttu-id="6e450-140">Mehrere Werte können in einer kommagetrennten Liste angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-140">Multiple values can be specified in a comma-separated list.</span></span> <span data-ttu-id="6e450-141">Die API verhindert, dass Benutzer Werte außerhalb dieser Liste angeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-141">The API will prevent users from specifying values outside this list.</span></span> <span data-ttu-id="6e450-142">Die Datenbitlänge wird an Ihren SPB-Treiber im _LEN-Feld der Verbindungsbeschreibung (ACPI Abschnitt 6.4.3.8.2.2) übergeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-142">The data bit length is passed to your SPB driver in the _LEN field of the connection descriptor (ACPI section 6.4.3.8.2.2).</span></span>  

<span data-ttu-id="6e450-143">Sie können sich diese Ressourcedeklarationen als „Vorlagen“ vorstellen.</span><span class="sxs-lookup"><span data-stu-id="6e450-143">You can think of these resource declarations as “templates.”</span></span> <span data-ttu-id="6e450-144">Einige der Felder werden beim Systemstart behoben, während andere dynamisch zur Laufzeit angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-144">Some of the fields are fixed at system boot while others are specified dynamically at runtime.</span></span> <span data-ttu-id="6e450-145">Die folgenden Felder der SPISerialBus-Beschreibung werden korrigiert:</span><span class="sxs-lookup"><span data-stu-id="6e450-145">The following fields of the SPISerialBus descriptor are fixed:</span></span> 

* <span data-ttu-id="6e450-146">DeviceSelection</span><span class="sxs-lookup"><span data-stu-id="6e450-146">DeviceSelection</span></span> 
* <span data-ttu-id="6e450-147">DeviceSelectionPolarity</span><span class="sxs-lookup"><span data-stu-id="6e450-147">DeviceSelectionPolarity</span></span> 
* <span data-ttu-id="6e450-148">WireMode</span><span class="sxs-lookup"><span data-stu-id="6e450-148">WireMode</span></span> 
* <span data-ttu-id="6e450-149">SlaveMode</span><span class="sxs-lookup"><span data-stu-id="6e450-149">SlaveMode</span></span> 
* <span data-ttu-id="6e450-150">ResourceSource</span><span class="sxs-lookup"><span data-stu-id="6e450-150">ResourceSource</span></span> 

<span data-ttu-id="6e450-151">Die folgenden Felder sind Platzhalter für Werte, die vom Benutzer zur Laufzeit angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-151">The following fields are placeholders for values specified by the user at runtime:</span></span> 

* <span data-ttu-id="6e450-152">DataBitLength</span><span class="sxs-lookup"><span data-stu-id="6e450-152">DataBitLength</span></span> 
* <span data-ttu-id="6e450-153">ConnectionSpeed</span><span class="sxs-lookup"><span data-stu-id="6e450-153">ConnectionSpeed</span></span> 
* <span data-ttu-id="6e450-154">ClockPolarity</span><span class="sxs-lookup"><span data-stu-id="6e450-154">ClockPolarity</span></span> 
* <span data-ttu-id="6e450-155">ClockPhase</span><span class="sxs-lookup"><span data-stu-id="6e450-155">ClockPhase</span></span> 

<span data-ttu-id="6e450-156">Da SPI1 nur ein Chip-Auswahlzeile enthält, wird eine einzelne `SPISerialBus()`-Ressource deklariert:</span><span class="sxs-lookup"><span data-stu-id="6e450-156">Since SPI1 contains only a single chip select line, a single `SPISerialBus()` resource is declared:</span></span> 

```cpp
// Index 2 

SPISerialBus(              // SCKL - GPIO 21 - Pin 40 
                           // MOSI - GPIO 20 - Pin 38 
                           // MISO - GPIO 19 - Pin 35 
                           // CE1  - GPIO 17 - Pin 11 
    1,                     // Device selection (CE1) 
    PolarityLow,           // Device selection polarity 
    FourWireMode,          // wiremode 
    0,                     // databit len: placeholder 
    ControllerInitiated,   // slave mode 
    0,                     // connection speed: placeholder 
    ClockPolarityLow,      // clock polarity: placeholder 
    ClockPhaseFirst,       // clock phase: placeholder 
    "\\_SB.SPI1",          // ResourceSource: SPI bus controller name 
    0,                     // ResourceSourceIndex 
                           // Resource usage 
    )                      // Vendor Data 

```

<span data-ttu-id="6e450-157">Die zugehörigen Anzeigenamendeklaration – die erforderlich ist – wird in der DSD angegeben und verweist auf den Index dieser Ressourcendeklaration.</span><span class="sxs-lookup"><span data-stu-id="6e450-157">The accompanying friendly name declaration – which is required – is specified in the DSD and refers to the index of this resource declaration.</span></span> 

```cpp
Package(2) { "bus-SPI-SPI1", Package() { 2 }}, 
```

<span data-ttu-id="6e450-158">Dadurch wird ein Bus mit dem Namen „SPI1“ erstellt und dem Ressourcenindex 2 zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="6e450-158">This creates a bus named “SPI1” and associates it with resource index 2.</span></span>  

#### <a name="spi-driver-requirements"></a><span data-ttu-id="6e450-159">SPI-Treiberanforderungen</span><span class="sxs-lookup"><span data-stu-id="6e450-159">SPI Driver Requirements</span></span> 

* <span data-ttu-id="6e450-160">Muss `SpbCx` verwenden oder SpbCx-kompatibel sein</span><span class="sxs-lookup"><span data-stu-id="6e450-160">Must use `SpbCx` or be SpbCx-compatible</span></span> 
* <span data-ttu-id="6e450-161">Muss die [MITT SPI-Tests](https://msdn.microsoft.com/library/windows/hardware/dn919873.aspx) bestanden haben</span><span class="sxs-lookup"><span data-stu-id="6e450-161">Must have passed the [MITT SPI Tests](https://msdn.microsoft.com/library/windows/hardware/dn919873.aspx)</span></span>
* <span data-ttu-id="6e450-162">Muss eine Taktfrequenz von 4Mhz unterstützen</span><span class="sxs-lookup"><span data-stu-id="6e450-162">Must support 4Mhz clock speed</span></span> 
* <span data-ttu-id="6e450-163">Muss 8-Bit-Datenlänge unterstützen</span><span class="sxs-lookup"><span data-stu-id="6e450-163">Must support 8-bit data length</span></span> 
* <span data-ttu-id="6e450-164">Muss alle SPI-Modi unterstützen: 0, 1, 2, 3</span><span class="sxs-lookup"><span data-stu-id="6e450-164">Must support all SPI Modes: 0, 1, 2, 3</span></span> 

### <a name="i2c"></a><span data-ttu-id="6e450-165">I2C</span><span class="sxs-lookup"><span data-stu-id="6e450-165">I2C</span></span> 

<span data-ttu-id="6e450-166">Als Nächstes deklarieren wir die I2C-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="6e450-166">Next, we declare the I2C resources.</span></span> <span data-ttu-id="6e450-167">Raspberry Pi macht einen einzelnen I2C-Bus auf den Pins 3 und 5 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6e450-167">Raspberry Pi exposes a single I2C bus on pins 3 and 5.</span></span> 

```cpp
// Index 3 
I2CSerialBus(              // Pin 3 (GPIO2, SDA1), 5 (GPIO3, SCL1) 
    0xFFFF,                // SlaveAddress: placeholder 
    ,                      // SlaveMode: default to ControllerInitiated 
    0,                     // ConnectionSpeed: placeholder 
    ,                      // Addressing Mode: placeholder 
    "\\_SB.I2C1",          // ResourceSource: I2C bus controller name 
    , 
    , 
    )                      // VendorData 

```

<span data-ttu-id="6e450-168">Die zugehörige Anzeigenamendeklaration – die erforderlich ist – wird in der DSD angegeben:</span><span class="sxs-lookup"><span data-stu-id="6e450-168">The accompanying friendly name declaration – which is required – is specified in the DSD:</span></span> 

```cpp
Package(2) { "bus-I2C-I2C1", Package() { 3 }}, 
```

<span data-ttu-id="6e450-169">Dadurch wird ein I2C-Bus mit Anzeigenamen „I2C1“ deklariert, der sich auf Ressourcenindex 3 bezieht, der der Index der I2CSerialBus()-Ressource ist, die wir soeben deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="6e450-169">This declares an I2C bus with friendly name “I2C1” that refers to resource index 3, which is the index of the I2CSerialBus() resource that we declared above.</span></span> 

<span data-ttu-id="6e450-170">Die folgenden Felder der I2CSerialBus()-Beschreibung werden korrigiert:</span><span class="sxs-lookup"><span data-stu-id="6e450-170">The following fields of the I2CSerialBus() descriptor are fixed:</span></span> 

* <span data-ttu-id="6e450-171">SlaveMode</span><span class="sxs-lookup"><span data-stu-id="6e450-171">SlaveMode</span></span> 
* <span data-ttu-id="6e450-172">ResourceSource</span><span class="sxs-lookup"><span data-stu-id="6e450-172">ResourceSource</span></span> 

<span data-ttu-id="6e450-173">Die folgenden Felder sind Platzhalter für Werte, die vom Benutzer zur Laufzeit angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-173">The following fields are placeholders for values specified by the user at runtime.</span></span> 

* <span data-ttu-id="6e450-174">SlaveAddress</span><span class="sxs-lookup"><span data-stu-id="6e450-174">SlaveAddress</span></span> 
* <span data-ttu-id="6e450-175">ConnectionSpeed</span><span class="sxs-lookup"><span data-stu-id="6e450-175">ConnectionSpeed</span></span> 
* <span data-ttu-id="6e450-176">AddressingMode</span><span class="sxs-lookup"><span data-stu-id="6e450-176">AddressingMode</span></span> 

#### <a name="i2c-driver-requirements"></a><span data-ttu-id="6e450-177">I2C-Treiberanforderungen</span><span class="sxs-lookup"><span data-stu-id="6e450-177">I2C Driver Requirements</span></span> 

* <span data-ttu-id="6e450-178">Muss SpbCx verwenden oder SpbCx-kompatibel sein</span><span class="sxs-lookup"><span data-stu-id="6e450-178">Must use SpbCx or be SpbCx-compatible</span></span> 
* <span data-ttu-id="6e450-179">Muss die [MITT I2C-Tests](https://msdn.microsoft.com/library/windows/hardware/dn919852.aspx) bestanden haben</span><span class="sxs-lookup"><span data-stu-id="6e450-179">Must have passed the [MITT I2C Tests](https://msdn.microsoft.com/library/windows/hardware/dn919852.aspx)</span></span> 
* <span data-ttu-id="6e450-180">Muss 7-Bit-Adressierung unterstützen</span><span class="sxs-lookup"><span data-stu-id="6e450-180">Must support 7-bit addressing</span></span> 
* <span data-ttu-id="6e450-181">Muss 100-kHz-Taktfrequenz unterstützen</span><span class="sxs-lookup"><span data-stu-id="6e450-181">Must support 100kHz clock speed</span></span> 
* <span data-ttu-id="6e450-182">Muss 400-kHz-Taktfrequenz unterstützen</span><span class="sxs-lookup"><span data-stu-id="6e450-182">Must support 400kHz clock speed</span></span> 

### <a name="gpio"></a><span data-ttu-id="6e450-183">GPIO</span><span class="sxs-lookup"><span data-stu-id="6e450-183">GPIO</span></span> 

<span data-ttu-id="6e450-184">Als Nächstes deklarieren wir die GPIO-Pins, die für den Benutzermodus verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-184">Next, we declare all the GPIO pins that are exposed to usermode.</span></span> <span data-ttu-id="6e450-185">Wir bieten die folgenden Richtlinien für die Entscheidung an, welche Pins verfügbar gemacht werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-185">We offer the following guidance in deciding which pins to expose:</span></span> 

* <span data-ttu-id="6e450-186">Deklarieren Sie alle Pins in verfügbar gemachten Headern.</span><span class="sxs-lookup"><span data-stu-id="6e450-186">Declare all pins on exposed headers.</span></span> 
* <span data-ttu-id="6e450-187">Deklarieren Sie Pins, die mit integrierten Funktionen wie Schaltflächen und LEDs verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-187">Declare pins that are connected to useful onboard functions like buttons and LEDs.</span></span> 
* <span data-ttu-id="6e450-188">Deklarieren Sie keine Pins, die für Systemfunktionen reserviert sind oder gar nicht verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-188">Do not declare pins that are reserved for system functions or are not connected to anything.</span></span> 

<span data-ttu-id="6e450-189">Im folgenden ASL-Block werden zwei Pins deklariert – GPIO4 und GPIO5.</span><span class="sxs-lookup"><span data-stu-id="6e450-189">The following block of ASL declares two pins – GPIO4 and GPIO5.</span></span> <span data-ttu-id="6e450-190">Die anderen Pins werden aus Platzgründen nicht hier aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="6e450-190">The other pins are not shown here for brevity.</span></span> <span data-ttu-id="6e450-191">AnhangC enthält ein Beispiel für das Powershell-Skript, das verwendet werden kann, um die GPIO-Ressourcen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-191">Appendix C contains a sample powershell script which can be used to generate the GPIO resources.</span></span> 

```cpp
// Index 4 – GPIO 4 
GpioIO(Shared, PullUp, , , , “\\_SB.GPI0”, , , , ) { 4 } 
GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, “\\_SB.GPI0”,) { 4 } 

// Index 6 – GPIO 5 
GpioIO(Shared, PullUp, , , , “\\_SB.GPI0”, , , , ) { 5 } 
GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, “\\_SB.GPI0”,) { 5 } 
```

<span data-ttu-id="6e450-192">Bei der Deklaration von GPIO-Pins müssen die folgenden Anforderungen beachtet werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-192">The following requirements must be observed when declaring GPIO pins:</span></span> 

* <span data-ttu-id="6e450-193">Nur im Speicher abgebildete GPIO-Controller werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e450-193">Only memory mapped GPIO controllers are supported.</span></span> <span data-ttu-id="6e450-194">Über I2C/SPIGPIO verbundene Controller werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e450-194">GPIO controllers interfaced over I2C/SPI are not supported.</span></span> <span data-ttu-id="6e450-195">Der Treiber für den Controller ist ein im Speicher abgebildeter Controller, wenn mit ihm das [MemoryMappedController](https://msdn.microsoft.com/library/windows/hardware/hh439449.aspx)-Flag in der Struktur [CLIENT_CONTROLLER_BASIC_INFORMATION](https://msdn.microsoft.com/library/windows/hardware/hh439358.aspx) als Antwort auf den [CLIENT_QueryControllerBasicInformation](https://msdn.microsoft.com/library/windows/hardware/hh439399.aspx)-Rückruf festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-195">The controller driver is a memory mapped controller if it sets the [MemoryMappedController](https://msdn.microsoft.com/library/windows/hardware/hh439449.aspx) flag in the [CLIENT_CONTROLLER_BASIC_INFORMATION](https://msdn.microsoft.com/library/windows/hardware/hh439358.aspx) structure in response to the [CLIENT_QueryControllerBasicInformation](https://msdn.microsoft.com/library/windows/hardware/hh439399.aspx) callback.</span></span> 
* <span data-ttu-id="6e450-196">Jeder Pin erfordert eine GpioIO- und eine GpioInt-Ressource.</span><span class="sxs-lookup"><span data-stu-id="6e450-196">Each pin requires both a GpioIO and a GpioInt resource.</span></span> <span data-ttu-id="6e450-197">Die GpioInt-Ressource muss direkt auf die GpioIO-Ressource folgen und muss auf dieselbe Pinnummer verweisen.</span><span class="sxs-lookup"><span data-stu-id="6e450-197">The GpioInt resource must immediately follow the GpioIO resource and must refer to the same pin number.</span></span> 
* <span data-ttu-id="6e450-198">GPIO-Ressourcen müssen nach aufsteigender Pinnummer geordnet werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-198">GPIO resources must be ordered by increasing pin number.</span></span> 
* <span data-ttu-id="6e450-199">Jede GpioIO- und GpioInt-Ressource muss genau eine Pinnummer in der Pinliste enthalten.</span><span class="sxs-lookup"><span data-stu-id="6e450-199">Each GpioIO and GpioInt resource must contain exactly one pin number in the pin list.</span></span> 
* <span data-ttu-id="6e450-200">Das ShareType-Feld der beiden Beschreibungen muss „Shared“ sein</span><span class="sxs-lookup"><span data-stu-id="6e450-200">The ShareType field of both descriptors must be Shared</span></span> 
* <span data-ttu-id="6e450-201">Das EdgeLevel-Feld der GpioInt-Beschreibung muss „Edge“ sein</span><span class="sxs-lookup"><span data-stu-id="6e450-201">The EdgeLevel field of the GpioInt descriptor must be Edge</span></span> 
* <span data-ttu-id="6e450-202">Das ActiveLevel-Feld der GpioInt-Beschreibung muss „ActiveBoth“ sein</span><span class="sxs-lookup"><span data-stu-id="6e450-202">The ActiveLevel field of the GpioInt descriptor must be ActiveBoth</span></span> 
* <span data-ttu-id="6e450-203">Das PinConfig-Feld</span><span class="sxs-lookup"><span data-stu-id="6e450-203">The PinConfig field</span></span> 
  * <span data-ttu-id="6e450-204">Muss für die GpioIO- und GpioInt-Beschreibungen identisch sein</span><span class="sxs-lookup"><span data-stu-id="6e450-204">Must be the same in both the GpioIO and GpioInt descriptors</span></span> 
  * <span data-ttu-id="6e450-205">Muss PullUp, PullDown oder PullNone sein.</span><span class="sxs-lookup"><span data-stu-id="6e450-205">Must be one of PullUp, PullDown, or PullNone.</span></span> <span data-ttu-id="6e450-206">Es kann nicht PullDefault sein.</span><span class="sxs-lookup"><span data-stu-id="6e450-206">It cannot be PullDefault.</span></span>
  * <span data-ttu-id="6e450-207">Die Pull-Konfiguration muss mit dem Einschaltzustand des Pins übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="6e450-207">The pull configuration must match the power-on state of the pin.</span></span> <span data-ttu-id="6e450-208">Wenn der Pin in den angegebenen Pull-Modus des Einschaltzustand versetzt wird, darf sich der Zustand des Pins nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="6e450-208">Putting the pin in the specified pull mode from power-on state must not change the state of the pin.</span></span> <span data-ttu-id="6e450-209">Wenn in der Tabelle angegeben ist, dass der Pin mit einem Pull-Up eingeblendet wird, legen Sie PinConfig als PullUp fest.</span><span class="sxs-lookup"><span data-stu-id="6e450-209">For example, if the datasheet specifies that the pin comes up with a pull up, specify PinConfig as PullUp.</span></span>  

<span data-ttu-id="6e450-210">Firmware, UEFI und Treiberinitialisierungscode sollten den Zustand eines Pins nicht entsprechend des Einschaltzustands während des Starts ändern.</span><span class="sxs-lookup"><span data-stu-id="6e450-210">Firmware, UEFI, and driver initialization code should not change the state of a pin from its power-on state during boot.</span></span> <span data-ttu-id="6e450-211">Nur der Benutzer weiß, was mit einer Pin verbunden ist und welche Zustandsübergänge daher sicher sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-211">Only the user knows what’s attached to a pin and therefore which state transitions are safe.</span></span> <span data-ttu-id="6e450-212">Der Einschaltzustand der einzelnen Pins muss dokumentiert werden, damit Benutzer Hardware entwerfen können, die ordnungsgemäß mit einem Pin verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-212">The power-on state of each pin must be documented so that users can design hardware that correctly interfaces with a pin.</span></span> <span data-ttu-id="6e450-213">Ein Pin darf den Zustand nicht unerwartet während des Starts ändern.</span><span class="sxs-lookup"><span data-stu-id="6e450-213">A pin must not change state unexpectedly during boot.</span></span>  

#### <a name="supported-drive-modes"></a><span data-ttu-id="6e450-214">Unterstützte Laufwerkmodi</span><span class="sxs-lookup"><span data-stu-id="6e450-214">Supported Drive Modes</span></span> 

<span data-ttu-id="6e450-215">Wenn Ihr GPIO-Controller integrierte Pull-Up- und Pull-Down-Widerstände zusätzlich zur hohen Impedanzeingabe und CMOS-Ausgabe unterstützt, müssen Sie dies mit der optionalen SupportedDriveModes-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-215">If your GPIO controller supports built-in pull up and pull down resistors in addition to high impedance input and CMOS output, you must specify this with the optional SupportedDriveModes property.</span></span> 

```cpp
Package (2) { “GPIO-SupportedDriveModes”, 0xf }, 
```

<span data-ttu-id="6e450-216">Die SupportedDriveModes-Eigenschaft gibt an, welche Laufwerkmodi vom GPIO-Controller unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-216">The SupportedDriveModes property indicates which drive modes are supported by the GPIO controller.</span></span> <span data-ttu-id="6e450-217">Im obigen Beispiel werden alle der folgenden Laufwerkmodi unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e450-217">In the example above, all of the following drive modes are supported.</span></span> <span data-ttu-id="6e450-218">Die Eigenschaft ist eine Bitmaske der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="6e450-218">The property is a bitmask of the following values:</span></span> 

| <span data-ttu-id="6e450-219">Flagwert</span><span class="sxs-lookup"><span data-stu-id="6e450-219">Flag Value</span></span> | <span data-ttu-id="6e450-220">Laufwerkmodus</span><span class="sxs-lookup"><span data-stu-id="6e450-220">Drive Mode</span></span> | <span data-ttu-id="6e450-221">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e450-221">Description</span></span> |
|------------|------------|-------------|
| <span data-ttu-id="6e450-222">0 x 1</span><span class="sxs-lookup"><span data-stu-id="6e450-222">0x1</span></span>        | <span data-ttu-id="6e450-223">InputHighImpedance</span><span class="sxs-lookup"><span data-stu-id="6e450-223">InputHighImpedance</span></span> | <span data-ttu-id="6e450-224">Der Pin unterstützt eine hohe Impedanzeingabe, die dem Wert „PullNone“ in ACPI entspricht.</span><span class="sxs-lookup"><span data-stu-id="6e450-224">The pin supports high impedance input, which corresponds to the “PullNone” value in ACPI.</span></span> |
| <span data-ttu-id="6e450-225">0 x 2</span><span class="sxs-lookup"><span data-stu-id="6e450-225">0x2</span></span>        | <span data-ttu-id="6e450-226">InputPullUp</span><span class="sxs-lookup"><span data-stu-id="6e450-226">InputPullUp</span></span> | <span data-ttu-id="6e450-227">Der Pin unterstützt einen integrierten Pull-Up-Widerstand, der dem Wert „PullUp“ in ACPI entspricht.</span><span class="sxs-lookup"><span data-stu-id="6e450-227">The pin supports a built-in pull-up resistor, which corresponds to the “PullUp” value in ACPI.</span></span> |
| <span data-ttu-id="6e450-228">0 x 4</span><span class="sxs-lookup"><span data-stu-id="6e450-228">0x4</span></span>        | <span data-ttu-id="6e450-229">InputPullDown</span><span class="sxs-lookup"><span data-stu-id="6e450-229">InputPullDown</span></span> | <span data-ttu-id="6e450-230">Der Pin unterstützt einen integrierten Pull-Down-Widerstand, der dem Wert „PullDown“ in ACPI entspricht.</span><span class="sxs-lookup"><span data-stu-id="6e450-230">The pin supports a built-in pull-down resistor, which corresponds to the “PullDown” value in ACPI.</span></span> |
| <span data-ttu-id="6e450-231">0 x 8</span><span class="sxs-lookup"><span data-stu-id="6e450-231">0x8</span></span>        | <span data-ttu-id="6e450-232">OutputCmos</span><span class="sxs-lookup"><span data-stu-id="6e450-232">OutputCmos</span></span> | <span data-ttu-id="6e450-233">Der Pin unterstützt sowohl die Generierung von starken Höhen als auch die von starken Tiefen (im Gegensatz zu einem offenen Ausgleich).</span><span class="sxs-lookup"><span data-stu-id="6e450-233">The pin supports generating both strong highs and strong lows (as opposed to open drain).</span></span> |

<span data-ttu-id="6e450-234">InputHighImpedance und OutputCmos werden von fast allen GPIO-Controllern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e450-234">InputHighImpedance and OutputCmos are supported by almost all GPIO controllers.</span></span> <span data-ttu-id="6e450-235">Wenn die SupportedDriveModes-Eigenschaft nicht angegeben wird, ist dies die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="6e450-235">If the SupportedDriveModes property is not specified, this is the default.</span></span> 

<span data-ttu-id="6e450-236">Wenn ein GPIO-Signal einen Levelshifter durchläuft, bevor es den verfügbar gemachten Header erreicht, deklarieren Sie die Laufwerkmodi, die vom SOC unterstützt werden, selbst, wenn der Laufwerkmodus nicht auf dem externen Header auszumachen wäre.</span><span class="sxs-lookup"><span data-stu-id="6e450-236">If a GPIO signal goes through a level shifter before reaching an exposed header, declare the drive modes supported by the SOC, even if the drive mode would not be observable on the external header.</span></span> <span data-ttu-id="6e450-237">Wenn ein Pin beispielsweise einen bidirektionalen Levelshifter durchläuft, der aus dem Pin einen offenen Ausgleich mit widerstandsfähigem Pull-Up macht, dann werden Sie niemals einen Zustand hoher Impendanz am verfügbar gemachten Header feststellen, selbst wenn der Pin als Eingabe mit hoher Impendanz konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-237">For example, if a pin goes through a bidirectional level shifter that makes a pin appear as open drain with resistive pull up, you will never observe a high impedance state on the exposed header even if the pin is configured as a high impedance input.</span></span> <span data-ttu-id="6e450-238">Sie sollten noch immer deklarieren, dass der Pin eine Eingabe mit hoher Impendanz unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e450-238">You should still declare that the pin supports high impedance input.</span></span> 

#### <a name="pin-numbering"></a><span data-ttu-id="6e450-239">Pinnummerierung</span><span class="sxs-lookup"><span data-stu-id="6e450-239">Pin Numbering</span></span> 

<span data-ttu-id="6e450-240">Windows unterstützt zwei Schemas für die Pinnummerierung:</span><span class="sxs-lookup"><span data-stu-id="6e450-240">Windows supports two pin numbering schemes:</span></span> 

* <span data-ttu-id="6e450-241">Sequenzielle Pinnummerierung – Benutzer sehen Zahlen wie 0, 1, 2... bis zur Anzahl der verfügbar gemachten Pins.</span><span class="sxs-lookup"><span data-stu-id="6e450-241">Sequential Pin Numbering – Users see numbers like 0, 1, 2... up to the number of exposed pins.</span></span> <span data-ttu-id="6e450-242">0 ist die erste in ASL deklarierte GpioIo-Ressource, 1 ist die zweite in ASL deklarierte GpioIo-Ressource usw.</span><span class="sxs-lookup"><span data-stu-id="6e450-242">0 is the first GpioIo resource declared in ASL, 1 is the second GpioIo resource declared in ASL, and so on.</span></span> 
* <span data-ttu-id="6e450-243">Native Pinnummerierung – Benutzer sehen die Pinnummern in GpioIo-Beschreibungen, z.B. 4, 5, 12, 13, ... .</span><span class="sxs-lookup"><span data-stu-id="6e450-243">Native Pin Numbering – Users see the pin numbers specified in GpioIo descriptors, e.g. 4, 5, 12, 13, ... .</span></span>  

```cpp
Package (2) { “GPIO-UseDescriptorPinNumbers”, 1 }, 
```

<span data-ttu-id="6e450-244">Die **UseDescriptorPinNumbers**-Eigenschaft weist Windows an, die native Pinnummerierung anstelle der sequenziellen Pinnummerierung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-244">The **UseDescriptorPinNumbers** property tells Windows to use native pin numbering instead of sequential pin numbering.</span></span> <span data-ttu-id="6e450-245">Wenn die UseDescriptorPinNumbers-Eigenschaft nicht angegeben wurde oder der Wert 0 (null) ist, verwendet Windows standardmäßig die sequenzielle Pinnummerierung.</span><span class="sxs-lookup"><span data-stu-id="6e450-245">If the UseDescriptorPinNumbers property is not specified or its value is zero, Windows will default to Sequential pin numbering.</span></span> 

<span data-ttu-id="6e450-246">Wenn native Pinnummerierung verwendet wird, müssen Sie auch die **PinCount**-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-246">If native pin numbering is used, you must also specify the **PinCount** property.</span></span> 

```cpp
Package (2) { “GPIO-PinCount”, 54 }, 
```

<span data-ttu-id="6e450-247">Die **PinCount**-Eigenschaft sollte dem durch die **TotalPins**-Eigenschaft beim [CLIENT_QueryControllerBasicInformation](https://msdn.microsoft.com/library/windows/hardware/hh439399.aspx)-Rückruf des `GpioClx`-Treibers zurückgegebenen Wert entsprechen.</span><span class="sxs-lookup"><span data-stu-id="6e450-247">The **PinCount** property should match the value returned through the **TotalPins** property in the [CLIENT_QueryControllerBasicInformation](https://msdn.microsoft.com/library/windows/hardware/hh439399.aspx) callback of the `GpioClx` driver.</span></span> 

<span data-ttu-id="6e450-248">Wählen Sie das Schema für die Nummerierung, das am kompatibelsten mit der veröffentlichten Dokumentation zu Ihrer Platine ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-248">Choose the numbering scheme that is most compatible with existing published documentation for your board.</span></span> <span data-ttu-id="6e450-249">Beispielsweise verwendet Raspberry Pi eine native Pinnummerierung, da viele vorhandene Pinout-Diagramme die BCM2835-Pinnummern verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-249">For example, Raspberry Pi uses native pin numbering because many existing pinout diagrams use the BCM2835 pin numbers.</span></span> <span data-ttu-id="6e450-250">MinnowBoardMax verwendet eine sequenzielle Pinnummerierung, da es einige vorhandene Pinout-Diagramme gibt und die sequenzielle Pinnummerierung Entwicklern die Arbeit erleichtert, da nur 10 von über 200 Pins verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-250">MinnowBoardMax uses sequential pin numbering because there are few existing pinout diagrams, and sequential pin numbering simplifies the developer experience because only 10 pins are exposed out of more than 200 pins.</span></span> <span data-ttu-id="6e450-251">Die Entscheidung zur Verwendung einer sequenziellen oder nativen Pinnummerierung sollte darauf abzielen, Verwechslungen durch Entwickler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6e450-251">The decision to use sequential or native pin numbering should aim to reduce developer confusion.</span></span> 

#### <a name="gpio-driver-requirements"></a><span data-ttu-id="6e450-252">GPIO-Treiberanforderungen</span><span class="sxs-lookup"><span data-stu-id="6e450-252">GPIO Driver Requirements</span></span> 

* <span data-ttu-id="6e450-253">Müssen verwenden:</span><span class="sxs-lookup"><span data-stu-id="6e450-253">Must use</span></span> `GpioClx`
* <span data-ttu-id="6e450-254">Müssen auf SOC-Speicher zugeordnet werden</span><span class="sxs-lookup"><span data-stu-id="6e450-254">Must be on-SOC memory mapped</span></span> 
* <span data-ttu-id="6e450-255">Müssen emulierte ActiveBoth-Interruptbehandlung verwenden</span><span class="sxs-lookup"><span data-stu-id="6e450-255">Must use emulated ActiveBoth interrupt handling</span></span> 

### <a name="uart"></a><span data-ttu-id="6e450-256">UART</span><span class="sxs-lookup"><span data-stu-id="6e450-256">UART</span></span> 

<span data-ttu-id="6e450-257">Wenn Ihre UART-Treiber `SerCx` oder `SerCx2` verwendet, können Sie Rhproxy verwenden, um den Treiber für den Benutzermodus verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="6e450-257">If your UART driver uses `SerCx` or `SerCx2`, you can use rhproxy to expose the driver to usermode.</span></span> <span data-ttu-id="6e450-258">UART-Treiber, die eine Geräteschnittstelle vom Typ `GUID_DEVINTERFACE_COMPORT` erstellen, müssen nicht Rhproxy verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-258">UART drivers that create a device interface of type `GUID_DEVINTERFACE_COMPORT` do not need to use rhproxy.</span></span> <span data-ttu-id="6e450-259">Der Posteingangstreiber `Serial.sys` gehört dazu.</span><span class="sxs-lookup"><span data-stu-id="6e450-259">The inbox `Serial.sys` driver is one of these cases.</span></span>

<span data-ttu-id="6e450-260">Um den `SerCx`-Stil UART für den Benutzermodus verfügbar zu machen, deklarieren Sie eine `UARTSerialBus`-Ressource wie folgt.</span><span class="sxs-lookup"><span data-stu-id="6e450-260">To expose a `SerCx`-style UART to usermode, declare a `UARTSerialBus` resource as follows.</span></span>

```cpp
// Index 2 
UARTSerialBus(           // Pin 17, 19 of JP1, for SIO_UART2 
    115200,                // InitialBaudRate: in bits ber second 
    ,                      // BitsPerByte: default to 8 bits 
    ,                      // StopBits: Defaults to one bit 
    0xfc,                  // LinesInUse: 8 1-bit flags to declare line enabled 
    ,                      // IsBigEndian: default to LittleEndian 
    ,                      // Parity: Defaults to no parity 
    ,                      // FlowControl: Defaults to no flow control 
    32,                    // ReceiveBufferSize 
    32,                    // TransmitBufferSize 
    "\\_SB.URT2",          // ResourceSource: UART bus controller name 
    , 
    , 
    , 
    )
```

<span data-ttu-id="6e450-261">Nur das ResourceSource-Feld ist festgelegt, alle anderen Felder hingegen sind Platzhalter für Werte, die zur Laufzeit vom Benutzer angegebenen werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-261">Only the ResourceSource field is fixed while all other fields are placeholders for values specified at runtime by the user.</span></span> 

<span data-ttu-id="6e450-262">Die zugehörigen Anzeigenamendeklaration ist:</span><span class="sxs-lookup"><span data-stu-id="6e450-262">The accompanying friendly name declaration is:</span></span> 

```cpp
Package(2) { "bus-UART-UART2", Package() { 2 }}, 
```

<span data-ttu-id="6e450-263">Dies weist dem Controller den Anzeigenamen „UART2“ zu. Dabei handelt es sich um den Bezeichner, den Benutzer verwenden, um im Benutzermodus auf den Bus zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="6e450-263">This assigns the friendly name “UART2” to the controller, which is the identifier users will use to access the bus from usermode.</span></span>  

## <a name="runtime-pin-muxing"></a><span data-ttu-id="6e450-264">Runtime-Pin-Muxing</span><span class="sxs-lookup"><span data-stu-id="6e450-264">Runtime Pin Muxing</span></span> 

<span data-ttu-id="6e450-265">Pin-Muxing bezeichnet die Möglichkeit, denselben physischen Pin für unterschiedliche Funktionen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-265">Pin muxing is the ability to use the same physical pin for different functions.</span></span> <span data-ttu-id="6e450-266">Mehrere verschiedene integrierte Peripheriegeräte, z.B. I2C-Controller, SPI-Controller und GPIO-Controller können an der gleichen physischen Pin auf einen SOC geleitet werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-266">Several different on-chip peripherals, such as an I2C controller, SPI controller, and GPIO controller, might be routed to the same physical pin on a SOC.</span></span> <span data-ttu-id="6e450-267">Der Mux-Block steuert, welche Funktion zu einem bestimmten Zeitpunkt auf dem Pin aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-267">The mux block controls which function is active on the pin at any given time.</span></span> <span data-ttu-id="6e450-268">Normalerweise ist Firmware für die Funktionszuweisung beim Start verantwortlich ist und diese Zuweisung bleibt während des Startvorgangs statisch.</span><span class="sxs-lookup"><span data-stu-id="6e450-268">Traditionally, firmware is responsible for establishing function assignments at boot, and this assignment remains static through the boot session.</span></span> <span data-ttu-id="6e450-269">Runtime-Pin-Muxing bietet die Möglichkeit, Pinfunktionszuweisungen zur Laufzeit neu zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-269">Runtime pin muxing adds the ability to reconfigure pin function assignments at runtime.</span></span> <span data-ttu-id="6e450-270">Wenn Benutzer die Pinfunktion zur Laufzeit auswählen können, wird die Entwicklung beschleunigt, da Benutzer die Pins einer Platine schnell neu konfigurieren können und da die Hardware mehr Anwendungen unterstützt, als sie es bei einer statischen Konfiguration tun würde.</span><span class="sxs-lookup"><span data-stu-id="6e450-270">Enabling users to choose a pin’s function at runtime speeds development by enabling users to quickly reconfigure a board’s pins, and enables hardware to support a broader range of applications than would a static configuration.</span></span> 

<span data-ttu-id="6e450-271">Benutzer können Muxing-Unterstützung für GPIO, I2C, SPI und UART nutzen, ohne zusätzlichen Code zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="6e450-271">Users consume muxing support for GPIO, I2C, SPI, and UART without writing any additional code.</span></span> <span data-ttu-id="6e450-272">Wenn ein Benutzer eine GPIO oder Bus mit [OpenPin()](https://msdn.microsoft.com/library/dn960157.aspx) oder [FromIdAsync()](https://msdn.microsoft.com/windows.devices.i2c.i2cdevice.fromidasync) öffnet, werden die zugrunde liegenden physische Pins automatisch an die angeforderte Funktion gemuxt.</span><span class="sxs-lookup"><span data-stu-id="6e450-272">When a user opens a GPIO or bus using [OpenPin()](https://msdn.microsoft.com/library/dn960157.aspx) or [FromIdAsync()](https://msdn.microsoft.com/windows.devices.i2c.i2cdevice.fromidasync), the underlying physical pins are automatically muxed to the requested function.</span></span> <span data-ttu-id="6e450-273">Wenn die Pins bereits von einer anderen Funktion verwendet werden, schlägt der OpenPin()- oder FromIdAsync()-Aufruf fehl.</span><span class="sxs-lookup"><span data-stu-id="6e450-273">If the pins are already in use by a different function, the OpenPin() or FromIdAsync() call will fail.</span></span> <span data-ttu-id="6e450-274">Wenn der Benutzer das Gerät schließt, indem er das Objekt [GpioPin](https://msdn.microsoft.com/library/windows/apps/windows.devices.gpio.gpiopin.aspx), [I2cDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.i2c.i2cdevice.aspx), [SpiDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.spi.spidevice.aspx) oder [SerialDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.serialcommunication.serialdevice.aspx) löscht, werden die Pins freigegeben, sodass sie später für eine andere Funktion geöffnet werden können.</span><span class="sxs-lookup"><span data-stu-id="6e450-274">When the user closes the device by disposing the [GpioPin](https://msdn.microsoft.com/library/windows/apps/windows.devices.gpio.gpiopin.aspx), [I2cDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.i2c.i2cdevice.aspx), [SpiDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.spi.spidevice.aspx), or [SerialDevice](https://msdn.microsoft.com/library/windows/apps/windows.devices.serialcommunication.serialdevice.aspx) object, the pins are released, allowing them to later be opened for a different function.</span></span> 

<span data-ttu-id="6e450-275">Windows enthält eine integrierte Unterstützung für Pin-Muxing in den [GpioClx](https://msdn.microsoft.com/library/windows/hardware/hh439515.aspx)-, [SpbCx](https://msdn.microsoft.com/library/windows/hardware/hh406203.aspx)- und [SerCx](https://msdn.microsoft.com/library/windows/hardware/dn265349.aspx)-Frameworks.</span><span class="sxs-lookup"><span data-stu-id="6e450-275">Windows contains built-in support for pin muxing in the [GpioClx](https://msdn.microsoft.com/library/windows/hardware/hh439515.aspx), [SpbCx](https://msdn.microsoft.com/library/windows/hardware/hh406203.aspx), and [SerCx](https://msdn.microsoft.com/library/windows/hardware/dn265349.aspx) frameworks.</span></span> <span data-ttu-id="6e450-276">Diese Frameworks arbeiten zusammen, um einen Pin automatisch an die richtige Funktion zu schalten, wenn auf einen GPIO-Pin oder Bus zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-276">These frameworks work together to automatically switch a pin to the correct function when a GPIO pin or bus is accessed.</span></span> <span data-ttu-id="6e450-277">Der Zugriff auf die Pins wird vermittelt, um Konflikte zwischen mehreren Clients zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6e450-277">Access to the pins is arbitrated to prevent conflicts among multiple clients.</span></span> <span data-ttu-id="6e450-278">Zusätzlich zu dieser integrierten Unterstützung sind die Schnittstellen und Protokolle für das Pin-Muxing universell einsetzbar und können erweitert werden, um zusätzliche Geräte und Szenarien zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6e450-278">In addition to this built-in support, the interfaces and protocols for pin muxing are general purpose and can be extended to support additional devices and scenarios.</span></span> 

<span data-ttu-id="6e450-279">In diesem Dokument werden zunächst die zugrunde liegenden Schnittstellen und Protokolle des Pin-Muxing beschrieben und anschließend wird beschrieben, wie Sie Unterstützung für Pin-Muxing GpioClx-, SpbCx- und SerCx-Controllertreiber hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e450-279">This document first describes the underlying interfaces and protocols involved in pin muxing, and then describes how to add support for pin muxing to GpioClx, SpbCx, and SerCx controller drivers.</span></span> 

### <a name="pin-muxing-architecture"></a><span data-ttu-id="6e450-280">Pin-Muxing-Architektur</span><span class="sxs-lookup"><span data-stu-id="6e450-280">Pin Muxing Architecture</span></span> 

<span data-ttu-id="6e450-281">In diesem Abschnitt werden die zugrunde liegenden Schnittstellen und Protokolle des Pin-Muxing beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6e450-281">This section describes the underlying interfaces and protocols involved in pin muxing.</span></span> <span data-ttu-id="6e450-282">Eine Kenntnis der zugrunde liegenden Protokolle ist nicht zwingend erforderlich, um Pin-Muxing mit SpbCx-/GpioClx-/SerCx-Treibern zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6e450-282">Knowledge of the underlying protocols is not necessarily needed to support pin muxing with GpioClx/SpbCx/SerCx drivers.</span></span> <span data-ttu-id="6e450-283">Ausführliche Informationen zur Unterstützung von Pin-Muxing mit SpbCx-/GpioCls-/SerCx-Treibern finden Sie unter [Implementieren von Pin-Muxing-Unterstützung in GpioClx-Clienttreibern](#supporting-muxing-support-in-gpioclx-client-drivers) und [Verwendung von Muxing-Unterstützung in SpbCx- und SerCx-Controllertreibern](#supporting-muxing-in-spbcx-and-sercx-controller-drivers).</span><span class="sxs-lookup"><span data-stu-id="6e450-283">For details on how to support pin muxing with GpioCls/SpbCx/SerCx drivers, see [Implementing pin muxing support in GpioClx client drivers](#supporting-muxing-support-in-gpioclx-client-drivers) and [Consuming muxing support in SpbCx and SerCx controller drivers](#supporting-muxing-in-spbcx-and-sercx-controller-drivers).</span></span> 

<span data-ttu-id="6e450-284">Pin-Muxing erfolgt durch Zusammenarbeit mehrerer Komponenten.</span><span class="sxs-lookup"><span data-stu-id="6e450-284">Pin muxing is accomplished by the cooperation of several components.</span></span> 

* <span data-ttu-id="6e450-285">Pin-Muxing-Server – Hierbei handelt es sich um Treiber, die den Pin-Muxing-Steuerblock steuern.</span><span class="sxs-lookup"><span data-stu-id="6e450-285">Pin muxing servers – these are drivers that control the pin muxing control block.</span></span> <span data-ttu-id="6e450-286">Pin-Muxing-Server erhalten Pin-Muxing-Anfragen von Clients über Anfragen zur Reservierung von Muxing-Ressourcen (über *IRP_MJ_CREATE*) und Anfragen zum Wechsel einer Pin-Funktion (über *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS*).</span><span class="sxs-lookup"><span data-stu-id="6e450-286">Pin muxing servers receive pin muxing requests from clients via requests to reserve muxing resources (via *IRP_MJ_CREATE*) requests, and requests to switch a pin’s function (via *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* requests).</span></span> <span data-ttu-id="6e450-287">Der Pin-Muxing-Server ist in der Regel der GPIO-Treiber, da der Muxing-Block manchmal Teil des GPIO-Blocks ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-287">The pin muxing server is usually the GPIO driver, since the muxing block is sometimes part of the GPIO block.</span></span> <span data-ttu-id="6e450-288">Auch, wenn der Muxing-Block ein separates Peripheriegerät ist, ist der GPIO-Treiber ein logischer Ort für die Muxing-Funktion.</span><span class="sxs-lookup"><span data-stu-id="6e450-288">Even if the muxing block is a separate peripheral, the GPIO driver is a logical place to put muxing functionality.</span></span> 
* <span data-ttu-id="6e450-289">Pin-Muxing-Clients – Treiber, die Pin-Muxing beanspruchen.</span><span class="sxs-lookup"><span data-stu-id="6e450-289">Pin muxing clients – these are drivers that consume pin muxing.</span></span> <span data-ttu-id="6e450-290">Pin-Muxing-Clients erhalten Pin-Muxing-Ressourcen von der ACPI-Firmware.</span><span class="sxs-lookup"><span data-stu-id="6e450-290">Pin muxing clients receive pin muxing resources from ACPI firmware.</span></span> <span data-ttu-id="6e450-291">Pin-Muxing-Ressourcen sind eine Art der Verbindungsressource und werden vom Ressourcenhub verwaltet.</span><span class="sxs-lookup"><span data-stu-id="6e450-291">Pin muxing resources are a type of connection resource and are managed by the resource hub.</span></span> <span data-ttu-id="6e450-292">Pin-Muxing-Clients reservieren Pin-Muxing-Ressourcen, indem sie ein Handle zur Ressource öffnen.</span><span class="sxs-lookup"><span data-stu-id="6e450-292">Pin muxing clients reserve pin muxing resources by opening a handle to the resource.</span></span> <span data-ttu-id="6e450-293">Damit eine Änderung an der Hardware wirksam ist, müssen Clients die Konfiguration durch Senden der Anforderung *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* übernehmen.</span><span class="sxs-lookup"><span data-stu-id="6e450-293">To effect a hardware change, clients must commit the configuration by sending an *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* request.</span></span> <span data-ttu-id="6e450-294">Clients geben Pin-Muxing-Ressourcen frei, indem Sie den Handel schließen. Die Muxing-Konfiguration wird dann wieder auf Standardeinstellungen zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="6e450-294">Clients release pin muxing resources by closing the handle, at which point muxing configuration is reverted to its default state.</span></span> 
* <span data-ttu-id="6e450-295">ACPI-Firmware – gibt die Muxing-Konfiguration mit `MsftFunctionConfig()`-Ressourcen an.</span><span class="sxs-lookup"><span data-stu-id="6e450-295">ACPI firmware – specifies muxing configuration with `MsftFunctionConfig()` resources.</span></span> <span data-ttu-id="6e450-296">MsftFunctionConfig-Ressourcen geben an, welche Pins in welcher Muxing-Konfiguration von einem Client benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-296">MsftFunctionConfig resources express which pins, in which muxing configuration, are required by a client.</span></span> <span data-ttu-id="6e450-297">MsftFunctionConfig-Ressourcen enthalten Funktionsnummer, Pull-Konfiguration und eine Liste der Pinnummern.</span><span class="sxs-lookup"><span data-stu-id="6e450-297">MsftFunctionConfig resources contain function number, pull configuration, and list of pin numbers.</span></span> <span data-ttu-id="6e450-298">MsftFunctionConfig-Ressourcen werden Pin-Muxing-Clients wie Hardwareressourcen bereitgestellt, die von Treibern beim PrepareHardware-Rückruf entsprechend GPIO- und SPB-Verbindungsressourcen empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-298">MsftFunctionConfig resources are supplied to pin muxing clients as hardware resources, which are received by drivers in their PrepareHardware callback similarly to GPIO and SPB connection resources.</span></span> <span data-ttu-id="6e450-299">Clients empfangen eine Ressourcen-Hub-ID, die verwendet werden kann, um ein Handle für die Ressource zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="6e450-299">Clients receive a resource hub ID which can be used to open a handle to the resource.</span></span> 

> <span data-ttu-id="6e450-300">Sie müssen die Befehlszeilenoption `/MsftInternal` an `asl.exe` übergeben, um ASL-Dateien mit `MsftFunctionConfig()`-Beschreibungen zu kompilieren, da diese Deskriptoren derzeit von der ACPI-Arbeitsgruppe überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-300">You must pass the `/MsftInternal` command line switch to `asl.exe` to compile ASL files containing `MsftFunctionConfig()` descriptors since these descriptors are currently under review by the ACPI working committee.</span></span> <span data-ttu-id="6e450-301">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e450-301">For example:</span></span> `asl.exe /MsftInternal dsdt.asl`

<span data-ttu-id="6e450-302">Nachfolgend finden Sie die Reihenfolge der Vorgänge des Pin-Muxing.</span><span class="sxs-lookup"><span data-stu-id="6e450-302">The sequence of operations involved in pin muxing is shown below.</span></span> 

![Pin-Muxing-Client-Server-Interaktion](images/usermode-access-diagram-1.png)

1.  <span data-ttu-id="6e450-304">Der Client empfängt MsftFunctionConfig-Ressourcen von der ACPI-Firmware bei seinem [EvtDevicePrepareHardware()](https://msdn.microsoft.com/library/windows/hardware/ff540880.aspx)-Rückruf.</span><span class="sxs-lookup"><span data-stu-id="6e450-304">The client receives MsftFunctionConfig resources from ACPI firmware in its [EvtDevicePrepareHardware()](https://msdn.microsoft.com/library/windows/hardware/ff540880.aspx) callback.</span></span>
2.  <span data-ttu-id="6e450-305">Der Client verwendet die Ressourcen-Hub-Hilfsfunktion, `RESOURCE_HUB_CREATE_PATH_FROM_ID()`um einen Pfad über die Ressourcen-ID zu erstellen. Anschließend öffnet er ein Handle zum Pfad (mit [ZwCreateFile()](https://msdn.microsoft.com/library/windows/hardware/ff566424.aspx), [IoGetDeviceObjectPointer()](https://msdn.microsoft.com/library/windows/hardware/ff549198.aspx) oder [WdfIoTargetOpen()](https://msdn.microsoft.com/library/windows/hardware/ff548634.aspx)).</span><span class="sxs-lookup"><span data-stu-id="6e450-305">The client uses the resource hub helper function `RESOURCE_HUB_CREATE_PATH_FROM_ID()` to create a path from the resource ID, then opens a handle to the path (using [ZwCreateFile()](https://msdn.microsoft.com/library/windows/hardware/ff566424.aspx), [IoGetDeviceObjectPointer()](https://msdn.microsoft.com/library/windows/hardware/ff549198.aspx), or [WdfIoTargetOpen()](https://msdn.microsoft.com/library/windows/hardware/ff548634.aspx)).</span></span>
3.  <span data-ttu-id="6e450-306">Der Server extrahiert die Ressourcen-Hub-ID aus dem Dateipfad mit der Ressourcen-Hub-Hilfsfunktionen `RESOURCE_HUB_ID_FROM_FILE_NAME()` und fragt dann beim Ressourcen-Hub die Beschreibung der Ressourcen ab.</span><span class="sxs-lookup"><span data-stu-id="6e450-306">The server extracts the resource hub ID from the file path using resource hub helper functions `RESOURCE_HUB_ID_FROM_FILE_NAME()`, then queries the resource hub to get the resource descriptor.</span></span>
4.  <span data-ttu-id="6e450-307">Der Server führt eine Freigabevermittlung für jeden Pin in der Beschreibung durch und schließt die Anforderung IRP_MJ_CREATE ab.</span><span class="sxs-lookup"><span data-stu-id="6e450-307">The server performs sharing arbitration for each pin in the descriptor and completes the IRP_MJ_CREATE request.</span></span>
5.  <span data-ttu-id="6e450-308">Der Client sendet eine *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS*-Anforderung an das empfangene Handle.</span><span class="sxs-lookup"><span data-stu-id="6e450-308">The client issues an *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* request on the received handle.</span></span>
6.  <span data-ttu-id="6e450-309">In Reaktion auf *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* führt der Server das Hardware-Muxing durch, indem er die angegebene Funktion auf jedem Pin aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6e450-309">In response to *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS*, the server performs the hardware muxing operation by making the specified function active on each pin.</span></span>
7.  <span data-ttu-id="6e450-310">Der Client setzt dann die Vorgänge fort, die von der Konfiguration des angeforderten Pin-Muxing abhängen.</span><span class="sxs-lookup"><span data-stu-id="6e450-310">The client proceeds with operations that depend on the requested pin muxing configuration.</span></span>
8.  <span data-ttu-id="6e450-311">Wenn der Client das Muxing der Pins nicht länger benötigt, wird das Handle geschlossen.</span><span class="sxs-lookup"><span data-stu-id="6e450-311">When the client no longer requires the pins to be muxed, it closes the handle.</span></span>
9.  <span data-ttu-id="6e450-312">In Reaktion auf das geschlossene Handle setzt der Server die Pins zurück in ihren Ausgangszustand.</span><span class="sxs-lookup"><span data-stu-id="6e450-312">In response to the handle being closed, the server reverts the pins back to their initial state.</span></span>

### <a name="protocol-description-for-pin-muxing-clients"></a><span data-ttu-id="6e450-313">Protokollbeschreibung für Pin-Muxing-Clients</span><span class="sxs-lookup"><span data-stu-id="6e450-313">Protocol description for pin muxing clients</span></span>

<span data-ttu-id="6e450-314">In diesem Abschnitt wird beschrieben, wie ein Client die Pin-Muxing-Funktionalität verwendet.</span><span class="sxs-lookup"><span data-stu-id="6e450-314">This section describes how a client consumes pin muxing functionality.</span></span> <span data-ttu-id="6e450-315">Dies gilt nicht für die Controllertreiber `SerCx` und `SpbCx`, da die Frameworks dieses Protokoll anstelle der Controllertreiber implementieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-315">This does not apply to `SerCx` and `SpbCx` controller drivers, since the frameworks implement this protocol on behalf of controller drivers.</span></span>

####    <a name="parsing-resources"></a><span data-ttu-id="6e450-316">Analysieren von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6e450-316">Parsing resources</span></span>

<span data-ttu-id="6e450-317">Ein WDF-Treiber empfängt `MsftFunctionConfig()`-Ressourcen in seiner [EvtDevicePrepareHardware()](https://msdn.microsoft.com/library/windows/hardware/ff540880.aspx)-Routine.</span><span class="sxs-lookup"><span data-stu-id="6e450-317">A WDF driver receives `MsftFunctionConfig()` resources in its [EvtDevicePrepareHardware()](https://msdn.microsoft.com/library/windows/hardware/ff540880.aspx) routine.</span></span> <span data-ttu-id="6e450-318">MsftFunctionConfig-Ressourcen können durch die folgenden Felder identifiziert werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-318">MsftFunctionConfig resources can be identified by the following fields:</span></span>

```cpp
CM_PARTIAL_RESOURCE_DESCRIPTOR::Type = CmResourceTypeConnection
CM_PARTIAL_RESOURCE_DESCRIPTOR::u.Connection.Class = CM_RESOURCE_CONNECTION_CLASS_FUNCTION_CONFIG
CM_PARTIAL_RESOURCE_DESCRIPTOR::u.Connection.Type = CM_RESOURCE_CONNECTION_TYPE_FUNCTION_CONFIG
```

<span data-ttu-id="6e450-319">Ein `EvtDevicePrepareHardware()`-Routine extrahiert MsftFunctionConfig-Ressourcen möglicherweise wie folgt:</span><span class="sxs-lookup"><span data-stu-id="6e450-319">An `EvtDevicePrepareHardware()` routine might extract MsftFunctionConfig resources as follows:</span></span>

```cpp
EVT_WDF_DEVICE_PREPARE_HARDWARE evtDevicePrepareHardware;

_Use_decl_annotations_
NTSTATUS
evtDevicePrepareHardware (
    WDFDEVICE WdfDevice,
    WDFCMRESLIST ResourcesTranslated
    )
{
    PAGED_CODE();

    LARGE_INTEGER connectionId;
    ULONG functionConfigCount = 0;

    const ULONG resourceCount = WdfCmResourceListGetCount(ResourcesTranslated);
    for (ULONG index = 0; index < resourceCount; ++index) {
        const CM_PARTIAL_RESOURCE_DESCRIPTOR* resDescPtr =
            WdfCmResourceListGetDescriptor(ResourcesTranslated, index);

        switch (resDescPtr->Type) {
        case CmResourceTypeConnection:
            switch (resDescPtr->u.Connection.Class) {
            case CM_RESOURCE_CONNECTION_CLASS_FUNCTION_CONFIG:
                switch (resDescPtr->u.Connection.Type) {
                case CM_RESOURCE_CONNECTION_TYPE_FUNCTION_CONFIG:                    
                    switch (functionConfigCount) {
                    case 0:
                        // save the connection ID
                        connectionId.LowPart = resDescPtr->u.Connection.IdLowPart;
                        connectionId.HighPart = resDescPtr->u.Connection.IdHighPart;
                        break;
                    } // switch (functionConfigCount)
                    ++functionConfigCount;
                    break; // CM_RESOURCE_CONNECTION_TYPE_FUNCTION_CONFIG

                } // switch (resDescPtr->u.Connection.Type)
                break; // CM_RESOURCE_CONNECTION_CLASS_FUNCTION_CONFIG
            } // switch (resDescPtr->u.Connection.Class)
            break;
        } // switch
    } // for (resource list)

    if (functionConfigCount < 1) {
        return STATUS_INVALID_DEVICE_CONFIGURATION;
    }
    // TODO: save connectionId in the device context for later use

    return STATUS_SUCCESS;
}
```

####    <a name="reserving-and-committing-resources"></a><span data-ttu-id="6e450-320">Reservieren und Übernehmen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6e450-320">Reserving and committing resources</span></span>

<span data-ttu-id="6e450-321">Wenn ein Client Mux-Pins möchte, reserviert und übernimmt er die MsftFunctionConfig-Ressource.</span><span class="sxs-lookup"><span data-stu-id="6e450-321">When a client wants to mux pins, it reserves and commits the MsftFunctionConfig resource.</span></span> <span data-ttu-id="6e450-322">Das folgende Beispiel zeigt, wie ein Client MsftFunctionConfig-Ressourcen reservieren und übernehmen kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-322">The following example shows how a client might reserve and commit MsftFunctionConfig resources.</span></span>

```cpp
_IRQL_requires_max_(PASSIVE_LEVEL)
NTSTATUS AcquireFunctionConfigResource (
    WDFDEVICE WdfDevice,
    LARGE_INTEGER ConnectionId,
    _Out_ WDFIOTARGET* ResourceHandlePtr
    )
{
    PAGED_CODE();

    //
    // Form the resource path from the connection ID
    //
    DECLARE_UNICODE_STRING_SIZE(resourcePath, RESOURCE_HUB_PATH_CHARS);
    NTSTATUS status = RESOURCE_HUB_CREATE_PATH_FROM_ID(
            &resourcePath,
            ConnectionId.LowPart,
            ConnectionId.HighPart);
    if (!NT_SUCCESS(status)) {
        return status;
    }
    
    //
    // Create a WDFIOTARGET
    //
    WDFIOTARGET resourceHandle;
    status = WdfIoTargetCreate(WdfDevice, WDF_NO_ATTRIBUTES, &resourceHandle);
    if (!NT_SUCCESS(status)) {
        return status;
    }

    //
    // Reserve the resource by opening a WDFIOTARGET to the resource
    //
    WDF_IO_TARGET_OPEN_PARAMS openParams;
    WDF_IO_TARGET_OPEN_PARAMS_INIT_OPEN_BY_NAME(
        &openParams,
        &resourcePath,
        FILE_GENERIC_READ | FILE_GENERIC_WRITE);

    status = WdfIoTargetOpen(resourceHandle, &openParams);
    if (!NT_SUCCESS(status)) {
        return status;
    }
    //
    // Commit the resource
    //
    status = WdfIoTargetSendIoctlSynchronously(
            resourceHandle,
            WDF_NO_HANDLE,      // WdfRequest
            IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS,
            nullptr,            // InputBuffer
            nullptr,            // OutputBuffer
            nullptr,            // RequestOptions
            nullptr);           // BytesReturned
    
    if (!NT_SUCCESS(status)) {
        WdfIoTargetClose(resourceHandle);
        return status;
    }

    //
    // Pins were successfully muxed, return the handle to the caller
    //
    *ResourceHandlePtr = resourceHandle;
    return STATUS_SUCCESS;
}
```

<span data-ttu-id="6e450-323">Der Treiber sollte das WDFIOTARGET in einem seiner Kontextbereiche speichern, damit dieses später geschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-323">The driver should store the WDFIOTARGET in one of its context areas so that it can be closed later.</span></span> <span data-ttu-id="6e450-324">Wenn der Treiber für die Veröffentlichung der Muxing-Konfiguration bereit ist, sollte das Ressourcenhandle durch Aufrufen von [WdfObjectDelete()](https://msdn.microsoft.com/library/windows/hardware/ff548734.aspx) oder [WdfIoTargetClose()](https://msdn.microsoft.com/library/windows/hardware/ff548586.aspx) geschlossen werden, wenn Sie WDFIOTARGET wiederverwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="6e450-324">When the driver is ready to release the muxing configuration, it should close the resource handle by calling [WdfObjectDelete()](https://msdn.microsoft.com/library/windows/hardware/ff548734.aspx), or [WdfIoTargetClose()](https://msdn.microsoft.com/library/windows/hardware/ff548586.aspx) if you intend to reuse the WDFIOTARGET.</span></span>

```cpp
    WdfObjectDelete(resourceHandle);
```

<span data-ttu-id="6e450-325">Wenn der Client das Ressourcenhandle schließt, werden die Pins auf ihren ursprünglichen Zustand zurück gemuxt und können jetzt von einem anderen Client verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-325">When the client closes its resource handle, the pins are muxed back to their initial state, and can now be acquired by a different client.</span></span>

### <a name="protocol-description-for-pin-muxing-servers"></a><span data-ttu-id="6e450-326">Protokollbeschreibung für Pin-Muxing-Server</span><span class="sxs-lookup"><span data-stu-id="6e450-326">Protocol description for pin muxing servers</span></span>

<span data-ttu-id="6e450-327">In diesem Abschnitt wird erläutert, wie ein Pin-Muxing-Server seine Funktionalität für Clients bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="6e450-327">This section describes how a pin muxing server exposes its functionality to clients.</span></span> <span data-ttu-id="6e450-328">Dies gilt nicht für `GpioClx`-Miniporttreiber, da das Framework dieses Protokoll anstelle des Clienttreibers implementiert.</span><span class="sxs-lookup"><span data-stu-id="6e450-328">This does not apply to `GpioClx` miniport drivers, since the framework implements this protocol on behalf of client drivers.</span></span> <span data-ttu-id="6e450-329">Ausführliche Informationen zur Unterstützung von Pin-Muxing bei `GpioClx`-Clienttreibern finden Sie unter [Implementieren von Muxing-Unterstützung bei GpioClx Clienttreibern](#supporting-muxing-support-in-gpioclx-client-drivers).</span><span class="sxs-lookup"><span data-stu-id="6e450-329">For details on how to support pin muxing in `GpioClx` client drivers, see [Implementing muxing support in GpioClx Client Drivers](#supporting-muxing-support-in-gpioclx-client-drivers).</span></span>

####    <a name="handling-irpmjcreate-requests"></a><span data-ttu-id="6e450-330">Behandeln von IRP_MJ_CREATE-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6e450-330">Handling IRP_MJ_CREATE requests</span></span>

<span data-ttu-id="6e450-331">Clients öffnen ein Handle für eine Ressource, wenn sie eine Pin-Muxing-Ressource reservieren möchten.</span><span class="sxs-lookup"><span data-stu-id="6e450-331">Clients open a handle to a resource when they want to reserve a pin muxing resource.</span></span> <span data-ttu-id="6e450-332">Ein Pin-Muxing-Server empfängt *IRP_MJ_CREATE*-Anfragen über einen Analysevorgang von der Hub-Ressource.</span><span class="sxs-lookup"><span data-stu-id="6e450-332">A pin muxing server receives *IRP_MJ_CREATE* requests by way of a reparse operation from the resource hub.</span></span> <span data-ttu-id="6e450-333">Die nachfolgende Pfadkomponente der *IRP_MJ_CREATE*-Anforderung enthält die Ressourcen-Hub-ID, eine 64-Bit-Ganzzahl im Hexadezimalformat.</span><span class="sxs-lookup"><span data-stu-id="6e450-333">The trailing path component of the *IRP_MJ_CREATE* request contains the resource hub ID, which is a 64-bit integer in hexadecimal format.</span></span> <span data-ttu-id="6e450-334">Der Server sollte die Ressourcen-Hub-ID aus dem Dateinamen mit `RESOURCE_HUB_ID_FROM_FILE_NAME()` aus reshub.h extrahieren und *IOCTL_RH_QUERY_CONNECTION_PROPERTIES* an den Ressourcen-Hub zum Abrufen der `MsftFunctionConfig()`-Beschreibung senden.</span><span class="sxs-lookup"><span data-stu-id="6e450-334">The server should extract the resource hub ID from the filename using `RESOURCE_HUB_ID_FROM_FILE_NAME()` from reshub.h, and send *IOCTL_RH_QUERY_CONNECTION_PROPERTIES* to the resource hub to obtain the `MsftFunctionConfig()` descriptor.</span></span>

<span data-ttu-id="6e450-335">Der Server sollte die Beschreibung überprüfen und den Freigabemodus und die Pinliste aus der Beschreibung extrahieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-335">The server should validate the descriptor and extract the sharing mode and pin list from the descriptor.</span></span> <span data-ttu-id="6e450-336">Anschließend sollte er eine Freigabevermittlung für die Pins durchführen. Wenn diese erfolgreich war, sollte er die Pins als reserviert markieren, bevor er die Abfrage abschließt.</span><span class="sxs-lookup"><span data-stu-id="6e450-336">It should then perform sharing arbitration for the pins, and if successful, mark the pins as reserved before completing the request.</span></span>

<span data-ttu-id="6e450-337">Die Freigabevermittlung war insgesamt erfolgreich, wenn die Freigabevermittlung für jeden Pin in der Pinliste erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="6e450-337">Sharing arbitration succeeds overall if sharing arbitration succeeds for each pin in the pin list.</span></span> <span data-ttu-id="6e450-338">Jede Pin sollte wie folgt vermittelt werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-338">Each pin should be arbitrated as follows:</span></span>

*   <span data-ttu-id="6e450-339">Wenn der Pin nicht bereits reserviert ist, verläuft die Freigabevermittlung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="6e450-339">If the pin is not already reserved, sharing arbitration succeeds.</span></span>
*   <span data-ttu-id="6e450-340">Ist der Pin bereits exklusiv reserviert, schlägt die Freigabevermittlung fehl.</span><span class="sxs-lookup"><span data-stu-id="6e450-340">If the pin is already reserved as exclusive, sharing arbitration fails.</span></span>
*   <span data-ttu-id="6e450-341">Wenn der Pin bereits als freigegeben reserviert ist,</span><span class="sxs-lookup"><span data-stu-id="6e450-341">If the pin is already reserved as shared,</span></span>
  * <span data-ttu-id="6e450-342">und die eingehende Anforderung wird freigegeben, dann verläuft die Freigabevermittlung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="6e450-342">and the incoming request is shared, sharing arbitration succeeds.</span></span>
  * <span data-ttu-id="6e450-343">und die eingehende Anforderung exklusiv ist, dann schlägt die Freigabevermittlung fehl.</span><span class="sxs-lookup"><span data-stu-id="6e450-343">and the incoming request is exclusive, sharing arbitration fails.</span></span>

<span data-ttu-id="6e450-344">Wenn die Freigabevermittlung fehlschlägt, sollte die Anforderung mit *STATUS_GPIO_INCOMPATIBLE_CONNECT_MODE* abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-344">If sharing arbitration fails, the request should be completed with *STATUS_GPIO_INCOMPATIBLE_CONNECT_MODE*.</span></span> <span data-ttu-id="6e450-345">Wenn Vermittlung Freigabe erfolgreich ist, sollte die Anforderung mit *STATUS_SUCCESS* abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-345">If sharing arbitration succeeds, the request should completed with *STATUS_SUCCESS*.</span></span>

<span data-ttu-id="6e450-346">Beachten Sie, dass der Freigabemodus der eingehenden Anforderung aus der MsftFunctionConfig-Beschreibung entnommen werden soll, nicht aus [IrpSp -> Parameters.Create.ShareAccess](https://msdn.microsoft.com/library/windows/hardware/ff548630.aspx).</span><span class="sxs-lookup"><span data-stu-id="6e450-346">Note that the sharing mode of the incoming request should be taken from the MsftFunctionConfig descriptor, not [IrpSp->Parameters.Create.ShareAccess](https://msdn.microsoft.com/library/windows/hardware/ff548630.aspx).</span></span>

####    <a name="handling-ioctlgpiocommitfunctionconfigpins-requests"></a><span data-ttu-id="6e450-347">Behandeln von IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS-Anfragen</span><span class="sxs-lookup"><span data-stu-id="6e450-347">Handling IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS requests</span></span>

<span data-ttu-id="6e450-348">Nachdem der Client erfolgreich eine MsftFunctionConfig-Ressource durch Öffnen eines Handle reserviert hat, kann er *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* senden, um anzufordern, dass der Server den Hardware-Muxing-Vorgang selbst durchführt.</span><span class="sxs-lookup"><span data-stu-id="6e450-348">After the client has successfully reserved a MsftFunctionConfig resource by opening a handle, it can send *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* to request the server to perform the actual hardware muxing operation.</span></span> <span data-ttu-id="6e450-349">Wenn der Server für jeden Pin in der Pinliste *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* empfängt, sollte er</span><span class="sxs-lookup"><span data-stu-id="6e450-349">When the server receives *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS*, for each pin in the pin list it should</span></span> 

*   <span data-ttu-id="6e450-350">den Pull-Modus, der im PinConfiguration-Element der Struktur PNP_FUNCTION_CONFIG_DESCRIPTOR in der Hardware festgelegt ist, angeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-350">Set the pull mode specified in the PinConfiguration member of the PNP_FUNCTION_CONFIG_DESCRIPTOR structure into hardware.</span></span>
*   <span data-ttu-id="6e450-351">den Pin zur Funktion muxen, die im FunctionNumber-Element der Struktur PNP_FUNCTION_CONFIG_DESCRIPTOR angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-351">Mux the pin to the function specified by the FunctionNumber member of the PNP_FUNCTION_CONFIG_DESCRIPTOR structure.</span></span>

<span data-ttu-id="6e450-352">Der Server sollte dann die Anforderung mit *STATUS_SUCCESS* abschließen.</span><span class="sxs-lookup"><span data-stu-id="6e450-352">The server should then complete the request with *STATUS_SUCCESS*.</span></span>

<span data-ttu-id="6e450-353">Die Bedeutung von FunctionNumber wird vom Server definiert, und es wird davon ausgegangen, dass die MsftFunctionConfig-Beschreibung mit Kenntnissen darüber erstellt wurde, wie der Servers dieses Feld interpretiert.</span><span class="sxs-lookup"><span data-stu-id="6e450-353">The meaning of FunctionNumber is defined by the server, and it is understood that the MsftFunctionConfig descriptor was authored with knowledge of how the server interprets this field.</span></span>

<span data-ttu-id="6e450-354">Denken Sie daran, dass, wenn das Handle geschlossen ist, der Server die Pins in der Konfiguration wiederherstellen muss, in der sie eingegangen sind, als IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS empfangen wurde. Der Server muss den Zustand der Pins also möglicherweise speichern, bevor diese geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="6e450-354">Remember that when the handle is closed, the server will have to revert the pins to the configuration they were in when IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS was received, so the server may need to save the pins’ state before modifying them.</span></span>

####    <a name="handling-irpmjclose-requests"></a><span data-ttu-id="6e450-355">Behandeln von IRP_MJ_CLOSE-Anfragen</span><span class="sxs-lookup"><span data-stu-id="6e450-355">Handling IRP_MJ_CLOSE requests</span></span>

<span data-ttu-id="6e450-356">Wenn ein Client eine Muxing-Ressource nicht länger benötigt, wird das Handle geschlossen.</span><span class="sxs-lookup"><span data-stu-id="6e450-356">When a client no longer requires a muxing resource, it closes its handle.</span></span> <span data-ttu-id="6e450-357">Wenn ein Server eine *IRP_MJ_CLOSE*-Anfrage empfängt, sollte er die Pins auf den Zustand wiederherstellen, als *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="6e450-357">When a server receives a *IRP_MJ_CLOSE* request, it should revert the pins to the state they were in when *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* was received.</span></span> <span data-ttu-id="6e450-358">Wenn der Client nie ein *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS* gesendet hat, ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6e450-358">If the client never sent a *IOCTL_GPIO_COMMIT_FUNCTION_CONFIG_PINS*, no action is necessary.</span></span> <span data-ttu-id="6e450-359">Der Server sollte die Pins dann nach Verfügbarkeit und im Hinblick auf die Freigabevermittlung markieren und die Anforderung mit *STATUS_SUCCESS* durchführen.</span><span class="sxs-lookup"><span data-stu-id="6e450-359">The server should then mark the pins as available with respect to sharing arbitration, and complete the request with *STATUS_SUCCESS*.</span></span> <span data-ttu-id="6e450-360">Achten Sie darauf, dass Sie die *IRP_MJ_CLOSE*-Handhabung ordnungsgemäß mit der *IRP_MJ_CREATE*-Handhabung synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-360">Be sure to properly synchronize *IRP_MJ_CLOSE* handling with *IRP_MJ_CREATE* handling.</span></span>

### <a name="authoring-guidelines-for-acpi-tables"></a><span data-ttu-id="6e450-361">Richtlinien für das Erstellen von ACPI-Tabellen</span><span class="sxs-lookup"><span data-stu-id="6e450-361">Authoring guidelines for ACPI tables</span></span>

<span data-ttu-id="6e450-362">In diesem Abschnitt wird beschrieben, wie Muxing-Ressourcen Clienttreibern bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-362">This section describes how to supply muxing resources to client drivers.</span></span> <span data-ttu-id="6e450-363">Beachten Sie, dass Sie Microsoft ASL Compiler Build 14327 oder höher zum Kompilieren von Tabellen mit `MsftFunctionConfig()`-Ressourcen benötigen.</span><span class="sxs-lookup"><span data-stu-id="6e450-363">Note that you will need Microsoft ASL compiler build 14327 or later to compile tables containing `MsftFunctionConfig()` resources.</span></span> `MsftFunctionConfig()` <span data-ttu-id="6e450-364">Ressourcen werden den Pin-Muxing-Clients als Hardwareressourcen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="6e450-364">resources are supplied to pin muxing clients as hardware resources.</span></span> `MsftFunctionConfig()` <span data-ttu-id="6e450-365">Ressourcen sollten Treibern bereitgestellt werden, die Pin-Muxing-Änderungen erfordern. Dies sind in der Regel SPB- und serielle Controllertreiber; sie sollten jedoch nicht SPB- und seriellen peripheren Gerätetreibern bereitgestellt werden, da die Controllertreiber für die Muxing-Konfiguration verantwortlich sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-365">resources should be supplied to drivers that require pin muxing changes, which are typically SPB and serial controller drivers, but should not be supplied to SPB and serial peripheral drivers, since the controller driver handles muxing configuration.</span></span>
<span data-ttu-id="6e450-366">Das `MsftFunctionConfig()`-ACPI-Makro wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="6e450-366">The `MsftFunctionConfig()` ACPI macro is defined as follows:</span></span>

```cpp
  MsftFunctionConfig(Shared/Exclusive
                PinPullConfig,
                FunctionNumber,
                ResourceSource,
                ResourceSourceIndex,
                ResourceConsumer/ResourceProducer,
                VendorData) { Pin List }

```

* <span data-ttu-id="6e450-367">Freigegeben/exklusiv – Bei „exklusiv“ kann der Pin nur von einem einzigen Client abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-367">Shared/Exclusive – If exclusive, this pin can be acquired by a single client at a time.</span></span> <span data-ttu-id="6e450-368">Bei „freigegeben“ können mehrere freigegebene Clients die Ressource abrufen.</span><span class="sxs-lookup"><span data-stu-id="6e450-368">If shared, multiple shared clients can acquire the resource.</span></span> <span data-ttu-id="6e450-369">Legen Sie diesen Wert immer auf „exklusiv“ fest, da mehrere unkoordinierte Clients mit Zugriff auf eine änderbare Ressource zu Datenrennen und damit zu unvorhersehbaren Ergebnissen führen können.</span><span class="sxs-lookup"><span data-stu-id="6e450-369">Always set this to exclusive since allowing multiple uncoordinated clients to access a mutable resource can lead to data races and therefore unpredictable results.</span></span> 
* <span data-ttu-id="6e450-370">PinPullConfig – Einer davon</span><span class="sxs-lookup"><span data-stu-id="6e450-370">PinPullConfig – one of</span></span> 
  * <span data-ttu-id="6e450-371">PullDefault – Verwenden der SOC-definierten Pull-Standardkonfiguration beim Einschalten</span><span class="sxs-lookup"><span data-stu-id="6e450-371">PullDefault – use the SOC-defined power-on default pull configuration</span></span> 
  * <span data-ttu-id="6e450-372">PullUp – Pull-Up-Widerstand aktivieren</span><span class="sxs-lookup"><span data-stu-id="6e450-372">PullUp – enable pull-up resistor</span></span> 
  * <span data-ttu-id="6e450-373">PullDown – Pull-Down-Widerstand aktivieren</span><span class="sxs-lookup"><span data-stu-id="6e450-373">PullDown – enable pull-down resistor</span></span> 
  * <span data-ttu-id="6e450-374">PullNone – Alle Pull-Widerstände deaktivieren</span><span class="sxs-lookup"><span data-stu-id="6e450-374">PullNone – disable all pull resistors</span></span> 
* <span data-ttu-id="6e450-375">FunctionNumber – Die in den Mux zu programmierende Funktionsnummer.</span><span class="sxs-lookup"><span data-stu-id="6e450-375">FunctionNumber – the function number to program into the mux.</span></span> 
* <span data-ttu-id="6e450-376">ResourceSource – Der ACPI-Namespace-Pfad des Pin-Muxing-Servers</span><span class="sxs-lookup"><span data-stu-id="6e450-376">ResourceSource – The ACPI namespace path of the pin muxing server</span></span> 
* <span data-ttu-id="6e450-377">ResourceSourceIndex – Legen Sie diesen Wert auf 0 fest</span><span class="sxs-lookup"><span data-stu-id="6e450-377">ResourceSourceIndex – set this to 0</span></span> 
* <span data-ttu-id="6e450-378">ResourceConsumer/ResourceProducer – Legen Sie diesen Wert auf ResourceConsumer fest</span><span class="sxs-lookup"><span data-stu-id="6e450-378">ResourceConsumer/ResourceProducer – set this to ResourceConsumer</span></span> 
* <span data-ttu-id="6e450-379">VendorData – Optional Binärdaten, deren Bedeutung vom Pin-Muxing-Server definiert wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-379">VendorData – optional binary data whose meaning is defined by the pin muxing server.</span></span> <span data-ttu-id="6e450-380">Dies Wert sollte in der Regel leer bleiben</span><span class="sxs-lookup"><span data-stu-id="6e450-380">This should usually be left blank</span></span>
* <span data-ttu-id="6e450-381">Pinliste – eine kommagetrennte Liste der Pinnummern für die die Konfiguration gilt.</span><span class="sxs-lookup"><span data-stu-id="6e450-381">Pin List – a comma separated list of pin numbers to which the configuration applies.</span></span> <span data-ttu-id="6e450-382">Wenn der Pin-Muxing-Server ein GpioClx-Treiber ist, sind dies GPIO-Pinnummern. Sie haben dieselbe Bedeutung wie Pinnummern in einer GpioIo-Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="6e450-382">When the pin muxing server is a GpioClx driver, these are GPIO pin numbers and have the same meaning as pin numbers in a GpioIo descriptor.</span></span> 

<span data-ttu-id="6e450-383">Das folgende Beispiel zeigt, wie eine MsftFunctionConfig()-Ressource an einem I2C-Controllertreiber bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-383">The following example shows how one might supply a MsftFunctionConfig() resource to an I2C controller driver.</span></span> 

```cpp
Device(I2C1) 
{ 
    Name(_HID, "BCM2841") 
    Name(_CID, "BCMI2C") 
    Name(_UID, 0x1) 
    Method(_STA) 
    { 
        Return(0xf) 
    } 
    Method(_CRS, 0x0, NotSerialized) 
    { 
        Name(RBUF, ResourceTemplate() 
        { 
            Memory32Fixed(ReadWrite, 0x3F804000, 0x20) 
            Interrupt(ResourceConsumer, Level, ActiveHigh, Shared) { 0x55 } 
            MsftFunctionConfig(Exclusive, PullUp, 4, "\\_SB.GPI0", 0, ResourceConsumer, ) { 2, 3 } 
        }) 
        Return(RBUF) 
    } 
} 
```

<span data-ttu-id="6e450-384">Zusätzlich zum Arbeitsspeicher und den Interruptressourcen, die normalerweise von einem Controllertreiber benötigt werden, wird eine `MsftFunctionConfig()`-Ressource ebenfalls angegeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-384">In addition to the memory and interrupt resources typically required by a controller driver, a `MsftFunctionConfig()` resource is also specified.</span></span> <span data-ttu-id="6e450-385">Diese Ressource ermöglicht es dem I2C-Controllertreiber, die Pins 2 und 3 – vom Geräteknoten am \\_SB.GPIO0 verwaltet – in Funktion 4 mit aktiviertem Pull-Up-Widerstand zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-385">This resource enables the I2C controller driver to put pins 2 and 3 - managed by the device node at \\_SB.GPIO0 – in function 4 with pull-up resistor enabled.</span></span> 

## <a name="supporting-muxing-support-in-gpioclx-client-drivers"></a><span data-ttu-id="6e450-386">Unterstützen der Muxing-Unterstützung im GpioClx-Clienttreiber</span><span class="sxs-lookup"><span data-stu-id="6e450-386">Supporting muxing support in GpioClx client drivers</span></span> 

`GpioClx` <span data-ttu-id="6e450-387">verfügt über integrierte Unterstützung für Pin-Muxing.</span><span class="sxs-lookup"><span data-stu-id="6e450-387">has built-in support for pin muxing.</span></span> <span data-ttu-id="6e450-388">GpioClx-Miniporttreiber (auch als „GpioClx-Clienttreiber“ bezeichnet) steuern die GPIO-Controller-Hardware.</span><span class="sxs-lookup"><span data-stu-id="6e450-388">GpioClx miniport drivers (also referred to as “GpioClx client drivers”), drive GPIO controller hardware.</span></span> <span data-ttu-id="6e450-389">Ab Windows 10 Build 14327 können GpioClx-Miniporttreiber durch die Implementierung von zwei neuen DDIs Unterstützung für Pin-Muxing hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="6e450-389">As of Windows 10 build 14327, GpioClx miniport drivers can add support for pin muxing by implementing two new DDIs:</span></span> 

* <span data-ttu-id="6e450-390">CLIENT_ConnectFunctionConfigPins – Aufgerufen von `GpioClx`, damit der Miniporttreiber die angegebene Muxing-Konfiguration anwendet.</span><span class="sxs-lookup"><span data-stu-id="6e450-390">CLIENT_ConnectFunctionConfigPins – called by `GpioClx` to command the miniport driver to apply the specified muxing configuration.</span></span> 
* <span data-ttu-id="6e450-391">CLIENT_ConnectFunctionConfigPins – Aufgerufen von `GpioClx`, damit der Miniporttreiber die angegebene Muxing-Konfiguration rückgängig macht.</span><span class="sxs-lookup"><span data-stu-id="6e450-391">CLIENT_DisconnectFunctionConfigPins – called by `GpioClx` to command the miniport driver to revert the muxing configuration.</span></span> 

<span data-ttu-id="6e450-392">Unter [GpioClx-Ereignisrückruffunktionen](https://msdn.microsoft.com/library/windows/hardware/hh439464.aspx) finden Sie eine Beschreibung dieser Routinen.</span><span class="sxs-lookup"><span data-stu-id="6e450-392">See [GpioClx Event Callback Functions](https://msdn.microsoft.com/library/windows/hardware/hh439464.aspx) for a description of these routines.</span></span>

<span data-ttu-id="6e450-393">Zusätzlich zu diesen beiden neuen DDIs, sollten bestehende DDIs auf Pin-Muxing-Kompatibilität überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-393">In addition to these two new DDIs, existing DDIs should be audited for pin muxing compatibility:</span></span> 

* <span data-ttu-id="6e450-394">CLIENT_ConnectIoPins/CLIENT_ConnectInterrupt – CLIENT_ConnectIoPins wird von GpioClx aufgerufen, damit der Miniporttreiber einen Satz Pins für die GPIO-Eingabe oder -Ausgabe konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="6e450-394">CLIENT_ConnectIoPins/CLIENT_ConnectInterrupt – CLIENT_ConnectIoPins is called by GpioClx to command the miniport driver to configure a set pins for GPIO input or output.</span></span> <span data-ttu-id="6e450-395">GPIO und MsftFunctionConfig schließen sich gegenseitig aus, d.h. ein Pin wird nie mit GPIO und MsftFunctionConfig gleichzeitig verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="6e450-395">GPIO is mutually exclusive with MsftFunctionConfig, meaning a pin will never be connected for GPIO and MsftFunctionConfig at the same time.</span></span> <span data-ttu-id="6e450-396">Da eine standardmäßige Pinfunktion von GPIO nicht benötigt wird, muss ein Pin nicht unbedingt an ein GPIO gemuxt werden, wenn ConnectIoPins aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-396">Since a pin’s default function is not required to be GPIO, a pin may not necessarily not be muxed to GPIO when ConnectIoPins is called.</span></span> <span data-ttu-id="6e450-397">ConnectIoPins ist erforderlich, um alle Vorgänge auszuführen, die erforderlich sind, um den Pin bereit für GPIO zu machen, einschließlich des Muxing-Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="6e450-397">ConnectIoPins is required to perform all operations necessary to make the pin ready for GPIO IO, including muxing operations.</span></span> <span data-ttu-id="6e450-398">*CLIENT_ConnectInterrupt* sollte sich ähnlich verhalten, da Interrupts als Sonderfall von GPIO-Eingaben angesehen werden können.</span><span class="sxs-lookup"><span data-stu-id="6e450-398">*CLIENT_ConnectInterrupt* should behave similarly, since interrupts can be thought of as a special case of GPIO input.</span></span> 
* <span data-ttu-id="6e450-399">CLIENT_DisconnectIoPins/CLIENT_DisconnectInterrupt – Diese Routine sollte Pins in den Zustand zurückversetzen, in dem sie waren, als CLIENT_ConnectIoPins/CLIENT_ConnectInterrupt aufgerufen wurde, es sei denn, das PreserveConfiguration-Flag ist angegeben.</span><span class="sxs-lookup"><span data-stu-id="6e450-399">CLIENT_DisconnectIoPins/CLIENT_DisconnectInterrupt – These routine should return pins to the state they were in when CLIENT_ConnectIoPins/CLIENT_ConnectInterrupt was called, unless the PreserveConfiguration flag is specified.</span></span> <span data-ttu-id="6e450-400">Zusätzlich zum Wiederherstellen der Richtung des Pins auf ihren Standardzustand, sollte der Miniport auch jeden Pin-Muxing-Zustand in den Zustand zurückversetzen, in dem er war, als die Routine _Connect aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="6e450-400">In addition to reverting the direction of pins to their default state, the miniport should also revert each pin’s muxing state to the state it was in when the _Connect routine was called.</span></span> 

<span data-ttu-id="6e450-401">Nehmen wir beispielsweise an, dass die Muxing-Standardkonfiguration eines Pins UART ist und dass der Pin auch als GPIO verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-401">For example, assume that a pin’s default muxing configuration is UART, and the pin can also be used as GPIO.</span></span> <span data-ttu-id="6e450-402">Wenn CLIENT_ConnectIoPins aufgerufen wird, um den Pin für GPIO zu verbinden, sollte der Pin auf GPIO gemuxt werden; bei CLIENT_DisconnectIoPins sollte der Pin zurück auf UART gemuxt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-402">When CLIENT_ConnectIoPins is called to connect the pin for GPIO, it should mux the pin to GPIO, and in CLIENT_DisconnectIoPins, it should mux the pin back to UART.</span></span> <span data-ttu-id="6e450-403">Im Allgemeinen sollten die _Disconnect-Routinen Vorgänge widerrufen, die von _Connect Routinen durchgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="6e450-403">In general, the _Disconnect routines should undo operations done by the _Connect routines.</span></span> 

## <a name="supporting-muxing-in-spbcx-and-sercx-controller-drivers"></a><span data-ttu-id="6e450-404">Unterstützen von Muxing bei SpbCx- und SerCx-Controllertreibern</span><span class="sxs-lookup"><span data-stu-id="6e450-404">Supporting muxing in SpbCx and SerCx controller drivers</span></span> 

<span data-ttu-id="6e450-405">Ab Windows 10 Build 14327 enthalten die `SpbCx`- und `SerCx`-Frameworks integrierte Unterstützung für Pin-Muxing, die die `SpbCx`- und `SerCx`-Controllertreiber zu Pin-Muxing-Clients macht, ohne Codeänderungen an den Controllertreibern selbst.</span><span class="sxs-lookup"><span data-stu-id="6e450-405">As of Windows 10 build 14327, the `SpbCx` and `SerCx` frameworks contain built-in support for pin muxing that enables `SpbCx` and `SerCx` controller drivers to be pin muxing clients without any code changes to the controller drivers themselves.</span></span> <span data-ttu-id="6e450-406">Durch die Erweiterung löst jeder periphere SpbCx-/SerCx-Treibern, der mit einem Muxing-aktivierten SpbCx-/SerCx-Controllertreiber verbunden ist, eine Pin-Muxing-Aktivität aus.</span><span class="sxs-lookup"><span data-stu-id="6e450-406">By extension, any SpbCx/SerCx peripheral driver that connects to a muxing-enabled SpbCx/SerCx controller driver will trigger pin muxing activity.</span></span> 

<span data-ttu-id="6e450-407">Das folgende Diagramm zeigt die Abhängigkeiten zwischen den einzelnen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="6e450-407">The following diagram shows the dependencies between each of these components.</span></span> <span data-ttu-id="6e450-408">Wie Sie sehen können, eröffnet das Pin-Muxing eine Abhängigkeit der SerCx- und SpbCx-Controllertreiber vom GPIO-Treiber, der in der Regel für Muxing zuständig ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-408">As you can see, pin muxing introduces a dependency from SerCx and SpbCx controller drivers to the GPIO driver, which is usually responsible for muxing.</span></span> 

![Pin-Muxing-Abhängigkeit](images/usermode-access-diagram-2.png)

<span data-ttu-id="6e450-410">Bei Gerätinitialisierung analysieren die `SpbCx`- und `SerCx`-Frameworks alle `MsftFunctionConfig()`-Ressourcen, die dem Gerät als Hardwareressourcen bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-410">At device initialization time, the `SpbCx` and `SerCx` frameworks parse all `MsftFunctionConfig()` resources supplied as hardware resources to the device.</span></span> <span data-ttu-id="6e450-411">SpbCx/SerCx erwerben dann Pin-Muxing-Ressourcen bzw. geben diese bei Bedarf frei.</span><span class="sxs-lookup"><span data-stu-id="6e450-411">SpbCx/SerCx then acquire and release the pin muxing resources on demand.</span></span>

`SpbCx` <span data-ttu-id="6e450-412">wendet die Pin-Muxing-Konfiguration in seinem *IRP_MJ_CREATE*-Handler direkt vor Aufruf des [EvtSpbTargetConnect()](https://msdn.microsoft.com/library/windows/hardware/hh450818.aspx)-Rückrufs des Clienttreibers an.</span><span class="sxs-lookup"><span data-stu-id="6e450-412">applies pin muxing configuration in its *IRP_MJ_CREATE* handler, just before calling the client driver’s [EvtSpbTargetConnect()](https://msdn.microsoft.com/library/windows/hardware/hh450818.aspx) callback.</span></span> <span data-ttu-id="6e450-413">Wenn die Muxing-Konfiguration nicht angewendet werden kann, wird der `EvtSpbTargetConnect()`-Rückruf des Controllertreibers nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="6e450-413">If muxing configuration could not be applied, the controller driver’s `EvtSpbTargetConnect()` callback will not be called.</span></span> <span data-ttu-id="6e450-414">Daher kann ein SPB-Controllertreiber davon ausgehen, dass Pins an die SPB-Funktion gemuxt werden, wenn `EvtSpbTargetConnect()` aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-414">Therefore, an SPB controller driver may assume that pins are muxed to the SPB function by the time `EvtSpbTargetConnect()` is called.</span></span>

`SpbCx` <span data-ttu-id="6e450-415">kehrt die Pin-Muxing-Konfiguration in seinem *IRP_MJ_CLOSE*-Handler direkt nach Aufrufen des [EvtSpbTargetDisconnect()](https://msdn.microsoft.com/library/windows/hardware/hh450820.aspx)-Rückruf des Controllertreibers um.</span><span class="sxs-lookup"><span data-stu-id="6e450-415">reverts pin muxing configuration in its *IRP_MJ_CLOSE* handler, just after invoking the controller driver’s [EvtSpbTargetDisconnect()](https://msdn.microsoft.com/library/windows/hardware/hh450820.aspx) callback.</span></span> <span data-ttu-id="6e450-416">Das Ergebnis ist, dass Pins an die SPB-Funktion gemuxt werden, sobald ein peripherer Treiber einen Handle für den SPB-Controllertreiber öffnet. Das Muxing wird entfernt, wenn der periphere Treiber seinen Handle schließt.</span><span class="sxs-lookup"><span data-stu-id="6e450-416">The result is that pins are muxed to the SPB function whenever a peripheral driver opens a handle to the SPB controller driver, and are muxed away when the peripheral driver closes their handle.</span></span>

`SerCx` <span data-ttu-id="6e450-417">verhält sich ähnlich.</span><span class="sxs-lookup"><span data-stu-id="6e450-417">behaves similarly.</span></span> `SerCx` <span data-ttu-id="6e450-418">erwirbt alle `MsftFunctionConfig()`-Ressourcen in seinem *IRP_MJ_CREATE*-Handler direkt vor Aufruf des [EvtSerCx2FileOpen()](https://msdn.microsoft.com/library/windows/hardware/dn265209.aspx)-Rückruf des Controllertreibers, und gibt alle Ressourcen im IRP_MJ_CLOSE-Handler nach dem [EvtSerCx2FileClose](https://msdn.microsoft.com/library/windows/hardware/dn265208.aspx)-Rückruf des Controllertreibers frei.</span><span class="sxs-lookup"><span data-stu-id="6e450-418">acquires all `MsftFunctionConfig()` resources in its *IRP_MJ_CREATE* handler just before invoking the controller driver’s [EvtSerCx2FileOpen()](https://msdn.microsoft.com/library/windows/hardware/dn265209.aspx) callback, and releases all resources in its IRP_MJ_CLOSE handler, just after invoking the controller driver’s [EvtSerCx2FileClose](https://msdn.microsoft.com/library/windows/hardware/dn265208.aspx) callback.</span></span>

<span data-ttu-id="6e450-419">Die Auswirkung des dynamischen Pin-Muxing für `SerCx` und `SpbCx`-Controllertreiber besteht darin, dass sie Pins tolerieren müssen, bei denen das Muxing von der SPB-/UART-Funktion zu bestimmten Zeiten entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-419">The implication of dynamic pin muxing for `SerCx` and `SpbCx` controller drivers is that they must be able to tolerate pins being muxed away from SPB/UART function at certain times.</span></span> <span data-ttu-id="6e450-420">Controllertreiber müssen wird davon ausgehen, dass Pins nicht gemuxt werden, bis `EvtSpbTargetConnect()` oder `EvtSerCx2FileOpen()` aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6e450-420">Controller drivers need to assume that pins will not be muxed until `EvtSpbTargetConnect()` or `EvtSerCx2FileOpen()` is called.</span></span> <span data-ttu-id="6e450-421">Pins werden nicht zwangsläufig während der folgenden Rückrufe an eine SPB-/UART-Funktion gemuxt.</span><span class="sxs-lookup"><span data-stu-id="6e450-421">Pins are not necessary muxed to SPB/UART function during the following callbacks.</span></span> <span data-ttu-id="6e450-422">Folgende Liste ist nicht vollständig, sie stellt jedoch die am häufigsten verwendeten PNP-Routinen dar, die von Controllertreibern implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-422">The following is not a complete list, but represents the most common PNP routines implemented by controller drivers.</span></span>

* <span data-ttu-id="6e450-423">DriverEntry</span><span class="sxs-lookup"><span data-stu-id="6e450-423">DriverEntry</span></span> 
* <span data-ttu-id="6e450-424">EvtDriverDeviceAdd</span><span class="sxs-lookup"><span data-stu-id="6e450-424">EvtDriverDeviceAdd</span></span> 
* <span data-ttu-id="6e450-425">EvtDevicePrepareHardware/EvtDeviceReleaseHardware</span><span class="sxs-lookup"><span data-stu-id="6e450-425">EvtDevicePrepareHardware/EvtDeviceReleaseHardware</span></span> 
* <span data-ttu-id="6e450-426">EvtDeviceD0Entry/EvtDeviceD0Exit</span><span class="sxs-lookup"><span data-stu-id="6e450-426">EvtDeviceD0Entry/EvtDeviceD0Exit</span></span> 

## <a name="verification"></a><span data-ttu-id="6e450-427">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="6e450-427">Verification</span></span> 

<span data-ttu-id="6e450-428">Wenn Sie bereit sind, Rhproxy zu testen, ist die folgende schrittweise Anleitung hilfreich.</span><span class="sxs-lookup"><span data-stu-id="6e450-428">When you're ready to test rhproxy, it's helpful to use the following step-by-step procedure.</span></span>

1. <span data-ttu-id="6e450-429">Stellen Sie sicher, dass jeder `SpbCx`, `GpioClx` und `SerCx`-Controllertreiber geladen und ordnungsgemäß ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="6e450-429">Verify that each `SpbCx`, `GpioClx`, and `SerCx` controller driver is loading and operating correctly</span></span>
1. <span data-ttu-id="6e450-430">Stellen Sie sicher, dass `rhproxy` im System vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="6e450-430">Verify that `rhproxy` is present on the system.</span></span> <span data-ttu-id="6e450-431">In einigen Editionen und Builds von Windows ist er nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="6e450-431">Some editions and builds of Windows do not have it.</span></span>
1. <span data-ttu-id="6e450-432">Kompilieren und laden Sie den Rhproxy-Knoten mit</span><span class="sxs-lookup"><span data-stu-id="6e450-432">Compile and load your rhproxy node using</span></span> `ACPITABL.dat`
1. <span data-ttu-id="6e450-433">Überprüfen Sie, ob der `rhproxy`-Geräteknoten vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-433">Verify that the `rhproxy` device node exists</span></span>
1. <span data-ttu-id="6e450-434">Überprüfen Sie, dass `rhproxy` geladen ist und startet</span><span class="sxs-lookup"><span data-stu-id="6e450-434">Verify that `rhproxy` is loading and starting</span></span>
1. <span data-ttu-id="6e450-435">Stellen Sie sicher, dass die erwarteten Geräte für den Benutzermodus verfügbar gemacht werden</span><span class="sxs-lookup"><span data-stu-id="6e450-435">Verify that the expected devices are exposed to usermode</span></span>
1. <span data-ttu-id="6e450-436">Stellen Sie sicher, dass Sie mit jedem Gerät über die Befehlszeile interagieren können</span><span class="sxs-lookup"><span data-stu-id="6e450-436">Verify that you can interact with each device from the command line</span></span>
1. <span data-ttu-id="6e450-437">Stellen Sie sicher, dass Sie mit jedem Gerät über die UWP-App interagieren können</span><span class="sxs-lookup"><span data-stu-id="6e450-437">Verify that you can interact with each device from a UWP app</span></span>
1. <span data-ttu-id="6e450-438">Führen Sie HLK-Tests aus</span><span class="sxs-lookup"><span data-stu-id="6e450-438">Run HLK tests</span></span>

### <a name="verify-controller-drivers"></a><span data-ttu-id="6e450-439">Überprüfen Sie die Controller-Treiber</span><span class="sxs-lookup"><span data-stu-id="6e450-439">Verify controller drivers</span></span>

<span data-ttu-id="6e450-440">Da „rhproxy” andere Geräte im System für den Benutzermodus verfügbar macht, funktioniert es nur, wenn diese Geräte bereits verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-440">Since rhproxy exposes other devices on the system to usermode, it only works if those devices are already working.</span></span> <span data-ttu-id="6e450-441">Der erste Schrittbesteht darin, zu überprüfen, ob die Geräte – die I2C, SPI, GPIO-Controller, die Sie verfügbar machen möchten – bereits funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-441">The first step is to verify that those devices - the I2C, SPI, GPIO controllers you wish to expose - are already working.</span></span>

<span data-ttu-id="6e450-442">Führen Sie an einer Eingabeaufforderung Folgendes aus</span><span class="sxs-lookup"><span data-stu-id="6e450-442">At the command prompt, run</span></span>
```
devcon status *
```

<span data-ttu-id="6e450-443">Sehen Sie sich die Ausgabe an und stellen Sie sicher, dass alle gewünschten Geräte gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-443">Look at the output and verify that all devices of interest are started.</span></span> <span data-ttu-id="6e450-444">Wenn ein Gerät einen Fehlercode aufweist, müssen Sie das Problem behandeln, sonst wird das Gerät nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="6e450-444">If a device has a problem code, you need to troubleshoot why that device is not loading.</span></span> <span data-ttu-id="6e450-445">Alle Geräte sollten während des anfänglichen Plattform-Starts aktiviert worden sein.</span><span class="sxs-lookup"><span data-stu-id="6e450-445">All devices should have been enabled during initial platform bringup.</span></span> <span data-ttu-id="6e450-446">Die Problembehandlung bei `SpbCx`, `GpioClx` oder `SerCx`-Controllertreibern ist nicht Gegenstand dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="6e450-446">Troubleshooting `SpbCx`, `GpioClx`, or `SerCx` controller drivers is beyond the scope of this document.</span></span>

### <a name="verify-that-rhproxy-is-present-on-the-system"></a><span data-ttu-id="6e450-447">Stellen Sie sicher, dass rhproxy im System vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="6e450-447">Verify that rhproxy is present on the system</span></span>

<span data-ttu-id="6e450-448">Stellen Sie sicher, dass der `rhproxy`-Dienst im System vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="6e450-448">Verify that the `rhproxy` service is present on the system.</span></span>

```
reg query HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\rhproxy
```

<span data-ttu-id="6e450-449">Wenn der Registrierungsschlüssel nicht vorhanden ist, existiert rhproxy nicht auf Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="6e450-449">If the reg key is not present, rhproxy doesn't exist on your system.</span></span> <span data-ttu-id="6e450-450">Rhproxy befindet sich auf allen Builds von IoT Core und Windows Enterprise-Build 15063 und höher.</span><span class="sxs-lookup"><span data-stu-id="6e450-450">Rhproxy is present on all builds of IoT Core and Windows Enterprise build 15063 and later.</span></span>

### <a name="compile-and-load-asl-with-acpitabldat"></a><span data-ttu-id="6e450-451">Kompilieren und Laden von ASL mit ACPITABL.dat</span><span class="sxs-lookup"><span data-stu-id="6e450-451">Compile and load ASL with ACPITABL.dat</span></span> 

<span data-ttu-id="6e450-452">Nachdem Sie einen Rhproxy-ASL-Knoten erstellt haben, ist es Zeit, diesen zu kompilieren und zu laden.</span><span class="sxs-lookup"><span data-stu-id="6e450-452">Now that you've authored an rhproxy ASL node, it's time to compile and load it.</span></span> <span data-ttu-id="6e450-453">Sie können den rhproxy-Knoten in einer eigenständigen AML-Datei kompilieren, die den System-ACPI-Tabellen hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-453">You can compile the rhproxy node into a standalone AML file that can be appended to the system ACPI tables.</span></span> <span data-ttu-id="6e450-454">Wenn Sie Zugriff auf Ihre System-ACPI-Quellen haben, können Sie alternativ den rhproxy-Knoten direkt auf Ihrer Plattform-ACPI-Tabellen einfügen.</span><span class="sxs-lookup"><span data-stu-id="6e450-454">Alternatively, if you have access to your system's ACPI sources, you can insert the rhproxy node directly to your platform's ACPI tables.</span></span> <span data-ttu-id="6e450-455">Während des anfänglichen Starts ist es möglicherweise einfacher, `ACPITABL.dat` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e450-455">However, during initial bringup it may be easier to use `ACPITABL.dat`.</span></span>

1. <span data-ttu-id="6e450-456">Erstellen Sie eine Datei mit dem Namen yourboard.asl, und fügen Sie den RHPX-Geräteknoten innerhalb eines DefinitionBlock ein:</span><span class="sxs-lookup"><span data-stu-id="6e450-456">Create a file named yourboard.asl and put the RHPX device node inside a DefinitionBlock:</span></span> 
```
DefinitionBlock ("ACPITABL.dat", "SSDT", 1, "MSFT", "RHPROXY", 1)
{
    Scope (\_SB)
    {
        Device(RHPX)
        {
        ...
        }
    }
}
```
2.  <span data-ttu-id="6e450-457">Laden Sie [WDK](https://docs.microsoft.com/windows-hardware/drivers/download-the-wdk) herunter und suchen Sie `asl.exe` unter</span><span class="sxs-lookup"><span data-stu-id="6e450-457">Download the [WDK](https://docs.microsoft.com/windows-hardware/drivers/download-the-wdk) and find `asl.exe` at</span></span> `C:\Program Files (x86)\Windows Kits\10\Tools\x64\ACPIVerify`
3.  <span data-ttu-id="6e450-458">Führen Sie den folgenden Befehl aus, um ACPITABL.dat zu generieren:</span><span class="sxs-lookup"><span data-stu-id="6e450-458">Run the following command to generate ACPITABL.dat:</span></span>
```
asl.exe yourboard.asl
```
4.  <span data-ttu-id="6e450-459">Kopieren Sie die Ausgabedatei ACPITABL.dat nach c:\windows\system32 auf Ihrem System Under Test.</span><span class="sxs-lookup"><span data-stu-id="6e450-459">Copy the resulting ACPITABL.dat file to c:\windows\system32 on your system under test.</span></span>
5.  <span data-ttu-id="6e450-460">Aktivieren Sie Testsigning auf Ihrem System Under Test:</span><span class="sxs-lookup"><span data-stu-id="6e450-460">Turn on testsigning on your system under test:</span></span>
```
bcdedit /set testsigning on
```
6.  <span data-ttu-id="6e450-461">Starten Sie das System Under Test neu.</span><span class="sxs-lookup"><span data-stu-id="6e450-461">Reboot the system under test.</span></span> <span data-ttu-id="6e450-462">Das System fügt die ACPI-Tabellen, die in ACPITABL.dat definiert sind, zu den System-Firmware-Tabellen hinzu.</span><span class="sxs-lookup"><span data-stu-id="6e450-462">The system will append the ACPI tables defined in ACPITABL.dat to the system firmware tables.</span></span>

### <a name="verify-that-the-rhproxy-device-node-exists"></a><span data-ttu-id="6e450-463">Überprüfen Sie, ob der rhproxy-Geräteknoten vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="6e450-463">Verify that the rhproxy device node exists</span></span>

<span data-ttu-id="6e450-464">Führen Sie den folgenden Befehl zum Auflisten des rhproxy-Geräteknotens aus.</span><span class="sxs-lookup"><span data-stu-id="6e450-464">Run the following command to enumerate the rhproxy device node.</span></span>
```
devcon status *msft8000
```
<span data-ttu-id="6e450-465">Die Ausgabe von devcon sollte anzeigen, dass das Gerät vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="6e450-465">The output of devcon should indicate that the device is present.</span></span> <span data-ttu-id="6e450-466">Wenn der Geräteknoten nicht vorhanden ist, wurden die ACPI-Tabellen nicht erfolgreich dem System hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6e450-466">If the device node is not present, the ACPI tables were not successfully added to the system.</span></span>

### <a name="verify-that-rhproxy-is-loading-and-starting"></a><span data-ttu-id="6e450-467">Überprüfen Sie, dass rhproxy geladen ist und startet</span><span class="sxs-lookup"><span data-stu-id="6e450-467">Verify that rhproxy is loading and starting</span></span>

<span data-ttu-id="6e450-468">Überprüfen Sie den Status von rhproxy:</span><span class="sxs-lookup"><span data-stu-id="6e450-468">Check the status of rhproxy:</span></span>
```
devcon status *msft8000
```
<span data-ttu-id="6e450-469">Wenn die Ausgabe angibt, dass rhproxy gestartet wurde, wurde rhproxy geladen und erfolgreich gestartet.</span><span class="sxs-lookup"><span data-stu-id="6e450-469">If the output indicates that rhproxy is started, rhproxy has loaded and started successfully.</span></span> <span data-ttu-id="6e450-470">Wenn ein Fehlercode angezeigt wird, müssen Sie dies untersuchen.</span><span class="sxs-lookup"><span data-stu-id="6e450-470">If you see a problem code, you need to investigate.</span></span> <span data-ttu-id="6e450-471">Einige häufige Problemcodes sind:</span><span class="sxs-lookup"><span data-stu-id="6e450-471">Some common problem codes are:</span></span>
* <span data-ttu-id="6e450-472">Problem 51 – `CM_PROB_WAITING_ON_DEPENDENCY` -Das System startet rhproxy nicht, da eine der Abhängigkeiten nicht geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="6e450-472">Problem 51 - `CM_PROB_WAITING_ON_DEPENDENCY` - The system is not starting rhproxy because one of it's dependencies has failed to load.</span></span> <span data-ttu-id="6e450-473">Dies bedeutet, dass die Ressourcen auf rhproxy auf einen ungültigen ACPI-Knoten hinweisen, oder dass die Zielgeräte nicht gestartet wurden.</span><span class="sxs-lookup"><span data-stu-id="6e450-473">This means that either the resources passed to rhproxy point to invalid ACPI nodes, or the target devices are not starting.</span></span> <span data-ttu-id="6e450-474">Überprüfen Sie zunächst, dass alle Geräte erfolgreich ausgeführt werden (siehe 'Überprüfen Sie die Controller-Treiber' weiter oben).</span><span class="sxs-lookup"><span data-stu-id="6e450-474">First, double check that all devices are running successfully (see 'Verify controller drivers' above).</span></span> <span data-ttu-id="6e450-475">Anschließend überprüfen Sie Ihre ASL und stellen Sie sicher, dass alle Pfade für die Ressource (z.B. `\_SB.I2C1`) korrekt sind, und auf gültige Knoten in Ihrem DSDT hinweisen.</span><span class="sxs-lookup"><span data-stu-id="6e450-475">Then, double check your ASL and ensure that all your resource paths (e.g. `\_SB.I2C1`) are correct and point to valid nodes in your DSDT.</span></span>
* <span data-ttu-id="6e450-476">Problem 10: `CM_PROB_FAILED_START` -Rhproxy konnte nicht gestartet werden, wahrscheinlich aufgrund eines Ressourceananalyseproblems.</span><span class="sxs-lookup"><span data-stu-id="6e450-476">Problem 10 - `CM_PROB_FAILED_START` - Rhproxy failed to start, most likely because of a resource parsing issue.</span></span> <span data-ttu-id="6e450-477">Überprüfen Sie die ASL und Ressourceindizes in der DSD, und stellen Sie sicher, dass die GPIO-Ressourcen in zunehmender Pin-Reihenfolge angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6e450-477">Go over your ASL and double check resource indices in the DSD, and verify that GPIO resources are specified in increasing pin number order.</span></span>

### <a name="verify-that-the-expected-devices-are-exposed-to-usermode"></a><span data-ttu-id="6e450-478">Stellen Sie sicher, dass die erwarteten Geräte für den Benutzermodus verfügbar gemacht werden</span><span class="sxs-lookup"><span data-stu-id="6e450-478">Verify that the expected devices are exposed to usermode</span></span>

<span data-ttu-id="6e450-479">Wenn rhproxy ausgeführt wird, sollte es Geräte-Schnittstellen erstellt haben, auf die vom Benutzermodus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e450-479">Now that rhproxy is running, it should have created devices interfaces that can be accessed by usermode.</span></span> <span data-ttu-id="6e450-480">Wir verwenden einige Befehlszeilentools zum Aufzählen von Geräten und sehen, ob sie vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6e450-480">We will use several command line tools to enumerate devices and see that they're present.</span></span>

<span data-ttu-id="6e450-481">Klon der [https://github.com/ms-iot/samples](https://github.com/ms-iot/samples) -Repository und erstellen die `GpioTestTool`, `I2cTestTool`, `SpiTestTool`, und `Mincomm` Beispiele.</span><span class="sxs-lookup"><span data-stu-id="6e450-481">Clone the [https://github.com/ms-iot/samples](https://github.com/ms-iot/samples) repository and build the `GpioTestTool`, `I2cTestTool`, `SpiTestTool`, and `Mincomm` samples.</span></span> <span data-ttu-id="6e450-482">Kopieren Sie die Tools auf Ihr Testgerät, und verwenden Sie die folgenden Befehle zur Auflistung der Geräte.</span><span class="sxs-lookup"><span data-stu-id="6e450-482">Copy the tools to your device under test and use the following commands to enumerate devices.</span></span>
```
I2cTestTool.exe -list
SpiTestTool.exe -list
GpioTestTool.exe -list
MinComm.exe -list
```
<span data-ttu-id="6e450-483">Sie sollten Ihre Geräte und die Anzeigenamen sehen.</span><span class="sxs-lookup"><span data-stu-id="6e450-483">You should see your devices and friendly names listed.</span></span> <span data-ttu-id="6e450-484">Wenn die richtigen Geräte und Anzeigenamen nicht angezeigt werden, überprüfen Sie Ihre ASL.</span><span class="sxs-lookup"><span data-stu-id="6e450-484">If you don't see the right devices and friendly names, double check your ASL.</span></span>

### <a name="verify-each-device-on-the-command-line"></a><span data-ttu-id="6e450-485">Überprüfen Sie jedes Gerät in der Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="6e450-485">Verify each device on the command line</span></span>

<span data-ttu-id="6e450-486">Der nächste Schrittist die Verwendung der Befehlszeilentools, um andere Geräte zu öffnen und mit ihnen zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-486">The next step is to use the command line tools to open and interact with the devices.</span></span>

<span data-ttu-id="6e450-487">I2CTestTool-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e450-487">I2CTestTool example:</span></span>
```
I2cTestTool.exe 0x55 I2C1
> write {1 2 3}
> read 3
> writeread {1 2 3} 3
```

<span data-ttu-id="6e450-488">SpiTestTool-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e450-488">SpiTestTool example:</span></span>
```
SpiTestTool.exe -n SPI1
> write {1 2 3}
> read 3
```

<span data-ttu-id="6e450-489">GpioTestTool-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e450-489">GpioTestTool example:</span></span>
```
GpioTestTool.exe 12
> setdrivemode output
> write 0
> write 1
> setdrivemode input
> read
> interrupt on
> interrupt off
```

<span data-ttu-id="6e450-490">MinComm (seriell) - Beispiel</span><span class="sxs-lookup"><span data-stu-id="6e450-490">MinComm (serial) example.</span></span> <span data-ttu-id="6e450-491">Schließen Sie Rx an Tx an, vor dem ausführen von:</span><span class="sxs-lookup"><span data-stu-id="6e450-491">Connect Rx to Tx before running:</span></span>
```
MinComm "\\?\ACPI#FSCL0007#3#{86e0d1e0-8089-11d0-9ce4-08003e301f73}\0000000000000006"
(type characters and see them echoed back)
```

### <a name="verify-each-device-from-a-uwp-app"></a><span data-ttu-id="6e450-492">Überprüfen Sie jedes Gerät von einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="6e450-492">Verify each device from a UWP app</span></span>

<span data-ttu-id="6e450-493">Verwenden Sie die folgenden Beispiele, um zu überprüfen, ob die Geräte ab UWP funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6e450-493">Use the following samples to validate that devices work from UWP.</span></span>

| <span data-ttu-id="6e450-494">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6e450-494">Sample</span></span> | <span data-ttu-id="6e450-495">Link</span><span class="sxs-lookup"><span data-stu-id="6e450-495">Link</span></span> |
|------|------|
| <span data-ttu-id="6e450-496">IoT-GPIO</span><span class="sxs-lookup"><span data-stu-id="6e450-496">IoT-GPIO</span></span> | https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/IoT-GPIO |
| <span data-ttu-id="6e450-497">IoT-I2C</span><span class="sxs-lookup"><span data-stu-id="6e450-497">IoT-I2C</span></span> | https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/IoT-I2C | 
| <span data-ttu-id="6e450-498">IoT-SPI</span><span class="sxs-lookup"><span data-stu-id="6e450-498">IoT-SPI</span></span> | https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/IoT-SPI |
| <span data-ttu-id="6e450-499">CustomSerialDeviceAccess</span><span class="sxs-lookup"><span data-stu-id="6e450-499">CustomSerialDeviceAccess</span></span> | https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomSerialDeviceAccess |

### <a name="run-the-hlk-tests"></a><span data-ttu-id="6e450-500">Führen Sie die HLK-Tests aus</span><span class="sxs-lookup"><span data-stu-id="6e450-500">Run the HLK Tests</span></span>

<span data-ttu-id="6e450-501">Herunterladen des [Hardware Lab Kit (HLK)](https://docs.microsoft.com/windows-hardware/test/hlk/windows-hardware-lab-kit).</span><span class="sxs-lookup"><span data-stu-id="6e450-501">Download the [Hardware Lab Kit (HLK)](https://docs.microsoft.com/windows-hardware/test/hlk/windows-hardware-lab-kit).</span></span> <span data-ttu-id="6e450-502">Die folgenden Test sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="6e450-502">The following tests are availble:</span></span>
 * [<span data-ttu-id="6e450-503">GPIO WinRT-Funktions- und Belastungstests</span><span class="sxs-lookup"><span data-stu-id="6e450-503">GPIO WinRT Functional and Stress Tests</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/f1fc0922-1186-48bd-bfcd-c7385a2f6f96)
 * [<span data-ttu-id="6e450-504">I2C WinRT-Schreibtests (EEPROM erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-504">I2C WinRT Write Tests (EEPROM Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/2ab0df1b-3369-4aaf-a4d5-d157cb7bf578)
 * [<span data-ttu-id="6e450-505">I2C WinRT-Lesetests (EEPROM erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-505">I2C WinRT Read Tests (EEPROM Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/ca91c2d2-4615-4a1b-928e-587ab2b69b04)
 * [<span data-ttu-id="6e450-506">I2C WinRT nicht vorhandene untergeordneten Adresse - Tests</span><span class="sxs-lookup"><span data-stu-id="6e450-506">I2C WinRT Nonexistent Slave Address Tests</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/2746ad72-fe5c-4412-8231-f7ed53d95e71)
 * [<span data-ttu-id="6e450-507">I2C WinRT erweiterte Funktionstests (Mbed LPC1768 erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-507">I2C WinRT Advanced Functional Tests (mbed LPC1768 Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/a60f5a94-12b2-4905-8416-e9774f539f1d)
 * [<span data-ttu-id="6e450-508">SPI WinRT Taktfrequenz-Überprüfungstest (Mbed LPC1768 erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-508">SPI WinRT Clock Frequency Verification Tests (mbed LPC1768 Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/50cf9ccc-bbd3-4514-979f-b0499cb18ed8)
 * [<span data-ttu-id="6e450-509">SPI WinRT IO Übertragungstests (Mbed LPC1768 erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-509">SPI WinRT IO Transfer Tests (mbed LPC1768 Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/00c892e8-c226-4c71-9c2a-68349fed7113)
 * [<span data-ttu-id="6e450-510">SPI WinRT Stride-Überprüfungstests</span><span class="sxs-lookup"><span data-stu-id="6e450-510">SPI WinRT Stride Verification Tests</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/20c6b079-62f7-4067-953f-e252bd271938)
 * [<span data-ttu-id="6e450-511">SPI WinRT Übertragungstests für die Lückenerkennung (Mbed LPC1768 erforderlich)</span><span class="sxs-lookup"><span data-stu-id="6e450-511">SPI WinRT Transfer Gap Detection Tests (mbed LPC1768 Required)</span></span>](https://docs.microsoft.com/windows-hardware/test/hlk/testref/6da79d04-940b-4c49-8f00-333bf0cfbb19)

<span data-ttu-id="6e450-512">Bei der Auswahl des rhproxy-Geräteknotens im HLK-Manager werden die entsprechenden Tests automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="6e450-512">When you select the rhproxy device node in HLK manager, the applicable tests will automatically be selected.</span></span>

<span data-ttu-id="6e450-513">Wählen Sie im HLK-Manager „Ressourcen-Hub-Proxygerät“:</span><span class="sxs-lookup"><span data-stu-id="6e450-513">In the HLK manager, select “Resource Hub Proxy device”:</span></span>

![HLK-Manager-Screenshot](images/usermode-hlk-1.png)

<span data-ttu-id="6e450-515">Klicken Sie dann auf der Registerkarte „Tests“ und wählen Sie I2C WinRT-, Gpio WinRT- und Spi WinRT-Tests.</span><span class="sxs-lookup"><span data-stu-id="6e450-515">Then click the Tests tab, and select I2C WinRT, Gpio WinRT, and Spi WinRT tests.</span></span>

![HLK-Manager-Screenshot](images/usermode-hlk-2.png)

<span data-ttu-id="6e450-517">Klicken Sie auf „Ausgewählte ausführen“.</span><span class="sxs-lookup"><span data-stu-id="6e450-517">Click Run Selected.</span></span> <span data-ttu-id="6e450-518">Weitere Dokumentation zu jedem Test steht zur Verfügung, wenn Sie mit der rechten Maustaste auf den Test klicken und anschließend auf „Testbeschreibung“ klicken.</span><span class="sxs-lookup"><span data-stu-id="6e450-518">Further documentation on each test is available by right clicking on the test and clicking “Test Description.”</span></span>

## <a name="resources"></a><span data-ttu-id="6e450-519">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6e450-519">Resources</span></span>

| <span data-ttu-id="6e450-520">Ziel</span><span class="sxs-lookup"><span data-stu-id="6e450-520">Destination</span></span> | <span data-ttu-id="6e450-521">Link</span><span class="sxs-lookup"><span data-stu-id="6e450-521">Link</span></span> |
|-------------|------|
| <span data-ttu-id="6e450-522">ACPI 5.0-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="6e450-522">ACPI 5.0 specification</span></span> | http://acpi.info/spec.htm |
| <span data-ttu-id="6e450-523">Asl.exe (Microsoft ASL Compiler)</span><span class="sxs-lookup"><span data-stu-id="6e450-523">Asl.exe (Microsoft ASL Compiler)</span></span> | https://msdn.microsoft.com/library/windows/hardware/dn551195.aspx |
| <span data-ttu-id="6e450-524">Windows.Devices.Gpio</span><span class="sxs-lookup"><span data-stu-id="6e450-524">Windows.Devices.Gpio</span></span>  | https://msdn.microsoft.com/library/windows/apps/windows.devices.gpio.aspx | 
| <span data-ttu-id="6e450-525">Windows.Devices.I2c</span><span class="sxs-lookup"><span data-stu-id="6e450-525">Windows.Devices.I2c</span></span> | https://msdn.microsoft.com/library/windows/apps/windows.devices.i2c.aspx |
| <span data-ttu-id="6e450-526">Windows.Devices.Spi</span><span class="sxs-lookup"><span data-stu-id="6e450-526">Windows.Devices.Spi</span></span> | https://msdn.microsoft.com/library/windows/apps/windows.devices.spi.aspx |
| <span data-ttu-id="6e450-527">Windows.Devices.SerialCommunication</span><span class="sxs-lookup"><span data-stu-id="6e450-527">Windows.Devices.SerialCommunication</span></span> | https://msdn.microsoft.com/library/windows/apps/windows.devices.serialcommunication.aspx |
| <span data-ttu-id="6e450-528">Test Authoring and Execution Framework (TAEF)</span><span class="sxs-lookup"><span data-stu-id="6e450-528">Test Authoring and Execution Framework (TAEF)</span></span> | https://msdn.microsoft.com/library/windows/hardware/hh439725.aspx |
| <span data-ttu-id="6e450-529">SpbCx</span><span class="sxs-lookup"><span data-stu-id="6e450-529">SpbCx</span></span> | https://msdn.microsoft.com/library/windows/hardware/hh450906.aspx |
| <span data-ttu-id="6e450-530">GpioClx</span><span class="sxs-lookup"><span data-stu-id="6e450-530">GpioClx</span></span>   | https://msdn.microsoft.com/library/windows/hardware/hh439508.aspx |
| <span data-ttu-id="6e450-531">SerCx</span><span class="sxs-lookup"><span data-stu-id="6e450-531">SerCx</span></span> | https://msdn.microsoft.com/library/windows/hardware/ff546939.aspx |
| <span data-ttu-id="6e450-532">MITT I2C-Tests</span><span class="sxs-lookup"><span data-stu-id="6e450-532">MITT I2C Tests</span></span> | https://msdn.microsoft.com/library/windows/hardware/dn919852.aspx |
| <span data-ttu-id="6e450-533">GpioTestTool</span><span class="sxs-lookup"><span data-stu-id="6e450-533">GpioTestTool</span></span> | https://developer.microsoft.com/windows/iot/samples/GPIOTestTool |
| <span data-ttu-id="6e450-534">I2cTestTool</span><span class="sxs-lookup"><span data-stu-id="6e450-534">I2cTestTool</span></span>   | https://developer.microsoft.com/windows/iot/samples/I2cTestTool | 
| <span data-ttu-id="6e450-535">SpiTestTool</span><span class="sxs-lookup"><span data-stu-id="6e450-535">SpiTestTool</span></span> | https://developer.microsoft.com/windows/iot/samples/spitesttool |
| <span data-ttu-id="6e450-536">MinComm (seriell)</span><span class="sxs-lookup"><span data-stu-id="6e450-536">MinComm (Serial)</span></span> |    https://github.com/ms-iot/samples/tree/develop/MinComm |
| <span data-ttu-id="6e450-537">Hardware Lab Kit (HLK)</span><span class="sxs-lookup"><span data-stu-id="6e450-537">Hardware Lab Kit (HLK)</span></span> | https://msdn.microsoft.com/library/windows/hardware/dn930814.aspx |

## <a name="apendix"></a><span data-ttu-id="6e450-538">Anhang</span><span class="sxs-lookup"><span data-stu-id="6e450-538">Apendix</span></span>

### <a name="appendix-a---raspberry-pi-asl-listing"></a><span data-ttu-id="6e450-539">AnhangA – Raspberry Pi-ASL-Verzeichnis</span><span class="sxs-lookup"><span data-stu-id="6e450-539">Appendix A - Raspberry Pi ASL Listing</span></span>

<span data-ttu-id="6e450-540">Header-Pinout:https://developer.microsoft.com/windows/iot/samples/PinMappingsRPi2</span><span class="sxs-lookup"><span data-stu-id="6e450-540">Header pinout: https://developer.microsoft.com/windows/iot/samples/PinMappingsRPi2</span></span>

```
DefinitionBlock ("ACPITABL.dat", "SSDT", 1, "MSFT", "RHPROXY", 1)
{

    Scope (\_SB)
    {
        //
        // RHProxy Device Node to enable WinRT API
        //
        Device(RHPX)
        {
            Name(_HID, "MSFT8000")
            Name(_CID, "MSFT8000")
            Name(_UID, 1)

            Name(_CRS, ResourceTemplate()
            {
                // Index 0
                SPISerialBus(              // SCKL - GPIO 11 - Pin 23
                                           // MOSI - GPIO 10 - Pin 19
                                           // MISO - GPIO 9  - Pin 21
                                           // CE0  - GPIO 8  - Pin 24
                    0,                     // Device selection (CE0)
                    PolarityLow,           // Device selection polarity
                    FourWireMode,          // wiremode
                    0,                     // databit len: placeholder
                    ControllerInitiated,   // slave mode
                    0,                     // connection speed: placeholder
                    ClockPolarityLow,      // clock polarity: placeholder
                    ClockPhaseFirst,       // clock phase: placeholder
                    "\\_SB.SPI0",          // ResourceSource: SPI bus controller name
                    0,                     // ResourceSourceIndex
                                           // Resource usage
                    )                      // Vendor Data

                // Index 1
                SPISerialBus(              // SCKL - GPIO 11 - Pin 23
                                           // MOSI - GPIO 10 - Pin 19
                                           // MISO - GPIO 9  - Pin 21
                                           // CE1  - GPIO 7  - Pin 26
                    1,                     // Device selection (CE1)
                    PolarityLow,           // Device selection polarity
                    FourWireMode,          // wiremode
                    0,                     // databit len: placeholder
                    ControllerInitiated,   // slave mode
                    0,                     // connection speed: placeholder
                    ClockPolarityLow,      // clock polarity: placeholder
                    ClockPhaseFirst,       // clock phase: placeholder
                    "\\_SB.SPI0",          // ResourceSource: SPI bus controller name
                    0,                     // ResourceSourceIndex
                                           // Resource usage
                    )                      // Vendor Data

                // Index 2
                SPISerialBus(              // SCKL - GPIO 21 - Pin 40
                                           // MOSI - GPIO 20 - Pin 38
                                           // MISO - GPIO 19 - Pin 35
                                           // CE1  - GPIO 17 - Pin 11
                    1,                     // Device selection (CE1)
                    PolarityLow,           // Device selection polarity
                    FourWireMode,          // wiremode
                    0,                     // databit len: placeholder
                    ControllerInitiated,   // slave mode
                    0,                     // connection speed: placeholder
                    ClockPolarityLow,      // clock polarity: placeholder
                    ClockPhaseFirst,       // clock phase: placeholder
                    "\\_SB.SPI1",          // ResourceSource: SPI bus controller name
                    0,                     // ResourceSourceIndex
                                           // Resource usage
                    )                      // Vendor Data
                // Index 3
                I2CSerialBus(              // Pin 3 (GPIO2, SDA1), 5 (GPIO3, SCL1)
                    0xFFFF,                // SlaveAddress: placeholder
                    ,                      // SlaveMode: default to ControllerInitiated
                    0,                     // ConnectionSpeed: placeholder
                    ,                      // Addressing Mode: placeholder
                    "\\_SB.I2C1",          // ResourceSource: I2C bus controller name
                    ,
                    ,
                    )                      // VendorData

                // Index 4 - GPIO 4 -
                GpioIO(Shared, PullUp, , , , "\\_SB.GPI0", , , , ) { 4 }
                GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, "\\_SB.GPI0",) { 4 }
                // Index 6 - GPIO 5 -
                GpioIO(Shared, PullUp, , , , "\\_SB.GPI0", , , , ) { 5 }
                GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, "\\_SB.GPI0",) { 5 }
                // Index 8 - GPIO 6 -
                GpioIO(Shared, PullUp, , , , "\\_SB.GPI0", , , , ) { 6 }
                GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, "\\_SB.GPI0",) { 6 }
                // Index 10 - GPIO 12 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 12 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 12 }
                // Index 12 - GPIO 13 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 13 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 13 }
                // Index 14 - GPIO 16 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 16 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 16 }
                // Index 16 - GPIO 18 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 18 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 18 }
                // Index 18 - GPIO 22 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 22 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 22 }
                // Index 20 - GPIO 23 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 23 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 23 }
                // Index 22 - GPIO 24 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 24 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 24 }
                // Index 24 - GPIO 25 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 25 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 25 }
                // Index 26 - GPIO 26 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 26 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 26 }
                // Index 28 - GPIO 27 -
                GpioIO(Shared, PullDown, , , , "\\_SB.GPI0", , , , ) { 27 }
                GpioInt(Edge, ActiveBoth, Shared, PullDown, 0, "\\_SB.GPI0",) { 27 }
                // Index 30 - GPIO 35 -
                GpioIO(Shared, PullUp, , , , "\\_SB.GPI0", , , , ) { 35 }
                GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, "\\_SB.GPI0",) { 35 }
                // Index 32 - GPIO 47 -
                GpioIO(Shared, PullUp, , , , "\\_SB.GPI0", , , , ) { 47 }
                GpioInt(Edge, ActiveBoth, Shared, PullUp, 0, "\\_SB.GPI0",) { 47 }
            })

            Name(_DSD, Package()
            {
                ToUUID("daffd814-6eba-4d8c-8a91-bc9bbf4aa301"),
                Package()
                {
                    // Reference http://www.raspberrypi.org/documentation/hardware/raspberrypi/spi/README.md
                    // SPI 0
                    Package(2) { "bus-SPI-SPI0", Package() { 0, 1 }},                       // Index 0 & 1
                    Package(2) { "SPI0-MinClockInHz", 7629 },                               // 7629 Hz
                    Package(2) { "SPI0-MaxClockInHz", 125000000 },                          // 125 MHz
                    Package(2) { "SPI0-SupportedDataBitLengths", Package() { 8 }},          // Data Bit Length
                    // SPI 1
                    Package(2) { "bus-SPI-SPI1", Package() { 2 }},                          // Index 2
                    Package(2) { "SPI1-MinClockInHz", 30518 },                              // 30518 Hz
                    Package(2) { "SPI1-MaxClockInHz", 125000000 },                          // 125 MHz
                    Package(2) { "SPI1-SupportedDataBitLengths", Package() { 8 }},          // Data Bit Length
                    // I2C1
                    Package(2) { "bus-I2C-I2C1", Package() { 3 }},
                    // GPIO Pin Count and supported drive modes
                    Package (2) { "GPIO-PinCount", 54 },
                    Package (2) { "GPIO-UseDescriptorPinNumbers", 1 },
                    Package (2) { "GPIO-SupportedDriveModes", 0xf },                        // InputHighImpedance, InputPullUp, InputPullDown, OutputCmos
                }
            })
        }
    }
}

```

### <a name="appendix-b---minnowboardmax-asl-listing"></a><span data-ttu-id="6e450-541">AnhangB – MinnowBoardMax-ASL-Verzeichnis</span><span class="sxs-lookup"><span data-stu-id="6e450-541">Appendix B - MinnowBoardMax ASL Listing</span></span>

<span data-ttu-id="6e450-542">Header-Pinout:https://developer.microsoft.com/windows/iot/samples/PinMappingsMBM</span><span class="sxs-lookup"><span data-stu-id="6e450-542">Header pinout: https://developer.microsoft.com/windows/iot/samples/PinMappingsMBM</span></span>

```
DefinitionBlock ("ACPITABL.dat", "SSDT", 1, "MSFT", "RHPROXY", 1)
{
    Scope (\_SB)
    {
        Device(RHPX)
        {
            Name(_HID, "MSFT8000")
            Name(_CID, "MSFT8000")
            Name(_UID, 1)

            Name(_CRS, ResourceTemplate() 
            {  
                // Index 0 
                SPISerialBus(            // Pin 5, 7, 9 , 11 of JP1 for SIO_SPI
                    1,                     // Device selection
                    PolarityLow,           // Device selection polarity
                    FourWireMode,          // wiremode
                    8,                     // databit len
                    ControllerInitiated,   // slave mode
                    8000000,               // Connection speed
                    ClockPolarityLow,      // Clock polarity
                    ClockPhaseSecond,      // clock phase
                    "\\_SB.SPI1",          // ResourceSource: SPI bus controller name
                    0,                     // ResourceSourceIndex
                    ResourceConsumer,      // Resource usage
                    JSPI,                  // DescriptorName: creates name for offset of resource descriptor
                    )                      // Vendor Data  
    
                // Index 1     
                I2CSerialBus(            // Pin 13, 15 of JP1, for SIO_I2C5 (signal)
                    0xFF,                  // SlaveAddress: bus address
                    ,                      // SlaveMode: default to ControllerInitiated
                    400000,                // ConnectionSpeed: in Hz
                    ,                      // Addressing Mode: default to 7 bit
                    "\\_SB.I2C6",          // ResourceSource: I2C bus controller name (For MinnowBoard Max, hardware I2C5(0-based) is reported as ACPI I2C6(1-based))
                    ,
                    ,
                    JI2C,                  // Descriptor Name: creates name for offset of resource descriptor
                    )                      // VendorData
    
                // Index 2
                UARTSerialBus(           // Pin 17, 19 of JP1, for SIO_UART2
                    115200,                // InitialBaudRate: in bits ber second
                    ,                      // BitsPerByte: default to 8 bits
                    ,                      // StopBits: Defaults to one bit
                    0xfc,                  // LinesInUse: 8 1-bit flags to declare line enabled
                    ,                      // IsBigEndian: default to LittleEndian
                    ,                      // Parity: Defaults to no parity
                    ,                      // FlowControl: Defaults to no flow control
                    32,                    // ReceiveBufferSize
                    32,                    // TransmitBufferSize
                    "\\_SB.URT2",          // ResourceSource: UART bus controller name
                    ,
                    ,
                    UAR2,                  // DescriptorName: creates name for offset of resource descriptor
                    )                      
    
                // Index 3
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO2",) {0}  // Pin 21 of JP1 (GPIO_S5[00])
                // Index 4
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO2",) {0} 
    
                // Index 5
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO2",) {1}  // Pin 23 of JP1 (GPIO_S5[01])
                // Index 6
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO2",) {1}
    
                // Index 7
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO2",) {2}  // Pin 25 of JP1 (GPIO_S5[02])
                // Index 8
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO2",) {2} 
    
                // Index 9
                UARTSerialBus(           // Pin 6, 8, 10, 12 of JP1, for SIO_UART1
                    115200,                // InitialBaudRate: in bits ber second
                    ,                      // BitsPerByte: default to 8 bits
                    ,                      // StopBits: Defaults to one bit
                    0xfc,                  // LinesInUse: 8 1-bit flags to declare line enabled
                    ,                      // IsBigEndian: default to LittleEndian
                    ,                      // Parity: Defaults to no parity
                    FlowControlHardware,   // FlowControl: Defaults to no flow control
                    32,                    // ReceiveBufferSize
                    32,                    // TransmitBufferSize
                    "\\_SB.URT1",          // ResourceSource: UART bus controller name
                    ,
                    ,
                    UAR1,              // DescriptorName: creates name for offset of resource descriptor
                    )  
    
                // Index 10
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {62}  // Pin 14 of JP1 (GPIO_SC[62])
                // Index 11
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {62} 

                // Index 12
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {63}  // Pin 16 of JP1 (GPIO_SC[63])
                // Index 13
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {63} 
    
                // Index 14
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {65}  // Pin 18 of JP1 (GPIO_SC[65])
                // Index 15
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {65} 
    
                // Index 16
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {64}  // Pin 20 of JP1 (GPIO_SC[64])
                // Index 17
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {64} 
    
                // Index 18
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {94}  // Pin 22 of JP1 (GPIO_SC[94])
                // Index 19
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {94} 
    
                // Index 20
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {95}  // Pin 24 of JP1 (GPIO_SC[95])
                // Index 21
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {95} 
    
                // Index 22
                GpioIo (Shared, PullNone, 0, 0, IoRestrictionNone, "\\_SB.GPO0",) {54}  // Pin 26 of JP1 (GPIO_SC[54])
                // Index 23
                GpioInt(Edge, ActiveBoth, SharedAndWake, PullNone, 0,"\\_SB.GPO0",) {54}
            })
    
            Name(_DSD, Package() 
            {
                ToUUID("daffd814-6eba-4d8c-8a91-bc9bbf4aa301"),
                Package() 
                {
                    // SPI Mapping
                    Package(2) { "bus-SPI-SPI0", Package() { 0 }},

                    Package(2) { "SPI0-MinClockInHz", 100000 },
                    Package(2) { "SPI0-MaxClockInHz", 15000000 },
                    // SupportedDataBitLengths takes a list of support data bit length
                    // Example : Package(2) { "SPI0-SupportedDataBitLengths", Package() { 8, 7, 16 }},
                    Package(2) { "SPI0-SupportedDataBitLengths", Package() { 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32 }},
                     // I2C Mapping
                    Package(2) { "bus-I2C-I2C5", Package() { 1 }},
                    // UART Mapping
                    Package(2) { "bus-UART-UART2", Package() { 2 }},
                    Package(2) { "bus-UART-UART1", Package() { 9 }},
                }
            })
        }
    }
}
```

### <a name="appendix-c---sample-powershell-script-to-generate-gpio-resources"></a><span data-ttu-id="6e450-543">AnhangC - Beispiel-Powershell-Skript zum Generieren von GPIO-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6e450-543">Appendix C - Sample Powershell script to generate GPIO resources</span></span>

<span data-ttu-id="6e450-544">Das folgende Skript kann zum Generieren der GPIO-Ressourcendeklarationen für Raspberry Pi verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="6e450-544">The following script can be used to generate the GPIO resource declarations for Raspberry Pi:</span></span>

```
$pins = @(
    @{PinNumber=4;PullConfig='PullUp'},
    @{PinNumber=5;PullConfig='PullUp'},
    @{PinNumber=6;PullConfig='PullUp'},
    @{PinNumber=12;PullConfig='PullDown'},
    @{PinNumber=13;PullConfig='PullDown'},
    @{PinNumber=16;PullConfig='PullDown'},
    @{PinNumber=18;PullConfig='PullDown'},
    @{PinNumber=22;PullConfig='PullDown'},
    @{PinNumber=23;PullConfig='PullDown'},
    @{PinNumber=24;PullConfig='PullDown'},
    @{PinNumber=25;PullConfig='PullDown'},
    @{PinNumber=26;PullConfig='PullDown'},
    @{PinNumber=27;PullConfig='PullDown'},
    @{PinNumber=35;PullConfig='PullUp'},
    @{PinNumber=47;PullConfig='PullUp'})
    
# generate the resources
$FIRST_RESOURCE_INDEX = 4
$resourceIndex = $FIRST_RESOURCE_INDEX
$pins | % {
    $a = @"
// Index $resourceIndex - GPIO $($_.PinNumber) - $($_.Name)
GpioIO(Shared, $($_.PullConfig), , , , "\\_SB.GPI0", , , , ) { $($_.PinNumber) }
GpioInt(Edge, ActiveBoth, Shared, $($_.PullConfig), 0, "\\_SB.GPI0",) { $($_.PinNumber) }
"@    
    Write-Host $a
    $resourceIndex += 2;
}
```
