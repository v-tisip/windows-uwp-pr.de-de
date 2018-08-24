---
author: jnHs
Description: You can help customers discover your app by linking to your app's listing in the Microsoft Store.
title: Erstellen eines Links zu Ihrer App
ms.assetid: 5420B65C-7ECE-4364-8959-D1683684E146
ms.author: wdg-dev-content
ms.date: 10/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Links, Windows Store-Protokoll, mit einer App verknüpfen, App verknüpfen
ms.localizationpriority: medium
ms.openlocfilehash: 0025321aa73a66cc0a976bd347e613de3c3c4765
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2836504"
---
# <a name="link-to-your-app"></a>Erstellen eines Links zu Ihrer App


Sie können Kunden Ihre app zu ermitteln, indem Sie zu Ihrer app Angebot in Microsoft Store verknüpfen.

## <a name="getting-the-link-to-your-apps-store-listing"></a>Abrufen des Links zum Store-Eintrag Ihrer App

Um die URL für den Store-Eintrag Ihrer App zu erhalten, wechseln Sie zur Seite der App [App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung**. Das URL-Format heißt **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.

Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet. Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.


## <a name="linking-to-your-apps-store-listing-with-the-microsoft-store-badge"></a>Verknüpfen mit Ihrer app Store-Eintrags mit der Microsoft Store-Logo

Sie können Sie eine direkte Verknüpfung Ihrer app-Angebot mit einer benutzerdefinierten Logo können Kunden wissen, dass Ihre app im Store Microsoft ist.

Wenn Ihr Logo erstellen möchten, finden Sie auf der Seite [Microsoft Store Badges](http://go.microsoft.com/fwlink/p/?LinkID=534236) . Sie benötigen die zwölfstellige **Store-ID** Ihrer App, um dieses Formular zum Generieren von Badge und Link verwenden zu können. Die **Store ID** Ihrer App finden Sie auf der Seite [App-Identität](view-app-identity-details.md) unter **App-Verwaltung**.

> [!NOTE]
> Info und Anforderungen in Bezug auf Ihre Verwendung des das Logo Microsoft Store finden Sie unter [App-marketing-Richtlinien](app-marketing-guidelines.md) .


## <a name="linking-directly-to-your-app-in-the-microsoft-store"></a>Direkte Verknüpfung mit Ihrer app im Microsoft-Speicher

Sie können einen Link, startet Microsoft Store und nehmen direkt an Ihre app-Angebotsseite ohne Öffnen eines Browsers mit, Erstellen der **ms-Windows-Store:** URI-Schema.

Diese Links sind hilfreich, wenn Sie wissen, dass Benutzer Windows-Geräte verwenden, und möchten, dass sie direkt zur Eintragsseite im Store gelangen. Sie sollten z.B. diesen Link verwenden, nachdem Sie die Zeichenfolge des Benutzer-Agent in einem Browser bestätigt haben, um zu überprüfen, dass das Betriebssystem des Benutzers den Store unterstützt, oder wenn Sie bereits über eine UWP-App kommunizieren.

Um diese URI-Schema verwenden, um direkt mit Ihrer app-Shop zu verknüpfen, fügen Sie Ihrer app-ID anmelden zu diesem Link:

`ms-windows-store://pdp/?ProductId=`

Weitere Informationen zur Verwendung des Microsoft Store-Protokolls finden Sie unter [Starten Sie die Microsoft-Anwendung](../launch-resume/launch-store-app.md).

 

 




