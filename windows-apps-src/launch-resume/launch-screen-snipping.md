---
title: Ausschnitt & Skizze starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder einen neuen Ausschnitt Öffnen verwenden.
ms.date: 8/1/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 7aa0b70aee50c79088a68378fa75664711c3d564
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8467677"
---
# <a name="launch-screen-snipping"></a>Ausschnitt & Skizze starten

Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas können Sie starten snipping oder Screenshots bearbeiten.

## <a name="open-a-new-snip-from-your-app"></a>Öffnen Sie einen neuen Ausschnitt aus Ihrer app

Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt. Der resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.

**ms-Screenclip:** hat die folgenden Parameter:

| Parameter | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Quelle | string | Nein | Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet. |
| delayInSeconds | int | nein | Eine ganze Zahl von 1 bis zu 30. Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt. |

## <a name="launching-the-snip--sketch-app"></a>Starten der Ausschnitt & Skizze App

Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der app Ausschnitt & Skizze, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.

**ms-Screensketch:** hat die folgenden Parameter:

| Parameter | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| sharedAccessToken | string | Nein | Ein Token, identifizieren die Datei in der app Ausschnitt & Skizze geöffnet. Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden. Wenn dieser Parameter nicht angegeben ist, wird die app ohne Öffnen der Datei gestartet werden. |
| Quelle | string | Nein | Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet. |
| isTemporary | bool | nein | Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet. |

Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer app zu senden.

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```
