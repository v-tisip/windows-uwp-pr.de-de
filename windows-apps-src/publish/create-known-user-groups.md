---
author: JnHs
Description: "Enthält Informationen zum Erstellen von bekannten Benutzergruppen für Flight-Pakete und vieles mehr."
title: Erstellen bekannter Benutzergruppen
ms.author: wdg-dev-content
ms.date: 08/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Segment, Segmente, Zielgruppe, Kunden
ms.openlocfilehash: fc3986520e55ae0c636eb2db731df065463002b5
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="create-known-user-groups"></a>Erstellen bekannter Benutzergruppen

Mit bekannten Benutzergruppen können Sie bestimmte Kontakte zu einer Gruppe hinzufügen, indem Sie die E-Mail-Adresse deren Microsoft-Kontos verwenden. Diese bekannten Benutzergruppen werden am häufigsten mit [Flight-Paketen](package-flights.md) verwendet, um bestimmte Pakete an eine ausgewählte Gruppe von Kontakte zu verteilen. Sie können dazu verwendet werden, [benutzerorientierte Benachrichtigungen](send-push-notifications-to-your-apps-customers.md) oder [benutzerorientierte Angebote](use-targeted-offers-to-maximize-engagement-and-conversions.md) an eine spezifische Gruppe von Kunden als Teil einer Interaktionskampagne zu senden.

Um als Mitglied der Gruppe gezählt zu werden, muss jede Person mit dem Store mithilfe der E-Mail-Adresse des Microsoft-Kontos authentifiziert werden, die Sie bereitstellen. Für Flight-Pakete müssen sie [ein Windows10-Gerät verwenden, das Flight-Pakete unterstützt](package-flights.md), um die App herunterzuladen.


## <a name="to-create-a-known-user-group"></a>So erstellen Sie eine bekannte Benutzergruppe

1.  Erweitern Sie im Windows Dev Center-Dashboard **Einbeziehen** im linken Navigationsmenü und wählen Sie dann **Kundengruppen** aus. 
2.  Wählen Sie im Abschnitt **Meine Kundengruppen** die Option **Neue Gruppe erstellen**.
3.  Wählen Sie auf der nächsten Seite das Optionsfeld **Neue Benutzergruppe**.
4.  Geben Sie im Feld **Gruppennamen** einen Namen für die bekannte Benutzergruppe ein.
5.  Geben Sie die E-Mail-Adressen der Kontakte an, die Sie der Gruppe hinzufügen möchten. Sie müssen mindestens eine E-Mail-Adresse mit maximal 10.000 Kontakten hinzufügen. Geben Sie E-Mail-Adressen direkt in das Feld ein (getrennt durch Leerzeichen, Kommas, Semikolons oder Zeilenumbrüche), oder klicken Sie auf den Link **CSV importieren**, um die Test-Flight-Gruppe aus einer Liste von E-Mail-Adressen in einer CSV-Datei zu erstellen.
6. Wählen Sie **Speichern**.

Die Gruppe ist jetzt für die Verwendung verfügbar.

Sie können auch eine bekannte Benutzergruppe erstellen, indem Sie **Flight-Gruppe erstellen** aus der [Flight-Paket](package-flights.md) Seite für die Erstellung auswählen. Beachten Sie, dass Sie alle Informationen, die Sie bereits auf der Paketseite der Flight-Erstellung bereitgestellt haben, erneut eingeben müssen, wenn Sie dies durchführen.

> [!IMPORTANT]
> Wenn Sie bekannte Benutzergruppen mit Flight-Paketen verwenden, vergewissern Sie sich, dass Sie alle erforderlichen Einverständniserklärungen von den Personen eingeholt haben, die Sie Ihrer Test-Flight-Gruppe hinzufügen, und dass diese Personen sich bewusst sind, dass sie andere Pakete als die aus Ihrer Übermittlung ohne Test-Flight erhalten. 

## <a name="to-edit-a-known-user-group"></a>So bearbeiten Sie eine bekannte Benutzergruppe

Sie können keine bekannte Benutzergruppe aus Ihrem Dashboard entfernen (oder den Namen ändern), nachdem sie erstellt wurde, Sie können jedoch die Mitgliedschaft zu jedem beliebigen Zeitpunkt bearbeiten.

Um Ihre bekannten Benutzergruppen zu überprüfen und zu bearbeiten, erweitern Sie das Menü **Einbeziehen** im linken Navigationsmenü und wählen Sie **Kundengruppen** aus. Wählen Sie unter **Meine Kundengruppen** den Namen der Gruppe aus, die Sie bearbeiten möchten. Sie können ebenfalls eine bekannte Benutzergruppe in der Erstellungsseite für Flight-Pakete bearbeiten, indem Sie **Vorhandene Gruppen anzeigen und verwalten** beim Erstellen eines neuen Test-Flights auswählen oder den Namen der Test-Flight-Gruppe in der Übersicht eines Flight-Pakets auswählen. 

Nachdem Sie die Gruppe, die Sie bearbeiten möchten, ausgewählt haben, können Sie E-Mail-Adressen direkt in dem Feld hinzufügen oder daraus entfernen.

Wählen Sie für größere Änderungen **Export .csv** aus, um die Mitgliedschafts-Gruppeninformationen in einer CSV-Datei zu speichern. Nehmen Sie in dieser Datei Ihre Änderungen vor, und klicken Sie dann auf **CSV importieren**, um die Gruppenmitgliedschaft mit der neuen Version zu aktualisieren.

Beachten Sie, dass es bis zu 30Minuten dauern kann, bis Änderungen an der Mitgliedschaft implementiert werden. Wenn Sie nach der Veröffentlichung des Flight-Pakets Kontakte zu einer bekannten Benutzergruppe hinzufügen, werden die Pakete für die neuen Kontakte automatisch bereitgestellt. Sie müssen keine neue Übermittlung für das Flight-Paket erstellen und veröffentlichen. 






