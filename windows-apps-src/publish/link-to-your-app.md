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
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4057162"
---
# <a name="link-to-your-app"></a>Erstellen eines Links zu Ihrer App


Sie können Kunden Ihre app zu entdecken, indem Sie mit dem Eintrag Ihrer app im Microsoft Store verknüpfen.

## <a name="getting-the-link-to-your-apps-store-listing"></a>Abrufen des Links zum Store-Eintrag Ihrer App

Um die URL für den Store-Eintrag Ihrer App zu erhalten, wechseln Sie zur Seite der App [App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung**. Das URL-Format heißt **`https://www.microsoft.com/store/apps/<your app's Store ID>`**.

Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet. Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.


## <a name="linking-to-your-apps-store-listing-with-the-microsoft-store-badge"></a>Verknüpfen mit Store-Eintrag Ihrer app mit dem Microsoft Store-badge

Sie können direkt mit dem Eintrag Ihrer app mit einem benutzerdefinierten Badge können Kunden wissen, dass Ihre app im Microsoft Store ist verknüpfen.

Zum Erstellen Ihres Badges finden Sie auf der Seite " [Microsoft Store-Badges](http://go.microsoft.com/fwlink/p/?LinkID=534236) ". Sie benötigen die zwölfstellige **Store-ID** Ihrer App, um dieses Formular zum Generieren von Badge und Link verwenden zu können. Die **Store ID** Ihrer App finden Sie auf der Seite [App-Identität](view-app-identity-details.md) unter **App-Verwaltung**.

> [!NOTE]
> Weitere Informationen und Anforderungen in Bezug auf Ihre Verwendung der Microsoft Store-Signals [App-Marketingrichtlinien](app-marketing-guidelines.md) zu.


## <a name="linking-directly-to-your-app-in-the-microsoft-store"></a>Direkt an Ihre app im Microsoft Store verknüpfen

Sie können einen Link, der im Microsoft Store und öffnen einen Browser mit direkt zur Eintragsseite Ihrer app wechselt Erstellen der **ms-Windows-Store:** URI-Schema.

Diese Links sind hilfreich, wenn Sie wissen, dass Benutzer Windows-Geräte verwenden, und möchten, dass sie direkt zur Eintragsseite im Store gelangen. Sie sollten z.B. diesen Link verwenden, nachdem Sie die Zeichenfolge des Benutzer-Agent in einem Browser bestätigt haben, um zu überprüfen, dass das Betriebssystem des Benutzers den Store unterstützt, oder wenn Sie bereits über eine UWP-App kommunizieren.

Um dieses URI-Schema verwenden, um direkt mit Store-Eintrag Ihrer app zu verknüpfen, fügen Sie Ihrer app Store-ID an diesen Link:

`ms-windows-store://pdp/?ProductId=`

Weitere Informationen zur Verwendung der Microsoft Store-Protokolls finden Sie in der [Starten der Microsoft-app](../launch-resume/launch-store-app.md).

 

 




