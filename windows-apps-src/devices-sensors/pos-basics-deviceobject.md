---
title: PointOfService-Geräteobjekte
description: Hier erfahren Sie, wie PointOfService-Geräteobjekte erstellt werden.
ms.date: 06/19/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: aba44cec7081d05f66e90b2540f0e9609b87ab83
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8342148"
---
# <a name="pointofservice-device-objects"></a><span data-ttu-id="a3834-104">PointOfService-Geräteobjekte</span><span class="sxs-lookup"><span data-stu-id="a3834-104">PointOfService device objects</span></span>

## <a name="creating-a-device-object"></a><span data-ttu-id="a3834-105">Erstellen eines Geräteobjekts</span><span class="sxs-lookup"><span data-stu-id="a3834-105">Creating a device object</span></span>
<span data-ttu-id="a3834-106">Nachdem Sie das PointOfService-Gerät, das Sie verwenden möchten, identifiziert haben, entweder über eine neue Aufzählung oder eine gespeicherte Geräte-ID, rufen Sie einfach [**FromIdAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) mit der [**DeviceID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) auf, die Sie programmgesteuert ausgewählt haben oder die der Benutzer ausgewählt hat, um ein neues PointofService-Geräteobjekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a3834-106">Once you have identified the PointOfService device that you want to use, either from a fresh enumeration or a stored DeviceID, you just call [**FromIdAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) with the[**DeviceID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) that you have chosen programmatically or the user has selected to create a new Point of Service device object.</span></span>

<span data-ttu-id="a3834-107">In diesem Beispiel wird versucht, ein neues BarcodeScanner-Objekt mit FromIdAsync über eine Geräte-ID zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a3834-107">This sample attempts to create a new BarcodeScanner object with FromIdAsync using a DeviceID.</span></span> <span data-ttu-id="a3834-108">Kommt es beim Erstellen des Objekts zu einem Fehler, wird eine Debugmeldung ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="a3834-108">If there is a failure creating the object a debug message is written.</span></span>

```Csharp

    BarcodeScanner barcodeScanner = await BarcodeScanner.FromIdAsync(DeviceId);

    if(barcodeScanner != null)
    {
        // after successful creation, claim the scanner for exclusive use and enable it to exchange data
    }
    else
    {
        Debug.WriteLine("Failure to create barcodeScanner object");
    }
    
```

<span data-ttu-id="a3834-109">Wenn Sie ein Geräteobjekt haben, können Sie auf die Methoden, Eigenschaften und Ereignisse des Geräts zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a3834-109">Once you have a device object, you can then access the device's methods, properties and events.</span></span>  

## <a name="device-object-lifecycle"></a><span data-ttu-id="a3834-110">Lebenszyklus des Geräteobjekts</span><span class="sxs-lookup"><span data-stu-id="a3834-110">Device object lifecycle</span></span>
<span data-ttu-id="a3834-111">Vor Windows 8 hatten Apps einen einfachen Lebenszyklus.</span><span class="sxs-lookup"><span data-stu-id="a3834-111">Before Windows 8, apps had a simple lifecycle.</span></span> <span data-ttu-id="a3834-112">Win32- und .NET-Apps werden entweder ausgeführt oder nicht. Und PointOfService-Peripheriegeräte wurden für gewöhnlich für den gesamten App-Lebenszyklus in Anspruch genommen.</span><span class="sxs-lookup"><span data-stu-id="a3834-112">Win32 and .NET apps are either running or not running and PointOfService peripehrals were usually claimed for the full app lifecycle.</span></span> <span data-ttu-id="a3834-113">Wenn ein Benutzer eine App minimiert oder verlässt, wird sie weiterhin ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a3834-113">When a user minimizes them, or switches away from them, they continue to run.</span></span> <span data-ttu-id="a3834-114">Dies war in Ordnung, bis tragbare Geräte und die effiziente Energienutzung immer wichtiger wurden.</span><span class="sxs-lookup"><span data-stu-id="a3834-114">This was fine until portable devices and power management became increasingly important.</span></span>

<span data-ttu-id="a3834-115">In Windows 8 wurde mit UWP-Apps ein neues Anwendungsmodell eingeführt.</span><span class="sxs-lookup"><span data-stu-id="a3834-115">Windows 8 introduced a new application model with UWP apps.</span></span> <span data-ttu-id="a3834-116">Auf oberer Ebene wurde der neue Zustand „Angehalten“ eingeführt.</span><span class="sxs-lookup"><span data-stu-id="a3834-116">At a high level, a new suspended state was added.</span></span> <span data-ttu-id="a3834-117">Kurze Zeit, nachdem der Benutzer eine UWP-App minimiert oder zu einer anderen App wechselt, wird sie angehalten.</span><span class="sxs-lookup"><span data-stu-id="a3834-117">A UWP app is suspended shortly after the user minimizes it or switches to another app.</span></span> <span data-ttu-id="a3834-118">Dies bedeutet Folgendes: die Threads der App werden angehalten, die App verbleibt im Arbeitsspeicher, es sei denn, das Betriebssystem muss Ressourcen zurückfordern, und alle Geräteobjekte, die PointOfService-Peripheriegeräte darstellen, werden automatisch geschlossen, damit andere Anwendungen auf die Peripheriegeräte zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="a3834-118">This means that the app's threads are stopped, the app is left in memory unless the operating system needs to reclaim resources, and any device objects representing PointOfService peripherals are automatically closed to allow other applications access to the peripherals.</span></span> <span data-ttu-id="a3834-119">Wenn der Benutzer zur App zurückwechselt, kann diese schnell in einen ausgeführten Zustand wiederhergestellt werden, und auch die Verbindungen mit PointOfService-Peripheriegeräten werden wiederhergestellt, sofern sie zum Fortsetzen noch verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a3834-119">When the user switches back to the app, it can be quickly restored to a running state and restore PointOfService peripherals connections provided they are still available on resume.</span></span>

<span data-ttu-id="a3834-120">Mit einem <DeviceObject>.Closed-Ereignishandler können Sie erkennen, wann ein Objekt aus irgendeinem Grund geschlossen wird. Notieren Sie sich dann die Geräte-ID, um die Verbindung in der Zukunft wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a3834-120">You can detect when an object is closed for any reason with a <DeviceObject>.Closed event handler then make note of the device ID for re-establishing the connection in the future.</span></span>   <span data-ttu-id="a3834-121">Alternativ möchten Sie dies ggf. mit einer Benachrichtigung zum Anhalten der App handhaben, um die Geräte-IDs zur Wiederherstellung der Geräteverbindungen bei Benachrichtigung zum Fortsetzen der App zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a3834-121">Alternatively, you may wish to handle this on an App Suspend notification to save the device ID's for re-establishing the device connections on App Resume notifiation.</span></span>  <span data-ttu-id="a3834-122">Stellen Sie sicher, dass Sie die Ereignishandler nicht duplizieren und keine doppelten Aktionen für das Geräteobjekt für <DeviceObject>.Closed und App Suspend ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a3834-122">Make sure that you do not double up on the event handlers and duplicate actions for the device object on both <DeviceObject>.Closed and App Suspend.</span></span>

> [!TIP]
> <span data-ttu-id="a3834-123">Weitere Informationen zum Anwendungslebenszyklus für die Universelle Windows-Plattform (UWP) in Windows10 finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="a3834-123">Please refer to the following topics for more information about Windows 10 Universal Windows Platform (UWP) application lifecycle:</span></span>
> - [<span data-ttu-id="a3834-124">Lebenszyklus von Windows 10-UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="a3834-124">Windows 10 Universal Windows Platform (UWP) app lifecycle</span></span>](../launch-resume/app-lifecycle.md)
> - [<span data-ttu-id="a3834-125">Behandeln des Anhaltens von Apps</span><span class="sxs-lookup"><span data-stu-id="a3834-125">Handle app suspension</span></span>](../launch-resume/suspend-an-app.md)
> - [<span data-ttu-id="a3834-126">Behandeln der App-Fortsetzung</span><span class="sxs-lookup"><span data-stu-id="a3834-126">Handle app resume</span></span>](../launch-resume/resume-an-app.md)
