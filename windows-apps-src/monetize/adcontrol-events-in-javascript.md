---
author: mcleanbyron
ms.assetid: 2383296e-c3d7-4b49-bcd2-621391228fdb
description: Hier erfahren Sie, wie Sie mit den Ereignissen der AdControl-Klasse umgehen.
title: AdControl-Ereignisse in JavaScript
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, JavaScript
ms.openlocfilehash: 62363ebce006f8ad21645d907c3e63360472887d
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="adcontrol-events-in-javascript"></a>AdControl-Ereignisse in JavaScript

Die folgenden Beispiele veranschaulichen die grundlegenden Ereignishandler für die folgenden [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Ereignisse: [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.erroroccurred.aspx), [AdRefreshed](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.adrefreshed.aspx) und [IsEngagedChanged](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.isengagedchanged.aspx). In diesen Beispielen wird davon ausgegangen, dass Sie die Ereignishandler bereits Ereignissen in Ihrem HTML-Markup zugewiesen haben. Weitere Informationen hierzu finden Sie unter [Beispiel für HTML-Eigenschaften](html-properties-example.md).

In JavaScript müssen die **AdControl**-Ereignisse von der [MarkSupportedForProcessing](http://msdn.microsoft.com/library/windows/apps/Hh967819.aspx)-Funktion eingeschlossen werden. Weitere Informationen zum Behandeln von Ereignissen in JavaScript finden Sie unter [Codieren einfacher Apps (HTML)](https://msdn.microsoft.com/library/windows/apps/hh780660.aspx#adding-event-handlers).

## <a name="examples"></a>Beispiele

> [!div class="tabbedCodeSnippets"]
[!code-javascript[AdControl](./code/AdvertisingSamples/AdControlSamples/js/main.js#EventHandlers)]

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)
* [AdControl-Fehlerbehandlung](adcontrol-error-handling.md)
* [RoutedEventArgs-Klasse](http://msdn.microsoft.com/library/system.windows.routedeventargs.aspx)

 

 
