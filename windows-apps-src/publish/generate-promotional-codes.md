---
author: jnHs
Description: You can generate promotional codes for an app or add-on that you have published in the Microsoft Store.
title: Generieren von Werbecodes
ms.assetid: 9B632266-64EC-4D62-A4C4-55B6643D8750
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Angebotscode, Angebotscodes, Token, Token
ms.localizationpriority: medium
ms.openlocfilehash: 2fe89f65ff4f3278b0ba88ef4c5ca9d22bc67817
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7555665"
---
# <a name="generate-promotional-codes"></a>Generieren von Werbecodes


[Partner Center](https://partner.microsoft.com/dashboard) können Sie das Generieren von werbecodes für Apps oder Add-Ons, die Sie im Microsoft Store veröffentlicht haben. Werbecodes sind eine einfache Möglichkeit, einflussreichen Benutzern kostenlosen Zugriff auf Ihre App oder Ihr Add-On zu ermöglichen. Sie können auch werbecodes Customer Service um Szenarien zu behandeln verwenden, durch einen Benutzer kostenlosen Zugriff auf Ihre app oder Add-on oder für [Betatests](beta-testing-and-targeted-distribution.md) , mit Windows 10. 

Jeder werbecode hat eine entsprechende eindeutige einlösbare URL, die ein Kunde klicken kann, um den Code einzulösen und Ihre app oder Ihr Add-on aus dem Microsoft Store zu installieren.  Hinweis: Ihre App muss die abschließende Veröffentlichungsphase des [App-Zertifizierungsprozesses](the-app-certification-process.md) bestehen, bevor Kunden einen Werbecode zur Installation einlösen können.

Sie können einmaligen Verwendung Codes generieren (und verteilen Sie eine für jeden Kunden), oder die Möglichkeit, einen Code, der verwendet werden kann, mehrere Male durch eine angegebene Anzahl von Kunden zu generieren.

> [!TIP]
> Sie können [benutzerorientierte Pushbenachrichtigungen](send-push-notifications-to-your-apps-customers.md) verwenden, um einen Werbecode an ein Segment Ihrer Kunden zu verteilen. Verwenden Sie dabei unbedingt einen Werbecode, der mehreren Kunden die Nutzung des gleichen Codes ermöglicht.


## <a name="promotional-code-policies"></a>Richtlinien für Werbecodes

Beachten Sie die folgenden Richtlinien für Werbecodes:

-   Werbecodes können für alle über den Microsoft Store veröffentlichten Apps oder Add-Ons (mit Ausnahme von Abonnements für Add-Ons) generiert werden. Kunden können die Codes mit allen Versionen von Windows einlösen, die von Ihren Apps oder Add-Ons unterstützt werden.
-   Werbecodes laufen sechs Monate nach dem Datum der Bestellung ab, es sei denn, Sie wählen ein früheres Ablaufdatum aus.
-   Sie können für alle Apps oder Add-Ons alle 6Monate Codes generieren, die bis zu 1600Einlösungen ermöglichen. Der Zeitraum von sechs Monaten beginnt mit der Übermittlung der ersten Werbecodebestellung, auch wenn Sie ein früheres Ablaufdatum auswählen. Die Summe aller 1600 Einlösungen pro Produkt bezieht sich auf Codes zur einmaligen Verwendung und Codes, die mehrmals verwendet werden können.
-   Sie müssen die in der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) definierten Anforderungen erfüllen, einschließlich Abschnitt **3k. Werbecodes**.

> [!NOTE]
> Sie können werbecodes verwenden, selbst wenn Ihre app nicht für Kunden verfügbar ist (d. h., wenn Sie **dieses Produkt verfügbar, aber nicht im Store sichtbar machen** mit der **Stop Acquisition ausgewählt haben: jeder Kunde mit einem direkten Link sehen die Produkt-Store Angebot, aber sie können nur herunterladen, wenn sie das Produkt vor, gehören oder einen werbecode besitzen und ein Windows 10-Gerät** Option in Ihrer Übermittlung [Auffindbarkeit](choose-visibility-options.md#discoverability) Abschnitt). Mit dieser Option müssen Kunden unter Windows 10 (einschließlich Xbox) sein, um Ihr Produkt mit einem werbecode zu erwerben.


## <a name="order-promotional-codes"></a>Bestellen von Werbecodes

Um bestellen Sie werbecodes für Apps oder Add-Ons:

1.  Klicken Sie im linken Navigationsmenü der [Partner Center](https://partner.microsoft.com/dashboard)erweitern Sie **bewerben** , und wählen Sie dann **Angebotscodes**.

2.   Klicken Sie auf der Seite **Werbecodes** auf **Codes bestellen**.

3.  Geben Sie auf der Seite **Neue Werbecodes bestellen** Folgendes ein:
    -   Wählen Sie die Apps oder Add-Ons, für die Sie Codes generieren möchten. (Beachten Sie, dass Sie keine Werbecodes für die Abonnement-Add-Ons erstellen können.)
    -   Geben Sie einen Namen für die Bestellung an. Anhand dieses Namens können Sie beim Überprüfen der Werbecode-Nutzungsdaten zwischen verschiedenen Codebestellungen unterscheiden.
    -   Wählen Sie den Auftragstyp. Sie können auch auswählen, dass ein Satz von Werbecodes generiert werden soll, die jeweils nur einmal verwendet werden können, oder dass ein Werbecode generiert wird, der mehrmals verwendet werden kann.
    -   Geben Sie die Anzahl der zu bestellenden Codes (sofern eine Reihe von Codes generiert wird) oder die Häufigkeit an, mit der der Code eingelöst werden kann (sofern ein Code generiert wird, der mehrmals verwendet werden kann).
    -   Geben Sie an, wann die Werbecodes aktiv werden sollen. Um ein spezifisches Startdatum und eine spezifische Startuhrzeit zu wählen, entfernen Sie die Markierung für das Kontrollkästchen **Codes werden umgehend aktiv**. Andernfalls werden die Codes sofort aktiv (obwohl Ihr Produkt den Veröffentlichungsprozess in der Reihenfolge für einen Kunden, die Verwendung von Code abgeschlossen haben, muss).
    -   Geben Sie an, wann die Werbecodes ablaufen sollen. Um ein spezifisches Ablaufdatum und eine frühere Ablaufzeit als sechs Monate zu wählen, deaktivieren Sie das Kontrollkästchen **Codes laufen nach 6 Monaten ab**.

4.  Klicken Sie auf **Codes bestellen**. Sie werden dann zurück auf die Seite **Werbecodes** geleitet, auf der Sie Ihre neue Bestellung in der Zusammenfassungstabelle der Werbecodebestellungen für diese App sehen.


## <a name="download-and-distribute-promotional-codes"></a>Herunterladen und Verteilen von Werbecodes

So laden Sie erfüllte Werbecodebestellungen herunter und verteilen die Codes an Kunden:

1.  Klicken Sie im linken Navigationsmenü der [Partner Center](https://partner.microsoft.com/dashboard), erweitern Sie **bewerben** , und wählen Sie dann **Angebotscodes.**
2.  Klicken Sie auf den Link zum **Herunterladen** Ihres Angebotscodes, und speichern Sie die Datei auf Ihrem Computer. Diese Datei enthält Informationen zu Ihrer Werbecodebestellung im TSV-Format (.tsv).
3.  Öffnen Sie die .tsv-Datei im Editor Ihrer Wahl. Öffnen Sie für ein optimales Ergebnis die .tsv-Datei in einer Anwendung, die Daten in tabellarischer Struktur anzeigen kann, z.B. Microsoft Excel. Allerdings können Sie die Datei auch in einem Text-Editor öffnen.

    Die Datei enthält Spalten mit den folgenden Daten für jeden Code:

    -   **Produktname**: Der Name der App oder des Add-Ons, dem der Code zugeordnet ist.
    -   **Bestellungsname**: Der Name der Bestellung, in der dieser Code erstellt wurde.
    -   **Werbecode**: Der Code selbst. Dies ist eine 5x5-Zeichenfolge von alphanumerischen Zeichen, die durch Bindestriche getrennt sind. Beispiel: DM3GY-M2GYM-6YMW6-4QHHT-23W2Z
    -   **Einlösbare URL**: Die URL, mit der ein Kunde den Code einlösen und die App bzw. das Add-On installieren kann. Die URL weist das folgende Format: http://go.microsoft.com/fwlink/?LinkId=532540&mstoken=&lt; Promotional_code >
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

Nachdem Sie einen werbecode (oder seine einlösbare URL) an Kunden verteilt haben, können sie die URL, um das Produkt kostenlos zu erhalten klicken. Durch das Klicken der einlösbaren URL wird eine authentifizierte Seite für die **Codeeinlösung** unter <https://account.microsoft.com/billing/redeem> geöffnet. Diese Seite enthält eine Beschreibung der App, für die der Benutzer den Code einlöst. Wenn der Kunde nicht mit seinem Microsoft-Konto angemeldet ist, kann er dazu aufgefordert werden. Ihre Kunden kann ebenfalls <https://account.microsoft.com/billing/redeem> besuchen und den Code direkt eingeben.

> [!IMPORTANT]
> Es wird empfohlen, dass Sie Werbecodes erst an Ihre Kunden verteilen, wenn Ihr Produkt den Veröffentlichungsprozess abgeschlossen hat (auch wenn Sie **Make this product available but not discoverable in the Store** ausgewählt haben). Kunden wird einen Fehler angezeigt, wenn sie versuchen, einen Werbecode für ein Produkt zu verwenden, das noch nicht veröffentlicht wurde.

Wenn der Kunde auf **Einlösen** klickt, wird die Übersicht der App im Microsoft Store geöffnet (auf einem Windows10- oder Windows8.1-Gerät). Dort kann er auf **Installieren** klicken, um die App kostenlos herunterzuladen und zu installieren. Wenn sich der Kunde an einem Computer oder einem Gerät befindet, auf dem Microsoft Store nicht installiert ist, öffnet der Link die Microsoft Store-Webseite für die App. Der Code wird auf das Microsoft-Konto des Kunden angewendet, damit er die App später kostenlos auf einem Windows-Gerät herunterladen kann (das mit dem gleichen Microsoft-Konto verknüpft ist).

> [!NOTE]
> In einigen Fällen kann ein Kunde eine Schaltfläche **kaufen** , anstatt Sie zu **Installieren**, finden Sie unter, obwohl die app erfolgreich über den werbecode eingelöst wurde. Der Kunde kann dann zum kostenlosen Installieren der App auf **Kaufen** klicken.


## <a name="review-your-promotional-codes"></a>Überprüfen der Werbecodes

Um eine ausführliche Zusammenfassung der werbecodebestellungen für Ihre apps und Add-ons zu überprüfen, navigieren Sie zur Seite **werbecodes** (im linken Navigationsmenü der Partner Center, erweitern Sie **bewerben** und wählen Sie dann die **Angebotscodes**). Sie können die folgenden detaillierten Informationen für Ihre aktuellen und inaktiven Werbecodes überprüfen:
-   Bestellungsname
-   App oder Add-On
-   Startdatum
-   Ablaufdatum
-   Verfügbar
-   Eingelöst

Sie können auch eine Bestellung aus dieser Tabelle [herunterladen](#download-and-distribute-promotional-codes).

 
