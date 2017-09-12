---
author: jnHs
Description: "Auf der Seite „Preise und Verfügbarkeit“ des App-Übermittlungsprozesses können Sie festlegen, wie viel Ihre App kosten soll, ob Sie eine kostenlose Testversion anbieten und wie, wann und wo sie für Kunden verfügbar ist."
title: "Festlegen der Preise und Verfügbarkeit von Apps"
ms.assetid: 37BE7C25-AA74-43CD-8969-CBA3BD481575
ms.author: wdg-dev-content
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 9686876bf0e5e3d89ce527eb07535f1c0a704f2a
ms.sourcegitcommit: 968187e803a866b60cda0528718a3d31f07dc54c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="set-app-pricing-and-availability"></a>Festlegen der Preise und Verfügbarkeit von Apps

> [!NOTE]
> Wir haben vor kurzem die verfügbaren Optionen auf dieser Seite aktualisiert. Wenn Sie laufende Übermittlungen hatten, bevor diese neueren Optionen verfügbar waren, zeigen diese Übermittlung immer noch die älteren Optionen an. Sie können diese Übermittlung löschen und dann eine neue erstellen, wenn Sie die neusten Optionen für diese App verwenden möchten. Andernfalls werden die neusten Optionen mit dem nächsten Update nach der Veröffentlichung der laufenden Übermittlung verfügbar.

Auf der Seite **Preise und Verfügbarkeit** des [App-Übermittlungsprozesses](app-submissions.md) können Sie festlegen, wie viel Ihre App kosten soll, ob Sie eine kostenlose Testversion anbieten und wie, wann und wo sie für Kunden verfügbar ist. Wir stellen Ihnen hier die auf dieser Seite verfügbaren Optionen vor und informieren Sie darüber, was Sie bei der Eingabe dieser Informationen beachten sollten.


## <a name="markets"></a>Märkte

Der Windows Store erreicht Kunden in über 200Ländern und Regionen in aller Welt. Standardmäßig werden Ihre App in allen möglichen Märkten angeboten. Falls gewünscht, können Sie die spezifischen Märkte auswählen, in denen Sie Ihre App anbieten möchten. 

Weitere Informationen erhalten Sie unter [Festlegen der Marktauswahl](define-pricing-and-market-selection.md).


## <a name="visibility"></a>Sichtbarkeit

Im Abschnitt **Sichtbarkeit** können Sie Einschränkungen dafür festlegen, wie die App gefunden und erworben werden kann.

Die Standardeinstellung ist **Make this product available and discoverable in the Store**. Das heißt, dass Ihre App im Store so eingetragen wird, dass sie von Kunden über den direkten Link zur App und/oder mit anderen Methoden wie z.B. Suchen, Browsen oder Einträgen in zusammengestellten Listen gefunden werden kann. 

Wenn Sie Ihre App im Store ausblenden, sie aber dennoch für bestimmte Personen zur Verfügung stellen möchten, wählen Sie **Optionen anzeigen**, um den Abschnittzu erweitern, und wählen Sie dann **Make this product available but not discoverable in the Store**. Dies bedeutet, dass kein Kunde Ihre App durch Suchen oder Browsen im Store finden kann, unabhängig von seiner Version des Betriebssystems. Sie müssen auch eine der folgenden Versionen wählen, um zu bestimmen, wie Ihre App erworben werden kann.

>[!IMPORTANT]
> Diese Optionen beschränken die Betriebssystemversionen, unter denen Kunden Ihre App erwerben können. Lesen Sie die Beschreibungen sorgfältig, um sicherzustellen, dass Sie wissen, welche Betriebssystemversionen unterstützt werden. Beachten Sie, dass Kunden mit Windows8 und Windows8.1 die App überhaupt nicht erhalten können, wenn Sie eine der Optionen unter **Make this product available but not discoverable in the Store** auswählen. 

- **Direct link only: Any customer with a direct link to the product’s listing can download it, except on Windows 8.x.** Jeder Kunde, der zum Eintrag Ihrer App über einen direkten Link gelangt, kann sie auf Geräten unter Windows10 oder Windows Phone8.1 und früher herunterladen. Kunden unter Windows8.x können die App mit dieser Option überhaupt nicht herunterladen.
- **Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before, or have a promotional code and are using a Windows 10 device.** Selbst wenn ein Kunde einen direkten Link besitzt, kann er die App nur herunterladen, wenn er einen [Werbecode](generate-promotional-codes.md) besitzt und ein Windows10-Gerät verwendet. Wenn Sie einem Kunden einen Code geben, kann er den Link und den Code verwenden, um Ihre App kostenlos (nur unter Windows10) zu erhalten, obwohl Sie sie nicht für andere Kunden anbieten. Abgesehen von der Verwendung eines Werbecodes gibt es keine Möglichkeit, Ihre App zu erhalten.
- **Individuals on Windows Phone 8.x only: Only people you specify below can download this product on a Windows Phone 8.x device. Anyone with a direct link and a promotional code may download the product on a Windows 10 device.** Diese Option wird möglicherweise nicht für alle Übermittlungen angezeigt. Sie gilt nur, wenn Sie Pakete haben, die unter Windows Phone 8.x ausgeführt werden können. Nur Kunden, deren (mit dem jeweiligen Microsoft-Konto verknüpfte) E-Mail-Adresse Sie in das Feld eingegeben haben (getrennt durch Semikolons), können die App unter Windows Phone 8.x über einen direkten Link zum App-Eintrag herunterladen. Sie können auch Werbecodes generieren und diese an bestimmte Windows 10-Benutzer wie oben beschrieben verteilen. 

> [!TIP]
> Wenn Sie eine App überhaupt nicht mehr für Kunden anbieten möchten, klicken Sie in der App-Übersicht auf **Make app unavailable**. Nachdem Sie bestätigt haben, dass die App nicht mehr verfügbar sein soll, wird sie innerhalb weniger Stunden im Store nicht mehr angezeigt, und neue Kunden haben keine Möglichkeit, sie herunterzuladen. Diese Aktion setzt alle hier ausgewählten Optionen außer Kraft: Die App ist für neue Kunden nicht verfügbar. Falls Sie sie für neue Kunden wieder verfügbar machen möchten, können Sie jederzeit in der App-Übersicht auf **Make app available** klicken. Weitere Informationen finden Sie unter [Entfernen einer App aus dem Store](guidance-for-app-package-management.md#removing-an-app-from-the-store).

## <a name="schedule"></a>Zeitplan

Standardmäßig (es sei denn, Sie haben eine der Optionen für **Make this app available but not discoverable in the Store** im Abschnitt **Sichtbarkeit** ausgewählt) wird Ihre App für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat. Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern. 

Weitere Informationen finden Sie unter [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md).

## <a name="display-release-date"></a>Anzeigen des Veröffentlichungsdatums

Standardmäßig ist das Veröffentlichungsdatum für Ihre App das Datum, an dem sie im Store angezeigt wird. Wenn Sie diese Einstellung außer Kraft setzen und ein benutzerdefiniertes Veröffentlichungsdatum angeben möchten, können Sie das Kontrollkästchen in diesem Abschnitt aktivieren und dann das Veröffentlichungsdatum eingeben. Beachten Sie, dass das Veröffentlichungsdatum nicht immer in Store-Einträgen angezeigt wird.

## <a name="pricing"></a>Preise

Sie müssen einen Grundpreis für Ihre App auswählen (es sei denn, Sie haben eine der Optionen für **Make this app available but not discoverable in the Store** im Abschnitt [Sichtbarkeit](#visibility) ausgewählt) und entweder **Kostenlos** oder eines der verfügbaren Preisniveaus auswählen. Sie können auch Preisänderungen planen, um das Datum und die Uhrzeit anzugeben, an dem bzw. zu der sich der Preis Ihrer App ändern soll. Darüber hinaus haben Sie die Möglichkeit, diese Änderungen für bestimmte Märkte anzupassen. 

Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md).

## <a name="free-trial"></a>Kostenlose Testversion

Viele Entwickler bieten Kunden die Möglichkeit, ihre App mithilfe der im Store verfügbaren Testfunktionen kostenlos auszuprobieren. Standardmäßig ist **Keine kostenlose Testversion** ausgewählt. Für Ihre App gibt es keine Testversion. Wenn Sie eine Testversion anbieten möchten, können Sie einen Wert aus der Dropdownliste **Kostenlose Testversion** auswählen.

Es gibt zwei Arten von Testversionen, die Sie auswählen können, und Sie haben die Möglichkeit zum Konfigurieren von Datum und Uhrzeit, an dem bzw. zu der das Angebot der Testversion starten und enden soll.

### <a name="time-limited"></a>Zeitlich begrenzt

Wählen Sie **Zeitlich begrenzt**, um es Benutzern zu ermöglichen, Ihre App für eine bestimmte Anzahl von Tagen kostenlos zu testen: **1 Tag**, **7 Tage**, **15 Tage** oder **30 Tage**. Sie können Features durch Hinzufügen von Code zum [Ausschließen oder Beschränken von Features in der Testversion](../monetize/in-app-purchases-and-trials.md) einschränken oder Kunden den Zugriff auf die vollständigen Funktionen während dieses Zeitraums gewähren. 
> [!NOTE]
> Zeitlich begrenzte Testversionen werden für Kunden unter Windows 10 Build 10.0.10586 oder früheren Versionen bzw. für Kunden unter Windows Phone8.1 und früheren Versionen nicht angezeigt.

### <a name="unlimited"></a>Unbegrenzt

Wählen Sie **Unbegrenzt**, damit Kunden unbegrenzte Zeit kostenlos auf Ihre App zugreifen dürfen. Da Sie Ihre Kunden zum Kauf der Vollversion animieren möchten, achten Sie darauf, mithilfe des geeigneten Codes [Features in der Testversion auszuschließen oder einzuschränken](../monetize/in-app-purchases-and-trials.md).

### <a name="start-and-end-dates"></a>Start- und Enddatum

Standardmäßig wird Ihre Testversion verfügbar, sobald Ihre App veröffentlicht wurde, und ihre Bereitstellung wird nie beendet. Wenn Sie möchten, können Sie das Datum und die Uhrzeit angeben, an dem bzw. zu der mit der Bereitstellung der Testversion begonnen und an dem bzw. zu der ihre Bereitstellung beendet werden soll. 

>[!NOTE]
> Diese Datumsangabe gilt nur für Kunden mit Windows10. Wenn Ihre Testversion für Kunden mit früheren Betriebssystemversionen gilt, wird die Testversion solange angeboten, solange Ihr Produkt verfügbar ist. 

Zum Festlegen des Datums für das Anbieten der Testversion ändern Sie die Angabe im Dropdownfeld **Starts on** und/oder **Ends on** in **at** und wählen anschließend Datum und Uhrzeit. In diesem Fall können Sie entweder **UTC** auswählen, sodass die ausgewählte Uhrzeit UTC-Zeit (Universal Coordinated Time, Koordinierte Weltzeit) ist, oder **Lokal** festlegen, damit diese Uhrzeiten in jeder Zeitzone für einen Markt verwendet werden. (Beachten Sie, dass für Märkte, die mehr als eine Zeitzone umfassen, nur eine Zeitzone in diesem Markt verwendet wird. Für die USA wird die Eastern Time verwendet.) 

>[!NOTE]
> Im Gegensatz zum Abschnitt [Zeitplan](configure-precise-release-scheduling.md) kann das Datum, das Sie für **Kostenlose Testversion** auswählen, nicht für bestimmte Märkte angepasst werden. 



## <a name="sale-pricing"></a>Sonderpreise

Wenn Sie Ihre App zu einem reduzierten Preis für einen begrenzten Zeitraum anbieten möchten, können Sie ein Sonderangebot erstellen und planen.

Weitere Informationen finden Sie unter [Anbieten von Apps und Add-Ons](put-apps-and-add-ons-on-sale.md).


## <a name="organizational-licensing"></a>Organisationslizenzierung

Standardmäßig kann Ihre App Organisationen für den Volumekauf angeboten werden. Sie können angeben, ob und wie Ihre App in diesem Abschnitt angeboten werden soll.

Weitere Informationen finden Sie unter [Optionen für die Organisationslizenzierung](organizational-licensing.md).

## <a name="publish-date"></a>Veröffentlichungsdatum

Standardmäßig beginnt Ihre Übermittlung den Veröffentlichungsprozess direkt nach der Zertifizierung, es sei denn, Sie haben Datumsangaben im [Abschnitt **Zeitplan**](#schedule) (oben beschrieben) konfiguriert. 

Um zu steuern, wann Ihre App im Store veröffentlicht werden soll, verwenden Sie den Abschnitt **Zeitplan**. Für die meisten Übermittlungen sollten Sie diesen Abschnittverwenden, um die Veröffentlichung der App zu planen. Behalten Sie für den Abschnitt **Veröffentlichungsdatum** die Standardoption **Publish this submission as soon as it passes certification** bei. Dadurch wird die Übermittlung nicht vor dem Datum veröffentlicht, das Sie im Abschnitt **Zeitplan** festgelegt haben. Das Datum, das Sie im Abschnitt **Zeitplan** ausgewählt haben, bestimmt, wann Ihre App für Kunden im Store verfügbar gemacht wird.

Wenn Sie noch kein Veröffentlichungsdatum festlegen möchten und Ihre Übermittlung unveröffentlicht bleiben soll, bis Sie manuell mit dem Veröffentlichungsprozess beginnen möchten, können Sie **Publish this submission manually** auswählen. Die Auswahl dieser Option bedeutet, dass Ihre Auswahl erst veröffentlicht wird, wenn Sie es angeben. Nachdem Ihre App die Zertifizierung bestanden hat, können Sie sie veröffentlichen, indem Sie auf der Seite mit dem Zertifizierungsstatus **Jetzt veröffentlichen** oder wie nachfolgend beschrieben ein bestimmtes Datum auswählen.

Wählen Sie **Nicht vor \[Datum\]**, um sicherzustellen, dass die Übermittlung nicht vor einem bestimmten Datum veröffentlicht wird. Mit dieser Option wird Ihre Übermittlung möglichst zum oder nach dem angegebenen Datum veröffentlicht. Das Datum muss mindestens 24Stunden in der Zukunft liegen. Zusammen mit dem Datum können Sie auch die Uhrzeit angeben, zu der die Veröffentlichung der Übermittlung beginnen soll.
 
> [!NOTE]
> Aufgrund von Verzögerungen bei der Zertifizierung oder Veröffentlichung kann das gewünschte Veröffentlichungsdatum unter Umständen nicht eingehalten werden. Es kann nicht garantiert werden, dass Ihre App (oder das Update) an einem bestimmten Datum im Windows Store zur Verfügung steht.  

Sie können das Veröffentlichungsdatum auch nach dem Einreichen der App ändern, solange sie noch nicht in die Phase Veröffentlichen eingetreten ist. 

