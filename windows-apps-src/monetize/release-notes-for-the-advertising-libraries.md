---
author: mcleanbyron
ms.assetid: ca92bed1-ad9e-4947-ad91-87d12de727c0
description: "Überprüfen Sie die Versionshinweise für die Microsoft Advertising-Bibliotheken im Microsoft Store Services SDK."
title: "Versionshinweise für die Advertising-Bibliotheken"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, Versionshinweise
ms.openlocfilehash: f3d07df6e64c96e9070cb82bd7ac6e96b9cad1ee
ms.sourcegitcommit: d053f28b127e39bf2aee616aa52bb5612194dc53
translationtype: HT
---
# <a name="release-notes-for-the-advertising-libraries"></a>Versionshinweise für die Advertising-Bibliotheken




Dieser Abschnitt enthält Versionshinweise für die aktuelle Version der Microsoft Advertising-Bibliotheken im Microsoft Store-Services-SDK (für UWP-Apps) und im Microsoft Advertising-SDK für Windows und Windows Phone8.x (für Windows8.1- und Windows Phone8.x-Apps). Diese Bibliotheken unterstützt XAML- und JavaScript/HTML-Apps für Windows 10, Windows 8.1, Windows Phone 8.1 und Windows Phone 8.

## <a name="installation"></a>Installation


Die Microsoft Advertising-Bibliotheken stehen als Teil der [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) (für UWP-Apps) und die [Microsoft Advertising SDK für Windows und Windows Phone8.x](http://aka.ms/store-8-sdk) (für Windows8.1 und Windows Phone8.x-Apps) zur Verfügung. Weitere Informationen zum Installieren des SDKs und der darin enthaltenen Bibliotheken finden Sie unter [Installieren der Microsoft Advertising-Bibliotheken](install-the-microsoft-advertising-libraries.md).

Um die Microsoft Advertising-Assemblys für Windows Phone 8.x Silverlight-Projekte abzurufen, installieren Sie den [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk), öffnen das Projekt in Visual Studio und wechseln dann zu **Projekt** > **Verbundenen Dienst hinzufügen** > **Ad Mediator**. Die Assemblys werden anschließend automatisch geladen. Im Anschluss daran können Sie die Ad Mediator-Referenzen aus Ihrem Projekt entfernen, wenn Sie Ad Mediator nicht verwenden möchten. Weitere Informationen finden Sie unter [AdControl in Windows Phone Silverlight](adcontrol-in-windows-phone-silverlight.md).


## <a name="uninstall-previous-versions"></a>Deinstallieren früherer Versionen

Vor der Installation der Microsoft Store-Services-SDK (für UWP-Apps) oder der Microsoft Advertising SDK für Windows und Windows Phone8.x (für Windows8.1 und Windows Phone8.x-Apps) wird dringend empfohlen, alle vorherigen Instanzen der Microsoft Universal Ad Client SDK oder der Microsoft Advertising SDK zu deinstallieren.

## <a name="target-architecture-specific-build-outputs"></a>Zielarchitekturspezifische Buildausgabe

Wenn Sie die Microsoft Advertising-Bibliotheken verwenden, können Sie in Ihrem Projekt nicht das Ziel **Any CPU** angeben. Sollte in Ihrem Projekt die Zielplattform **Any CPU** definiert sein, wird in Ihrem Projekt eine Warnung ausgegeben, sobald Sie einen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen. Um diese Warnung zu entfernen, müssen Sie eine architekturspezifische Buildausgabe verwenden (beispielsweise **x86**) und das Projekt entsprechend aktualisieren. Weitere Informationen finden Sie unter [Bekannte Probleme](known-issues-for-the-advertising-libraries.md).

## <a name="c-support"></a>C++-Unterstützung

Die Microsoft Advertising-Bibliotheken (in den die Klassen **AdControl** und **InterstitialAd** enthalten sind) unterstützen in C++ geschriebene Apps sowie DirectX mit Windows-Runtime-Interoperabilität (*interop*). Weitere Informationen und Beispiele zum Programmieren mit XAML und C++ finden Sie unter [Typsystem](https://msdn.microsoft.com/library/windows/apps/xaml/hh755822.aspx).

## <a name="no-toolbox-control"></a>Kein Toolbox-Steuerelement

In der aktuellen Version der Microsoft Advertising-Bibliotheken in der Microsoft Store-Services SDK oder der Microsoft Advertising SDK für Windows und Windows Phone8.x gibt es kein Toolbox-Steuerelement zum Ziehen einer **AdControl** oder **InterstitialAd** auf eine Entwurfsoberfläche in Ihrer App. Informationen zum Hinzufügen dieser Steuerelemente in Ihrem Markup und Code finden Sie in der [Exemplarische Vorgehensweisen für Entwickler](developer-walkthroughs.md).

## <a name="latitude-and-longitude-properties-no-longer-available"></a>Eigenschaften Latitude und Longitude nicht mehr verfügbar

Die **AdControl**-Klasse verfügt nicht mehr über die Eigenschaften **Latitude** und **Longitude** für UWP-Apps. Stattdessen erkennt der Code im Anzeigensteuerelement diese Werte und sendet sie für die App an die Anzeigenserver.


 

 
