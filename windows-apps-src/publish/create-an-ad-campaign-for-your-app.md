---
Description: You can create ad campaigns in Partner Center to help promote your app and grow your app's user base.
title: Erstellen einer Anzeigenkampagne für Ihre App
ms.assetid: 10D94929-92C4-4379-AA5F-6FEF879F2463
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Anzeige, Kampagne, bewerben
ms.localizationpriority: medium
ms.openlocfilehash: 8ece97d2e2cf96d2905902fd563f1de9027aa64a
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8752743"
---
# <a name="create-an-ad-campaign-for-your-app"></a>Erstellen einer Anzeigenkampagne für Ihre App

Sie können Anzeigenkampagnen erstellen, im [Partner Center](https://partner.microsoft.com/dashboard) zum bewerben Ihrer app und seine Benutzerbasis. Standardmäßig wählen wir die Zielgruppe für Ihre basierend auf den Einstellungen für Ihre app im Partner Center anzeigen, aber Sie können auch eigene Zielgruppe zu definieren. Außerdem können Sie einen Standardsatz von Anzeigenvorlagen verwenden oder eigene Anzeigenentwürfe hochladen. Weitere Informationen zur Anzeigenkampagnen finden Sie unter [Allgemeine Fragen zu Anzeigenkampagnen](common-questions.md).

Sie können Anzeigenkampagnen nur für Apps erstellen, die die letzte Veröffentlichungsphase des [App-Zertifizierungsprozesses](the-app-certification-process.md) durchlaufen haben.

> [!NOTE]
> In diesem Abschnitt der Dokumentation wird das Erstellen einer Anzeigenkampagne im Partner Center beschrieben. Sie können auch die [Microsoft Store-Werbungs-API](../monetize/run-ad-campaigns-using-windows-store-services.md) zum programmgesteuerten Erstellen und Verwalten von Anzeigenkampagnen verwenden.

## <a name="instructions"></a>Anweisungen

So erstellen Sie eine Anzeigenkampagne zum Bewerben einer App.

1.  Klicken Sie im linken Navigationsmenü der [Partner Center](https://partner.microsoft.com/dashboard)erweitern Sie **bewerben** , und wählen Sie dann **Anzeigenkampagnen**.
2.  Wählen Sie **Erstellen einer Anzeigenkampagne** (oder wenn Sie bereits Kampagnen erstellt haben, wählen Sie **Neue Kampagne**) aus.
3.  Wählen Sie auf der nächsten Seite im Abschnitt **Objekttyp** eine der folgenden Optionen aus:
    * **Mehr Installationen für Ihre App**. Wählen Sie diese Option, wenn Ihre Anzeigenkampagne darauf abzielt, dass Kunden Ihre App installieren.
    * **Mehr Interaktion in Ihrer App**. Wählen Sie diese Option aus, wenn Ihre Anzeigenkampagne Ihre Kunden dazu bringen soll, Ihre App häufiger zu verwenden. Wenn Sie diese Option auswählen, können Sie Ihre Anzeigenkampagne auf bestimmte, von Ihnen definierte [Kundensegmente](create-customer-segments.md) ausrichten.

4.  Wählen Sie die App aus, die Sie mit dieser Kampagne bewerben möchten. Beachten Sie, dass die App im Store bereits vorhanden sein muss.
5.  Überprüfen Sie den Namen für Ihre Kampagne im Feld **Kampagnennamen** und ändern Sie ihn wenn notwendig.
6.  Wählen Sie unter **Kampagnentyp** eine der folgenden Optionen aus:
    * **Kostenpflichtige Anzeige:** Diese Anzeigen werden in jeder App angezeigt, die dem Zielgerät und der Zielkategorie der App entspricht. Neue, nach dem 9.Januar2017 erstellte Kampagnen, zeigen Ihre Anzeigen auch in MSN.com, Outlook.com, Skype und anderen Microsoft-Premium-Eigenschaften an. Werbekampagnen für Apps, deren Ziel Apps und Microsoft-Premium-Eigenschaften sind, werden als *universelle* Kampagnen bezeichnet.
    * **Kostenlose Community-Anzeigen:** Diese Anzeigen werden in Apps ausgeführt, die von anderen Entwicklern veröffentlicht wurden, die ebenfalls Community-Anzeigenkampagnen erstellen. Bevor Sie diese Option auswählen können, müssen Sie auf der Seite **Gewinnbringende Nutzung** -> **In-App Anzeigen** dem Anzeigen von Community-Anzeigen in Ihrer App zugestimmt haben. Weitere Informationen finden Sie unter [Über Community-Anzeigen](about-community-ads.md).
    * **Kostenlose Eigenwerbung:** Diese Anzeigen werden nur in Ihren Apps angezeigt, die dem Gerätetyp der beworbenen App entsprechen. Eigenwerbung ist kostenlos. Weitere Informationen finden Sie unter [Über Eigenwerbung](about-house-ads.md).

7.  Bei kostenpflichtigen Anzeigenkampagnen müssen Sie die die **Kampagnendauer** bestätigen (die Zeitspanne, auf die Ihr Kampagnenbudget angewendet wird). Die Standardoption ist **Monatlich**, wobei Ihr Kampagnenbudget regelmäßig monatlich ausgegeben wird, bis Sie die Kampagne beenden. Wenn Sie über ein Premiumkonto verfügen, können Sie optional **Benutzerdefiniert** auswählen, um einen benutzerdefinierten Datums- und Uhrzeitbereich auszuwählen, der während Ihres Kampagnenbudgets angewendet werden soll. Weitere Informationen zu Premienkonten finden Sie unter [Allgemeine Fragen zu Anzeigenkampagnen](common-questions.md#how-can-i-increase-the-maximum-monthly-budget-amount-allowed-for-my-ad-campaign).

8.  Bestätigen Sie Ihr Budget und die Zahlungsinformationen. (Wenn Sie eine Kampagne für Eigenwerbung oder Community-Anzeigen erstellen, werden diese Optionen nicht angezeigt, da diese Kampagnen kostenlos sind).
    * Legen Sie mithilfe des Schiebereglers unter **Budget**den Betrag fest, den Sie monatlich für diese Anzeige aufwenden möchten (oder das gesamte Budget, wenn Sie eine benutzerdefinierte Kampagnendauer ausgewählt haben).

        Das monatliche Budget wird für den Monat, in dem die Anzeigenkampagne erstellt wird, anteilig berechnet. Wenn Sie also eine Anzeigenkampagne in der Mitte des Monats erstellen, zahlen Sie für den betreffenden Monat die Hälfte des Monatsbudgets.

    * Legen Sie eine Zahlungsmethode für Ihre Anzeigenkampagne fest, indem Sie auf **Neue Zahlungsmethode hinzufügen** klicken und Ihre Kontodaten eingeben. Wenn Sie bereits ein Zahlungsmittel angegeben haben, können Sie **Eine andere Zahlungsmethode auswählen**, wenn Sie sie aktualisieren müssen. Das Land/die Region der Rechnungsadresse Ihrer Zahlungsmethode muss das Land/die Region mit Ihrem Entwicklerkonto verknüpft ist übereinstimmen.

    * Wenn Sie von Microsoft einen Gutschein für eine Anzeigenkampagne erhalten haben, klicken Sie auf **Use a coupon**, geben Sie den Gutscheincode ein, und klicken Sie auf **Übernehmen**, um den Gutschein für die Kampagne zu übernehmen.

    Klicken Sie anschließend auf **Speichern und Weiter**, um zum Schritt **Zielgruppe** zu gelangen. Dieser Schritt ist nicht für eigenwerbungskampagnen, verfügbar, da diese nur in Ihren eigenen apps ausgeführt werden.

9.  Auf der Seite **Zielgruppe** zeigen wir die Einstellungen für die Zielgruppe an, die für Ihre Kampagne empfohlen wird. Optional können Sie diese Informationen anpassen:
    * **Länder/Regionen**: Wählen Sie bis zu 5 Länder oder Regionen, in denen die Anzeige angezeigt werden soll. Eine Liste der unterstützten Länder oder Regionen finden Sie unter [Häufig gestellte Fragen zu Anzeigenkampagnen](common-questions.md#where-will-my-ad-appear).

    * **Geräte**: Wählen Sie die Gerätetypen aus, auf denen diese Anzeigen erscheinen sollen. Es werden nur die von der App unterstützten Gerätetypen angezeigt.

    * **Oberfläche**: Wenn Sie **Universell** wählen, wird Ihre Anzeige auch in MSN.com, Outlook.com, Skype und anderen Microsoft-Premium-Eigenschaften angezeigt. Wählen Sie **App**, wenn die Anzeige nur in Apps angezeigt werden soll.

    * **Betriebssystem**: Wählen Sie die Betriebssysteme, auf denen die Werbung angezeigt werden soll. Es werden nur die von der App unterstützten Betriebssysteme angezeigt.

    * **Geschlecht**: Wählen Sie aus, ob Sie die Zielgruppe für Ihre Anzeige auf das Geschlecht beschränken.

    * **Altersbereich**:Wählen Sie den Altersbereich der gewünschten Zielgruppe aus.

    In diesem Abschnitt wird auch das Diagramm **Geschätzte Reichweite** angezeigt. Das Diagramm zeigt die Zielgruppe, die Sie mit Ihrer aktuellen Auswahl für die Adressierung erreichen, als Prozentsatz aller Benutzer von Windows-Apps mit Anzeigenunterstützung in den ausgewählten Märkten an.

10.  Wenn Sie **Mehr Interaktion in Ihrer App** als Ziel Ihrer Kampagne ausgewählt haben, können Sie eines Ihrer Kundensegmente als Zielgruppe auswählen. Mit dieser Kampagne erstellte Anzeigen werden nur den Kunden angezeigt, die zum jeweiligen Segment gehören. Pro Anzeigenkampagne kann nur ein Segment ausgewählt werden. Informationen zu Kundensegmenten finden Sie unter [Erstellen von Kundensegmenten](create-customer-segments.md). Klicken Sie anschließend auf **Speichern und Weiter**, um zum Schritt **Anzeigenentwurf** zu gelangen. Dieser Schritt ist nicht für eigenwerbungskampagnen, verfügbar, da diese nur in Ihren eigenen apps ausgeführt werden.

11.  Wählen Sie auf der Seite **Anzeigenentwurf** eine der folgenden Optionen aus:
    * **Automatisch generiert**. Dies ist die Standardoption, und es können Sie eine Anzeige mit unseren Standardvorlagen erstellen. Sie können die Inhalte Ihrer Anzeigen durch Auswahlen anpassen. Wir sehen uns eine Vorschau Ihrer Anzeige basierend auf den Auswahlmöglichkeiten an (dies wird automatisch aktualisiert, wenn Sie eine Auswahl treffen).
        * Wählen Sie im Dropdownmenü **Sprache** die Sprache der Anzeigen aus. Der Text für das Microsoft Store-Signal wird in der Sprache angezeigt, die Sie auswählen.
        * Um Ihrer Anzeige eine zusätzliche Textzeile hinzuzufügen, geben Sie den Text im Feld **Benutzerdefinierter Slogan** ein.
            > [!NOTE]
            > Der von Ihnen eingegebene Text muss in die ausgewählte Sprache lokalisiert werden. Der benutzerdefinierte Slogan wird zurückgewiesen, wenn der Text nicht mit den [Bing Ads-Richtlinien](http://go.microsoft.com/fwlink?LinkId=398341) konform ist. Auf dieser Seite finden Sie Informationen zum Stil und zu nicht zulässigen Inhalten.
        * Um die Anzeige weiter anzupassen, erweitern Sie **Anzeigendesign anpassen/Alle Größen anzeigen** und wählen eine der folgenden Optionen aus:
            * **Hintergrundfarbe**. Treffen Sie Ihre Auswahl aus den verfügbaren Optionen.
            * **Bilder** Wählen Sie eine der verfügbaren Bilder aus (aus der Store-Eintrag Ihrer App).
            * **Bewertung meiner App anzeigen**. Aktivieren Sie dieses Kontrollkästchen, wenn die Bewertung der App angezeigt werden soll.
            * **Anzeigen, dass meine App kostenlos ist**. Wenn Ihre App in allen ausgewählten Märkten kostenlos ist, können Sie dieses Kontrollkästchen aktivieren.
            * **Handlungsaufforderung**. Wenn **Mehr Interaktion in Ihrer App** als Ziel für Ihre Kampagne wählen, können Sie die Schaltfläche für die Handlungsaufforderung in Ihrer App auf **Öffnen**, **Spielen**, **Lesen**, **Hören** oder **Kaufen** festlegen.  

    * **Benutzerdefiniert**. Wählen Sie diese Option aus, um Ihren eigenen Anzeigenentwurf zu verwenden. Beachten Sie, dass Sie ein Kundensegment früher ausgewählt haben, Sie benutzerdefinierte Werbemittel verwenden müssen. Sie können verschiedene Dateien für jede der verfügbaren Anzeigengrößen hochladen. Die Dateien müssen folgenden Anforderungen und Richtlinien entsprechen:
        * Jede Datei muss eine PNG- oder JPG-Datei mit höchstens 40KB sein.
        * Ihre Anzeigenentwürfe müssen die in der [Microsoft Creative Acceptance Policy](http://go.microsoft.com/fwlink?LinkId=532595) dargelegten Anforderungen erfüllen.
        * Der Inhalt in Ihren Anzeigenentwürfen muss für die beworbene App relevant sein. Anzeigenentwürfe, die nicht mit der App zusammenhängen, werden nicht in anderen Apps verteilt.
        * Alle Inhalte in Ihren Anzeigenentwürfen sollten deutlich lesbar sein. Beispielsweise sollten Inhalte nicht verschwommen, verpixelt oder gestreckt sein.

12.  Wenn Sie ein [Premiumkonto](common-questions.md#how-can-i-increase-the-maximum-monthly-budget-amount-allowed-for-my-ad-campaign) besitzen, können Sie mithilfe des Kontrollkästchens **Ziel-URL** steuern, was geschieht, wenn ein Kunde auf Ihre Anzeige klickt.
    * Wenn Sie das Kontrollkästchen nicht aktivieren, wird der Store-Eintrag Ihrer App angezeigt, wenn ein Kunde auf Ihre Anzeige klickt.
    * Wenn Sie Kochava oder Tune verwenden, um die Installationsdaten für Ihre App zu messen, geben Sie die Installationsverfolgungs-URL von Kochava oder Tune ein. Beim Speichern der Kampagne wird die Verfolgungs-URL überprüft, um sicherzustellen, dass sie zur Eintragsseite für Ihre App im Microsoft Store aufgelöst wird. Weitere Informationen zur Installationsverfolgung mit Kochava und Tune finden Sie in der [Kochava](http://support.kochava.com/)- und [Tune](https://help.tune.com/)-Dokumentation.
    * Wenn Sie **Mehr Interaktion in Ihrer App** als Kampagnenziel wählen, können Sie einen [Deep-Link-URI](../launch-resume/handle-uri-activation.md) angeben, um Kunden aus den ausgewählten Segment zu einer bestimmten Seite in Ihrer App umzuleiten.
    * Wenn Sie ein Ziel angeben, bei dem es sich nicht um die Beschreibungsseite Ihrer App oder eine Seite innerhalb Ihrer App handelt, wird Ihre Kampagne automatisch angehalten.

13.  Klicken Sie abschließend auf **Überprüfen**, um die Einstellungen der Anzeigenkampagne – und falls es sich um eine kostenpflichtige Kampagne handelt – das Budget und die Zahlungsinformationen zu bestätigen. Klicken Sie auf **Bestätigen**. Ihre Anzeigen werden in der Regel nach wenigen Stunden angezeigt.

## <a name="review-ad-campaign-performance"></a>Überprüfen der Leistung einer Anzeigenkampagne

Gehen Sie auf die Seite **Anzeigenkampagnen** zurück, um die Leistung Ihrer Kampagnen anzuzeigen. Wählen Sie **Abschnittfilter** aus, um festzulegen, was im Bericht nach **Datum**, **Kampagnenziel**, **App-Name**, **Kampagnentyp** oder **Status** enthalten sein soll. Zusätzlich zum Anzeigen von Informationen zu den **Aufrufen**, **Klicks**, **Konvertierungen** und **Ausgaben** für Ihre Kampagne können Sie den Bericht zum **Anhalten** oder **Fortsetzen** einer Kampagne verwenden. Weitere Informationen finden Sie unter [Bericht „Anzeigenkampagne“](promote-your-app-report.md).

Um eine Kampagne zu bearbeiten, wählen Sie ihren Namen in der Liste aus.
