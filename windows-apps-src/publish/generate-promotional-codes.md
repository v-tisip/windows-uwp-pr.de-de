---
author: jnHs
Description: You can generate promotional codes for an app or add-on that you have published in the Microsoft Store.
title: Generieren von Werbecodes
ms.assetid: 9B632266-64EC-4D62-A4C4-55B6643D8750
ms.author: wdg-dev-content
ms.date: 01/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Angebotscode, Angebotscodes, Token, Token
ms.localizationpriority: high
ms.openlocfilehash: 634c0857982924ca1b588519172d77d97dd74791
ms.sourcegitcommit: b6915c7fa2c7292e9b4e3d3e9927dc8746ec1ffb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="generate-promotional-codes"></a>Generieren von Werbecodes


Sie können Werbecodes für Apps oder Add-Ons generieren, die Sie im Microsoft Store veröffentlicht haben. Werbecodes sind eine einfache Möglichkeit, einflussreichen Benutzern kostenlosen Zugriff auf Ihre App oder Ihr Add-On zu ermöglichen. Sie können Werbecodes auch in Kundendienstszenarien verwenden, indem Sie Benutzern kostenlosen Zugriff auf Ihre App oder Ihr Add-On gewähren, oder für [Betatests](beta-testing-and-targeted-distribution.md) mit Windows10.

Jeder Werbecode hat eine entsprechende eindeutige einlösbare URL, die Sie an einen einzelnen Kunden oder eine Kundengruppe verteilen können. Der Kunde muss nur auf die URL klicken, um den Code einzulösen und Ihre App oder Ihr Add-On über den Microsoft Store zu installieren.

> [!TIP]
> Sie können [benutzerorientierte Pushbenachrichtigungen](send-push-notifications-to-your-apps-customers.md) verwenden, um einen Werbecode an ein Segment Ihrer Kunden zu verteilen. Verwenden Sie dabei unbedingt einen Werbecode, der mehreren Kunden die Nutzung des gleichen Codes ermöglicht.

Auf dem Windows Dev Center-Dashboard können Sie folgende Aktionen ausführen:

-   Bestellen von Werbecodes für Ihre App oder Ihr Add-On
-   Herunterladen einer erfüllten Werbecodebestellung
-   Überprüfen der Werbecodenutzung

> [!NOTE]
> Sie können Werbecodes generieren, auch wenn Sie für [Sichtbarkeit](set-app-pricing-and-availability.md#visibility) die Option **Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before, or have a promotional code and are using a Windows 10 device.** ausgewählt haben.

Hinweis: Ihre App muss die abschließende Veröffentlichungsphase des [App-Zertifizierungsprozesses](the-app-certification-process.md) bestehen, bevor Kunden einen Werbecode zur Installation einlösen können.


## <a name="promotional-code-policies"></a>Richtlinien für Werbecodes

Beachten Sie die folgenden Richtlinien für Werbecodes:

-   Werbecodes können für alle über den Microsoft Store veröffentlichten Apps oder Add-Ons (mit Ausnahme von Abonnements für Add-Ons) generiert werden. Kunden können die Codes mit allen Versionen von Windows einlösen, die von Ihren Apps oder Add-Ons unterstützt werden.
-   Werbecodes laufen sechs Monate nach dem Datum der Bestellung ab, es sei denn, Sie wählen ein früheres Ablaufdatum aus.
-   Sie können für alle Apps oder Add-Ons alle 6Monate Codes generieren, die bis zu 1600Einlösungen ermöglichen. Der Zeitraum von sechs Monaten beginnt mit der Übermittlung der ersten Werbecodebestellung, auch wenn Sie ein früheres Ablaufdatum auswählen. Die Summe aller 1600 Einlösungen pro Produkt bezieht sich auf Codes zur einmaligen Verwendung und Codes, die mehrmals verwendet werden können.
-   Sie müssen die in der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) definierten Anforderungen erfüllen, einschließlich Abschnitt **3k. Werbecodes**.


## <a name="order-promotional-codes"></a>Bestellen von Werbecodes

So bestellen Sie Werbecodes für Apps oder Add-Ons, die Sie im Microsoft Store veröffentlicht haben:

1.  Erweitern Sie im linken Navigationsmenü des Windows Dev Center-Dashboards **Bewerben** und wählen Sie dann **Angebotscodes** aus.

2.   Klicken Sie auf der Seite **Werbecodes** auf **Codes bestellen**.

3.  Geben Sie auf der Seite **Neue Werbecodes bestellen** Folgendes ein:
    -   Wählen Sie die Apps oder Add-Ons, für die Sie Codes generieren möchten. (Beachten Sie, dass Sie keine Werbecodes für die Abonnement-Add-Ons erstellen können.)
    -   Geben Sie einen Namen für die Bestellung an. Anhand dieses Namens können Sie beim Überprüfen der Werbecode-Nutzungsdaten zwischen verschiedenen Codebestellungen unterscheiden.
    -   Wählen Sie den Auftragstyp. Sie können auch auswählen, dass ein Satz von Werbecodes generiert werden soll, die jeweils nur einmal verwendet werden können, oder dass ein Werbecode generiert wird, der mehrmals verwendet werden kann.
    -   Geben Sie die Anzahl der zu bestellenden Codes (sofern eine Reihe von Codes generiert wird) oder die Häufigkeit an, mit der der Code eingelöst werden kann (sofern ein Code generiert wird, der mehrmals verwendet werden kann).
    -   Geben Sie an, wann die Werbecodes aktiv werden sollen. Um ein spezifisches Startdatum und eine spezifische Startuhrzeit zu wählen, entfernen Sie die Markierung für das Kontrollkästchen **Codes werden umgehend aktiv**. Andernfalls werden die Codes sofort aktiv.
    -   Geben Sie an, wann die Werbecodes ablaufen sollen. Um ein spezifisches Ablaufdatum und eine frühere Ablaufzeit als sechs Monate zu wählen, deaktivieren Sie das Kontrollkästchen **Codes laufen nach 6 Monaten ab**.

4.  Klicken Sie auf **Codes bestellen**. Sie werden dann zurück auf die Seite **Werbecodes** geleitet, auf der Sie Ihre neue Bestellung in der Zusammenfassungstabelle der Werbecodebestellungen für diese App sehen.


## <a name="download-and-distribute-promotional-codes"></a>Herunterladen und Verteilen von Werbecodes

So laden Sie erfüllte Werbecodebestellungen herunter und verteilen die Codes an Kunden:

1.  Erweitern Sie im linken Navigationsmenü des Windows Dev Center-Dashboards **Bewerben** und wählen Sie dann **Angebotscodes** aus.
2.  Klicken Sie auf den Link zum **Herunterladen** Ihres Angebotscodes, und speichern Sie die Datei auf Ihrem Computer. Diese Datei enthält Informationen zu Ihrer Werbecodebestellung im TSV-Format (.tsv).
3.  Öffnen Sie die .tsv-Datei im Editor Ihrer Wahl. Öffnen Sie für ein optimales Ergebnis die .tsv-Datei in einer Anwendung, die Daten in tabellarischer Struktur anzeigen kann, z.B. Microsoft Excel. Allerdings können Sie die Datei auch in einem Text-Editor öffnen.

    Die Datei enthält Spalten mit den folgenden Daten für jeden Code:

    -   **Produktname**: Der Name der App oder des Add-Ons, dem der Code zugeordnet ist.
    -   **Bestellungsname**: Der Name der Bestellung, in der dieser Code erstellt wurde.
    -   **Werbecode**: Der Code selbst. Dies ist eine 5x5-Zeichenfolge von alphanumerischen Zeichen, die durch Bindestriche getrennt sind. Beispiel: DM3GY-M2GYM-6YMW6-4QHHT-23W2Z
    -   **Einlösbare URL**: Die URL, mit der ein Kunde den Code einlösen und die App bzw. das Add-On installieren kann. Die URL hat das folgende Format: http://go.microsoft.com/fwlink/?LinkId=532540&mstoken=&lt;Werbecode>
    -   **Startdatum**: Das Datum, an dem dieser Code aktiv wurde.
    -   **Ablaufdatum**: Das Datum, an dem dieser Code abläuft.
    -   **Code-ID**: Eine eindeutige ID für diesen Code.
    -   **Bestellungs-ID**: Eine eindeutige ID für die Bestellung, in der dieser Code erstellt wurde.
    -   **Ausgegeben an**: Ein leeres Feld, mit dem Sie nachverfolgen können, welchem Kunden Sie den Code gegeben haben.
    -   **Verfügbar**: Wie häufig der Code noch eingelöst werden kann (zum Zeitpunkt der Dateierstellung).
    -   **Eingelöst**: Wie häufig der Code eingelöst wurde (zum Zeitpunkt der Dateierstellung).

4.  Sie können die einlösbaren URLs in einem beliebigen, von Ihnen bevorzugten Kommunikationsformat an Kunden verteilen (z.B. zielgruppenorientierte Benachrichtigungen, E-Mail, SMS-Nachricht oder gedruckte Karten). Die Kommunikation sollte Folgendes enthalten:
    -   Eine Erklärung, für welche App bzw. welches Add-On der Werbecode vorgesehen ist, und optional eine Beschreibung, warum der Kunde den Code erhält.
    -   Die einlösbare URL für den Code.
    -   Anweisungen zum Aufrufen der einlösbaren URL, Anmelden mit dem Microsoft-Konto und Befolgen der Anweisungen zum Herunterladen und Installieren Ihrer App.


## <a name="code-redemption-user-experience"></a>Benutzererfahrung bei Einlösung des Codes

Nachdem Sie einen Werbecode (oder seine einlösbare URL) an Kunden verteilt haben, können sie diese URL verwenden, um das Produkt kostenlos zu erhalten. Durch Klicken auf die einlösbare URL wird eine authentifizierte Seite **Code einlösen** unter <https://account.microsoft.com/billing/redeem> geöffnet. Diese Seite enthält eine Beschreibung der App, für die der Benutzer den Code einlöst. Wenn der Kunde nicht mit seinem Microsoft-Konto angemeldet ist, kann er dazu aufgefordert werden. Der Kunde kann auch <https://account.microsoft.com/billing/redeem> aufrufen und den Code direkt eingeben.

> [!IMPORTANT]
> Es wird empfohlen, dass Sie Werbecodes erst an Ihre Kunden verteilen, wenn Ihr Produkt den Veröffentlichungsprozess abgeschlossen hat (auch wenn Sie **Make this product available but not discoverable in the Store** ausgewählt haben). Kunden wird einen Fehler angezeigt, wenn sie versuchen, einen Werbecode für ein Produkt zu verwenden, das noch nicht veröffentlicht wurde.

Wenn der Kunde auf **Einlösen** klickt, wird die Übersicht der App im Microsoft Store geöffnet (auf einem Windows10- oder Windows8.1-Gerät). Dort kann er auf **Installieren** klicken, um die App kostenlos herunterzuladen und zu installieren. Wenn sich der Kunde an einem Computer oder einem Gerät befindet, auf dem Microsoft Store nicht installiert ist, öffnet der Link die Microsoft Store-Webseite für die App. Der Code wird auf das Microsoft-Konto des Kunden angewendet, damit er die App später kostenlos auf einem Windows-Gerät herunterladen kann (das mit dem gleichen Microsoft-Konto verknüpft ist).

> [!NOTE]
> In einigen Fällen wird dem Kunden womöglich die Schaltfläche **Kaufen** anstelle der Schaltfläche **Installieren** angezeigt, obwohl die App erfolgreich über den Werbecode eingelöst wurde. Der Kunde kann dann zum kostenlosen Installieren der App auf **Kaufen** klicken.


## <a name="review-your-promotional-codes"></a>Überprüfen der Werbecodes

Um eine ausführliche Zusammenfassung der Werbecodebestellungen für Ihre Apps und Add-Ons zu sehen, wechseln Sie zur Seite **Werbecodes** (erweitern Sie im linken Navigationsmenü im Dev Center-Dashboard **Bewerben** und wählen Sie **Angebotscodes** aus). Sie können die folgenden detaillierten Informationen für Ihre aktuellen und inaktiven Werbecodes überprüfen:
    -   Bestellungsname
    -   App oder Add-On
    -   Startdatum
    -   Ablaufdatum
    -   Verfügbar
    -   Eingelöst

Sie können auch eine Bestellung aus dieser Tabelle [herunterladen](#download-and-distribute-promotional-codes).

 
