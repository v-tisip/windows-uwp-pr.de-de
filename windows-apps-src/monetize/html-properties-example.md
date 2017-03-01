---
author: mcleanbyron
ms.assetid: 5fa16a27-fdc0-43b2-84cd-8547fd4915de
description: Erfahren Sie, wie **AdControl**-Eigenschaften in HTML zugewiesen werden.
title: "Beispiel für AdControl-Eigenschaften in HTML"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Anzeigen, Werbung, AdControl, HTML, Eigenschaften"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: a879944dc14ca161c3e52a49ffe4a8cebfa7d69f
ms.lasthandoff: 02/07/2017

---

# <a name="adcontrol-html-properties-example"></a>Beispiel für AdControl-Eigenschaften in HTML

Das folgende Beispiel zeigt, wie Sie [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Eigenschaften in HTML zuweisen. **ApplicationId** und **AdUnitId** sind erforderliche Eigenschaften. Die anderen Eigenschaften und Ereignisse sind optional. Wenn Sie keine Werte für optionale Eigenschaften angeben, verwendet das Steuerelement Standardwerte, die eine Anzeige erstellen, die mit der Benutzeroberfläche der App konsistent ist.

Die letzten fünf Zeilen sind ein Beispiel für die Registrierung von Funktionen für **AdControl**-Ereignisse. Sie können nur Funktionen registrieren, die Sie in Ihrem JavaScript-Code definiert haben.

Diese Werte dienen als Beispiele. In Ihrem Code legen Sie die Werte dieser Funktionen und Eigenschaften entsprechend Ihrer App fest.

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
    data-win-control="MicrosoftNSJS.Advertising.AdControl"
    data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1',
                       adUnitId: '10865270',
                       isAutoRefreshEnabled: false,
                       onAdRefreshed: myAdRefreshed,
                       onErrorOccurred: myAdError,
                       onEngagedChanged: myAdEngagedChanged,
                       onPointerDown: myPointerDown,
                       onPointerUp: myPointerUp }" />
```

## <a name="related-topics"></a>Verwandte Themen

* [„AdControl“ in HTML 5 und JavaScript](adcontrol-in-html-5-and-javascript.md)
* [Anzeigenbeispiele auf GitHub](http://aka.ms/githubads)

 

