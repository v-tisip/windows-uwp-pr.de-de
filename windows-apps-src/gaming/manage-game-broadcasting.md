---
author: drewbatgit
ms.assetid: 
description: "Zeigt, wie Sie die Übertragung von Spielen durch eine UWP-App verwalten."
title: "Übertragen von Spielen verwalten"
ms.author: drewbat
ms.date: 09/27/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, Spiel, Übertragung"
ms.localizationpriority: medium
ms.openlocfilehash: 613dd69c00257ac5d750bc67b174d7ff010e0b59
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="manage-game-broadcasting"></a>Übertragen von Spielen verwalten
In diesem Artikel wird erläutert, wie Sie die Übertragung von Spielen durch eine UWP-App verwalten. Benutzer müssen die Übertragung von Spielen mithilfe der Systembenutzeroberfläche initiieren, die in Windows integriert ist. Aber ab Version 1709 von Windows 10 können Apps die Übertragungsoberfläche des Systems starten und Benachrichtigungen empfangen, wenn die Übertragung gestartet oder beendet wird.

## <a name="add-the-windows-desktop-extensions-for-the-uwp-to-your-app"></a>Hinzufügen der „Windows Desktop Extensions for the UWP” zu Ihrer App
Die APIs aus dem Namespace **[Windows.Media.AppBroadcasting](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting)** zur Verwaltung der App-Übertragung sind nicht im Universal API-Vertrag enthalten. Für den Zugriff auf die APIs müssen Sie Ihrer App mit den folgenden Schritten einen Verweis auf die „Windows Desktop Extensions for the UWP” hinzufügen.

1. Erweitern Sie im **Projektmappen-Explorer** Ihr UWP-Projekt, klicken Sie mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen** aus. 
2. Erweitern Sie den Knoten **Universal Windows**, und wählen Sie **Erweiterungen** aus.
3. In der Liste der Erweiterungen aktivieren Sie das Kontrollkästchen neben dem Eintrag **Windows Desktop Extensions for the UWP**, der dem Zielbuild für Ihr Projekt entspricht. Die Übertragungsfeatures der App sind ab der Version 1709 verfügbar.
4. Klicken Sie auf **OK**.

## <a name="launch-the-system-ui-to-allow-the-user-to-initiate-broadcasting"></a>Starten Sie die Systembenutzeroberfläche, damit der Benutzer die Übertragung initiieren kann.
Es gibt verschiedene Gründe dafür, dass Ihre App momentan möglicherweise nicht übertragen kann. Beispielsweise könnte das aktuelle Gerät nicht den Hardwareanforderungen für Übertragungen entsprechen, oder eine andere App überträgt gerade Daten. Vor dem Starten der Systembenutzeroberfläche sollten Sie überprüfen, ob Ihre App momentan übertragen kann. Überprüfen Sie zunächst, ob die Übertragungs-APIs auf dem aktuellen Gerät verfügbar sind. Die APIs sind nur auf Geräten verfügbar, auf denen Version 1709 (oder höher) von Windows10 ausgeführt wird. Statt die Version des Betriebssystems zu überprüfen, können Sie die Methode **[ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsApiContractPresent_System_String_System_UInt16_System_UInt16_)** verwenden, um festzustellen, ob Version 1.0 von *Windows.Media.AppBroadcasting.AppBroadcastingContract* vorhanden ist. Wenn dieser Vertrag vorhanden ist, sind die Übertragungs-APIs auf dem Gerät verfügbar.

Als Nächstes rufen eine Instanz der Klasse **[AppBroadcastingUI](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingui)** ab, indem Sie die Factorymethode **[GetDefault](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingui#Windows_Media_AppBroadcasting_AppBroadcastingUI_GetDefault)** auf einem PC aufrufen, auf dem nur ein einzelner Benutzer angemeldet ist. Auf XBox, wo mehrere Benutzer angemeldet sein können, rufen Sie stattdessen **[GetForUser](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingui#Windows_Media_AppBroadcasting_AppBroadcastingUI_GetForUser_Windows_System_User_)** auf. Rufen Sie dann **[GetStatus](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingui#Windows_Media_AppBroadcasting_AppBroadcastingUI_GetStatus)** auf, um den Übertragungsstatus Ihrer App zu ermitteln.

Über die Eigenschaft **[CanStartBroadcast](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingstatus#Windows_Media_AppBroadcasting_AppBroadcastingStatus_CanStartBroadcast)** der Klasse **AppBroadcastingStatus** erfahren Sie, ob die App momentan eine Übertragung starten kann. Wenn sie das nicht kann, überprüfen Sie die Eigenschaft **[Details](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingstatus#Windows_Media_AppBroadcasting_AppBroadcastingStatus_Details)**, um festzustellen, warum keine Übertragung möglich ist. Je nach Ursache sollten Sie dem Benutzer den Status oder Anweisungen zum Aktivieren der Übertragung anzeigen.

[!code-cpp[CanStartBroadcast](./code/AppBroadcast/cpp/AppBroadcastExampleApp/App.cpp#SnippetCanStartBroadcast)]

Veranlassen Sie, dass die Übertragungsbenutzeroberfläche der App vom System angezeigt wird, indem Sie **[ShowBroadcastUI](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingui#Windows_Media_AppBroadcasting_AppBroadcastingUI_ShowBroadcastUI)** aufrufen.

> [!NOTE] 
> Die Methode **ShowBroadcastUI** ist eine Anforderung, die auch fehlschlagen kann. Der Erfolg ist vom aktuellen Zustand des Systems abhängig. Ihre App sollte nicht davon ausgehen, dass die Übertragung nach dem Aufrufen dieser Methode begonnen hat. Verwenden Sie das Ereignis **[IsCurrentAppBroadcastingChanged](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingmonitor#Windows_Media_AppBroadcasting_AppBroadcastingMonitor_IsCurrentAppBroadcastingChanged)**, um benachrichtigt zu werden, ob die Übertragung startet oder beendet wird.

[!code-cpp[LaunchBroadcastUI](./code/AppBroadcast/cpp/AppBroadcastExampleApp/App.cpp#SnippetLaunchBroadcastUI)]

## <a name="receive-notifications-when-broadcasting-starts-and-stops"></a>Empfangen von Benachrichtigungen beim Starten und Beenden von Übertragungen
Um Benachrichtigungen zu erhalten, wenn der Benutzer eine App-Übertragung über die Systembenutzeroberfläche startet oder beendet, initialisieren Sie eine Instanz der Klasse **[AppBroadcastingMonitor](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingmonitor)**, und registrieren Sie einen Handler für das Ereignis **[IsCurrentAppBroadcastingChanged](https://docs.microsoft.com/uwp/api/windows.media.appbroadcasting.appbroadcastingmonitor#Windows_Media_AppBroadcasting_AppBroadcastingMonitor_IsCurrentAppBroadcastingChanged)**. Wie im vorherigen Abschnitt erläutert, müssen Sie zu einem bestimmten Zeitpunkt die Methode **[ApiInformation.IsApiContractPresent](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.apiinformation#Windows_Foundation_Metadata_ApiInformation_IsApiContractPresent_System_String_System_UInt16_System_UInt16_)** verwenden, um sicherzustellen, dass die Übertragungs-APIs auf dem Gerät vorhanden sind, bevor Sie versuchen, diese APIs zu verwenden. 

[!code-cpp[AppBroadcastingRegisterChangedHandler](./code/AppBroadcast/cpp/AppBroadcastExampleApp/App.cpp#SnippetAppBroadcastingRegisterChangedHandler)]

Im Handler für das Ereignis **IsCurrentAppBroadcastingChanged** können Sie die Benutzeroberfläche Ihrer App dem aktuellen Status der Übertragung entsprechend aktualisieren.

[!code-cpp[AppBroadcastingChangedHandler](./code/AppBroadcast/cpp/AppBroadcastExampleApp/App.cpp#SnippetAppBroadcastingChangedHandler)]

## <a name="related-topics"></a>Verwandte Themen

* [Gaming](index.md)

 

 




