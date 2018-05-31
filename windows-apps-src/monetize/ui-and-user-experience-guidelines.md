---
author: mcleanbyron
ms.assetid: 7a38a352-6e54-4949-87b1-992395a959fd
description: Erfahren Sie mehr über Richtlinien für die Benutzeroberfläche und Benutzerumgebung für Anzeigen in Apps.
title: Richtlinien für die Benutzeroberfläche und Benutzerumgebung für Anzeigen
ms.author: mcleans
ms.date: 08/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, Richtlinien, bewährte Methoden
ms.localizationpriority: medium
ms.openlocfilehash: 6eaeacdb24428b8870e941e5f93ca40dfa554903
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1690806"
---
# <a name="ui-and-user-experience-guidelines-for-ads"></a>Richtlinien für die Benutzeroberfläche und Benutzerumgebung für Anzeigen

Dieser Artikel enthält Richtlinien für die Bereitstellung hervorragender Umgebungen mit Banneranzeigen, Interstitialanzeigen und nativen Anzeigen in Ihren Apps. Allgemeine Informationen zur Gestaltung des Erscheinungsbilds für Apps finden Sie unter [Design und UI](https://developer.microsoft.com/windows/apps/design).

> [!IMPORTANT]
> Jegliche Verwendung von Werbung in Ihrer App muss ohne Einschränkung den Microsoft Store-Richtlinien entsprechen, einschließlich [Richtlinie 10.10](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) (Werbung – Verhaltensregeln und Inhalt). Insbesondere die Implementierung von Banneranzeigen oder Interstitialanzeigen in Ihrer App muss die Anforderungen in der Microsoft Store-Richtlinie [Richtlinie 10.10.1](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) erfüllen. Dieser Artikel enthält Beispiele für Implementierungen, die gegen diese Richtlinie verstoßen würden. Diese Beispiele dienen lediglich zu Informationszwecken und zum besseren Verständnis der Richtlinie. Diese Beispiele sind nicht umfassend, und möglicherweise gibt es viele weitere Arten, gegen die Microsoft Store-Richtlinien zu verstoßen, die nicht in diesem Artikel aufgeführt sind.

## <a name="guidelines-for-banner-ads"></a>Richtlinien für Banneranzeigen

Die folgenden Abschnitte enthalten Empfehlungen für das Implementieren von [Banneranzeigen](banner-ads.md) in Ihrer App mithilfe von [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) und Beispiele für Implementierungen, die einen Verstoß gegen [Richtlinie 10.10.1](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) der Microsoft Store-Richtlinien darstellen.

### <a name="best-practices"></a>Empfohlene Methoden

Wir empfehlen diese Methoden beim Implementieren von Banneranzeigen in Ihrer App:

* Widmen Sie den Großteil der Benutzeroberfläche Ihrer App Steuerelementen und Inhalten.

* Binden Sie die Werbung in die Erfahrung ein. Geben Sie den Designern eine Beispielanzeige vor, an der sie erkennen können, wie Sie sich die Werbung vorstellen. Zwei Beispiele für gut durchdachte Anzeigen in Apps sind das Layout, bei der die Anzeige als Inhalt fungiert, und das Split-Layout.

  Verwenden Sie während der Entwicklungs- und Testphase unsere [Testmodus-Anzeigeneinheiten](set-up-ad-units-in-your-app.md#test-ad-units), um zu sehen, wie die verschiedenen Anzeigengrößen in Ihrer App aussehen und funktionieren. Sobald Sie mit dem Testen fertig sind, müssen Sie die [App anhand von Live-Anzeigeneinheiten aktualisieren](set-up-ad-units-in-your-app.md#live-ad-units), bevor Sie die App zur Zertifizierung übermitteln.

* Verwenden Sie [Anzeigengrößen](supported-ad-sizes-for-banner-ads.md), die gut in das Layout für das aktive Gerät passen.

* Planen Sie für Zeiten, wenn keine Anzeigen verfügbar sind. Zu gewissen Zeiten kann es passieren, dass keine Anzeigen an Ihre App gesendet werden. Gestalten Sie Ihre Seiten so, dass sie gut aussehen, unabhängig davon, ob sie eine Anzeige enthalten oder nicht. Weitere Informationen finden Sie unter [Behandeln von Fehlern bei Anzeigen](error-handling-with-advertising-libraries.md).

* Bei einem Szenario mit Benachrichtigung des Benutzers, das am besten mit einem Overlay abgewickelt wird, rufen Sie [AdControl.Suspend](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.suspend.aspx) auf, zeigen Sie das Overlay an, und rufen Sie dann [AdControl.Resume](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.resume.aspx) auf, wenn das Benachrichtigungsszenario abgeschlossen ist.

<span />

### <a name="practices-to-avoid"></a>Nicht empfehlenswerte Methoden

Wir empfehlen folgende Methoden beim Implementieren von Banneranzeigen in Ihrer App nicht:

* Füllen Sie freie Flächen nicht mit Anzeigen aus. Nutzen Sie nicht gleich die erste freie Fläche, die Sie finden können, als Werbefläche. Stattdessen sollten die Anzeigen in den Gesamtentwurf integriert werden.

* Schalten Sie nicht übermäßig viele Anzeigen in der App. Zu viele Anzeigen beeinträchtigen das Erscheinungsbild der App sowie deren Benutzerfreundlichkeit. Sie möchten durch die Werbung zwar Geld verdienen, aber nicht auf Kosten der App selbst.

* Lenken Sie die Benutzer nicht von ihren Kernaufgaben ab. Der Schwerpunkt sollte immer auf der App liegen. Werbeflächen sollten so eingebettet werden, dass sie eine untergeordnete Rolle spielen.

<span />

### <a name="examples-of-policy-violations"></a>Beispiele für Verstöße gegen Richtlinien

Dieser Abschnitt enthält Beispiele für Szenarien mit Banneranzeigen, die einen Verstoß gegen [Richtlinie 10.10.1](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) der Microsoft Store-Richtlinien darstellen. Diese Beispiele dienen lediglich zu Vorführungszwecken und zum besseren Verständnis der Richtlinie. Diese Beispiele sind nicht umfassend, und möglicherweise gibt es viele weitere Arten, gegen die Richtlinie 10.10.1 zu verstoßen, die hier nicht aufgeführt sind.

* Jegliches Beeinträchtigen der Möglichkeit des Benutzers, die Banneranzeige zu sehen, wie etwa das Verändern der Transparenz von [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) oder das Platzieren eines anderen Steuerelements über **AdControl** (ohne vorheriges Aufrufen von [AdControl.Suspend](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.suspend.aspx)).

* Auffordern der Benutzer, auf eine Banneranzeige zu klicken, um eine Aufgabe in Ihrer App auszuführen, oder Zwingen der Benutzer, als Folge des Designs Ihrer App auf Banneranzeigen zu klicken.

* Beliebig geartetes Umgehen des integrierten minimalen Zeitgebers für die Aktualisierung der Banneranzeigen, einschließlich (aber nicht beschränkt auf) Austauschen von [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Objekten oder Erzwingen einer Seitenaktualisierung ohne Eingreifen des Benutzers.

* Verwenden von Live-Anzeigeneinheiten (d.h. Anzeigeneinheiten, die Sie aus dem Windows Dev Center-Dashboard erhalten) während der Entwicklungs- und Testphase oder in einem Emulator.

* Schreiben oder Verteilen von Code, der Anzeigendienste auf andere Weise aufruft als die Microsoft Advertising-Bibliotheken, die im Zusammenhang mit Ihrer App ausgeführt werden.

* Interagieren mit nicht dokumentierten Schnittstellen oder untergeordneten Objekten, die von den Microsoft Advertising-Bibliotheken erstellt wurden, z.B. **WebView** oder **MediaElement**.

<span id="interstitialbestpractices10">

## <a name="guidelines-for-interstitial-ads"></a>Richtlinien für Interstitialanzeigen

Wenn [Interstitialanzeigen](interstitial-ads.md) geschickt eingesetzt werden, können sie den Umsatz Ihrer App erheblich erhöhen, ohne dass sich dies negativ auf die Kundenzufriedenheit auswirkt. Werden Sie jedoch unangemessen eingesetzt, dann können solche Anzeigen das genaue Gegenteil bewirken.

Die folgenden Abschnitte enthalten Empfehlungen für das Implementieren von Videointerstitialanzeigen und Interstitial-Banneranzeigen in Ihrer App mithilfe von [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) und Beispiele für Implementierungen, die einen Verstoß gegen [Richtlinie 10.10.1](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) der Microsoft Store-Richtlinien darstellen. Da Sie Ihre App, abgesehen von den Richtlinien, am besten kennen, überlassen wir Ihnen die endgültige Entscheidung. Beachten Sie dabei, dass die App-Bewertungen und Ihre Einnahmen eng miteinander verknüpft sind.

### <a name="best-practices"></a>Empfohlene Methoden

Wir empfehlen diese Methoden beim Implementieren von Interstitialanzeigen in Ihrer App:

* Bauen Sie Interstitialanzeigen in den natürlichen Fluss der App ein, wie zum Beispiel zwischen den verschiedenen Schwierigkeitsebenen des Spiels.

* Verbinden Sie die Anzeigen mit konkreten Vorteilen, wie beispielsweise:

    * Hinweise, die zum erfolgreichen Abschließen einer Schwierigkeitsebene führen.

    * Zusätzliche Zeit, um eine Ebene auszuführen.

    * Benutzerdefinierte Avatar-Features, wie ein Tattoo oder ein Hut.

* Sollte es bei Ihrer App erforderlich sein, eine Videointerstitialanzeige bis zum Schluss anzusehen, dann erwähnen Sie diese Regel im Vorfeld, damit die Benutzer beim Schließen nicht von einer Fehlermeldung überrascht werden.

* Vorabrufen der Anzeige (durch Aufrufen von [InterstitialAd.RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.requestad.aspx)) im Idealfall 30 - 60 Sekunden, bevor Sie die Anzeige schalten möchten.

* Abonnieren Sie alle vier Ereignisse, die in der [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)-Klasse offengelegt werden(**Canceled**, **Completed**, **AdReady** und **ErrorOccurred**) und setzen Sie sie ein, um die richtigen Entscheidungen für Ihre App zu treffen.

* Stellen Sie anstelle einer vom Server abgestimmten Anzeige einige integrierte Funktionen bereit. Das könnte in einigen Situationen hilfreich sein:

    * Im Offlinemodus, wenn die Anzeigenserver nicht erreicht werden können.

    * Wenn das **ErrorOccurred**-Ereignis ausgelöst wird.

    * Wenn Sie sich dafür entscheiden, basierend auf dem [ConnectionProfile](https://docs.microsoft.com/uwp/api/Windows.Networking.Connectivity.ConnectionProfile) an der Benutzerbandbreite einzusparen, stehen Ihnen in der **ConnectionProfile**-Klasse APIs zur Verfügung, die Ihnen dabei behilflich sein können.

* Verwenden Sie das Standardtimeout (30 Sekunden). Liegt jedoch ein berechtigter Grund vor, der dagegen spricht, dann gehen Sie in diesem Fall nicht unter 10 Sekunden. Das Herunterladen von Interstitialwerbung dauert erheblich länger als das von Standardbanneranzeigen. Dies ist besonders für Märkte wichtig, die nicht über Hochgeschwindigkeitsverbindungen verfügen.

<span/>

* Berücksichtigen Sie daher den Datentarifplan der Nutzer. Verzichten Sie beispielsweise darauf, eine Videointerstitialanzeige auf einem mobilen Gerät anzuzeigen, das kurz davor ist, das Datenlimit zu überschreiten oder es bereits überschritten hat bzw. warnen Sie den Nutzer vorher. In der [ConnectionProfile](https://docs.microsoft.com/uwp/api/Windows.Networking.Connectivity.ConnectionProfile)-Klasse finden Sie APIs, die Ihnen hierbei helfen.

* Optimieren Sie Ihre App nach der ersten Übermittlung fortlaufend. Sehen Sie sich die [Anzeigenberichte](../publish/advertising-performance-report.md) an, und nehmen Sie Designänderungen vor, um die Füll- und Abschlussraten von Interstitialvideos zu verbessern.

<span />

### <a name="practices-to-avoid"></a>Nicht empfehlenswerte Methoden

Wir empfehlen folgende Methoden beim Implementieren von Interstitialanzeigen in Ihrer App nicht:

* Übertreiben Sie es nicht. Erzwingen Sie Anzeigen nicht häufiger als etwa alle 5 Minuten, es sei denn der Benutzer verfolgt aktiv einen konkreten Vorteil, der über den eigentlichen Spielverlauf hinausgeht.

* Schalten Sie keine Interstitialanzeigen beim Starten der App – Benutzer könnten annehmen, dass sie die falsche Kachel angeklickt haben.

* Schalten Sie keine Interstitialanzeigen beim Beenden. Dies wäre eine schlechte Inventarentscheidung, da die Abschlussraten wahrscheinlich nahe Null liegen würden.

* Schalten Sie nicht zwei oder mehr Interstitialanzeigen nacheinander. Es würde die Benutzer frustrieren, wenn sie feststellen, dass die Statusanzeige für Anzeigen wieder an den Ausgangspunkt zurückgesetzt wurde. Viele Benutzer werden annehmen, dass es sich dabei schlichtweg um einen Fehler bei der Programmierung oder der Anzeigenbereitstellung handelt.

* Rufen Sie Interstitialvideos nicht mehr als 5 Minuten vor dem Aufrufen von [InterstitialAd.Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx) ab. Gutes Inventar wird die Konvertierung von vorab abgerufenen Anzeigen in berechenbare Anzeigenaufrufe maximieren.

* Bestrafen Sie Benutzer nicht für Probleme bei der Anzeigenbereitstellung, d.h., wenn beispielsweise keine Anzeigen verfügbar sind. Wenn Sie beispielsweise eine UI-Option anzeigen, die lautet „Sehen Sie sich eine Anzeige an und erhalten Sie *xxx*“, dann sollten Sie *xxx* auch tatsächlich bereitstellen, wenn der Benutzer seinen Teil erfüllt. Berücksichtigen Sie die folgenden beiden Optionen:

    * Bieten Sie die Option nur an, wenn das [InterstitialAd.AdReady](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.adready.aspx)-Ereignis bereits ausgelöst wurde.

    * Sorgen Sie dafür, dass die App eine integrierte Funktion enthält, die die gleichen Vorteile bietet, wie eine wirkliche Anzeige.

* Verwenden Sie keine Interstitialanzeigen, damit ein Benutzer einen Wettbewerbsvorteil in einem Multiplayer-Spiel erhält. Locken Sie Benutzer beispielsweise nicht mit einer besseren Waffe in einem Ego-Shooter, wenn sie eine Interstitialanzeige ansehen. Ein individuelles T-Shirt für den Avatar des Spielers ist in Ordnung, solange es keine Tarnung bietet!

<span />

### <a name="examples-of-policy-violations"></a>Beispiele für Verstöße gegen Richtlinien

Dieser Abschnitt enthält Beispiele für Szenarien mit Interstitialanzeigen, die einen Verstoß gegen [Richtlinie 10.10.1](https://docs.microsoft.com/legal/windows/agreements/store-policies#1010-advertising-conduct-and-content) der Microsoft Store-Richtlinien darstellen. Diese Beispiele dienen lediglich zu Vorführungszwecken und zum besseren Verständnis der Richtlinie. Diese Beispiele sind nicht umfassend, und möglicherweise gibt es viele weitere Arten, gegen die Richtlinie 10.10.1 zu verstoßen, die hier nicht aufgeführt sind.

* Das Platzieren eines Benutzeroberflächenelement des Containers für Interstitialanzeigen.

* Das Aufrufen von [InterstitialAd.Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx), während der Benutzer mit der App beschäftigt ist.

* Das Verwenden von Interstitialanzeigen, um etwas zu erhalten, das als Währung eingesetzt oder mit anderen Benutzern getauscht werden könnte.

* Das Anfordern neuer Interstitialanzeigen im Kontext des Ereignishandlers für das Ereignis [InterstitialAd.ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.erroroccurred.aspx). Dies kann zu einer Endlosschleife und Problemen beim Werbedienst führen.

* Das Anfordern von Interstitialanzeigen, nur um eine Sicherungsanzeige für eine Wasserfallfolge von Anzeigen zu erhalten. Wenn Sie eine Interstitialanzeige anfordern und anschließend das [InterstitialAd.AdReady](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.adready.aspx)-Ereignis erhalten, muss die nächste Interstitialanzeige in Ihrer App die Anzeige sein, die für die Anzeige über die Methode [InterstitialAd.Show](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.show.aspx) bereit ist.

* Verwenden von Live-Anzeigeneinheiten (d.h. Anzeigeneinheiten, die Sie aus dem Windows Dev Center-Dashboard erhalten) während der Entwicklungs- und Testphase oder in einem Emulator.

* Schreiben oder Verteilen von Code, der Anzeigendienste auf andere Weise aufruft als die Microsoft Advertising-Bibliotheken, die im Zusammenhang mit Ihrer App ausgeführt werden.

* Interagieren mit nicht dokumentierten Schnittstellen oder untergeordneten Objekten, die von den Microsoft Advertising-Bibliotheken erstellt wurden, z.B. **WebView** oder **MediaElement**.

## <a name="guidelines-for-native-ads"></a>Richtlinien für native Anzeigen

Mit [nativen Anzeigen](native-ads.md) haben Sie eine hohe Kontrolle über die Darstellung von Werbeinhalten für Ihre Benutzer. Befolgen Sie diese Anforderungen und Richtlinien, um sicherzustellen, dass die Werbebotschaft Ihre Benutzer erreicht und gleichzeitig eine verwirrend Anzeigeerfahrung für Ihre Benutzer verhindert wird.

### <a name="register-the-container-for-your-native-ad"></a>Registrieren Sie den Container für die native Anzeige

In Ihrem Code müssen Sie die [RegisterAdContainer](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.registeradcontainer.aspx)-Methode des **NativeAd**-Objekts aufrufen, um das UI-Element zu registrieren, das als Container für die native Anzeige agiert und optional alle speziellen Steuerelemente, die Sie als klickbare Ziele für die Anzeige registrieren möchten. Dies ist erforderlich, um Anzeigenaufrufe und -klicks ordnungsgemäß nachzuverfolgen.

Es gibt zwei Überladungen für die **RegisterAdContainer**-Methode, die Sie verwenden können:

* Wenn Sie den gesamten Container für alle nativen Anzeigenelemente klickbar gestalten möchten, rufen Sie die [RegisterAdContainer(FrameworkElement)](https://msdn.microsoft.com/library/windows/apps/mt809188.aspx)-Methode auf und übergeben den zu steuernden Container an die Methode. Wenn Sie beispielsweise alle nativen Anzeigenelemente in separaten Steuerelementen anzeigen, die alle in einem **StackPanel** gehostet werden, und das gesamte **StackPanel** klickbar sein soll, übergeben Sie das **StackPanel** an diese Methode.

* Wenn Sie nur bestimmte native Anzeigenelemente klickbar gestalten möchten, rufen Sie die [RegisterAdContainer (FrameworkElement, IVector(FrameworkElement))](https://msdn.microsoft.com/library/windows/apps/mt809189.aspx)-Methode auf. Nur die Steuerelemente, die Sie über den zweiten Parameter übergeben, werden klickbar.

### <a name="required-native-ad-elements"></a>Erforderliche native Anzeigenelemente

Sie müssen mindestens folgenden Elemente der native Anzeigenelemente für den Benutzer anzeigen. Wenn Sie diese Elemente nicht einbeziehen, entsteht möglicherweise eine schlechte Leistung und es gibt wenige Aufrufe für Ihre Anzeigeneinheit.

1. Zeigen Sie immer den Titel der nativen Anzeige an (verfügbar in der [Titel](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.title.aspx)-Eigenschaft des **NativeAd**-Objekts). Bieten Sie ausreichend Platz zum Anzeigen von mindestens 25 Zeichen. Wenn der Titel länger ist, ersetzen Sie den zusätzlichen Text mit den Auslassungszeichen.
2. Zeigen Sie immer mindestens eines der folgenden Elemente an, um die native Anzeige vom Rest der App klar zu unterscheiden und die Herkunft der Inhalte von einem Werbepartner herauszustellen:
  * Das eindeutige *Anzeigen*-Symbol (verfügbar in der [AdIcon](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.adicon.aspx)-Eigenschaft des **NativeAd**-Objekts). Dieses Symbol wird von Microsoft bereitgestellt.
  * Der *unterstützt von*-Text (verfügbar in der [SponsoredBy](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.sponsoredby.aspx)-Eigenschaft des **NativeAd**-Objekts). Dieser Text wird vom Werbepartner bereitgestellt.
  * Als Alternative zum *unterstützt von*-Text können Sie einige andere Text anzeigen, die die native Anzeige vom Rest der App abgrenzen (z.B. „Gesponsert Inhalt“, „Werbeinhalte“, „Empfohlene Inhalte“).

### <a name="user-experience"></a>Benutzerfreundlichkeit

Ihre native Anzeige sollte von den restlichen Ihrer App klar abgegrenzt werden und mit einem Rand versehentliche Klicks verhindern. Verwenden Sie Rahmen, andere Hintergründen und andere UI-Elemente, um die Inhalte vom Rest der App zu trennen. Bedenken Sie, dass versehentlich Anzeigen-Klicks auf lange Sicht nicht für den Umsatz mit Anzeigen oder Ihre Endbenutzererfahrung von Vorteil sind.

### <a name="description"></a>Description

Wenn Sie die Beschreibung für die Anzeige anzeigen (verfügbar in der [Description](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.description.aspx) Eigenschaft des **NativeAd**-Objekts), bieten Sie ausreichend Platz zum Anzeigen von mindestens 75 Zeichen. Es wird empfohlen, dass Sie eine Animation verwenden, um den gesamten Inhalt der Anzeigenbeschreibung anzuzeigen.

### <a name="call-to-action"></a>Handlungsaufforderung

Der *Handlungsaufforderung*-Text (verfügbar in der [CallToAction](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.calltoaction.aspx)-Eigenschaft des **NativeAd**-Objekts) ist eine wichtige Komponente der Anzeige. Wenn Sie diesen Text anzeigen möchten, befolgen Sie diese Richtlinien:

* Zeigen Sie den *Handlungsaufforderung*-Text immer auf einen klickbaren Steuerelemente (z.B. eine Schaltfläche oder einen Link) für den Benutzer an.
* Zeigen Sie den *Handlungsaufforderung*-Text immer vollständig an.
* Stellen Sie sicher, dass der *Handlungsaufforderung*-Text vom restlichen Werbetext des Werbepartners getrennt ist.
