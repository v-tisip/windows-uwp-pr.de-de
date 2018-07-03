---
author: TerryWarwick
title: PointOfService-Gerätebeanspruchungsmodell
description: Weitere Informationen zum PointOfService-Beanspruchungsmodell
ms.author: jken
ms.date: 06/4/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 202234530945e55ef9c0d0fb68cf9ca83d2e15c3
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983731"
---
# <a name="point-of-service-device-claim-model"></a><span data-ttu-id="4d488-104">POS-Gerätebeanspruchungsmodell</span><span class="sxs-lookup"><span data-stu-id="4d488-104">Point of Service device claim model</span></span>

## <a name="claiming-a-device-for-exclusive-use"></a><span data-ttu-id="4d488-105">Beanspruchung der exklusiven Nutzung eines Geräts</span><span class="sxs-lookup"><span data-stu-id="4d488-105">Claiming a device for exclusive use</span></span>

<span data-ttu-id="4d488-106">Nachdem Sie erfolgreich ein PointOfService-Geräteobjekt erfolgreich erstellt haben, müssen Sie es mithilfe der entsprechenden Beanspruchungsmethode für den Gerätetyp beanspruchen, bevor Sie das Gerät für die Ein- und Ausgabe verwenden können.</span><span class="sxs-lookup"><span data-stu-id="4d488-106">After you have successfully created a PointOfService device object, you must claim it using the appropriate claim method for the device type before you can use the device for input or output.</span></span>  <span data-ttu-id="4d488-107">Die Beanspruchung gewährt der Anwendung einen exklusiven Zugriff auf viele Funktionen des Geräts, um sicherzustellen, dass eine Anwendung die Verwendung des Geräts durch eine andere Anwendung nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="4d488-107">Claim grants the application exclusive access to many of the device's functions to ensure that one application does not interfere with the use of the device by another application.</span></span>  <span data-ttu-id="4d488-108">Es kann jeweils nur eine Anwendung die exklusive Verwendung eines PointOfService-Geräts beanspruchen.</span><span class="sxs-lookup"><span data-stu-id="4d488-108">Only one application can claim a PointOfService device for exclusive use at a time.</span></span> 

<span data-ttu-id="4d488-109">Im folgenden Beispiel ist gezeigt, wie Sie ein Strichcodescanner-Gerät beanspruchen, nachdem Sie erfolgreich ein Strichcodescanner-Objekt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="4d488-109">This sample shows how to claim a barcode scanner device after you have successfully created a barcode scanner object.</span></span>

```Csharp
try
{
    claimedBarcodeScanner = await barcodeScanner.ClaimScannerAsync();
}
catch (Exception ex)
{
    Debug.WriteLine("EX: ClaimScannerAsync() - " + ex.Message);
}
```

> [!Warning]
> <span data-ttu-id="4d488-110">Ein Anspruch kann unter den folgenden Umständen verloren gehen:</span><span class="sxs-lookup"><span data-stu-id="4d488-110">A claim can be lost in the following circumstances:</span></span>
> 1. <span data-ttu-id="4d488-111">Eine andere App hat einen Anspruch auf dasselbe Gerät angefordert, und Ihre App hat kein **RetainDevice** in Reaktion auf das Ereignis **ReleaseDeviceRequested** ausgestellt.</span><span class="sxs-lookup"><span data-stu-id="4d488-111">Another app has requested a claim of the same device and your app did not issue a **RetainDevice** in response to the **ReleaseDeviceRequested** event.</span></span>  <span data-ttu-id="4d488-112">(Weitere Informationen finden Sie im Abschnitt [Anspruchsaushandlung](#Claim-negotiation) weiter unten).</span><span class="sxs-lookup"><span data-stu-id="4d488-112">(See [Claim negotiation](#Claim-negotiation) below for more information.)</span></span>
> 2. <span data-ttu-id="4d488-113">Ihre App wurde unterbrochen, was dazu geführt hat, dass das Geräteobjekt geschlossen wurde und der Anspruch daher nicht mehr gültig ist.</span><span class="sxs-lookup"><span data-stu-id="4d488-113">Your app has been suspended, which resulted in the device object being closed and as a result the claim is no longer valid.</span></span> <span data-ttu-id="4d488-114">(Weitere Informationen finden Sie unter [Lebenszyklus von Geräteobjekten](pos-basics-deviceobject.md#device-object-lifecycle).)</span><span class="sxs-lookup"><span data-stu-id="4d488-114">(See [Device object lifecycle](pos-basics-deviceobject.md#device-object-lifecycle) for more information.)</span></span>

### <a name="apis-used-for-claiming"></a><span data-ttu-id="4d488-115">Für die Beanspruchung verwendete APIs</span><span class="sxs-lookup"><span data-stu-id="4d488-115">APIs used for claiming</span></span>

|<span data-ttu-id="4d488-116">Gerät</span><span class="sxs-lookup"><span data-stu-id="4d488-116">Device</span></span>|<span data-ttu-id="4d488-117">Anspruch</span><span class="sxs-lookup"><span data-stu-id="4d488-117">Claim</span></span> |
|-|:-|
|<span data-ttu-id="4d488-118">BarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="4d488-118">BarcodeScanner</span></span> | [<span data-ttu-id="4d488-119">ClaimScannerAsync</span><span class="sxs-lookup"><span data-stu-id="4d488-119">ClaimScannerAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync) | 
|<span data-ttu-id="4d488-120">CashDrawer</span><span class="sxs-lookup"><span data-stu-id="4d488-120">CashDrawer</span></span> | [<span data-ttu-id="4d488-121">ClaimDrawerAsync</span><span class="sxs-lookup"><span data-stu-id="4d488-121">ClaimDrawerAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.cashdrawer.claimdrawerasync) | 
|<span data-ttu-id="4d488-122">LineDisplay</span><span class="sxs-lookup"><span data-stu-id="4d488-122">LineDisplay</span></span> | [<span data-ttu-id="4d488-123">ClaimAsync</span><span class="sxs-lookup"><span data-stu-id="4d488-123">ClaimAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.linedisplay.claimasync) |
|<span data-ttu-id="4d488-124">MagneticStripeReader</span><span class="sxs-lookup"><span data-stu-id="4d488-124">MagneticStripeReader</span></span> | [<span data-ttu-id="4d488-125">ClaimReaderAsync</span><span class="sxs-lookup"><span data-stu-id="4d488-125">ClaimReaderAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.claimreaderasync) | 
|<span data-ttu-id="4d488-126">PosPrinter</span><span class="sxs-lookup"><span data-stu-id="4d488-126">PosPrinter</span></span> | [<span data-ttu-id="4d488-127">ClaimPrinterAsync</span><span class="sxs-lookup"><span data-stu-id="4d488-127">ClaimPrinterAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.posprinter.claimprinterasync) | 
|

## <a name="claim-negotiation"></a><span data-ttu-id="4d488-128">Anspruchsaushandlung</span><span class="sxs-lookup"><span data-stu-id="4d488-128">Claim negotiation</span></span>

<span data-ttu-id="4d488-129">Da Windows eine Multitaskingumgebung ist, fordern möglicherweise mehrere Anwendungen auf demselben Computer einen Zugriff auf Peripheriegeräte auf kooperative Weise an.</span><span class="sxs-lookup"><span data-stu-id="4d488-129">Since Windows is a multi-tasking environment it is possible for multiple applications on the same computer to require access to peripherals in a cooperative manner.</span></span>  <span data-ttu-id="4d488-130">Die PointOfService-APIs bieten ein Aushandlungsmodell, das mehreren Anwendungen die gemeinsame Verwendung von an den Computer angeschlossenen Peripheriegeräten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="4d488-130">The PointOfService APIs provide a negotiation model that allows for multiple applications to share peripherals connected to the computer.</span></span>

<span data-ttu-id="4d488-131">Wenn eine zweite Anwendung auf demselben Computer ein PointOfService-Peripheriegerät beansprucht, das bereits von einer anderen Anwendung in Anspruch genommen wird, wird eine **ReleaseDeviceRequested**-Ereignisbenachrichtigung veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="4d488-131">When a second application on the same computer requests a Claim for a PointOfService peripheral that is already claimed by another application, a **ReleaseDeviceRequested** event notification is published.</span></span> <span data-ttu-id="4d488-132">Die Anwendung mit dem aktiven Anspruch muss auf die Ereignisbenachrichtigung reagieren, indem **RetainDevice** aufgerufen wird, wenn die Anwendung das Gerät derzeit verwendet, damit der Anspruch nicht verloren geht.</span><span class="sxs-lookup"><span data-stu-id="4d488-132">The application with the active claim must respond to the event notification by calling **RetainDevice** if the application is currently using the device to avoid losing the claim.</span></span> 

<span data-ttu-id="4d488-133">Wenn die Anwendung mit dem aktiven Anspruch nicht sofort mit **RetainDevice** antwortet, wird davon ausgegangen, dass die Anwendung unterbrochen wurde oder das Gerät nicht benötigt, und der Anspruch wird widerrufen und an die neue Anwendung übergeben.</span><span class="sxs-lookup"><span data-stu-id="4d488-133">If the application with the active claim does not respond with **RetainDevice** right away it is assumed that the application has been suspended or does not need the device and the claim is revoked and given to the new application.</span></span> 

<span data-ttu-id="4d488-134">In diesem Beispiel wird veranschaulicht, wie der Anspruch auf einen Strichcodescanner aufrechterhalten wird, wenn eine andere App fordert, das Gerät freizugegeben.</span><span class="sxs-lookup"><span data-stu-id="4d488-134">This example shows how to retain a claimed barcode scanner after another app has requested that the device be released.</span></span>  

```Csharp
claimedBarcodeScanner.ReleaseDeviceRequested += claimedBarcodeScanner_ReleaseDeviceRequested;

void claimedBarcodeScanner_ReleaseDeviceRequested(object sender, ClaimedBarcodeScanner myScanner)
{
    // Retain exclusive access to the device
    myScanner.RetainDevice();  
}
```
### <a name="apis-used-for-claim-negotiation"></a><span data-ttu-id="4d488-135">Für die Anspruchsaushandlung verwendete APIs</span><span class="sxs-lookup"><span data-stu-id="4d488-135">APIs used for claim negotiation</span></span>

|<span data-ttu-id="4d488-136">Beanspruchtes Gerät</span><span class="sxs-lookup"><span data-stu-id="4d488-136">Claimed device</span></span>|<span data-ttu-id="4d488-137">Benachrichtigungsversion</span><span class="sxs-lookup"><span data-stu-id="4d488-137">Release Notification</span></span>| <span data-ttu-id="4d488-138">Gerät beibehalten</span><span class="sxs-lookup"><span data-stu-id="4d488-138">Retain Device</span></span> |
|-|:-|:-|
|<span data-ttu-id="4d488-139">ClaimedBarcodeScanner</span><span class="sxs-lookup"><span data-stu-id="4d488-139">ClaimedBarcodeScanner</span></span> | [<span data-ttu-id="4d488-140">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="4d488-140">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.releasedevicerequested) | [<span data-ttu-id="4d488-141">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="4d488-141">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.retaindevice)
|<span data-ttu-id="4d488-142">ClaimedCashDrawer</span><span class="sxs-lookup"><span data-stu-id="4d488-142">ClaimedCashDrawer</span></span> | [<span data-ttu-id="4d488-143">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="4d488-143">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.releasedevicerequested) | [<span data-ttu-id="4d488-144">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="4d488-144">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedcashdrawer.retaindevice)
|<span data-ttu-id="4d488-145">ClaimedLineDisplay</span><span class="sxs-lookup"><span data-stu-id="4d488-145">ClaimedLineDisplay</span></span> | [<span data-ttu-id="4d488-146">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="4d488-146">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.releasedevicerequested) | [<span data-ttu-id="4d488-147">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="4d488-147">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|<span data-ttu-id="4d488-148">ClaimedMagneticStripeReader</span><span class="sxs-lookup"><span data-stu-id="4d488-148">ClaimedMagneticStripeReader</span></span> | [<span data-ttu-id="4d488-149">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="4d488-149">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.releasedevicerequested) | [<span data-ttu-id="4d488-150">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="4d488-150">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedlinedisplay.retaindevice)
|<span data-ttu-id="4d488-151">ClaimedPosPrinter</span><span class="sxs-lookup"><span data-stu-id="4d488-151">ClaimedPosPrinter</span></span> | [<span data-ttu-id="4d488-152">ReleaseDeviceRequested</span><span class="sxs-lookup"><span data-stu-id="4d488-152">ReleaseDeviceRequested</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.releasedevicerequested) | [<span data-ttu-id="4d488-153">RetainDevice</span><span class="sxs-lookup"><span data-stu-id="4d488-153">RetainDevice</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedposprinter.retaindevice)
|
