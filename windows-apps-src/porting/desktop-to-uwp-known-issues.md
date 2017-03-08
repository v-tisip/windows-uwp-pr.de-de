---
author: awkoren
Description: "Dieser Artikel enthält bekannte Probleme mit der Desktop-zu-UWP-Brücke."
Search.Product: eADQiWindows 10XVcnh
title: "Bekannte Probleme mit der Desktop-Brücke"
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: 71f8ffcb-8a99-4214-ae83-2d4b718a750e
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: d7f7cfef59c02c3a8930c1bbc2c87cc40675ca22
ms.lasthandoff: 02/08/2017

---
# <a name="known-issues-with-the-desktop-bridge"></a>Bekannte Probleme mit der Desktop-Brücke

Dieser Artikel enthält bekannte Probleme mit der Desktop-zu-UWP-Brücke.

## <a name="blue-screen-with-error-code-0x139-kernelsecuritycheckfailure"></a>Blauer Bildschirm mit dem Fehlercode 0x139 (KERNEL_SECURITY_CHECK_FAILURE)

Nach dem Installieren oder Starten bestimmter Apps aus dem Windows Store wird Ihr Computer unter Umständen unerwartet mit folgendem Fehler neu gestartet: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.

Bekannte betroffene Apps: Kodi, JT2Go, Ear Trumpet, Teslagrad usw.

Am 27.10.2016 wurde ein [Windows-Update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) veröffentlich, das wichtige Fehlerbehebungen für dieses Problem enthält. Falls bei Ihnen dieses Problem auftritt, aktualisieren Sie Ihren Computer. Falls Sie Ihren PC nicht aktualisieren können, weil er neu gestartet wird, bevor Sie sich anmelden können, müssen Sie die Systemwiederherstellung verwenden, um für Ihr System einen Zeitpunkt herzustellen, der vor der Installation einer der betroffenen Apps liegt. Informationen zur Systemwiederherstellung finden Sie unter [Wiederherstellungsoptionen unter Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options). 

Falls das Problem durch das Update nicht behoben werden kann oder Sie nicht sicher sind, wie Sie die Wiederherstellung für den PC ausführen, wenden Sie sich an den [Microsoft-Support](https://support.microsoft.com/contactus/). 

Wenn Sie Entwickler sind, möchten Sie die Installation der Desktop-Brücken-Apps unter Versionen von Windows vielleicht verhindern, die dieses Update nicht enthalten. Beachten Sie, dass Ihre App dadurch nicht für Kunden verfügbar ist, die das Update noch nicht installiert haben. Um die Verfügbarkeit Ihrer App auf Benutzer zu beschränken, die dieses Update installiert haben, ändern Sie die Datei „AppxManifest.xml“ wie folgt:

```<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.351" MaxVersionTested="10.0.14393.351"/>```

Details zum Windows-Update finden Sie hier: 
* https://support.microsoft.com/kb/3197954
* https://support.microsoft.com/help/12387/windows-10-update-history
