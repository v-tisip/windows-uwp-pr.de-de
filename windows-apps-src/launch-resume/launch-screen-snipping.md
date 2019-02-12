---
title: Ausschnitt & Skizze starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch-URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der Ausschnitt & Skizze app oder einen neuen Ausschnitt Öffnen verwenden.
ms.date: 8/1/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 2bddea1dd2b5f21a145bde789f1ad760bb5e556a
ms.sourcegitcommit: b126940932935ebd2965ea68078798fb6e876b23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "9065987"
---
# <a name="launch-screen-snipping"></a>Ausschnitt & Skizze starten

Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas ermöglicht es Ihnen, snipping oder Bearbeiten von Screenshots zu initiieren.

## <a name="open-a-new-snip-from-your-app"></a>Öffnen Sie einen neuen Ausschnitt aus Ihrer app

Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten einen neuen Ausschnitt. Der resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.

**ms-Screenclip:** hat die folgenden Parameter:

| Parameter | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| Quelle | string | Nein | Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet. |
| delayInSeconds | int | nein | Eine ganze Zahl von 1 bis 30. Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt. |
| callbackformat | string | Nein | Dieser Parameter ist nicht verfügbar. |

## <a name="launching-the-snip--sketch-app"></a>Starten der Ausschnitt & Skizze-App

Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der Ausschnitt & Skizze-app, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.

**ms-Screensketch:** hat die folgenden Parameter:

| Parameter | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| sharedAccessToken | string | Nein | Ein Token, identifizieren die Datei in der Ausschnitt & Skizze app zu öffnen. Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden. Wenn dieser Parameter ausgelassen wird, wird die app ohne Öffnen der Datei gestartet werden. |
| secondarySharedAccessToken | string | Nein | Eine Zeichenfolge, die eine JSON-Datei mit Metadaten zu den Ausschnitt identifiziert. Die Metadaten können ein **ClipPoints** Feld ein Array von x, y-Koordinaten und/oder ein [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity)enthalten. |
| Quelle | string | Nein | Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet. |
| isTemporary | bool | nein | Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet. |

Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus des Benutzers app zu senden.

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```

Das folgende Beispiel veranschaulicht, wie eine Datei, die durch den **SecondarySharedAccessToken** -Parameter des **ms-Screensketch** angegebenen enthalten kann:

```json
{
  "clipPoints": [
    {
      "x": 0,
      "y": 0
    },
    {
      "x": 2080,
      "y": 0
    },
    {
      "x": 2080,
      "y": 780
    },
    {
      "x": 0,
      "y": 780
    }
  ],
  "userActivity": "{\"$schema\":\"http://activity.windows.com/user-activity.json\",\"UserActivity\":\"type\",\"1.0\":\"version\",\"cross-platform-identifiers\":[{\"platform\":\"windows_universal\",\"application\":\"Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge\"},{\"platform\":\"host\",\"application\":\"edge.activity.windows.com\"}],\"activationUrl\":\"microsoft-edge:https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"contentUrl\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"visualElements\":{\"attribution\":{\"iconUrl\":\"https://www.microsoft.com/favicon.ico?v2\",\"alternateText\":\"microsoft.com\"},\"description\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"backgroundColor\":\"#FF0078D7\",\"displayText\":\"Use snipping tool to capture screenshots - Windows Help\",\"content\":{\"$schema\":\"http://adaptivecards.io/schemas/adaptive-card.json\",\"type\":\"AdaptiveCard\",\"version\":\"1.0\",\"body\":[{\"type\":\"Container\",\"items\":[{\"type\":\"TextBlock\",\"text\":\"Use snipping tool to capture screenshots - Windows Help\",\"weight\":\"bolder\",\"size\":\"large\",\"wrap\":true,\"maxLines\":3},{\"type\":\"TextBlock\",\"text\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"size\":\"normal\",\"wrap\":true,\"maxLines\":3}]}]}},\"isRoamable\":true,\"appActivityId\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\"}"
}

```
