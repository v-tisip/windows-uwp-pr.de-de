---
author: jnHs
Description: "Das WindowsDevCenter-Dashboard bietet Ihnen die Möglichkeit, Ihre App nur für bestimmte Personen bereitzustellen. Auf diese Weise können Tester die App ausprobieren, bevor Sie sie für die Allgemeinheit anbieten."
title: Betatests und zielgerichtete Verteilung
ms.assetid: 38E4ED22-D6C1-40D8-9B16-6B3E51BD962E
ms.author: wdg-dev-content
ms.date: 08/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 7dd0e346e6be147935503eeb0b685568bfce726c
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="beta-testing-and-targeted-distribution"></a>Betatests und zielgerichtete Verteilung

Wie sorgfältig Sie Ihre App auch testen: Es geht nichts über einen Praxistest, bei dem die App von anderen Benutzern verwendet wird. Das Windows Dev Center-Dashboard bietet Ihnen Optionen, eine App-Übermittlung nur für bestimmte Personen bereitzustellen. Auf diese Weise können Tester die App ausprobieren, bevor Sie sie für die Öffentlichkeit anbieten. Die Betatester finden möglicherweise Probleme, die Sie übersehen haben, wie z. B. Rechtschreibfehler, unübersichtliche Benutzerführungen der App und sogar Fehler, die dazu führen können, dass die App abstürzt. Sie haben dann die Möglichkeit, diese Probleme zu beheben, bevor Sie die Übermittlung für die Allgemeinheit verfügbar machen. So erhalten Sie ein hochwertigeres Endprodukt.

Wir bieten verschiedene Möglichkeiten, um die Verteilung Ihrer Apps auf Ihre Tester zu beschränken, ohne eine separate Version Ihrer App mit eigenem Namen und eigener Paketidentität erstellen zu müssen. (Selbstverständlich können Sie bei Bedarf auch eine separate App zum Testen erstellen. In diesem Fall muss sich der Name der App allerdings vom endgültigen öffentlichen Namen der App unterscheiden.)

Mit welcher Methode Sie Ihre App an die Tester verteilen, hängt davon ab, auf welche Betriebssysteme Ihre App ausgerichtet ist. Im Anschluss finden Sie Optionen für Windows10 und für Windows Phone8.1 (und ältere Versionen).

## <a name="making-your-app-available-to-testers-on-windows-10-devices"></a>Bereitstellen Ihrer App für Tester auf Windows10-Geräten

Wir bieten zwei Optionen, mit denen Sie die Verteilung Ihrer Apps auf bestimmte Benutzer von Windows10-Geräten beschränken können.

### <a name="package-flights"></a>Flight-Pakete

Falls Sie bereits Ihre App veröffentlicht haben, können Sie Flight-Pakete erstellen, um den gewünschten Benutzern einen anderen Satz von Paketen bereitzustellen. Sie können ebenfalls für die gleiche App mehrere Flight-Pakete erstellen und jeweils für unterschiedliche Benutzergruppen verwenden. So können Sie komfortabel mehrere Pakete parallel testen und Pakete aus einem Flight in die Übermittlung ohne Test-Flight überführen, falls Sie zu dem Schluss kommen, dass die Pakete für die allgemeine Bereitstellung bereit sind.

Weitere Informationen finden Sie unter [Flight-Pakete](package-flights.md).

> [!NOTE]
> Wenn Sie spezifische Pakete auf eine zufällige Auswahl Ihrer Windows10-Kunden nach einem angegebenen Prozentsatz verteilen möchten, anstatt auf eine angegebene Gruppe bestimmter Kunden, helfen Ihnen die Informationen unter [Schrittweises Paketrollout](gradual-package-rollout.md) weiter. Sie können das Rollout auch mit Ihren Flight-Paketen kombinieren, wenn Sie ein Update schrittweise auf eine Ihrer Test-Flight-Gruppen verteilen möchten.

<span id="hide" />
### <a name="hiding-the-app-in-the-store-and-using-promotional-codes"></a>Ausblenden der App im Store und Verwenden von Werbecodes

Wenn Sie eine App nur an eine bestimmte Gruppe von Testern verteilen möchten, **ohne** vorher eine allgemein verfügbare Übermittlung zu veröffentlichen, können Sie den gleichen [App-Übermittlungsprozess](app-submissions.md) wie bei allen anderen Apps verwenden. Gehen Sie wie folgt vor, wenn Sie möchten, dass die App nur von bestimmten Benutzern kostenlos bezogen werden kann und andere Kunden weder den App-Eintrag sehen noch die App herunterladen können:

-   Wählen Sie in Ihrer Übermittlung im Abschnitt [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) der Seite **Preise und Verfügbarkeit** die Option **Make this product available but not discoverable in the Store**.  Wählen Sie die Option für **Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before, or have a promotional code and are using a Windows 10 device**. Dadurch wird verhindert, dass Benutzer Ihre App über die Suche oder durch Browsen im Store finden.
-   Nach der Zertifizierung der App [generieren Sie Angebotscodes](generate-promotional-codes.md) für die App, und verteilen Sie sie dann an Ihre Tester. Sie können für einen Zeitraum von sechs Monaten für eine einzelne App Codes generieren, die bis zu 1.600 Einlösungen ermöglichen. Diese Codes bieten Ihren Testern einen direkten Link zum Eintrag der App, damit sie die App kostenlos herunterladen können, auch wenn Sie bei der Einreichung einen Preis für die App festgelegt haben.

Nachdem Sie die Angebotscodelinks an Ihre Tester verteilt haben, können sie sie testen und Ihnen Feedback senden, um Sie bei der Optimierung der App zu unterstützen. Wenn Sie dann bereit sind, Ihre App für die Allgemeinheit zur Verfügung zu stellen, können Sie eine neue Übermittlung erstellen und die Option **Sichtbarkeit** in **Diese App im Store verfügbar und leicht auffindbar machen** ändern (sowie ggf. andere gewünschte Änderungen vornehmen).

Hierbei sind einige Dinge zu beachten:

-   Sie können Ihren Testern jederzeit eine aktualisierte Version Ihrer App bereitstellen, indem Sie eine neue Übermittlung erstellen. Stellen Sie mit der Option **Stop acquisition** sicher, dass die Option **Sichtbarkeit** auf **Make this product available but not discoverable in the Store** festgelegt bleibt. Die Tester erhalten das Update, nachdem es den Zertifizierungsprozess durchlaufen hat. Andere Personen haben keine Möglichkeit, darauf zuzugreifen.
-   Ihre Tester benötigen ein Windows10-Gerät, auf dem sie die App installieren können. (Ihre App muss jedoch keine Windows10-Pakete umfassen, damit diese Methode für Testzwecke verwendet werden kann.)
-   Sie können jederzeit weitere [Angebotscodes](generate-promotional-codes.md) für die Verteilung erstellen (bis zu 1600 Einlösungen pro App für einen Zeitraum von sechs Monaten).
-   Sie können den Zugriff auf die App nicht widerrufen, nachdem sie von den Testern heruntergeladen wurde. Nachdem sie die App heruntergeladen haben, können sie diese weiterhin verwenden, und sie erhalten sämtliche Updates, die Sie anschließend veröffentlichen.
-   Sie müssen festlegen, auf welche Weise Sie Feedback von Ihren Testern einholen möchten. Denken Sie daran, ein Link in die Beta-App einzufügen, damit Ihre Tester Ihnen einfach Feedback per E-Mail oder über den [Feedback-Hub](../monetize/launch-feedback-hub-from-your-app.md) senden können.
-   Sie können [Analyseberichte](analytics.md) für Ihre App überprüfen, einschließlich der Nutzungs- und Integritätsberichte von Ihren Testern abgegebenen Bewertungen und Kommentare.
-   Sie können Add-Ons einbinden, wenn Sie Ihre App an Tester verteilen. Da Sie wahrscheinlich keine Kosten erheben möchten, müssen Sie sicherstellen, dass Sie für den Preis der Add-Ons **Kostenlos** festlegen, während Sie die Tests durchführen. Wenn Sie die App dann für andere Kunden verfügbar machen, können Sie für jedes Add-On eine neue Übermittlung erstellen, um den Preis zu ändern.


## <a name="other-methods-for-distributing-apps-to-testers"></a>Andere Methoden zum Verteilen von Apps an Tester

Die Verteilung Ihrer App kann auch mithilfe der zusätzlichen Optionen im Abschnitt [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) im Abschnitt der App-Übermittlungsseite **Verfügbarkeit und Preise** auf eine bestimmte Gruppe von Benutzern beschränkt werden. Bedenken Sie, dass diese Optionen nicht für Kunden aller Betriebssystemversionen geeignet sind. Insbesondere funktioniert keine davon für Kunden unter Windows8 oder Windows8.1.

### <a name="targeted-distribution-to-customers-with-a-link-to-your-apps-listing"></a>Zielgerichtete Verteilung an Kunden mit einem Link zum App-Eintrag

Bei dieser Option können nur Personen mit einem direkten Link zum Eintrag Ihrer App gelangen, um sie herunterzuladen. Sie finden diese **URL** auf der Seite [App-Identität](view-app-identity-details.md) im Dashboard. Kein Kunde ist in der Lage, die App durch Suchen oder Browsen im Store zu finden. Aber jeder Kunde mit dem entsprechenden Link kann die App auf einem Gerät mit Windows Phone 8.1 oder früher oder unter Windows10 herunterladen. 

> [!NOTE]
> Damit die Tester Ihre App kostenlos herunterladen können, müssen Sie als Preis **Kostenlos** festlegen.

Wählen Sie zur Verwendung dieser Option im Abschnitt [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) der Seite **Preise und Verfügbarkeit** die Option **Make this product available but not discoverable in the Store**. Wählen Sie dann die Option für **Direct link only: Any customer with a direct link to the product’s listing can download it, except on Windows 8.x.**.  


### <a name="targeted-distribution-to-customers-with-specified-email-addresses"></a>Zielgerichtete Verteilung an Kunden mit angegebenen E-Mail-Adressen

Für Tests **ausschließlich auf Windows Phone8.1 und früher** ist es mit dieser Option möglich, die Verteilung der App zu beschränken. Nur Benutzer, deren (mit dem jeweiligen Microsoft-Konto verknüpfte) E-Mail-Adresse Sie in das Feld eingegeben haben, können die App über einen direkten Link zum App-Eintrag herunterladen.

> [!IMPORTANT]
> Benutzer mit den eingegebenen E-Mail-Adressen können die App nur auf Geräten unter Windows Phone8.1 (oder einer früheren Version) herunterladen.
 
Sie finden den direkten Link Ihrer App auf der Seite [App-Identität](view-app-identity-details.md) im Dashboard. Kein Kunde ist in der Lage, die App durch Suchen oder Browsen im Store zu finden. Auch wenn sie über den Link zum App-Eintrag verfügen, können sie die App nur mit einem Microsoft-Konto herunterladen, das einer E-Mail-Adresse zugeordnet ist, die Sie beim Übermitteln der App bereitgestellt haben.

> [!NOTE]
Wenn Sie diese Option verwenden, können Sie die App trotzdem für Tester auf Windows 10-Geräten verfügbar machen, indem Sie wie oben beschrieben [Angebotscodes generieren](generate-promotional-codes.md). Jeder Benutzer mit einem der Angebotscodes Ihrer App kann diese auf ein Windows10-Gerät herunterladen, auch wenn Sie dessen E-Mail-Adresse hier nicht eingegeben haben.

Wählen Sie zur Verwendung dieser Option im Abschnitt [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) der Seite **Preise und Verfügbarkeit** die Option **Make this product available but not discoverable in the Store**. Wählen Sie dann die Option für **Individuals on Windows Phone 8.x only: Only people you specify below can download this product on a Windows Phone 8.x device. Anyone with a direct link and a promotional code may download the product on a Windows 10 device.** 

Wenn Sie diese Option auswählen, beachten Sie Folgendes:

-   Diese Option kann nur ausgewählt werden, wenn Sie die App zuvor noch nie über die Option [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) mit der Einstellung **Diese App im Store verfügbar machen** veröffentlicht haben.
-   Für Ihre App muss der Preis **Kostenlos** festgelegt sein, damit sie von den Testern kostenlos heruntergeladen werden kann.
-   Ihre Tester können die App nur unter Windows Phone8.1 und früheren Versionen herunterladen. Tester müssen zur Verwendung der App über ein Windows Phone-Einzelhandelsgerät verfügen, das jedoch nicht entsperrt oder registriert sein muss.
-   Ihre Tester benötigen ein Microsoft-Konto, um auf den Windows Store zuzugreifen und die App herunterzuladen. Sie benötigen von jedem Tester die E-Mail-Adresse seines Microsoft-Kontos, um ihn in Ihre Liste aufzunehmen. Unter [Konto erstellen](http://go.microsoft.com/fwlink/p/?LinkId=618945) können Tester ein neues Microsoft-Konto erstellen.
-   Sie können in dem Textfeld bis zu 10.000 E-Mail-Adressen bereitstellen.
-   E-Mail-Adressen müssen durch Semikolons getrennt sein.
-   Sie können später weitere Adressen hinzufügen, aber Sie müssen dazu eine neue Einreichung erstellen.
-   Sie können den Zugriff auf die App nicht widerrufen, nachdem sie von den Testern heruntergeladen wurde. Nachdem sie die App heruntergeladen haben, können sie diese weiterhin verwenden, und sie erhalten sämtliche Updates, die Sie übermitteln.
