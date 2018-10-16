---
author: jnHs
Description: The Windows Dev Center dashboard gives you the option to make your app available only to specified people so that you can have testers try it out before you offer it to the public.
title: Betatests und zielgerichtete Verteilung
ms.assetid: 38E4ED22-D6C1-40D8-9B16-6B3E51BD962E
ms.author: wdg-dev-content
ms.date: 05/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Betatests, eingeschränkter Vertrieb, Beta, Betas, testen, Tester
ms.localizationpriority: medium
ms.openlocfilehash: e453be22d752ed78263cb34011cdf9a333057e03
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4621058"
---
# <a name="beta-testing-and-targeted-distribution"></a>Betatests und zielgerichtete Verteilung

Wie sorgfältig Sie Ihre App auch testen: Es geht nichts über einen Praxistest, bei dem die App von anderen Benutzern verwendet wird. Die Betatester finden möglicherweise Probleme, die Sie übersehen haben, wie z. B. Rechtschreibfehler, unübersichtliche Benutzerführungen der App und sogar Fehler, die dazu führen können, dass die App abstürzt. Sie haben dann die Möglichkeit, diese Probleme zu beheben, bevor Sie die Übermittlung für die Allgemeinheit verfügbar machen. So erhalten Sie ein hochwertigeres Endprodukt. 

Das Windows Dev Center-Dashboard bietet Ihnen mehrere Optionen, eine App-Übermittlung nur für bestimmte Personen bereitzustellen. Auf diese Weise können Tester die App ausprobieren, bevor Sie sie für die Öffentlichkeit anbieten. 

Unabhängig von der gewählten Methode, müssen Sie einige Dinge in puncto Betatests für Ihrer App berücksichtigen.

- Sie können den Zugriff auf die App nicht widerrufen, nachdem sie von einem Tester heruntergeladen wurde. Nachdem sie die App heruntergeladen haben, können sie diese weiterhin verwenden, und sie erhalten sämtliche Updates, die Sie anschließend veröffentlichen.
- Sie müssen festlegen, auf welche Weise Sie Feedback von Ihren Testern einholen möchten. Denken Sie daran, ein Link in die Beta-App einzufügen, damit Ihre Tester Ihnen einfach Feedback per E-Mail senden können (oder über den [Feedback-Hub](../monetize/launch-feedback-hub-from-your-app.md), wenn Vertraulichkeit kein Problem ist). 
- Sie können [Analyseberichte](analytics.md) für Ihre App überprüfen, einschließlich der Nutzungs- und Integritätsberichte von Ihren Testern abgegebenen Bewertungen und Kommentare.
- Sie können Add-Ons einbinden, wenn Sie Ihre App an Tester verteilen. Da Sie wahrscheinlich kein Geld für ein Add-On erheben möchten, können Sie durch das [Generieren von Werbecodes](generate-promotional-codes.md) und das Verteilen an Ihre Tester das Add-On kostenlos vertreiben. Sie können ebenfalls festlegen, dass der Preis für das Add-On während der Testphase **Kostenlos** ist (bevor Sie die App anderen Kunden zur Verfügung stellen, erstellen Sie die Übermittlung für das Add-On erneut, um den Preis zu ändern). Beachten Sie, dass jedes Add-On nur einmal pro Microsoft-Konto erworben werden kann, damit der gleiche Tester den Add-On-Kauf nicht mehr als einmal testen kann. 
- Sie können Ihren Testern jederzeit eine aktualisierte Version Ihrer App bereitstellen, indem Sie eine neue Übermittlung mit neuen Paketen erstellen. Ihre Tester erhalten das Update, nachdem es den Zertifizierungsprozess durchlaufen hat, auf die gleiche Art und Weise, wie sie das ursprüngliche Paket erhalten haben. Anderer Benutzer können darauf nicht zugreifen (es sei denn, Sie nehmen zusätzliche Änderungen daran vor wie z.B. wenn Sie die App von einer **Privaten Zielgruppe** auf eine **Öffentliche Zielgruppe** ändern oder die Mitgliedschaft der Gruppen ändern, die diese abrufen können).

## <a name="private-audience"></a>Private Zielgruppe

Wenn Tester Ihre App verwenden sollen, bevor diese für andere Benutzer verfügbar ist, und sicher stellen wollen, dass niemand sie sehen kann, verwenden Sie die Option **private Zielgruppe** unter der Option [Sichtbarkeit](choose-visibility-options.md) (auf der Seite **Preise und Verfügbarkeit** der Übermittlung). Dies ist die einzige Methode, mit der Sie Ihre App an Tester verteilen können und verhindert wird, dass andere Personen den App Store-Eintrag sehen können, auch wenn sie den direkten Link eingeben. 

Der **privaten** zielgruppenoptionen kann nur verwendet werden können, das Wenn Sie nicht bereits Ihre app für eine öffentliche Zielgruppe veröffentlicht haben ist. Sie können diese Option verwenden, mit apps für jede Betriebssystemversion, aber Ihre Tester müssen Windows 10, Version 1607 oder höher (einschließlich Xbox One), ausgeführt werden und müssen mit dem Microsoft-Konto zugeordnete e-Mail-Adresse, die Sie bereitstellen angemeldet sein.

Weitere Informationen finden Sie unter [Private Zielgruppe](choose-visibility-options.md#audience).


## <a name="package-flights"></a>Flight-Pakete

Falls Sie bereits Ihre App veröffentlicht haben, können Sie Flight-Pakete erstellen, um den gewünschten Benutzern einen anderen Satz von Paketen bereitzustellen. Sie können ebenfalls für die gleiche App mehrere Flight-Pakete erstellen und jeweils für unterschiedliche Benutzergruppen verwenden. So können Sie komfortabel mehrere Pakete parallel testen und Pakete aus einem Flight in die Übermittlung ohne Test-Flight überführen, falls Sie zu dem Schluss kommen, dass die Pakete für die allgemeine Bereitstellung bereit sind.

Flight-Pakete können mit Apps für jede Betriebssystemversion verwendet werden, Ihre Tester können allerdings die App nur dann abrufen, wenn sie Windows.Desktop Build 10586 oder höher, Windows.Mobile Build 10586.63 oder höher oder Xbox One ausführen.

Weitere Informationen finden Sie unter [Flight-Pakete](package-flights.md).


<span id="hide" />

## <a name="hiding-the-app-in-the-store-and-using-promotional-codes"></a>Ausblenden der App im Store und Verwenden von Werbecodes

Diese Option bietet eine weitere Möglichkeit, um die Verteilung einer App auf eine bestimmte Gruppe von Testern verteilen möchten, während nicht ermitteln kann Ihre app im Store, dass andere Personen beschränken (oder ohne einen werbecode Erwerb). Allerdings kann im Gegensatz zu den privaten Zielgruppenoptionen möglicherweise jeder Benutzer den App-Eintrag sehen, wenn er über den direkten Link verfügt. Wenn die Vertraulichkeit für Ihre Übermittlung entscheidend ist, empfehlen wir stattdessen, diese nur an eine private Zielgruppe zu veröffentlichen.

Das Ausblenden der App und das Verwenden von Werbecodes kann für Apps für jede Betriebssystemversion verwendet werden, Ihre Tester können die App allerdings nur dann abrufen, wenn sie Windows10 ausführen.

So verwenden Sie diese Option:

- Wählen Sie im Abschnitt **Sichtbarkeit** der Seite **Preise und Verfügbarkeit** unter [Erkennbarkeit](choose-visibility-options.md#discoverability), die Option **Make this product available but not discoverable in the Store**. Wählen Sie die Option für **Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before, or have a promotional code and are using a Windows 10 device**. 
- Nach der Zertifizierung der App [generieren Sie Angebotscodes](generate-promotional-codes.md) für die App, und verteilen Sie sie dann an Ihre Tester. Sie können für einen Zeitraum von sechs Monaten für eine einzelne App Codes generieren, die bis zu 1.600 Einlösungen ermöglichen. Diese Codes bieten Ihren Testern einen direkten Link zum Eintrag der App, damit sie die App kostenlos herunterladen können, auch wenn Sie bei der Einreichung einen Preis für die App festgelegt haben.
- Wenn Sie bereit sind, Ihre App für die Allgemeinheit zur Verfügung zu stellen, können Sie eine neue Übermittlung erstellen und die Option **Sichtbarkeit** in **Make this product available and discoverable in the Store** ändern (sowie ggf. andere gewünschte Änderungen vornehmen).


## <a name="targeted-distribution-with-a-link-to-your-apps-listing"></a>Zielgerichtete Verteilung mit einem Link zum App-Eintrag

Im Gegensatz zu den oben beschriebenen Optionen eignet sich diese Option für Kunden mit Windows Phone8.1 und Windows10 (allerdings nicht für Windows8 x). Kein Kunde ist in der Lage, die App durch Suchen oder Browsen im Store zu finden. Aber jeder Kunde mit dem entsprechenden direkten Link zum Store-Eintrag kann die App auf einem Gerät mit Windows Phone 8.1 oder früher oder unter Windows10 herunterladen. Damit die Tester Ihre App kostenlos herunterladen können, müssen Sie als Preis **Kostenlos** festlegen.

So verwenden Sie diese Option:
- Wählen Sie im Abschnitt **Sichtbarkeit** der Seite **Preise und Verfügbarkeit** unter [Erkennbarkeit](choose-visibility-options.md#discoverability), die Option **Make this product available but not discoverable in the Store**. Wählen Sie die Option für **Direct link only: Any customer with a direct link to the product’s listing can download it, except on Windows 8.x.**.
- Nachdem Ihr Produkt veröffentlicht wurde, geben Sie den Link (die **URL** auf der [Seite App-Identität](view-app-identity-details.md)) an Ihre Tester, damit sie die App ausprobieren können.
- Wenn Sie bereit sind, Ihre App für die Allgemeinheit zur Verfügung zu stellen, können Sie eine neue Übermittlung erstellen und die Option **Sichtbarkeit** in **Make this product available and discoverable in the Store** ändern (sowie ggf. andere gewünschte Änderungen vornehmen).


## <a name="targeted-distribution-to-windows-phone-customers-with-specified-email-addresses"></a>Zielgerichtete Verteilung an Kunden mit Windows Phone mit angegebenen E-Mail-Adressen

> [!IMPORTANT]
> Diese Option steht nicht für neue Übermittlungen zur Verfügung. Wenn Sie diese Option vorher für eine App für Windows Phone8.1 oder früher ausgewählt haben, können Sie diese auch weiterhin für diese App verwenden. Sie können die Liste der Tester (bis zu 10.000) ändern, indem Sie eine neue Übermittlung erstellen. 

Mit dieser Option können Personen mit der angegebenen E-Mail-Adresse Ihre App über einen direkten Link zum Eintrag herunterladen (auf einem Gerät mit Windows Phone8.1 oder früher). Anderen Kunden können die App nicht herunterladen, auch wenn sie über den Link verfügen, und sie können die App weder durch Suchen noch Browsen im Store finden. Damit Tester die App herunterladen können, müssen Sie ihnen den Link senden (die **URL** auf der [Seite App-Identität](view-app-identity-details.md)), und sie müssen mit einem Microsoft-Konto angemeldet sein, das mit einer E-Mail-Adresse verbunden ist, die Sie angegeben haben. Sie können die App ebenfalls für Tester auf Windows10-Geräten durch [Generieren von Werbecodes](generate-promotional-codes.md) verfügbar machen. Jeder Benutzer mit einem Werbecode Ihrer App kann sie auf ein Windows10-Gerät herunterladen, auch wenn Sie ihre E-Mail-Adresse hier nicht eingegeben haben.
