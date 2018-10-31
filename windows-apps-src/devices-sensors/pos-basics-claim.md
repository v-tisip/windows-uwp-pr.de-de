---
author: TerryWarwick
title: PointOfService-Geräts beanspruchen und aktivieren Sie Modell
description: Erfahren Sie mehr über PointOfService Anspruch und Modell aktivieren
ms.author: jken
ms.date: 06/19/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: df9c4764b8f7d752a132d6759054660f481cce55
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5820935"
---
# <a name="point-of-service-device-claim-and-enable-model"></a><span data-ttu-id="c0c2f-104">POS-Gerät beanspruchen und aktivieren Sie Modell</span><span class="sxs-lookup"><span data-stu-id="c0c2f-104">Point of Service device claim and enable model</span></span>

## <a name="claiming-for-exclusive-use"></a><span data-ttu-id="c0c2f-105">Für die exklusive Nutzung beanspruchen</span><span class="sxs-lookup"><span data-stu-id="c0c2f-105">Claiming for exclusive use</span></span>

<span data-ttu-id="c0c2f-106">Nachdem Sie erfolgreich ein PointOfService-Geräteobjekt erfolgreich erstellt haben, müssen Sie es mithilfe der entsprechenden Beanspruchungsmethode für den Gerätetyp beanspruchen, bevor Sie das Gerät für die Ein- und Ausgabe verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-106">After you have successfully created a PointOfService device object, you must claim it using the appropriate claim method for the device type before you can use the device for input or output.</span></span>  <span data-ttu-id="c0c2f-107">Die Beanspruchung gewährt der Anwendung einen exklusiven Zugriff auf viele Funktionen des Geräts, um sicherzustellen, dass eine Anwendung die Verwendung des Geräts durch eine andere Anwendung nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-107">Claim grants the application exclusive access to many of the device's functions to ensure that one application does not interfere with the use of the device by another application.</span></span>  <span data-ttu-id="c0c2f-108">Es kann jeweils nur eine Anwendung die exklusive Verwendung eines PointOfService-Geräts beanspruchen.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-108">Only one application can claim a PointOfService device for exclusive use at a time.</span></span> 

> [!Note]
> <span data-ttu-id="c0c2f-109">Die Aktion Anspruch stellt eine exklusive Sperre auf einem Gerät her, jedoch nicht in den betriebsbereiten Zustand versetzt.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-109">The claim action establishes an exclusive lock to a device, but does not put it into an operational state.</span></span>  <span data-ttu-id="c0c2f-110">Weitere Informationen finden Sie unter [Aktivieren Geräts für die e/a-Vorgänge](#Enable-device-for-I/O-operations) .</span><span class="sxs-lookup"><span data-stu-id="c0c2f-110">See [Enable device for I/O operations](#Enable-device-for-I/O-operations) for more information.</span></span>

### <a name="apis-used-to-claim--release"></a><span data-ttu-id="c0c2f-111">APIs verwendet, um beanspruchen / release</span><span class="sxs-lookup"><span data-stu-id="c0c2f-111">APIs used to claim / release</span></span>

|<span data-ttu-id="c0c2f-112">Gerät</span><span class="sxs-lookup"><span data-stu-id="c0c2f-112">Device</span></span>|<span data-ttu-id="c0c2f-113">Anspruch</span><span class="sxs-lookup"><span data-stu-id="c0c2f-113">Claim</span></span> | <span data-ttu-id="c0c2f-114">Version</span><span class="sxs-lookup"><span data-stu-id="c0c2f-114">Release</span></span> | 
|-|:-|:-|
|<span data-ttu-id="c0c2f-115">BarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="c0c2f-115">BarcodeScanner</span></span> | [<span data-ttu-id="c0c2f-116">BarcodeScanner.ClaimScannerAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-116">BarcodeScanner.ClaimScannerAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync) | [<span data-ttu-id="c0c2f-117">ClaimedBarcodeScanner.Close</span><span class="sxs-lookup"><span data-stu-id="c0c2f-117">ClaimedBarcodeScanner.Close</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.close) |
|<span data-ttu-id="c0c2f-118">CashDrawer</span><span class="sxs-lookup"><span data-stu-id="c0c2f-118">CashDrawer</span></span> | [<span data-ttu-id="c0c2f-119">CashDrawer.ClaimDrawerAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-119">CashDrawer.ClaimDrawerAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.claimdrawerasync) | [<span data-ttu-id="c0c2f-120">ClaimedCashDrawer.Close</span><span class="sxs-lookup"><span data-stu-id="c0c2f-120">ClaimedCashDrawer.Close</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.close) | 
|<span data-ttu-id="c0c2f-121">LineDisplay</span><span class="sxs-lookup"><span data-stu-id="c0c2f-121">LineDisplay</span></span> | [<span data-ttu-id="c0c2f-122">LineDisplay.ClaimAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-122">LineDisplay.ClaimAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.claimasync) |  [<span data-ttu-id="c0c2f-123">ClaimedineDisplay.Close</span><span class="sxs-lookup"><span data-stu-id="c0c2f-123">ClaimedineDisplay.Close</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.close) | 
|<span data-ttu-id="c0c2f-124">MagneticStripeReader</span><span class="sxs-lookup"><span data-stu-id="c0c2f-124">MagneticStripeReader</span></span> | [<span data-ttu-id="c0c2f-125">MagneticStripeReader.ClaimReaderAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-125">MagneticStripeReader.ClaimReaderAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.claimreaderasync) |  [<span data-ttu-id="c0c2f-126">ClaimedMagneticStripeReader.Close</span><span class="sxs-lookup"><span data-stu-id="c0c2f-126">ClaimedMagneticStripeReader.Close</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.close) | 
|<span data-ttu-id="c0c2f-127">PosPrinter</span><span class="sxs-lookup"><span data-stu-id="c0c2f-127">PosPrinter</span></span> | [<span data-ttu-id="c0c2f-128">PosPrinter.ClaimPrinterAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-128">PosPrinter.ClaimPrinterAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.claimprinterasync) |  [<span data-ttu-id="c0c2f-129">ClaimedPosPrinter.Close</span><span class="sxs-lookup"><span data-stu-id="c0c2f-129">ClaimedPosPrinter.Close</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.close) | 
 | 

## <a name="enable-device-for-io-operations"></a><span data-ttu-id="c0c2f-130">Aktivieren des Geräts für die e/a-Vorgänge</span><span class="sxs-lookup"><span data-stu-id="c0c2f-130">Enable device for I/O operations</span></span>

<span data-ttu-id="c0c2f-131">Die Aktion Anspruch einfach stellt einen exklusiven Zugriff auf das Gerät her, jedoch nicht in den betriebsbereiten Zustand versetzt.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-131">The claim action simply establishes an exclusive rights to the device, but does not put it into an operational state.</span></span>  <span data-ttu-id="c0c2f-132">Um Ereignisse empfangen oder keine Ausgabevorgänge ausführen, müssen Sie das Gerät mithilfe der **EnableAsync**aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-132">In order to receive events or perform any output operations you must enable the device using **EnableAsync**.</span></span>  <span data-ttu-id="c0c2f-133">Im Gegensatz dazu können Sie **DisableAsync** zum Überwachen von Ereignissen über das verwendete Gerät oder eine Ausgabe beenden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-133">Conversely, you can call **DisableAsync** to stop listening to events from the device or performing output.</span></span>  <span data-ttu-id="c0c2f-134">Sie können auch **IsEnabled** verwenden, um den Zustand des Geräts zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-134">You can also use **IsEnabled** to determine the state of your device.</span></span>

### <a name="apis-used-enable--disable"></a><span data-ttu-id="c0c2f-135">Verwendete APIs aktivieren / deaktivieren</span><span class="sxs-lookup"><span data-stu-id="c0c2f-135">APIs used enable / disable</span></span>

| <span data-ttu-id="c0c2f-136">Gerät</span><span class="sxs-lookup"><span data-stu-id="c0c2f-136">Device</span></span> | <span data-ttu-id="c0c2f-137">Aktivieren</span><span class="sxs-lookup"><span data-stu-id="c0c2f-137">Enable</span></span> | <span data-ttu-id="c0c2f-138">Deaktivieren</span><span class="sxs-lookup"><span data-stu-id="c0c2f-138">Disable</span></span> | <span data-ttu-id="c0c2f-139">IsEnabled?</span><span class="sxs-lookup"><span data-stu-id="c0c2f-139">IsEnabled?</span></span> |
|-|:-|:-|:-|
|<span data-ttu-id="c0c2f-140">ClaimedBarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="c0c2f-140">ClaimedBarcodeScanner</span></span> | [<span data-ttu-id="c0c2f-141">EnableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-141">EnableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.enableasync) | [<span data-ttu-id="c0c2f-142">DisableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-142">DisableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.disableasync) | [<span data-ttu-id="c0c2f-143">IsEnabled</span><span class="sxs-lookup"><span data-stu-id="c0c2f-143">IsEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isenabled) | 
|<span data-ttu-id="c0c2f-144">ClaimedCashDrawer</span><span class="sxs-lookup"><span data-stu-id="c0c2f-144">ClaimedCashDrawer</span></span> | [<span data-ttu-id="c0c2f-145">EnableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-145">EnableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.enableasync) | [<span data-ttu-id="c0c2f-146">DisableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-146">DisableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.disableasync) | [<span data-ttu-id="c0c2f-147">IsEnabled</span><span class="sxs-lookup"><span data-stu-id="c0c2f-147">IsEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.isenabled) |
|<span data-ttu-id="c0c2f-148">ClaimedLineDisplay</span><span class="sxs-lookup"><span data-stu-id="c0c2f-148">ClaimedLineDisplay</span></span> | <span data-ttu-id="c0c2f-149">Nicht Applicable¹</span><span class="sxs-lookup"><span data-stu-id="c0c2f-149">Not Applicable¹</span></span> | <span data-ttu-id="c0c2f-150">Nicht Applicable¹</span><span class="sxs-lookup"><span data-stu-id="c0c2f-150">Not Applicable¹</span></span> | <span data-ttu-id="c0c2f-151">Nicht Applicable¹</span><span class="sxs-lookup"><span data-stu-id="c0c2f-151">Not Applicable¹</span></span> | 
|<span data-ttu-id="c0c2f-152">ClaimedMagneticStripeReader</span><span class="sxs-lookup"><span data-stu-id="c0c2f-152">ClaimedMagneticStripeReader</span></span> | [<span data-ttu-id="c0c2f-153">EnableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-153">EnableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.enableasync) | [<span data-ttu-id="c0c2f-154">DisableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-154">DisableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.disableasync) | [<span data-ttu-id="c0c2f-155">IsEnabled</span><span class="sxs-lookup"><span data-stu-id="c0c2f-155">IsEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.isenabled) |  
|<span data-ttu-id="c0c2f-156">ClaimedPosPrinter</span><span class="sxs-lookup"><span data-stu-id="c0c2f-156">ClaimedPosPrinter</span></span> | [<span data-ttu-id="c0c2f-157">EnableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-157">EnableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.enableasync) | [<span data-ttu-id="c0c2f-158">DisableAsync</span><span class="sxs-lookup"><span data-stu-id="c0c2f-158">DisableAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.disableasyc) | [<span data-ttu-id="c0c2f-159">IsEnabled</span><span class="sxs-lookup"><span data-stu-id="c0c2f-159">IsEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.isenabled) |
|

<span data-ttu-id="c0c2f-160">¹ Zeilenanzeige erfordert keine explizit aktivieren, das Gerät für die e/a-Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-160">¹ Line Display does not require you to explicitly enable the device for I/O operations.</span></span>  <span data-ttu-id="c0c2f-161">Aktivierung erfolgt automatisch durch die PointOfService-LineDisplay-APIs die e/a durchführen.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-161">Enabling is performed automatically by the PointOfService LineDisplay APIs which perform I/O.</span></span>

## <a name="code-sample-claim-and-enable"></a><span data-ttu-id="c0c2f-162">Codebeispiel: beanspruchen und aktivieren</span><span class="sxs-lookup"><span data-stu-id="c0c2f-162">Code sample: claim and enable</span></span>

<span data-ttu-id="c0c2f-163">Im folgenden Beispiel ist gezeigt, wie Sie ein Strichcodescanner-Gerät beanspruchen, nachdem Sie erfolgreich ein Strichcodescanner-Objekt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-163">This sample shows how to claim a barcode scanner device after you have successfully created a barcode scanner object.</span></span>

```Csharp

    BarcodeScanner barcodeScanner = await BarcodeScanner.FromIdAsync(DeviceId);

    if(barcodeScanner != null)
    {
        // after successful creation, claim the scanner for exclusive use 
        claimedBarcodeScanner = await barcodeScanner.ClaimScannerAsync();

        if(claimedBarcodeScanner != null)
        {
            // after successful claim, enable scanner for data events to fire
            await claimedBarcodeScanner.EnableAsync();
        }
        else
        {
            Debug.WriteLine("Failure to claim barcodeScanner");
        }
    }
    else
    {
        Debug.WriteLine("Failure to create barcodeScanner object");
    }
    
```

> [!Warning]
> <span data-ttu-id="c0c2f-164">Ein Anspruch kann unter den folgenden Umständen verloren gehen:</span><span class="sxs-lookup"><span data-stu-id="c0c2f-164">A claim can be lost in the following circumstances:</span></span>
> 1. <span data-ttu-id="c0c2f-165">Eine andere App hat einen Anspruch auf dasselbe Gerät angefordert, und Ihre App hat kein **RetainDevice** in Reaktion auf das Ereignis **ReleaseDeviceRequested** ausgestellt.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-165">Another app has requested a claim of the same device and your app did not issue a **RetainDevice** in response to the **ReleaseDeviceRequested** event.</span></span>  <span data-ttu-id="c0c2f-166">(Weitere Informationen finden Sie im Abschnitt [Anspruchsaushandlung](#Claim-negotiation) weiter unten).</span><span class="sxs-lookup"><span data-stu-id="c0c2f-166">(See [Claim negotiation](#Claim-negotiation) below for more information.)</span></span>
> 2. <span data-ttu-id="c0c2f-167">Ihre App wurde unterbrochen, was dazu geführt hat, dass das Geräteobjekt geschlossen wurde und der Anspruch daher nicht mehr gültig ist.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-167">Your app has been suspended, which resulted in the device object being closed and as a result the claim is no longer valid.</span></span> <span data-ttu-id="c0c2f-168">(Weitere Informationen finden Sie unter [Lebenszyklus von Geräteobjekten](pos-basics-deviceobject.md#device-object-lifecycle).)</span><span class="sxs-lookup"><span data-stu-id="c0c2f-168">(See [Device object lifecycle](pos-basics-deviceobject.md#device-object-lifecycle) for more information.)</span></span>


## <a name="claim-negotiation"></a><span data-ttu-id="c0c2f-169">Anspruchsaushandlung</span><span class="sxs-lookup"><span data-stu-id="c0c2f-169">Claim negotiation</span></span>

<span data-ttu-id="c0c2f-170">Da Windows eine Multitaskingumgebung ist, fordern möglicherweise mehrere Anwendungen auf demselben Computer einen Zugriff auf Peripheriegeräte auf kooperative Weise an.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-170">Since Windows is a multi-tasking environment it is possible for multiple applications on the same computer to require access to peripherals in a cooperative manner.</span></span>  <span data-ttu-id="c0c2f-171">Die PointOfService-APIs bieten ein Aushandlungsmodell, das mehreren Anwendungen die gemeinsame Verwendung von an den Computer angeschlossenen Peripheriegeräten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-171">The PointOfService APIs provide a negotiation model that allows for multiple applications to share peripherals connected to the computer.</span></span>

<span data-ttu-id="c0c2f-172">Wenn eine zweite Anwendung auf demselben Computer ein PointOfService-Peripheriegerät beansprucht, das bereits von einer anderen Anwendung in Anspruch genommen wird, wird eine **ReleaseDeviceRequested**-Ereignisbenachrichtigung veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-172">When a second application on the same computer requests a Claim for a PointOfService peripheral that is already claimed by another application, a **ReleaseDeviceRequested** event notification is published.</span></span> <span data-ttu-id="c0c2f-173">Die Anwendung mit dem aktiven Anspruch muss auf die Ereignisbenachrichtigung reagieren, indem **RetainDevice** aufgerufen wird, wenn die Anwendung das Gerät derzeit verwendet, damit der Anspruch nicht verloren geht.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-173">The application with the active claim must respond to the event notification by calling **RetainDevice** if the application is currently using the device to avoid losing the claim.</span></span> 

<span data-ttu-id="c0c2f-174">Wenn die Anwendung mit dem aktiven Anspruch nicht sofort mit **RetainDevice** antwortet, wird davon ausgegangen, dass die Anwendung unterbrochen wurde oder das Gerät nicht benötigt, und der Anspruch wird widerrufen und an die neue Anwendung übergeben.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-174">If the application with the active claim does not respond with **RetainDevice** right away it is assumed that the application has been suspended or does not need the device and the claim is revoked and given to the new application.</span></span> 

<span data-ttu-id="c0c2f-175">Der erste Schritt ist einen Ereignishandler erstellen, die auf das Ereignis **ReleaseDeviceRequested** mit **RetainDevice**reagiert.</span><span class="sxs-lookup"><span data-stu-id="c0c2f-175">The first step is to create an event handler which responds to the **ReleaseDeviceRequested** event with **RetainDevice**.</span></span>  

```Csharp
    /// <summary>
    /// Event handler for the ReleaseDeviceRequested event which occurs when 
    /// the claimed barcode scanner receives a Claim request from another application
    /// </summary>
    void claimedBarcodeScanner_ReleaseDeviceRequested(object sender, ClaimedBarcodeScanner myScanner)
    {
        // Retain exclusive access to the device
        myScanner.RetainDevice();
    }
```

<span data-ttu-id="c0c2f-176">Klicken Sie dann registrieren Sie den Ereignishandler im Zusammenhang mit Ihrem beanspruchtes Gerät</span><span class="sxs-lookup"><span data-stu-id="c0c2f-176">Then register the event handler in association with your claimed device</span></span>

```Csharp
    BarcodeScanner barcodeScanner = await BarcodeScanner.FromIdAsync(DeviceId);

    if(barcodeScanner != null)
    {
        // after successful creation, claim the scanner for exclusive use 
        claimedBarcodeScanner = await barcodeScanner.ClaimScannerAsync();

        if(claimedBarcodeScanner != null)
        {
            // register a release request handler to prevent loss of scanner during active use
            claimedBarcodeScanner.ReleaseDeviceRequested += claimedBarcodeScanner_ReleaseDeviceRequested;

            // after successful claim, enable scanner for data events to fire
            await claimedBarcodeScanner.EnableAsync();          
        }
        else
        {
            Debug.WriteLine("Failure to claim barcodeScanner");
        }
    }
    else
    {
        Debug.WriteLine("Failure to create barcodeScanner object");
    }
```



### <a name="apis-used-for-claim-negotiation"></a><span data-ttu-id="c0c2f-177">Für die Anspruchsaushandlung verwendete APIs</span><span class="sxs-lookup"><span data-stu-id="c0c2f-177">APIs used for claim negotiation</span></span>

|<span data-ttu-id="c0c2f-178">Beanspruchtes Gerät</span><span class="sxs-lookup"><span data-stu-id="c0c2f-178">Claimed device</span></span>|<span data-ttu-id="c0c2f-179">Benachrichtigungsversion</span><span class="sxs-lookup"><span data-stu-id="c0c2f-179">Release Notification</span></span>| <span data-ttu-id="c0c2f-180">Gerät beibehalten</span><span class="sxs-lookup"><span data-stu-id="c0c2f-180">Retain Device</span></span> |
|-|:-|:-|
|<span data-ttu-id="c0c2f-181">ClaimedBarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="c0c2f-181">ClaimedBarcodeScanner</span></span> | [<span data-ttu-id="c0c2f-182">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="c0c2f-182">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.releasedevicerequested) | [<span data-ttu-id="c0c2f-183">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="c0c2f-183">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.retaindevice)
|<span data-ttu-id="c0c2f-184">ClaimedCashDrawer</span><span class="sxs-lookup"><span data-stu-id="c0c2f-184">ClaimedCashDrawer</span></span> | [<span data-ttu-id="c0c2f-185">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="c0c2f-185">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.releasedevicerequested) | [<span data-ttu-id="c0c2f-186">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="c0c2f-186">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.retaindevice)
|<span data-ttu-id="c0c2f-187">ClaimedLineDisplay</span><span class="sxs-lookup"><span data-stu-id="c0c2f-187">ClaimedLineDisplay</span></span> | [<span data-ttu-id="c0c2f-188">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="c0c2f-188">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.releasedevicerequested) | [<span data-ttu-id="c0c2f-189">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="c0c2f-189">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|<span data-ttu-id="c0c2f-190">ClaimedMagneticStripeReader</span><span class="sxs-lookup"><span data-stu-id="c0c2f-190">ClaimedMagneticStripeReader</span></span> | [<span data-ttu-id="c0c2f-191">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="c0c2f-191">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.releasedevicerequested) | [<span data-ttu-id="c0c2f-192">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="c0c2f-192">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|<span data-ttu-id="c0c2f-193">ClaimedPosPrinter</span><span class="sxs-lookup"><span data-stu-id="c0c2f-193">ClaimedPosPrinter</span></span> | [<span data-ttu-id="c0c2f-194">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="c0c2f-194">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.releasedevicerequested) | [<span data-ttu-id="c0c2f-195">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="c0c2f-195">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.retaindevice)
|
