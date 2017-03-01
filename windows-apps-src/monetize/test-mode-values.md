---
author: mcleanbyron
ms.assetid: 2ed21281-f996-402d-a968-d1320a4691df
description: "Verwenden Sie die für Tests vorgesehene Anwendungs-ID und die Anzeigeneinheits-ID aus diesem Artikel, um zu prüfen, wie Ihre App die Werbung während der Testphase rendert."
title: Testmoduswerte
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Anzeigen, Werbung, Tests
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 89818e91ff1c1b8fee2ca82951742ed7e55a2a5a
ms.lasthandoff: 02/07/2017

---

# <a name="test-mode-values"></a>Testmoduswerte

Wenn Sie [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) oder [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) zum Anzeigen von Werbung in Ihrer App verwenden, müssen Sie eine Anwendungs-ID und eine Anzeigeneinheits-ID angeben. Während Sie Ihre App entwickeln, verwenden Sie die entsprechende Testanwendungs-ID und Anzeigenblock-ID, um zu beobachten, wie die Werbung während der Testphase von Ihrer App gerendert wird.


Wenn Sie Testwerte in einer veröffentlichten App verwenden, wird die App keine Livewerbung empfangen. Um Werbung in Ihrer veröffentlichten App zu empfangen, müssen Sie in Ihrem Code die Anwendungs-ID und die Anzeigeneinheits-ID verwenden, die im Windows Dev Center-Dashboard bereitgestellt wird. Weitere Informationen finden Sie unter [Einrichten von Anzeigeneinheiten in Ihrer App](set-up-ad-units-in-your-app.md).
 
Verwenden Sie die folgende Testwerte für interstitielles Video und Banneranzeigen.

* Für interstitielle Videoanzeigen:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">AdUnitId</th>
    <th align="left">AppId</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>11389925</p></td>
    <td align="left"><p>d25517cb-12d4-4699-8bdc-52040c712cab</p></td>
    </tr>
    </tbody>
    </table>

     
* Für Banneranzeigen:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">AdUnitId</th>
    <th align="left">AppId</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>10865270</p></td>
    <td align="left"><p>3f83fe91-d6be-434d-a0ae-7351c5a997f1</p></td>
    </tr>
    </tbody>
    </table>


> **Wichtig**&nbsp;&nbsp;Die Größe einer Liveanzeige wird durch die Eigenschaften **Width** und **Height** von **AdControl** bestimmt. Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass die Eigenschaften **Width** und **Height** zu den [unterstützten Eigenschaften für Banneranzeigen](supported-ad-sizes-for-banner-ads.md) gehören. Die Eigenschaften **Width** und **Height** ändern sich nicht entsprechend der Größe einer Liveanzeige.



 

 

