---
author: TylerMSFT
title: "Verbundene Apps und Geräte (Project Rome)"
description: "In diesem Abschnitt wird beschrieben, wie Sie mithilfe der Remote Systems-Plattform Remotegeräte entdecken, eine App auf einem Remotegerät starten und mit einem App-Dienst auf einem Remotegerät kommunizieren."
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 7f39d080-1fff-478c-8c51-526472c1326a
ms.openlocfilehash: 29b7db48f2dbd699f9c4f674a8870fe8f8ca446d
ms.sourcegitcommit: 73c61e8e409b071365a2f6ebd89bd8a769b2a7c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2017
---
# <a name="connected-apps-and-devices-project-rome"></a>Verbundene Apps und Geräte (Project Rome)

In diesem Abschnitt wird beschrieben, wie Apps mithilfe von Project „Rome“ geräte- und plattformübergreifend verbunden werden. Erfahren Sie, wie Sie Remotegeräte entdecken, eine App auf einem Remotegerät starten und mit einem App-Dienst auf einem Remotegerät kommunizieren.

Die meisten Benutzer verfügen über mehrere Geräte, wobei sie häufig eine Aktivität auf einem Gerät beginnen und auf einem anderen Gerät abschließen. Dazu müssen Apps geräte- und plattformübergreifend sein.

Die mit Windows 10, Version 1607, eingeführten [Remotesysteme-APIs](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems) ermöglichen es Ihnen, Apps zu schreiben, mit denen Benutzer eine Aufgabe auf einem Gerät starten und auf einem anderen Gerät abschließen können. Die Aufgabe bleibt der zentrale Fokus, und Benutzer können an dem für sie komfortabelsten Gerät arbeiten. Zum Beispiel hören Sie im Auto vielleicht Radio auf Ihrem Mobiltelefon. Aber zu Hause angekommen möchten Sie möglicherweise die Wiedergabe auf Ihre Xbox One übertragen, die in Ihre Heim-Stereoanlage eingebunden ist.

Sie können Project "Rome" auch für Begleitgeräte oder Remotesteuerungsszenarien verwenden. Verwenden Sie die App-Messaging-APIs, um einen App-Kanal zwischen zwei Geräten zum Senden und Empfangen von benutzerdefinierten Nachrichten zu erstellen. Beispielsweise können Sie eine App für Ihr Mobiltelefon schreiben, die die Wiedergabe auf Ihrem Fernsehgerät steuert, oder eine Begleit-App, die Informationen über die Charaktere in einer Fernsehsendung bereitstellt, die Sie sich auf einer anderen App ansehen.  

Geräte können über Bluetooth und Wireless LAN proximal verbunden werden, oder remote über die Cloud, und sind über das Microsoft-Konto der Person verbunden, die sie verwendet.

Unter [Beispiel für Remotesysteme](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems ) finden Sie Beispiele für die Vorgehensweise zum Erkennen eines Remotesystems, Starten einer App auf einem Remotesystem und Verwenden von App-Diensten zum Senden von Nachrichten zwischen Apps, die auf zwei Systemen ausgeführt werden.

| Thema | Beschreibung |
|-------|-------------|
| [Entdecken von Remotegeräten](discover-remote-devices.md)  | Erfahren Sie, wie Sie Geräte entdecken, zu denen Sie eine Verbindung herstellen können. |
| [Starten einer App auf einem Remotegerät](launch-a-remote-app.md) | Erfahren Sie, wie Sie eine App auf einem Remotegerät starten.  |
| [Kommunizieren mit einem App-Remotedienst](communicate-with-a-remote-app-service.md) | Erfahren Sie, wie Sie mit einer App auf einem Remotegerät interagieren. |
