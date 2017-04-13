---
author: mcleanbyron
ms.assetid: 48a1ef86-8514-4af8-9c93-81e869d36de7
description: Hier erfahren Sie, wie Sie programmgesteuert ein **AdControl** (Anzeigensteuerelement) mit JavaScript erstellen.
title: Erstellen eines AdControl-Elements in JavaScript
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, JavaScript
ms.openlocfilehash: b669925c3b630ddbfe82086231c46c951072244b
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="create-an-adcontrol-in-javascript"></a>Erstellen eines AdControl-Elements in JavaScript




Die Beispiele in diesem Artikel zeigen, wie Sie programmgesteuert ein [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Element mit JavaScript erstellen. In diesem Artikel wird davon ausgegangen, dass Sie die erforderlichen Verweise auf das Projekt zur Verwendung eines **AdControl**-Elements bereits hinzugefügt haben. Weitere Informationen, einschließlich einer ausführlichen exemplarischem Vorgehensweise zum Erstellen und Initialisieren eines **AdControl**-Elements im HTML-Markup anstelle von JavaScript, finden Sie unter [„AdControl“ in HTML5 und Javascript](adcontrol-in-html-5-and-javascript.md).

## <a name="html-div-for-an-adcontrol"></a>HTML-div-Element für „AdControl“

**AdControl** benötigt ein **div**-Element auf der HTML-Seite, auf der die Werbung angezeigt wird. Der folgende Code ist ein Beispiel für so ein **div**-Element.

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 50px; left: 0px; width: 300px; height: 250px; z-index: 1"
    data-win-control="MicrosoftNSJS.Advertising.AdControl">
</div>
```

## <a name="javascript-for-creating-an-adcontrol"></a>JavaScript zum Erstellen eines AdControl

Im folgenden Beispiel wird davon ausgegangen, dass Sie in Ihrem HTML-Code ein vorhandenes **div**-Element mit der ID **MyAd** verwenden.

Instanziieren Sie **AdControl** in der **app.onactivated**-Funktion.

> [!div class="tabbedCodeSnippets"]
[!code-javascript[AdControl](./code/AdvertisingSamples/AdControlSamples/js/main.js#DeclareAdControl)]

In diesem Beispiel wird davon ausgegangen, dass Sie die Ereignishandlermethoden **myAdError**, **myAdRefreshed** und **myAdEngagedChanged** bereits deklariert haben.

>**Hinweis**&nbsp;&nbsp;Die in diesem Beispiel angezeigten Werte *applicationId* und *adUnitId* sind [Testmoduswerte](test-mode-values.md). Sie müssen [diese Werte mit Livewerten aus Windows Dev Center ersetzen](set-up-ad-units-in-your-app.md), bevor Sie Ihre App für die Übermittlung einreichen.

Wenn Sie diesen Code verwenden und keine Anzeigen angezeigt werden, können Sie versuchen, ein **position:relativ**-Attribut im **div**-Element einzufügen, das das **AdControl** enthält. Dadurch wird die Standardeinstellung von **IFrame** überschrieben. Anzeigen werden ordnungsgemäß angezeigt, sofern sie nicht aufgrund des Werts dieses Attributs nicht angezeigt werden. Beachten Sie, dass neue Anzeigeeinheiten unter Umständen bis zu 30 Minuten nicht verfügbar sind.

## <a name="related-topics"></a>Verwandte Themen

* [Anzeigenbeispiele bei GitHub](http://aka.ms/githubads)

 

 
