---
author: v-angraf
title: Geräteportal für Xbox– REST-API
description: API-Referenz für UWP auf Xbox One.
ms.author: v-angraf
ms.date: 10/25/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 5ae8e953-0465-487b-81dd-54a85c904daf
ms.localizationpriority: medium
ms.openlocfilehash: 894bc6f657f4a65072056a14171bf86b92cced38
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5984494"
---
# <a name="xbox-device-portal-rest-api"></a>Geräteportal für Xbox– REST-API

Dieser Abschnitt enthält Referenzthemen für die REST-API für das Xbox-Geräteportal. Diese wird verwendet, um Ihre Konsole per Fernzugriff zu konfigurieren und zu verwalten.

| URI        | Beschreibung |
|------------|-------------|
|[/api/app/packagemanager/register](wdp-loose-folder-register-api.md)| Registriert eine App, die in einem losen Ordner enthalten ist. |
|[/api/app/packagemanager/upload](wdp-folder-upload.md)| Lädt einen ganzen Ordner zur Konsole hoch. |
|[/ext/App/sshpins](uwp-sshpins-api.md)| Löschen Sie alle vertrauenswürdigen SSH-PINs per Fernzugriff. Dies erfordert die erneute PIN-Kopplung für die UWP-Entwicklung in Visual Studio. |
|[/ext/app/deployinfo](uwp-deployinfo-api.md)| Fordert Bereitstellungsinformationen für ein oder mehrere installierte Pakete an. |
|[/ext/fiddler](wdp-fiddler-api.md)| Zum Aktivieren und Deaktivieren der Fiddler-Netzwerkablaufverfolgung |
|[/ext/httpmonitor/sessions](wdp-httpMonitor-api.md)| Abrufen des HTTP-Datenverkehrs aus der fokussierten App auf der Xbox |
|[/ext/networkcredential](uwp-networkcredentials-api.md)| Hinzufügen, Entfernen oder Aktualisieren der Netzwerkanmeldeinformationen |
|[/ext/remoteinput](uwp-remoteinput-api.md)| Senden von Tastatur-, Maus- oder Controllereingaben auf einer Xbox per Fernzugriff |
|[/ext/remoteinput/controllers](uwp-remoteinput-controllers-api.md)| Abrufen der Anzahl der angeschlossenen physischen Controller oder Deaktivieren aller physischen Controller |
|[/ext/screenshot](wdp-media-capture-api.md)| Erfasst eine PNG-Darstellung des Bildschirms, der zurzeit auf der Konsole angezeigt wird. |
|[/ext/settings](wdp-xboxsettings-api.md)| Greift auf Xbox One-Entwicklereinstellungen zu. |
|[/ext/smb/developerfolder](wdp-smb-api.md)| Greift über den Datei-Explorer auf Ihrem Entwicklungscomputer auf den Entwicklerordner auf Ihrer Konsole zu. |
|[/ext/user](wdp-user-management.md)| Verwaltet Benutzer auf der Xbox One Konsole. |
|[/ext/xbox/info](wdp-xboxinfo-api.md)| Bietet Informationen zum Xbox One-Gerät |
|[/ext/xboxlive/sandbox](wdp-sandbox-api.md)| Verwaltet Ihren Xbox Live-Sandkasten. |

## <a name="see-also"></a>Siehe auch

- [UWP auf Xbox One](index.md)
- [Windows-Geräteportal](../debug-test-perf/device-portal.md)