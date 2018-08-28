---
author: PatrickFarley
title: Verbundene Apps und Geräte (Project Rome)
description: In diesem Abschnitt wird beschrieben, wie Sie mithilfe der Remote Systems-Plattform Remotegeräte entdecken, eine App auf einem Remotegerät starten und mit einem App-Dienst auf einem Remotegerät kommunizieren.
ms.author: pafarley
ms.date: 06/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Geräte für Windows 10, Uwp, verbunden, remote-Systemen, ROM, Project ROM
ms.assetid: 7f39d080-1fff-478c-8c51-526472c1326a
ms.localizationpriority: medium
ms.openlocfilehash: d3efb7e094ce1464028dadaa14c6f0bfb3f3b214
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2884697"
---
# <a name="connected-apps-and-devices-project-rome"></a>Verbundene Apps und Geräte (Project Rome)

In diesem Abschnitt wird beschrieben, wie Apps mithilfe von Project Rome geräte- und plattformübergreifend verbunden werden. Erfahren Sie, wie Sie Remotegeräte entdecken, eine App auf einem Remotegerät starten und mit einem App-Dienst auf einem Remotegerät kommunizieren.

Die meisten Benutzer verfügen über mehrere Geräte, wobei sie häufig eine Aktivität auf einem Gerät beginnen und auf einem anderen Gerät abschließen. Dazu müssen Apps geräte- und plattformübergreifend sein.

Die mit Windows 10, Version 1607, eingeführten [Remotesysteme-APIs](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems) ermöglichen Ihnen das Schreiben von Apps, mit denen Benutzer eine Aufgabe auf einem Gerät starten und auf einem anderen Gerät abschließen können. Die Aufgabe bleibt der zentrale Fokus, und Benutzer können an dem für sie komfortabelsten Gerät arbeiten. Zum Beispiel hört ein Benutzer vielleicht Radio auf seinem Mobiltelefon. Aber zu Hause angekommen möchte er möglicherweise die Wiedergabe auf seine Xbox One übertragen, die in die Heim-Stereoanlage eingebunden ist.

Sie können Project Rome auch für Begleitgeräte oder Remotesteuerungsszenarien verwenden. Verwenden Sie die App-Dienst-Messaging-APIs, um einen App-Kanal zwischen zwei Geräten zum Senden und Empfangen von benutzerdefinierten Nachrichten zu erstellen. Beispielsweise können Sie eine App für Ihr Mobiltelefon schreiben, die die Wiedergabe auf Ihrem Fernsehgerät steuert, oder eine Begleit-App, die Informationen über die Charaktere in einer Fernsehsendung bereitstellt, die Sie sich in einer anderen App ansehen.  

Geräte können über Bluetooth und Wireless LAN proximal oder remote über die Cloud verbunden werden und sind über das Microsoft-Konto (MSA) der Person verbunden, die sie verwendet.

Unter [UWP-Beispiel für Remotesysteme](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems ) finden Sie Beispiele für die Vorgehensweise zum Erkennen eines Remotesystems, Starten einer App auf einem Remotesystem und Verwenden von App-Diensten zum Senden von Nachrichten zwischen Apps, die auf zwei Systemen ausgeführt werden.

Weitere Informationen zu Project Rome im Allgemeinen, einschließlich Ressourcen für die plattformübergreifende Integration, finden Sie unter [aka.ms/project-rome](https://aka.ms/project-rome).

| Thema | Beschreibung |
|-------|-------------|
| [Starten einer App auf einem Remotegerät](launch-a-remote-app.md) | Erfahren Sie, wie Sie eine App auf einem Remotegerät starten. In diesem Thema werden der einfachste Anwendungsfall und die vorläufige Einrichtung behandelt.  |
| [Erkennen von Remotegeräten](discover-remote-devices.md)  | Erfahren Sie, wie Sie Geräte erkennen, zu denen Sie eine Verbindung herstellen können. |
| [Kommunizieren mit einem App-Remotedienst](communicate-with-a-remote-app-service.md) | Erfahren Sie, wie Sie mit einer App auf einem Remotegerät interagieren. |
| [Verbinden von Geräten über Remotesitzungen](remote-sessions.md) | Ermöglichen Sie die gemeinsame Nutzung auf verbundenen Geräten, indem Sie diese in einer Remotesitzung vereinen. |
| [Benutzeraktivitäten geräteübergreifend fortsetzen](useractivities.md)| Helfen Sie Benutzern fortsetzen, was sie sogar über mehrere Geräte in Ihrer app getan haben.|
| [Bewährte Methoden für Benutzer Aktivitäten](useractivities-best-practices.md)| Hier erfahren Sie die empfohlenen Vorgehensweisen zum Erstellen und aktualisieren die Benutzeraktivitäten.|
