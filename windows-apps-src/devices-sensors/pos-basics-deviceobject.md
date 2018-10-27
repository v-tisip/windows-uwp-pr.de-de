---
author: TerryWarwick
title: PointOfService-Geräteobjekte
description: Hier erfahren Sie, wie PointOfService-Geräteobjekte erstellt werden.
ms.author: jken
ms.date: 06/19/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 31af943ab4a9231f58fb2e3d5489e9ae80d8d565
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5707361"
---
# <a name="pointofservice-device-objects"></a>PointOfService-Geräteobjekte

## <a name="creating-a-device-object"></a>Erstellen eines Geräteobjekts
Nachdem Sie das PointOfService-Gerät, das Sie verwenden möchten, identifiziert haben, entweder über eine neue Aufzählung oder eine gespeicherte Geräte-ID, rufen Sie einfach [**FromIdAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) mit der [**DeviceID**](https://docs.microsoft.com/uwp/api/windows.devices.enumeration.deviceinformation.id) auf, die Sie programmgesteuert ausgewählt haben oder die der Benutzer ausgewählt hat, um ein neues PointofService-Geräteobjekt zu erstellen.

In diesem Beispiel wird versucht, ein neues BarcodeScanner-Objekt mit FromIdAsync über eine Geräte-ID zu erstellen. Kommt es beim Erstellen des Objekts zu einem Fehler, wird eine Debugmeldung ausgegeben.

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

Wenn Sie ein Geräteobjekt haben, können Sie auf die Methoden, Eigenschaften und Ereignisse des Geräts zugreifen.  

## <a name="device-object-lifecycle"></a>Lebenszyklus des Geräteobjekts
Vor Windows 8 hatten Apps einen einfachen Lebenszyklus. Win32- und .NET-Apps werden entweder ausgeführt oder nicht. Und PointOfService-Peripheriegeräte wurden für gewöhnlich für den gesamten App-Lebenszyklus in Anspruch genommen. Wenn ein Benutzer eine App minimiert oder verlässt, wird sie weiterhin ausgeführt. Dies war in Ordnung, bis tragbare Geräte und die effiziente Energienutzung immer wichtiger wurden.

In Windows 8 wurde mit UWP-Apps ein neues Anwendungsmodell eingeführt. Auf oberer Ebene wurde der neue Zustand „Angehalten“ eingeführt. Kurze Zeit, nachdem der Benutzer eine UWP-App minimiert oder zu einer anderen App wechselt, wird sie angehalten. Dies bedeutet Folgendes: die Threads der App werden angehalten, die App verbleibt im Arbeitsspeicher, es sei denn, das Betriebssystem muss Ressourcen zurückfordern, und alle Geräteobjekte, die PointOfService-Peripheriegeräte darstellen, werden automatisch geschlossen, damit andere Anwendungen auf die Peripheriegeräte zugreifen können. Wenn der Benutzer zur App zurückwechselt, kann diese schnell in einen ausgeführten Zustand wiederhergestellt werden, und auch die Verbindungen mit PointOfService-Peripheriegeräten werden wiederhergestellt, sofern sie zum Fortsetzen noch verfügbar sind.

Mit einem <DeviceObject>.Closed-Ereignishandler können Sie erkennen, wann ein Objekt aus irgendeinem Grund geschlossen wird. Notieren Sie sich dann die Geräte-ID, um die Verbindung in der Zukunft wiederherzustellen.   Alternativ möchten Sie dies ggf. mit einer Benachrichtigung zum Anhalten der App handhaben, um die Geräte-IDs zur Wiederherstellung der Geräteverbindungen bei Benachrichtigung zum Fortsetzen der App zu speichern.  Stellen Sie sicher, dass Sie die Ereignishandler nicht duplizieren und keine doppelten Aktionen für das Geräteobjekt für <DeviceObject>.Closed und App Suspend ausgeführt werden.

> [!TIP]
> Weitere Informationen zum Anwendungslebenszyklus für die Universelle Windows-Plattform (UWP) in Windows10 finden Sie in den folgenden Themen:
> - [Lebenszyklus von Windows 10-UWP-Apps (Universelle Windows-Plattform)](../launch-resume/app-lifecycle.md)
> - [Behandeln des Anhaltens von Apps](../launch-resume/suspend-an-app.md)
> - [Behandeln der App-Fortsetzung](../launch-resume/resume-an-app.md)
