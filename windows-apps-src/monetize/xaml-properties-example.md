---
author: mcleanbyron
ms.assetid: d074e9d5-b3e0-4f16-b1e4-02b32ac99b2c
description: Erfahren Sie, wie Werten **AdControl**-Eigenschaften zugewiesen werden.
title: "Beispiel für AdControl-XAML-Eigenschaften"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, Uwp, Werbung, Advertising, AdControl, XAML, Eigenschaften"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: dbcc08b1373c7f73d5b9ebf541ec82bb01fd9df3
ms.lasthandoff: 02/07/2017

---

# <a name="adcontrol-xaml-properties-example"></a>Beispiel für AdControl-XAML-Eigenschaften

Im folgenden XAML-Beispiel wird veranschaulicht, wie Werten [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Eigenschaften zugewiesen werden. Wenn eine Eigenschaft nicht festgelegt ist, verwendet **AdControl** Standardwerte, um eine Anzeige zu erstellen, die mit der Benutzeroberfläche der App konsistent ist.

Die Werte dienen als Beispiele. In Ihrem Code legen Sie die Werte dieser Funktionen und Eigenschaften entsprechend für Ihre App fest.

> [!div class="tabbedCodeSnippets"]
``` xml
<UI:AdControl Width="300",
    Height="250",
    AdUnitId="10865270",
    ApplicationId="3f83fe91-d6be-434d-a0ae-7351c5a997f1",
    IsAutoRefreshEnabled="false",
    AdRefreshed="OnAdRefresh",
    ErrorOcurred="OnAdError",
    IsEngagedChanged="OnAdEngagedChanged" />
```

## <a name="related-topics"></a>Verwandte Themen

* [„AdControl“ in XAML und .NET](adcontrol-in-xaml-and--net.md)
* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)

 

