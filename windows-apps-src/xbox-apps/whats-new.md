---
author: v-angraf
title: "Neuigkeiten für UWP auf Xbox One"
description: "Vorstellung neuer Features für UWP-Apps auf Xbox One."
ms.author: v-angraf
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: fe63c527-8f06-43a5-868f-de909f5664b3
ms.openlocfilehash: 5546177401630e8938f0d25d77ea42afdbfb55d7
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="whats-new-for-developers-in-the-latest-update-of-uwp-on-xbox-one"></a>Neuigkeiten für Entwickler in der neuesten Aktualisierung von UWP auf Xbox One

Die Developer Preview-Version vom Juli2016 für die Universelle Windows-Plattform (UWP) auf Xbox One enthält die folgenden neuen Features, Featureupdates und Fehlerkorrekturen.

## <a name="networking-using-tcpudp-sockets-is-now-available"></a>Netzwerke auf der Basis von TCP/UDP-Sockets sind jetzt verfügbar  
Der ein- und ausgehende Netzwerkzugriff von Konsolen, die herkömmliche TCP/UDP-Sockets (WinSock, Windows.Networking.Sockets) verwenden, ist nun verfügbar.

## <a name="fiddler-support"></a>Fiddler-Unterstützung
Sie können nun Fiddler als Proxy für eine Konsole aktivieren, für die die Universelle Windows Plattform (UWP) auf Xbox One aktiviert ist. Fiddler ermöglicht Ihnen die Anmeldung und Überprüfung des gesamten HTTP-/HTTPS-Datenverkehrs zu und von Xbox-Diensten und Webdiensten vertrauender Parteien. Weitere Informationen finden Sie unter [Verwendung von Fiddler mit Xbox One bei der Entwicklung für UWP](uwp-fiddler.md).

## <a name="mouse-mode-is-now-enabled-by-default"></a>Mausmodus nun standardmäßig aktiviert
Der Mausmodus ist jetzt standardmäßig für XAML- und gehostete Web-Apps aktiviert.
Es wird nachdrücklich empfohlen, diese Option zu deaktivieren und die direktionale Navigation über den Controller zu optimieren.
Informationen zum Deaktivieren des Mausmodus finden Sie unter [So wird's gemacht: Deaktivieren des Mausmodus](how-to-disable-mouse-mode.md).
Weitere Informationen dazu, wie Sie großartige Apps für die Xbox entwerfen, finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](../input-and-devices/designing-for-tv.md#mouse-mode).

## <a name="extended-uwp-api-surface-area-is-now-functional-on-the-console"></a>Der erweiterte UWP-API-Oberflächenbereich ist jetzt in der Konsole verwendungsbereit.
Zusätzliche UWP-APIs sind jetzt in der Xbox-Konsole verwendungsbereit. Weitere Informationen zur UWP-API-Unterstützung finden Sie unter [UWP-Funktionen, die noch nicht auf Xbox One unterstützt werden](http://go.microsoft.com/fwlink/p/?LinkID=760755). 

## <a name="background-music-and-audio-capabilities"></a>Funktionen für Hintergrundmusik und -audio
Sie können jetzt Musik und Audio einer im Hintergrund ausgeführten App wiedergeben.

## <a name="xaml-improvements"></a>XAML-Verbesserungen
Die XAML-Plattform wurde wie folgt verbessert:
-    Das Fokusrechteck ist jetzt für ein 10-Fuß-TV-Erlebnis gestaltet.
-    Xbox-Sounds sind jetzt in die XAML-Plattform eingebettet.
-    Die XY-Fokusnavigation zwischen UI-Elementen wurde verbessert. 

## <a name="you-can-now-change-the-size-of-allocated-developer-storage-on-the-console"></a>Sie können jetzt die Größe des zugewiesenen Entwicklerspeichers auf der Konsole ändern.
Mithilfe einer neuen Einstellung in der Dev Home-App können Sie den zugeordneten Entwicklerspeicher auf der Konsole vergrößern oder verkleinern. Weitere Informationen zum Ändern der Größe des zugeordneten Entwicklerspeichers finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).

## <a name="wdp-tool-enhancements"></a>Verbesserungen am WDP-Tool
Am WDP (Windows Device Portal)-Tool für Xbox wurden folgende Verbesserungen vorgenommen:
 - Das Tool enthält zusätzliche Konsoleneinstellungen. Weitere Informationen zu Konsoleneinstellungen finden Sie im Referenzthema [/ext/settings](wdp-xboxsettings-api.md). 
 - Benutzer können auf der Konsole an- und abgemeldet werden. Weitere Informationen zu Benutzern finden Sie im Referenzthema [/ext/user](wdp-user-management.md).
 - Sie können jetzt einen Screenshot der Konsole erstellen. Weitere Informationen zum Erstellen eines Screenshots finden Sie im Referenzthema [/ext/screenshot](wdp-media-capture-api.md).
 - Das Tool kann einen losen Dateibuild Ihrer App bereitstellen. Weitere Informationen zu losen Dateibuilds finden Sie im Referenzthema [/api/app/packagemanager/register](wdp-loose-folder-register-api.md).
 - Sie können auf Entwicklerdateien auf der Konsole über einen Datei-Explorer auf Ihrem Entwicklungscomputer zugreifen. Weitere Informationen zum Zugreifen auf Dateien über einen Datei-Explorer finden Sie im Referenzthema [/ext/smb/developerfolder](wdp-smb-api.md).

## <a name="see-also"></a>Weitere Informationen
- [Bekannte Probleme](known-issues.md)
- [UWP auf XboxOne](index.md)
