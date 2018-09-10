---
author: JnHs
Description: Learn how to create customer segments so you can target a subset of your customer base for promotional or engagement purposes.
title: Erstellen von Kundensegmenten
ms.author: wdg-dev-content
ms.date: 07/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Segment, Segmente, Zielgruppe, Kunden
ms.assetid: 58185f6c-d61f-478b-ab24-753d8986cd5a
ms.localizationpriority: medium
ms.openlocfilehash: 4ec3bdd1d46927c9d6037906ebdb07e7a5c8f3f1
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3825940"
---
# <a name="create-customer-segments"></a>Erstellen von Kundensegmenten

Es gibt Situationen, in denen Sie sich für Werbungs- oder Interaktionszwecke an einen Teil Ihrer Kunden wenden möchten. Hierzu können Sie in Windows Dev Center eine Art von [Kundengruppe](create-customer-groups.md) erstellen, die als *Segment* bezeichnet wird und die Windows10-Kunden enthält, die den von Ihnen gewählten demografischen oder Umsatzkriterien entsprechen.

So könnten Sie beispielsweise ein Segment erstellen, das nur Kunden ab einem Alter von 50Jahren enthält, oder eines mit Kunden, die im Microsoft Store mehr als 10€ ausgegeben haben. Sie könnten diese Kriterien auch miteinander kombinieren und so ein Segment mit allen Kunden über 50Jahren erstellen, die im Store mehr als 10Euro ausgegeben haben. 

Wir stellen Ihnen für den Anfang einige Segmentvorlagen zur Verfügung. Sie können die Kriterien jedoch ganz nach Ihren Wünschen definieren und miteinander kombinieren.

> [!TIP]
> Segmente können dazu verwendet werden, [benutzerorientierte Benachrichtigungen](send-push-notifications-to-your-apps-customers.md) oder [benutzerorientierte Angebote](use-targeted-offers-to-maximize-engagement-and-conversions.md) an eine Gruppe von Kunden als Teil einer Interaktionskampagne zu senden.

Wichtige Punkte zu Kundensegmenten:
- Nach dem Speichern eines Segments dauert es 24Stunden, bis Sie es für [benutzerorientierte Pushbenachrichtigungen](send-push-notifications-to-your-apps-customers.md) verwenden können.
- Segmentergebnisse werden täglich aktualisiert, damit Sie die Gesamtanzahl der Kunden im Rahmen der täglichen Segmentänderungen sehen können, während Kunden neu die Segmentkriterien erfüllen oder sie nicht mehr erfüllen.
- Die meisten dieser Segmente werden auf der Grundlage aller historischen Daten berechnet, es gibt jedoch einige Ausnahmen. So sind etwa **App-Kaufdatum**, **Kampagnen-ID**, **Anzeigedatum der Store-Seite** und **Verweiser-URI-Domäne** auf die Daten der letzten 90Tage eingeschränkt.
- Segmente enthalten nur Kunden, die Ihre App auf Windows10 erworben hatten, während sie mit einem gültigen Microsoft-Konto angemeldet waren. 
- Segmente schließen alle Kunden aus, die jünger als 17Jahre sind.

## <a name="to-create-a-customer-segment"></a>So erstellen Sie ein Kundensegment

1.  Erweitern Sie im Windows Dev Center-Dashboard **Einbeziehen** im linken Navigationsmenü und wählen Sie dann **Kundengruppen** aus.
2.  Führen Sie auf der Seite **Kundengruppen** eine der folgenden Aktionen aus:
 - Wählen Sie im Abschnitt **Meine Kundengruppen** die Option **Neue Gruppe erstellen**, um ein neues Segment zu definieren. Wählen Sie auf der nächsten Seite das Optionsfeld **Segment**.
 - Wählen Sie im Abschnitt **Segmentvorlagen** die Option **Kopieren** neben dem vordefinierten Segment aus (um ein vordefiniertes Segment unverändert zu verwenden oder an Ihre Anforderungen anzupassen).
3.  Geben Sie im Feld **Gruppennamen** einen Namen für Ihr Segment ein.
4.  Wählen Sie in der Liste **Kunden von dieser App einschließen** eine Ihrer Apps als Ziel aus.
5.  Wählen Sie im Abschnitt **Einschlusskriterien festlegen** die Filterkriterien für das Segment.

    Sie können aus einer Vielzahl von Filterkriterien wählen, einschließlich **Erwerb**, **Kaufquelle**, **Nutzung**, **Demografie**, **Bewertung**, **Änderungsumfang-Vorhersage**, **Store-Erwerb**, **Store-Käufe** und **Store-Ausgaben**.

    Wenn Sie zum Beispiel ein Segment erstellen möchten, das nur Ihre App-Kunden zwischen 18 und 24Jahren enthält, wählen Sie in den Dropdownlisten die Filterkriterien [**Demografie**] [**Altersgruppe**] [**ist**] [**18 bis 24**] aus.

    Mit UND/ODER-Abfragen können Sie komplexere Segmente erstellen, bei denen Kunden auf der Grundlage verschiedener Attribute ein- oder ausgeschlossen werden. Wählen Sie für eine OR-Abfrage **+ OR-Anweisung**. Wählen Sie zum Hinzufügen einer ADD-Abfrage **Einen anderen Filter hinzufügen** aus.

    Wenn Sie also Ihr Segment so verfeinern möchten, dass es nur männliche Kunden im angegebenen Altersbereich enthält, wählen Sie **Einen anderen Filter hinzufügen** und dann die zusätzlichen Filterkriterien [**Demografie**] [**Geschlecht**] [**ist**] [**Männlich**] aus. Bei diesem Beispiel zeigt die **Segmentdefinition** an: **Altersgruppe == 18 bis 24 && Geschlecht == Männlich**.

    ![Beispiel für die Filterkriterien für ein Segment](images/create-segment-inclusions.png)
6. Wählen Sie **Speichern** aus.

> [!IMPORTANT]
> Ein Segment, das zu wenige Kunden enthält, kann nicht verwendet werden. Wenn Ihre Segmentdefinition nicht genug Kunden enthält, können Sie die Segmentkriterien anpassen oder es später erneut versuchen, wenn Ihre App möglicherweise mehr Kunden akquiriert hat, die Ihren Segmentkriterien entsprechen.


## <a name="app-statistics"></a>App-Statistik

Der Abschnitt **App-Statistik** für das Segment enthält einige Informationen zu Ihrer App sowie die Größe des Segments, das Sie soeben erstellt haben.

Beachten Sie, dass **Verfügbare App-Kunden** nicht die tatsächliche Anzahl von Kunden wiedergibt, die Ihre App erworben haben, sondern nur die Anzahl der Kunden, die für die Segmente verfügbar sind (d.h. Kunden, die den Altersbedingungen entsprechen, Ihre App unter Windows10 erworben haben und über ein gültiges Microsoft-Konto verfügen).

Wenn Sie die Ergebnisse anzeigen und der Bereich **Kunden in diesem Segment** die Information **Klein** anzeigt, enthält das System nicht genügend Kunden und wird als inaktiv markiert. Inaktive Segmente können nicht für Benachrichtigungen oder andere Funktionen verwendet werden. Möglicherweise können Sie auf folgende Weise ein Segment aktivieren und verwenden:

- Passen Sie in **Einschlusskriterien festlegen** die Filterkriterien so an, dass das Segment mehr Kunden enthält.
- Wählen Sie auf der Seite **Kundengruppen** im Abschnitt **inaktive Segmente** die Option **Aktualisieren** aus, um zu sehen, ob das Segment jetzt genug Kunden enthält (z.B. ob mehr Kunden, die Ihren Segmentkriterien entsprechen, Ihre App heruntergeladen haben, seit Sie das Segment erstellt haben oder vorhandenen Kunden jetzt Ihren Segmentkriterien entsprechen).
