---
author: jnHs
Description: "Sie können Kunden helfen, Ihre App zu entdecken, indem Sie einen Link zum Store-Eintrag Ihrer App einfügen."
title: Erstellen eines Links zu Ihrer App
ms.assetid: 5420B65C-7ECE-4364-8959-D1683684E146
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Links, Windows Store-Protokoll, mit einer App verknüpfen, App verknüpfen"
ms.openlocfilehash: 2d0750493926937a6326c5f72f568d4294b137c5
ms.sourcegitcommit: fadde8afee46238443ec1cb71846d36c91db9fb9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2017
---
# <a name="link-to-your-app"></a>Erstellen eines Links zu Ihrer App


Sie können Kunden helfen, Ihre App zu entdecken, indem Sie einen Link zum Store-Eintrag Ihrer App einfügen.

## <a name="getting-the-link-to-your-apps-store-listing"></a>Abrufen des Links zum Store-Eintrag Ihrer App

Um die URL für den Store-Eintrag Ihrer App zu erhalten, wechseln Sie zur Seite der App [App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung**. Das URL-Format heißt **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.

Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet. Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.


## <a name="linking-to-your-apps-store-listing-with-the-windows-store-badge"></a>Setzen eines Links zum Store-Eintrag Ihrer App mit dem Windows Store-Badge

Sie können mit einem benutzerdefinierten Badge einen direkten Link zum Eintrag Ihrer App erstellen, um Kunden darüber zu informieren, dass Ihre App im Windows Store vorhanden ist.

Besuchen Sie zum Erstellen Ihres Badges die Seite [WindowsStore-Badges](http://go.microsoft.com/fwlink/p/?LinkID=534236). Sie benötigen die zwölfstellige **Store-ID** Ihrer App, um dieses Formular zum Generieren von Badge und Link verwenden zu können. Die **Store ID** Ihrer App finden Sie auf der Seite [App-Identität](view-app-identity-details.md) unter **App-Verwaltung**.

> [!NOTE]
> Weitere Informationen und Anforderungen in Bezug auf Ihre Verwendung der Windows Store-Signals finden Sie unter [Marketingrichtlinien für Apps](app-marketing-guidelines.md).


## <a name="linking-directly-to-your-app-in-the-windows-store"></a>Erstellen direkter Links zum Windows Store

Sie können unter Verwendung des **ms-windows-store:**-URI-Schemas einen Link erstellen, der den Windows Store öffnet und direkt zur Eintragsseite Ihrer App wechselt.

Diese Links sind hilfreich, wenn Sie wissen, dass Benutzer Windows-Geräte verwenden, und möchten, dass sie direkt zur Eintragsseite im Store gelangen. Sie sollten z.B. diesen Link verwenden, nachdem Sie die Zeichenfolge des Benutzer-Agent in einem Browser bestätigt haben, um zu überprüfen, dass das Betriebssystem des Benutzers den Store unterstützt, oder wenn Sie bereits über eine UWP-App kommunizieren.

Um das Windows Store-Protokoll für einen direkten Link mit dem Store-Eintrag Ihrer App zu verwenden, fügen Sie diesem Link die Store-ID der App hinzu:

`ms-windows-store://pdp/?ProductId=`

Weitere Informationen zur Verwendung des Windows Store-Protokolls finden Sie unter [Starten der Windows Store-App](../launch-resume/launch-store-app.md).

 

 




