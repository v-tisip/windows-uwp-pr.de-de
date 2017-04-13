---
author: TylerMSFT
title: "Starten einer App auf einem Remotegerät"
description: "Erfahren Sie, wie Sie mithilfe von Project Rome eine App auf einem Remotegerät starten können."
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 54f6a33d-a3b5-4169-8664-653dbab09175
ms.openlocfilehash: 15ab4c39f4da1bb524f912d4e6ab6b3e6a5f34c6
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="launch-an-app-on-a-remote-device"></a>Starten einer App auf einem Remotegerät

In diesem Artikel wird das Starten einer Windows-App auf einem Remotegerät beschrieben.

Ab Windows10, Version 1607, kann eine UWP-App eine UWP-App oder Windows-Desktopanwendung remote auf einem anderen Geräte starten, auf dem ebenfalls Windows10, Version 1607 oder höher, ausgeführt wird. Voraussetzung ist, dass beide Geräte mit dem gleichen Microsoft-Konto (MSA) angemeldet sind.

Das Feature für den Remotestart ermöglicht aufgabenorientierte Benutzeroberflächen, in denen ein Benutzer eine Aufgabe auf einem Gerät starten und auf einem anderen Gerät beenden kann. Wenn Benutzer beispielsweise auf dem Mobiltelefon im Auto Musik hören, könnten sie die Wiedergabe anschließend an ihre Xbox One übertragen, wenn sie zu Hause ankommen. Durch Remotestarten können Sie kontextbezogene Daten an die Remote-App übergeben, die gestartet wird, damit diese den Vorgang an der Stelle fortsetzt, an der dieser unterbrochen wurde.

## <a name="add-the-remotesystem-capability"></a>Hinzufügen der Funktionen „remoteSystem“

Damit Ihre App eine App auf einem Remotegerät starten kann, müssen Sie Ihrem App-Paketmanifest die Funktion `remoteSystem` hinzufügen. Sie können den Paketmanifest-Designer verwenden, um die Funktion hinzuzufügen, indem Sie auf der Registerkarte **Funktionen** die Option **Remotesystem** auswählen. Sie können auch der Datei „Package.appxmanifest“ Ihres Projekts die folgende Zeile manuell hinzufügen.

``` xml
<Capabilities>
   <uap3:Capability Name="remoteSystem"/>
 </Capabilities>
```
## <a name="find-a-remote-device"></a>Suchen eines Remotegeräts

Sie müssen zunächst das Gerät suchen, zu dem Sie eine Verbindung herstellen möchten. Eine detaillierte Anleitung dazu finden Sie unter [Ermitteln von Remotegeräten](discover-remote-devices.md). Wir verwenden hier eine einfache Methode, bei der die Funktionen zum Filtern nach Gerät oder nach Verbindungsart nicht verwendet werden. Wir erstellen ein Überwachungselement, das nach Remotesystemen sucht, und erstellen Handler für die Ereignisse, die ausgelöst werden, wenn Geräte erkannt oder entfernt werden. Auf diese Weise erhalten wir eine Sammlung von Remotegeräten.

Der Code in diesen Beispielen setzt voraus, dass Sie über eine `using Windows.System.RemoteSystems`-Anweisung in Ihrer Datei verfügen.

[!code-cs[Main](./code/RemoteLaunchScenario/MainPage.xaml.cs#SnippetBuildDeviceList)]

Als Erstes müssen Sie vor einem Remotestart die Funktion `RemoteSystem.RequestAccessAsync()` aufrufen. Überprüfen Sie den Rückgabewert, um sicherzustellen, dass Ihre App auf Remotegeräte zugreifen darf. Diese Überprüfung ist beispielsweise nicht erfolgreich, wenn Sie Ihrer App nicht die Funktion `remoteSystem` hinzugefügt haben.

Die Ereignishandler der Systemüberwachung werden aufgerufen, wenn ein Gerät, mit dem wir eine Verbindung herstellen können, erkannt wird oder nicht mehr verfügbar ist. Wir verwenden diese Ereignishandler, um eine fortlaufend aktualisierte Liste der Geräte zu führen, mit denen wir eine Verbindung herstellen können.

[!code-cs[Main](./code/RemoteLaunchScenario/MainPage.xaml.cs#SnippetEventHandlers)]

Wir verfolgen die Geräte nach Remotesystem-ID unter Verwendung eines **Wörterbuchs** nach. Es wird eine **ObservableCollection** verwendet, die eine Liste der enumerierbaren Geräte enthält. Eine **ObservableCollection** vereinfacht auch das Binden der Geräteliste an die UI, auch wenn wir dies in diesem Beispiel nicht ausführen.

[!code-cs[Main](./code/RemoteLaunchScenario/MainPage.xaml.cs#SnippetMembers)]

Fügen Sie Ihrem App-Startcode einen Aufruf an `BuildDeviceList()` hinzu, bevor Sie versuchen, eine Remote-App zu starten.

## <a name="launch-an-app-on-a-remote-device"></a>Starten einer App auf einem Remotegerät

Sie starten eine App remote, indem Sie das Gerät, mit dem Sie eine Verbindung herstellen möchten, an die [**RemoteLauncher.LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/windows.system.remotelauncher.launchuriasync.aspx)-API übergeben. Für diese Methode gibt es drei Überladungen. Die einfachste Überladung, die in diesem Beispiel gezeigt wird, gibt den URI an, der die App auf dem Remotegerät aktiviert. In diesem Beispiel öffnet der URI die Karten-App auf dem Remotecomputer mit einer 3D-Ansicht der Space Needle.

Andere **RemoteLauncher.LaunchUriAsync**-Überladungen ermöglichen die Angabe von Optionen, wie den URI der Website, die angezeigt werden soll, wenn keine entsprechende App auf dem Remotegerät gestartet werden kann, und die Angabe einer optionalen Liste der Paketfamiliennamen, die zum Starten des URIs auf dem Remotegerät verwendet werden können. Sie können auch Daten in Form von Schlüssel-Wert-Paaren bereitstellen. Sie können beispielsweise Daten an die App übergeben, die Sie aktivieren, um einen Kontext für die Remote-App bereitzustellen, etwa den Namen des wiederzugebenden Titels oder die aktuelle Position der Wiedergabe bei der Übergabe von einem Gerät an ein anderes.

In Szenarien in der Praxis können Sie eine Benutzeroberfläche bereitstellen, um das Zielgerät auszuwählen. In diesem Beispiel verwenden wir zur Vereinfachung nur das erste Remotegerät in der Liste.

[!code-cs[Main](./code/RemoteLaunchScenario/MainPage.xaml.cs#SnippetRemoteUriLaunch)]

Das [**RemoteLaunchUriStatus**](https://msdn.microsoft.com/library/windows/apps/windows.system.remotelaunchuristatus.aspx)-Objekt, das von **RemoteLauncher.LaunchUriAsync()** zurückgegeben wird, enthält Informationen dazu, ob der Remotestart erfolgreich war. Wenn bei dem Remotestart ein Fehler aufgetreten ist, wird ein Grund angegeben.

## <a name="related-topics"></a>Verwandte Themen

[API-Referenz für Remotesysteme](https://msdn.microsoft.com/library/windows/apps/Windows.System.RemoteSystems)  
[Übersicht über verbundene Apps und Geräte (Project Rome)](connected-apps-and-devices.md)  
[Ermitteln von Remotegeräten](discover-remote-devices.md)  
Das [Beispiel für Remotesysteme](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) zeigt die Vorgehensweise zum Erkennen eines Remotesystems, Starten einer App auf einem Remotesystem und Verwenden von App-Diensten zum Senden von Nachrichten zwischen Apps, die auf zwei Systemen ausgeführt werden.
