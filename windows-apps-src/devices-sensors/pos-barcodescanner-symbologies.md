---
author: TerryWarwick
title: Arbeiter mit Strichcodescanner-Symbologien
description: Dieser Artikel enthält Informationen über Strichcodescanner-Symbologien.
ms.author: jken
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 8bd1dffe4da7b3725ef7716fe9cf28bdf8eaf34f
ms.sourcegitcommit: 72710baeee8c898b5ab77ceb66d884eaa9db4cb8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2018
ms.locfileid: "3851470"
---
# <a name="working-with-symbologies"></a><span data-ttu-id="bfd58-104">Arbeiten mit Symbologien</span><span class="sxs-lookup"><span data-stu-id="bfd58-104">Working with symbologies</span></span>
<span data-ttu-id="bfd58-105">Eine [Strichcodesymbologie](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) ist eine Zuordnung von Daten zu einem bestimmten Strichcodeformat.</span><span class="sxs-lookup"><span data-stu-id="bfd58-105">A [barcode symbology](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) is the mapping of data to a specific barcode format.</span></span> <span data-ttu-id="bfd58-106">Einige allgemeinen Symbologien enthalten UPC, Code 128, QR-Code und So weiter.</span><span class="sxs-lookup"><span data-stu-id="bfd58-106">Some common symbologies include UPC, Code 128, QR Code, and so on.</span></span>  <span data-ttu-id="bfd58-107">Die universelle Windows-Plattform-Strichcodescanner-APIs ermöglichen einer Anwendung zu steuern, wie der Scanner die Symbologien verarbeitet, ohne manuell den Scanner konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="bfd58-107">The Universal Windows Platform barcode scanner APIs allow an application to control how the scanner processes these symbologies without manually configuring the scanner.</span></span> 

## <a name="determine-which-symbologies-are-supported"></a><span data-ttu-id="bfd58-108">Bestimmen Sie, welche Symbologien unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="bfd58-108">Determine which symbologies are supported</span></span> 
<span data-ttu-id="bfd58-109">Da die Anwendung unterschiedliche Strichcodescannermodelle verschiedener Hersteller verwenden kann, sollten Sie den Scanner befragen, um die Liste der Symbologien zu ermitteln, die er unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bfd58-109">Since your application may be used with different barcode scanner models from multiple manufacturers, you may want to query the scanner to determine the list of symbologies that it supports.</span></span>  <span data-ttu-id="bfd58-110">Dies kann nützlich sein, wenn die Anwendung eine bestimmte Symbologie erfordert, die möglicherweise nicht von allen Scannern unterstützt wird oder Sie müssen Symbologien aktivieren, die entweder manuell oder programmgesteuert auf dem Scanner deaktiviert wurden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-110">This can be useful if your application requires a specific symbology that may not be supported by all scanners or you need to enable symbologies that have been either manually or programmatically disabled on the scanner.</span></span>

<span data-ttu-id="bfd58-111">Sobald Sie ein [BarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner)-Objekt über [BarcodeScanner.FromIdAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) erhalten haben, rufen Sie [GetSupportedSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getsupportedsymbologiesasync#Windows_Devices_PointOfService_BarcodeScanner_GetSupportedSymbologiesAsync) auf, um eine Liste der Symbologien abzurufen, die vom Gerät unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-111">Once you have a [BarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner) object by using [BarcodeScanner.FromIdAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync), call [GetSupportedSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getsupportedsymbologiesasync#Windows_Devices_PointOfService_BarcodeScanner_GetSupportedSymbologiesAsync) to obtain a list of symbologies supported by the device.</span></span>

<span data-ttu-id="bfd58-112">Das folgende Beispiel ruft eine Liste der unterstützten Symbologien des-Strichcodescanners ab, und zeigt sie in einem Textblock:</span><span class="sxs-lookup"><span data-stu-id="bfd58-112">The following example gets a list of the supported symbologies of the barcode scanner, and displays them in a text block:</span></span>

```cs
private void DisplaySupportedSymbologies(BarcodeScanner barcodeScanner, TextBlock textBlock) 
{
    var supportedSymbologies = await barcodeScanner.GetSupportedSymbologiesAsync();

    foreach (uint item in supportedSymbologies)
    {
        string symbology = BarcodeSymbologies.GetName(item);
        textBlock.Text += (symbology + "\n");
    }
}
```

## <a name="determine-if-a-specific-symbology-is-supported"></a><span data-ttu-id="bfd58-113">Bestimmen Sie, ob eine bestimmte Symbologie unterstützt wird</span><span class="sxs-lookup"><span data-stu-id="bfd58-113">Determine if a specific symbology is supported</span></span>
<span data-ttu-id="bfd58-114">Um festzustellen, ob der Scanner eine bestimmte Symbologie unterstützt, können Sie [IsSymbologySupportedAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.issymbologysupportedasync#Windows_Devices_PointOfService_BarcodeScanner_IsSymbologySupportedAsync_System_UInt32_)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bfd58-114">To determine if the scanner supports a specific symbology you can call [IsSymbologySupportedAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.issymbologysupportedasync#Windows_Devices_PointOfService_BarcodeScanner_IsSymbologySupportedAsync_System_UInt32_).</span></span>

<span data-ttu-id="bfd58-115">Im folgenden Beispiel wird überprüft, ob der Strichcodescanner die **Code32** Symbologie unterstützt:</span><span class="sxs-lookup"><span data-stu-id="bfd58-115">The following example checks if the barcode scanner supports the **Code32** symbology:</span></span>

```cs
bool symbologySupported = await barcodeScanner.IsSymbologySupportedAsync(BarcodeSymbologies.Code32);
```

## <a name="change-which-symbologies-are-recognized"></a><span data-ttu-id="bfd58-116">Ändern Sie, welche Symbologien erkannt werden</span><span class="sxs-lookup"><span data-stu-id="bfd58-116">Change which symbologies are recognized</span></span>
<span data-ttu-id="bfd58-117">In einigen Fällen möchten Sie möglicherweise eine Teilmenge Symbologien verwenden, die der Strichcodescanner unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bfd58-117">In some cases, you may want to use a subset of symbologies that the barcode scanner supports.</span></span>  <span data-ttu-id="bfd58-118">Dies ist besonders nützlich, um Symbologien zu blockieren, die Sie nicht in Ihrer Anwendung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="bfd58-118">This is particularly useful to block symbologies that you do not intend to use in your application.</span></span> <span data-ttu-id="bfd58-119">Um sicherzustellen, dass ein Benutzer den richtigen Strichcode scannt, können Sie das Scannen auf UPC oder EAN beim Kauf von Element-SKUs beschränken und das Scannen auf Code 128 beim Kauf von Seriennummern beschränken.</span><span class="sxs-lookup"><span data-stu-id="bfd58-119">For example, to ensure a user scans the right barcode, you could constrain scanning to UPC or EAN when acquiring item SKUs and constrain scanning to Code 128 when acquiring serial numbers.</span></span>

<span data-ttu-id="bfd58-120">Wenn Sie die Symbologien kennen, die der Scanner unterstützt, können Sie die Symbologien festlegen, die Sie erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="bfd58-120">Once you know the symbologies that your scanner supports, you can set the symbologies that you want it to recognize.</span></span>  <span data-ttu-id="bfd58-121">Dies kann erfolgen, wenn Sie ein [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) -Objekt, das mit [ClaimScannerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync)eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="bfd58-121">This can be done after you have established a [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) object using [ClaimScannerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync).</span></span> <span data-ttu-id="bfd58-122">Rufen Sie [SetActiveSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setactivesymbologiesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetActiveSymbologiesAsync_Windows_Foundation_Collections_IIterable_System_UInt32__) auf, um eine bestimmte Anzahl von Symbologien zu aktivieren. Die in der Liste nicht berücksichtigten Symbologien werden deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="bfd58-122">You can call [SetActiveSymbologiesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setactivesymbologiesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetActiveSymbologiesAsync_Windows_Foundation_Collections_IIterable_System_UInt32__) to enable a specific set of symbologies while those omitted from your list are disabled.</span></span>

<span data-ttu-id="bfd58-123">Im folgenden Beispiel wird die aktiven Symbologien der einen Anspruch Strichcodescanner [Code39](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.code39#Windows_Devices_PointOfService_BarcodeSymbologies_Code39) und [Code39Ex](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.code39ex):</span><span class="sxs-lookup"><span data-stu-id="bfd58-123">The following example sets the active symbologies of a claimed barcode scanner to [Code39](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.code39#Windows_Devices_PointOfService_BarcodeSymbologies_Code39) and [Code39Ex](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies.code39ex):</span></span>

```cs
private async void SetSymbologies(ClaimedBarcodeScanner claimedBarcodeScanner) 
{
    var symbologies = new List<uint>{ BarcodeSymbologies.Code39, BarcodeSymbologies.Code39Ex };
    await claimedBarcodeScanner.SetActiveSymbologiesAsync(symbologies);
}
```

## <a name="barcode-symbology-attributes"></a><span data-ttu-id="bfd58-124">Barcode-symbologieattribute</span><span class="sxs-lookup"><span data-stu-id="bfd58-124">Barcode symbology attributes</span></span>
<span data-ttu-id="bfd58-125">Verschiedene Strichcodescanner-Symbologien haben verschiedene Attribute, z. B. unterstützen mehrere Länge, übertragen die Prüfziffer an den Host als Teil der unformatierten Daten zu decodieren, und überprüfen Sie Ziffer Validierung.</span><span class="sxs-lookup"><span data-stu-id="bfd58-125">Different barcode symbologies can have different attributes, such as supporting multiple decode lengths, transmitting the check digit to the host as part of the raw data, and check digit validation.</span></span> <span data-ttu-id="bfd58-126">Mit der [BarcodeSymbologyAttributes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes) -Klasse können Sie abrufen und diese Attribute für eine bestimmten [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) und Strichcode-Symbologie festlegen.</span><span class="sxs-lookup"><span data-stu-id="bfd58-126">With the [BarcodeSymbologyAttributes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes) class, you can get and set these attributes for a given [ClaimedBarcodeScanner](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner) and barcode symbology.</span></span>

<span data-ttu-id="bfd58-127">Sie können die Attribute der eine bestimmte Symbologie mit [GetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.getsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_GetSymbologyAttributesAsync_System_UInt32_)abrufen.</span><span class="sxs-lookup"><span data-stu-id="bfd58-127">You can get the attributes of a given symbology with [GetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.getsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_GetSymbologyAttributesAsync_System_UInt32_).</span></span> <span data-ttu-id="bfd58-128">Der folgende Codeausschnitt Ruft die Attribute der Upca Symbologie für eine **ClaimedBarcodeScanner**ab.</span><span class="sxs-lookup"><span data-stu-id="bfd58-128">The following code snippet gets the attributes of the Upca symbology for a **ClaimedBarcodeScanner**.</span></span>

```cs
BarcodeSymbologyAttributes barcodeSymbologyAttributes = 
    await claimedBarcodeScanner.GetSymbologyAttributesAsync(BarcodeSymbologies.Upca);
```

<span data-ttu-id="bfd58-129">Wenn Sie ändern der Attribute abgeschlossen haben und bereit sind, die sie festlegen, können Sie [SetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setsymbologyattributesasync)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bfd58-129">When you've finished modifying the attributes and are ready to set them, you can call [SetSymbologyAttributesAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setsymbologyattributesasync).</span></span> <span data-ttu-id="bfd58-130">Diese Methode gibt **ein boolescher Wert**, das ist **"true"** , wenn die Attribute erfolgreich festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-130">This method returns a **bool**, which is **true** if the attributes were successfully set.</span></span>

```cs
bool success = await claimedBarcodeScanner.SetSymbologyAttributesAsync(
    BarcodeSymbologies.Upca, barcodeSymbologyAttributes);
```

### <a name="restrict-scan-data-by-data-length"></a><span data-ttu-id="bfd58-131">Einschränken von gescannten Daten nach Datenlänge</span><span class="sxs-lookup"><span data-stu-id="bfd58-131">Restrict scan data by data length</span></span>
<span data-ttu-id="bfd58-132">Einige Symbologien haben verschiedene Längen z.B. Code 39 oder Code 128.</span><span class="sxs-lookup"><span data-stu-id="bfd58-132">Some symbologies are variable length such as Code 39 or Code 128.</span></span>  <span data-ttu-id="bfd58-133">Strichcodes mit dieser Symbologien können sich nahe beieinander, enthält verschiedene Daten einer bestimmten Länge befinden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-133">Barcodes of these symbologies can be located near each other containing different data often of specific length.</span></span> <span data-ttu-id="bfd58-134">Das Festlegen der bestimmten Länge der Daten, die Sie benötigen, kann ungültige Überprüfungen verhindern.</span><span class="sxs-lookup"><span data-stu-id="bfd58-134">Setting the specific length of the data you require can prevent invalid scans.</span></span>

<span data-ttu-id="bfd58-135">Vor dem Festlegen der Decodierung Länge, überprüfen Sie, ob der Strichcode-Symbologie mehrere Länge mit [IsDecodeLengthSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.isdecodelengthsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsDecodeLengthSupported)unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bfd58-135">Before setting the decode length, check whether the barcode symbology supports multiple lengths with [IsDecodeLengthSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.isdecodelengthsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsDecodeLengthSupported).</span></span> <span data-ttu-id="bfd58-136">Wenn Sie wissen, dass es unterstützt wird, können Sie die [DecodeLengthKind](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelengthkind#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_DecodeLengthKind)festlegen, die vom Typ [BarcodeSymbologyDecodeLengthKind](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologydecodelengthkind).</span><span class="sxs-lookup"><span data-stu-id="bfd58-136">Once you know that it's supported, you can set the [DecodeLengthKind](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelengthkind#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_DecodeLengthKind), which is of type [BarcodeSymbologyDecodeLengthKind](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologydecodelengthkind).</span></span> <span data-ttu-id="bfd58-137">Diese Eigenschaft kann eines der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="bfd58-137">This property can be any of the following values:</span></span>

* <span data-ttu-id="bfd58-138">**AnyLength**: Länge einer beliebigen Anzahl zu decodieren.</span><span class="sxs-lookup"><span data-stu-id="bfd58-138">**AnyLength**: Decode lengths of any number.</span></span>
* <span data-ttu-id="bfd58-139">**Diskret**: Länge der [DecodeLength1](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelength1) oder [DecodeLength2](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelength2) Single-Byte-Zeichen zu decodieren.</span><span class="sxs-lookup"><span data-stu-id="bfd58-139">**Discrete**: Decode lengths of either [DecodeLength1](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelength1) or [DecodeLength2](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.decodelength2) single-byte characters.</span></span>
* <span data-ttu-id="bfd58-140">**Bereich**: Länge zwischen **DecodeLength1** und **DecodeLength2** Single-Byte-Zeichen zu decodieren.</span><span class="sxs-lookup"><span data-stu-id="bfd58-140">**Range**: Decode lengths between **DecodeLength1** and **DecodeLength2** single-byte characters.</span></span> <span data-ttu-id="bfd58-141">Die Reihenfolge der **DecodeLength1** und **DecodeLength2** keine Rolle (entweder kann höheren oder niedrigeren als die andere sein).</span><span class="sxs-lookup"><span data-stu-id="bfd58-141">The order of **DecodeLength1** and **DecodeLength2** do not matter (either can be higher or lower than the other).</span></span>

<span data-ttu-id="bfd58-142">Schließlich können Sie festlegen, die Werte **DecodeLength1** und **DecodeLength2** , um die Länge der Daten zu steuern, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="bfd58-142">Finally, you can set the values of **DecodeLength1** and **DecodeLength2** to control the length of the data you require.</span></span>

<span data-ttu-id="bfd58-143">Der folgende Codeausschnitt veranschaulicht das Festlegen der Decodierung Länge:</span><span class="sxs-lookup"><span data-stu-id="bfd58-143">The following code snippet demonstrates setting the decode length:</span></span>

```cs
private async Task<bool> SetDecodeLength(
    ClaimedBarcodeScanner scanner,
    uint symbology, 
    BarcodeSymbologyDecodeLengthKind kind, 
    uint decodeLength1, 
    uint decodeLength2)
{
    bool success = false;
    BarcodeSymbologyAttributes attributes = await scanner.GetSymbologyAttributesAsync(symbology);

    if (attributes.IsDecodeLengthSupported)
    {
        attributes.DecodeLengthKind = kind;
        attributes.DecodeLength1 = decodeLength1;
        attributes.DecodeLength2 = decodeLength2;
        success = await scanner.SetSymbologyAttributesAsync(symbology, attributes);
    }

    return success;
}
```

### <a name="check-digit-transmission"></a><span data-ttu-id="bfd58-144">Überprüfen Sie die Ziffer Übertragung</span><span class="sxs-lookup"><span data-stu-id="bfd58-144">Check digit transmission</span></span>

<span data-ttu-id="bfd58-145">Ein weiteres Attribut, die, das Sie für eine Symbologie festlegen können, ist, ob die Prüfziffer als Teil der unformatierten Daten an den Host übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-145">Another attribute you can set on a symbology is whether the check digit will be transmitted to the host as part of the raw data.</span></span> <span data-ttu-id="bfd58-146">Bevor Sie diese Einstellung, stellen Sie sicher, dass die Symbologie, Kontrollkästchen unterstützt Ziffer Datenübertragung mit [IsCheckDigitTransmissionSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionsupported).</span><span class="sxs-lookup"><span data-stu-id="bfd58-146">Before setting this, make sure that the symbology supports check digit transmission with [IsCheckDigitTransmissionSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionsupported).</span></span> <span data-ttu-id="bfd58-147">Legen Sie anschließend, ob Kontrollkästchen Ziffer Übertragung mit [IsCheckDigitTransmissionEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionenabled)aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="bfd58-147">Then, set whether check digit transmission is enabled with [IsCheckDigitTransmissionEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionenabled).</span></span>

<span data-ttu-id="bfd58-148">Der folgende Codeausschnitt veranschaulicht Einstellung Kontrollkästchen Ziffer Übertragung:</span><span class="sxs-lookup"><span data-stu-id="bfd58-148">The following code snippet demonstrates setting check digit transmission:</span></span>

```cs
private async Task<bool> SetCheckDigitTransmission(ClaimedBarcodeScanner scanner, uint symbology, bool isEnabled)
{
    bool success = false;
    BarcodeSymbologyAttributes attributes = await scanner.GetSymbologyAttributesAsync(symbology);

    if (attributes.IsCheckDigitTransmissionSupported)
    {
        attributes.IsCheckDigitTransmissionEnabled = isEnabled;
        success = await scanner.SetSymbologyAttributesAsync(symbology, attributes);
    }

    return success;
}
```

### <a name="check-digit-validation"></a><span data-ttu-id="bfd58-149">Überprüfen Sie Ziffer Validierung</span><span class="sxs-lookup"><span data-stu-id="bfd58-149">Check digit validation</span></span>

<span data-ttu-id="bfd58-150">Sie können auch festlegen, ob die Barcode-Prüfziffer überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="bfd58-150">You can also set whether the barcode check digit will be validated.</span></span> <span data-ttu-id="bfd58-151">Bevor Sie diese Einstellung, stellen Sie sicher, dass die Symbologie, Kontrollkästchen unterstützt Ziffer Validierung mit [IsCheckDigitValidationSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationsupported).</span><span class="sxs-lookup"><span data-stu-id="bfd58-151">Before setting this, make sure that the symbology supports check digit validation with [IsCheckDigitValidationSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationsupported).</span></span> <span data-ttu-id="bfd58-152">Legen Sie anschließend, ob Kontrollkästchen Ziffer Überprüfung mit [IsCheckDigitValidationEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationenabled)aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="bfd58-152">Then, set whether check digit validation is enabled with [IsCheckDigitValidationEnabled](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationenabled).</span></span>

<span data-ttu-id="bfd58-153">Der folgende Codeausschnitt veranschaulicht Einstellung Kontrollkästchen Ziffer Überprüfung:</span><span class="sxs-lookup"><span data-stu-id="bfd58-153">The following code snippet demonstrates setting check digit validation:</span></span>

```cs
private async Task<bool> SetCheckDigitValidation(ClaimedBarcodeScanner scanner, uint symbology, bool isEnabled)
{
    bool success = false;
    BarcodeSymbologyAttributes attributes = await scanner.GetSymbologyAttributesAsync(symbology);

    if (attributes.IsCheckDigitValidationSupported)
    {
        attributes.IsCheckDigitValidationEnabled = isEnabled;
        success = await scanner.SetSymbologyAttributesAsync(symbology, attributes);
    }

    return success;
}
```

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a><span data-ttu-id="bfd58-154">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="bfd58-154">See also</span></span>

* [<span data-ttu-id="bfd58-155">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="bfd58-155">Barcode scanner</span></span>](pos-barcodescanner.md)
* [<span data-ttu-id="bfd58-156">BarcodeSymbologies-Klasse</span><span class="sxs-lookup"><span data-stu-id="bfd58-156">BarcodeSymbologies Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies)
* [<span data-ttu-id="bfd58-157">BarcodeScanner-Klasse</span><span class="sxs-lookup"><span data-stu-id="bfd58-157">BarcodeScanner Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner)
* [<span data-ttu-id="bfd58-158">ClaimedBarcodeScanner-Klasse</span><span class="sxs-lookup"><span data-stu-id="bfd58-158">ClaimedBarcodeScanner Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner)
* [<span data-ttu-id="bfd58-159">BarcodeSymbologyAttributes-Klasse</span><span class="sxs-lookup"><span data-stu-id="bfd58-159">BarcodeSymbologyAttributes Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes)
* [<span data-ttu-id="bfd58-160">BarcodeSymbologyDecodeLengthKind-Enumeration</span><span class="sxs-lookup"><span data-stu-id="bfd58-160">BarcodeSymbologyDecodeLengthKind Enum</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologydecodelengthkind)