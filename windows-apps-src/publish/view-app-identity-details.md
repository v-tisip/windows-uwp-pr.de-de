---
author: jnHs
Description: "Sie können Details zur eindeutigen Identität der App anzeigen, die ihr im Windows Store zugewiesen wurde, und einen Link zum Eintrag Ihrer App im Store abrufen."
title: "Anzeigen von Details zur App-Identität"
ms.assetid: 86F05A79-EFBC-4705-9A71-3A056323AC65
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: d509189ae6392be3d4335732965b70fbc9c77436
ms.sourcegitcommit: fadde8afee46238443ec1cb71846d36c91db9fb9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2017
---
# <a name="view-app-identity-details"></a>Anzeigen von Details zur App-Identität


Bei der Arbeit mit einer App im Windows Dev Center-Dashboard können Sie Details zur eindeutigen Identität der App anzeigen, die ihr im Windows Store zugewiesen wurde. Rufen Sie einen Link zum Eintrag Ihrer App im Store ab.

Um diese Informationen zu suchen, navigieren Sie zu einer Ihrer Apps und erweitern im linken Navigationsmenü **App-Verwaltung**. Wählen Sie **App-Identität** aus, um diese Details anzuzeigen.


## <a name="values-to-include-in-your-app-package-manifest"></a>In das App-Paketmanifest einzuschließende Werte

Die folgenden Werte müssen im appx-Paketmanifest enthalten sein. Wenn Sie Ihre [Pakete mit Microsoft Visual Studio erstellen](../packaging/packaging-uwp-apps.md) und mit demselben Microsoft-Konto angemeldet sind, das Sie mit Ihrem Entwicklerkonto verknüpft haben, werden diese Details automatisch eingefügt. Wenn Sie Ihr Paket manuell erstellen, müssen Sie folgende Details selbst hinzufügen:

-   **Paket/Identität/Name**
-   **Paket/Identität/Herausgeber**
-   **Paket/Eigenschaften/PublisherDisplayName**

Weitere Informationen finden Sie unter [**Identity**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-identity) in der [Paketmanifestschema-Referenz](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/schema-root).

Zusammen werden durch diese Elemente die Identität Ihrer App deklariert und die „Paketfamilie“ gebildet, der alle zugehörigen Pakete angehören. Einzelne Pakete verfügen über zusätzliche Details, z.B. die Architektur und Version.


## <a name="additional-values-for-package-family"></a>Zusätzliche Werte für die Paketfamilie

Die folgenden zusätzlichen Werte beziehen sich auf die Paketfamilie der App, werden aber nicht in Ihr Manifest eingeschlossen.

-   **Paketfamilienname (PFN)**: Dieser Wert wird bei bestimmten Windows-APIs verwendet.
-   **Paket-SID**: Sie benötigen diesen Wert, um WNS-Benachrichtigungen an Ihre App zu senden. Weitere Informationen finden Sie unter [Übersicht über den Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)](../controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview.md).


## <a name="link-to-your-apps-listing"></a>Erstellen eines Links zum Eintrag Ihrer App

Der direkte Link zu Ihrer App-Seite kann geteilt werden, um Kunden das Auffinden der App im Store zu erleichtern. Dieser Link hat das Format **`https://www.microsoft.com/store/apps/<your app's Store ID>`**. Wenn ein Kunde auf diesen Link klickt, wird die webbasierte Eintragsseite für Ihre App geöffnet. Auf Windows-Geräten wird die Store-App auch ebenfalls Ihren App-Eintrag starten und anzeigen.

Die **Store-ID** Ihrer App wird in diesem Abschnitt auch angezeigt. Diese Store-ID kann dazu verwendet werden, [Store-Badges zu generieren](http://go.microsoft.com/fwlink/p/?LinkId=534236) oder Ihre App anderweitig zu identifizieren.

Das **Store-Protokolllink** kann verwendet werden, um Ihre App im Store direkt und ohne einen neuen Browser zu öffnen, als ob Sie es innerhalb der App verknüpfen. Weitere Informationen finden Sie unter [Erstellen eines Links zu Ihrer App](link-to-your-app.md).



 

 




