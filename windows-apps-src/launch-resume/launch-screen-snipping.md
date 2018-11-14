---
author: QuinnRadich
title: Ausschnitt & Skizze starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder öffnen einen neuen Ausschnitt verwenden.
ms.author: quradic
ms.date: 8/1/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.openlocfilehash: 64df8d9768fa20a6d6819e93fe06904feede6223
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6264641"
---
# <a name="launch-screen-snipping"></a>Ausschnitt & Skizze starten

Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas ermöglicht es Ihnen, snipping oder Bearbeiten von Screenshots zu initiieren.

## <a name="open-a-new-snip-from-your-app"></a>Öffnen Sie einen neuen Ausschnitt aus Ihrer app

Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt. Die resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.

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
| sharedAccessToken | string | Nein | Ein Token, identifizieren die Datei in der app Ausschnitt & Skizze geöffnet. Von [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen. Wenn dieser Parameter ausgelassen wird, wird die app ohne Öffnen der Datei gestartet werden. |
| Quelle | string | Nein | Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet. |
| isTemporary | bool | nein | Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet. |

Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer die app zu senden.

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```