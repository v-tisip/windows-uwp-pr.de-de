---
author: mcleanbyron
ms.assetid: 2fba38c4-11be-4058-bfa3-5f979390791c
description: Hier erfahren Sie, wie Sie mit den Ereignissen der AdControl-Klasse umgehen.
title: AdControl-Ereignisse in C#
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Anzeigen, Werbung, AdControl, Ereignisse"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: cf285ebb4207b9a9a215bfb4a739b0bc6a2d934b
ms.lasthandoff: 02/07/2017

---

# <a name="adcontrol-events-in-c"></a>AdControl-Ereignisse in C\# #  


Die folgenden Beispiele veranschaulichen die grundlegenden Ereignishandler für die folgenden [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Ereignisse: [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.erroroccurred.aspx), [AdRefreshed](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.adrefreshed.aspx) und [IsEngagedChanged](https://msdn.microsoft.com/library/windows/apps/xaml/microsoft.advertising.winrt.ui.adcontrol.isengagedchanged.aspx). In diesen Beispielen wird davon ausgegangen, dass Sie die Ereignishandler bereits Ereignissen in Ihrem XAML-Code zugewiesen haben. Weitere Informationen hierzu finden Sie unter [Beispiel für XAML-Eigenschaften](xaml-properties-example.md).

Weitere Informationen zum Behandeln von Ereignissen in C# finden Sie unter [Übersicht über Ereignisse und Routingereignisse (Universelle Windows-Apps mit C#/VB/C++ und XAML)](http://msdn.microsoft.com/library/windows/apps/hh758286).

## <a name="examples"></a>Beispiele

> [!div class="tabbedCodeSnippets"]
[!code-cs[AdControl](./code/AdvertisingSamples/AdControlSamples/cs/MainPage.xaml.cs#EventHandlers)]

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)
* [AdControl-Fehlerbehandlung](adcontrol-error-handling.md)
* [RoutedEventArgs-Klasse](http://msdn.microsoft.com/library/system.windows.routedeventargs.aspx)

 

 

