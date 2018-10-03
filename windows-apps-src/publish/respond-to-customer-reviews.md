---
author: jnHs
Description: You can respond directly to reviews of your app to let customers know you’re listening to their feedback.
title: Reagieren auf Kundenrezensionen
ms.assetid: 96AA2108-E793-4DD0-8CDA-0D115423C68D
ms.author: wdg-dev-content
ms.date: 7/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Überprüfen Sie Windows 10, Uwp, reagiert, Antworten
ms.localizationpriority: medium
ms.openlocfilehash: 2a043a0b721ee6eabdc3520960ae6da253587c33
ms.sourcegitcommit: 1938851dc132c60348f9722daf994b86f2ead09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4268207"
---
# <a name="respond-to-customer-reviews"></a>Reagieren auf Kundenrezensionen


Sie können auf Rezensionen Ihrer App zu ermöglichen, dass Kunden wissen, dass Sie ihr Feedback ernst reagieren. Wenn Sie auf Kritiken antworten, können Sie Kunden über neue Features oder behobene Schwachstellen informieren, die in Bezug zu ihren Kommentaren stehen, oder Sie erhalten detaillierteres Feedback mit Verbesserungsvorschlägen für Ihre App. Ihre Antworten werden im Microsoft Store für alle Windows 10-Kunden angezeigt. Sie können auch auswählen, um Ihre Antwort per e-Mail an dem Kunden zu senden, (Wenn sie noch nicht zugelassen und ein Gerät mit Windows 10, Version 1803 oder höher).

Um die Rezensionen zu Ihrer App anzuzeigen und Antworten bereitzustellen, suchen Sie die App im Windows Dev Center-Dashboard. Erweitern Sie im linken Navigationsmenü **Analysen** und klicken Sie dann auf **Rezensionen**, um den [Bericht „Rezensionen“](reviews-report.md) anzuzeigen. Wählen Sie aus, um Ihre Antwort bereitzustellen, **reagieren, um zu überprüfen** .

> [!TIP]
> Zusätzlich zur Verwendung des Dashboards zum Reagieren auf Rezensionen, können Sie auf Rezensionen [programmgesteuert](../monetize/submit-responses-to-app-reviews.md)oder über die [Dev Center-app](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws)reagieren.

Standardmäßig wird Ihre Antwort im Store direkt unterhalb der ursprünglichen kundenrezension verbucht. Diese Antworten werden allen Kunden, die den Store auf einem Windows 10-Gerät anzeigen. Wenn der Kunde, der der Rezension verwendet ein Gerät mit Windows 10, Version 1803 oder höher, und sie noch nicht den Empfang von Antworten e-Mail entschieden, wird eine Kopie der Ihre Antwort auch an die Kunden per e-Mail gesendet.  Sie müssen eine gültige e-Mail-Adresse angeben, um Ihre Antwort übermitteln, die wir in der e-Mail an den Kunden enthält. Sie können dann diese e-Mail-Adresse, Sie direkt kontaktieren.

Wenn Sie nicht möchten, dass Ihre Antwort im Store angezeigt, und stattdessen nur per e-Mail an den Kunden antworten möchten, deaktivieren Sie das **Diese Antwort veröffentlichen** . Beachten Sie, dass es nicht möglich ist, Deaktivieren dieses Kontrollkästchen, wenn der Kunde den Empfang von Antworten e-Mail entschieden hat bzw. Wenn sie ein Gerät verwenden, die nicht Windows 10, Version 1803 oder höher ausgeführt wird.

## <a name="guidelines-for-responses"></a>Richtlinien für Antworten

Beim Beantworten von Kundenrezensionen müssen folgende Richtlinien beachtet werden. Dies gilt für alle Antworten, ob sie öffentlich oder nicht befinden.

> [!IMPORTANT]
> Nicht möglich, ändern die Antworten, die Sie an den Store postet, (es sei denn, der Kunde überarbeitet seine ursprüngliche Rezension), daher sollten Sie Ihre Antwort sorgfältig überprüfen. Wenn ein Kunde seine ursprüngliche Rezension überarbeitet, wird Ihre Antwort von der app Store-Eintragsseite entfernt werden. Sie haben dann die Möglichkeit, eine neue Antwort zur überarbeiteten Rezension zu senden, indem Sie auswählen, **Aktualisieren Sie Ihre Antwort**.

-   Antworten dürfen maximal 1.000Zeichen umfassen.
-   Sie dürfen Benutzern keine Gegenleistungen, einschließlich digitaler Apps, anbieten, um sie zum Ändern ihrer App-Bewertung zu animieren. Wie Sie bereits wissen, dürfen Sie gemäß der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) keine Bewertungen manipulieren.
-   Ihre Antwort sollte keine Marketing- oder Werbeinhalte enthalten. Derjenige, der die Rezension verfasst hat, ist bereits Ihr Kunde.
-   Bewerben Sie in Ihrer Antwort keine anderen Apps oder Dienste.
-   Ihre Antwort muss sich direkt auf die jeweilige App und die damit verbundene Rezension beziehen. Dieselbe Antwort darf nicht an einen großen Kreis von Benutzern gesendet werden, wenn sich die enthaltene Antwort nicht auf dieselbe Frage bezieht.
-   Ihre Antwort sollte keine profanen, aggressiven, persönlichen oder bösartigen Inhalte enthalten. Bleiben Sie stets höflich und denken Sie daran, dass zufriedene Kunden die wahrscheinlich beste Werbung für Ihre App sind.

> [!NOTE]
> Kunden können eine unangemessene Antwort, mit der ein Entwickler auf eine Rezension reagiert, an Microsoft melden. Sie können auch den Empfang von Antworten per e-Mail ablehnen.
>
> Microsoft behält sich das Recht vor, die Genehmigung für einen Entwickler zum Senden von Antworten aus jeglichem Grund zu widerrufen, beispielsweise, wenn auf Ihre Rezensionsantworten übermäßig viele unangemessene Antworten gemeldet werden oder ungewöhnlich viele Kunden den Empfang von Antworten auf ihre Rezensionen abwählen.

Sie alleine sind für die Kommunikation mit Ihren Kunden verantwortlich. Microsoft beteiligt sich nicht an Meinungsverschiedenheiten zwischen Entwicklern und Kunden. Jedoch, wenn eine Rezension Ihrer App anstößige, profane oder beleidigende Sprache enthält, öffnen Sie eine [Supportanfrage](http://go.microsoft.com/fwlink/p/?LinkID=401178).


## <a name="use-customer-reviews-to-improve-your-app"></a>Kundenrezensionen als Verbesserungschance für Ihre App

Ihren Kunden zuzuhören und auf sie einzugehen, ist erst der Anfang. Entscheidend ist es, das Feedback praktisch umzusetzen. Wenn Sie an Ihrer App erhebliche Verbesserungen vornehmen, sollten Sie diese unbedingt im Store veröffentlichen, indem Sie eine [neue Einreichung erstellen](app-submissions.md), um Ihre App zu aktualisieren.
