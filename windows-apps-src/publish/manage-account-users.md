---
author: jnHs
Description: "Fügen Sie Ihrem Dev Center-Konto Benutzer hinzu, und weisen Sie diesen Rollen mit bestimmten Berechtigungen zu."
title: Verwalten von Kontobenutzern
ms.assetid: 9245F0D0-7D8F-4741-AFB4-FBA5601D0A9B
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 7eaddcfc2d02805e60043132328ef482872a9000
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="manage-account-users"></a>Verwalten von Kontobenutzern


Sie können mit Azure Active Directory Ihrem Dev Center-Konto Benutzer hinzufügen. Jedem Benutzer wird eine Rolle zugewiesen, mit der er bestimmte Berechtigungen für das Konto erhält. Sie können eine Rolle auch einer Gruppe von Benutzern oder einer Azure AD-App zuweisen.

> **Wichtig**  Zum Hinzufügen und Verwalten von Kontobenutzern müssen Sie zunächst Ihr Dev Center-Konto dem Azure Active Directory Ihres Unternehmens zuordnen. Dazu müssen Sie sich bei Azure AD mit einem [globalen Administratorkonto](http://go.microsoft.com/fwlink/?LinkId=746654) anmelden. Nachdem Sie diese Zuordnung festgelegt haben, können Sie sie erst nach Rücksprache mit dem Support wieder entfernen.

## <a name="associate-your-dev-center-account-with-your-organizations-azure-active-directory"></a>Zuordnen Ihres Dev Center-Kontos zum Azure Active Directory des Unternehmens

Windows Dev Center nutzt Azure Active Directory zum Verwalten mehrerer Benutzer und zum Zuweisen von Rollen. Wenn in Ihrer Organisation bereits mit Office 365 oder Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie schon über Azure AD. Andernfalls können Sie innerhalb von Dev Center ohne zusätzliche Kosten ein neues Azure AD erstellen.

Beachten Sie, dass einem Azure AD jeweils nur ein Dev Center-Konto zugeordnet werden kann. Ebenso kann einem Dev Center-Konto auch nur eine Azure AD zugeordnet werden.

> **Hinweis**   Wenn Sie Benutzer hinzufügen möchten, die sich nicht in der Azure AD Ihrer Organisation befinden, Sie jedoch keine neue Azure AD-Konten für diese Benutzer erstellen möchten, dann können Sie die [Benutzer per E-Mail einladen](#add-and-manage-account-users).

### <a name="associate-your-dev-center-account-with-your-organizations-existing-azure-ad"></a>Zuordnen Ihres Dev Center-Kontos zur vorhandenen Azure AD Ihrer Organisation

Wenn Ihre Organisation Azure AD bereits verwendet, gehen Sie folgendermaßen vor, um Ihr Dev Center-Konto zu verknüpfen.

1.  Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.
2.  Klicken Sie auf die **Schaltfläche zum Zuordnen Ihres Dev Center-Kontos zu Azure AD**.
3.  Melden Sie sich bei Ihrem AzureAD-Konto an. Dieses Konto muss über Berechtigungen des [globalen Administrators](http://go.microsoft.com/fwlink/?LinkId=746654) verfügen, damit die Zuordnung eingerichtet werden kann.
4.  Überprüfen Sie den Organisations- und den Domänennamen für das Azure AD-Konto. Klicken Sie zum Abschließen der Zuordnung auf **Bestätigen**.
5.  Wenn die Zuordnung erfolgreich abgeschlossen wurde, können Sie nun auf der Seite **Benutzer verwalten** Ihres Kontos Kontobenutzer hinzufügen und verwalten wie in den folgenden Abschnitten beschrieben.

### <a name="create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account"></a>Erstellen eines völlig neuen Azure AD, um diesem Ihr Dev Center-Konto zuzuordnen

Wenn Sie ein neues Azure AD einrichten müssen, um diesem Ihr Dev Center-Konto zuzuordnen, gehen Sie folgendermaßen vor.

1.    Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.
2.    Klicken Sie auf die Schaltfläche **Neues Azure AD erstellen**.
3.    Geben Sie die Verzeichnisinformationen für das neue Azure AD ein:
 - **Domänenname**: Der eindeutige Name, der für Ihre Azure AD-Domäne verwendet wird, zusammen mit „.onmicrosoft.com“. Wenn Sie beispielsweise „beispiel“ eingegeben haben, wäre Ihre Azure AD-Domäne „beispiel.onmicrosoft.com“.
 - **Kontakt-E-Mail-Adresse**: Eine E-Mail-Adresse, unter der wir Sie hinsichtlich Ihres Kontos erreichen können, wenn notwendig.
 - **Benutzerkontoinformationen für den globalen Administrator**: Vorname, Nachname, Benutzername und Kennwort, die Sie für das neue Administratorkonto verwenden möchten.
4.    Klicken Sie auf **Erstellen**, um die neue Domäne und die Kontoinformationen zu bestätigen.
5.    Melden Sie sich mit dem neuen Azure AD-Benutzernamen und -Kennwort als globaler Administrator an, um auf der Seite **Benutzer verwalten** zusätzliche Kontobenutzer hinzuzufügen und zu verwalten, wie in den folgenden Abschnitten beschrieben.


> **Wichtig**  Nachdem Sie Ihr Dev Center-Konto dem Azure AD zugeordnet haben, müssen Sie sich am Dev Center stets mithilfe des globalen Azure AD-Administratorkontos (und nicht mit einem persönlichen Microsoft-Konto) anmelden, um Kontobenutzer hinzuzufügen und zu verwalten.

## <a name="add-and-manage-account-users-groups-and-azure-ad-applications"></a>Hinzufügen und Verwalten von Kontobenutzern, Gruppen und Azure AD-Anwendungen

Nachdem Sie die Zuordnung hergestellt haben, können Sie Ihrem Konto Benutzer, Gruppen und Azure AD-Apps hinzufügen. Sie können auch Rollen ändern, Kontodetails bearbeiten und Benutzer entfernen.

> **Hinweis**  Wenn Ihre Organisation die [Verzeichnisintegration](http://go.microsoft.com/fwlink/p/?LinkID=724033) zum Synchronisieren des lokalen Verzeichnisdiensts mit AzureAD verwendet, können Sie in DevCenter keine neuen Benutzer, Gruppen oder AzureAD-Anwendungen erstellen. Sie (oder ein anderer Administrator in Ihrem lokalen Verzeichnis) müssen sie direkt im lokalen Verzeichnis erstellen, bevor sie in DevCenter angezeigt und hinzugefügt werden können.

Beachten Sie beim Verwalten von Benutzern Folgendes:

-   Alle Dev Center-Benutzer müssen über ein aktives Konto im Azure AD Ihrer Organisation verfügen.
-   Beim Erstellen **neuer** Benutzer oder Gruppen in Dev Center werden diese auch dem Azure AD Ihrer Organisation hinzugefügt.
-   Wenn Sie den Namen eines Benutzers oder einer Gruppe in Dev Center ändern, werden diese Änderungen auch im Azure AD der Organisation vorgenommen.
-   Benutzer (einschließlich von Gruppen und Azure AD-Anwendungen) können mit den Berechtigungen für ihre jeweils zugewiesene Rolle auf das gesamte Dev Center-Konto zugreifen. Wenn Sie [Berechtigungen anpassen](set-custom-permissions-for-account-users.md), können Sie den Zugriff für Benutzer einschränken, so dass sie nur mit bestimmten Apps und/oder Add-Ons arbeiten können.
-   Sie können einem Benutzer, einer Gruppe oder einer Azure AD-Anwendung den Zugriff auf die Funktionen mehrerer Rollen gewähren, indem Sie mehrere Rollen auswählen oder indem Sie mithilfe [benutzerdefinierter Berechtigungen](set-custom-permissions-for-account-users.md) den Zugriff gewähren, den Sie ihnen geben möchten.
-   Ein Benutzer mit einer bestimmten Rolle (oder einer Reihe [benutzerdefinierter Berechtigungen](set-custom-permissions-for-account-users.md)) kann auch Teil einer Gruppe mit einer anderen Rolle (oder einem anderen Satz von Berechtigungen) sein. In diesem Fall hat der Benutzer Zugriff auf alle Funktionen, die mit der Gruppe und dem individuellen Konto verbunden sind.

## <a name="roles-and-permissions"></a>Rollen und Berechtigungen

Wenn Sie einen Benutzer, eine Gruppe oder eine Azure AD-Anwendung hinzufügen, müssen Sie deren Berechtigungen angeben. Sie können diesen dazu eine **Standardrolle** zuweisen oder [ihre Berechtigungen anpassen](set-custom-permissions-for-account-users.md).

Sofern Sie keine benutzerdefinierten Berechtigungen verwenden, müssen alle Benutzer, Gruppen oder Azure AD-Anwendungen, die Sie einem Konto hinzufügen, mindestens einer der folgenden Standardrollen zugewiesen sein. Jede Rolle verfügt über spezifische Berechtigungen, mit denen bestimmte Funktionen innerhalb des Kontos ausgeführt werden können. 

> **Hinweis**  Der Besitzer des Kontos ist die Person, die es als erste mit einem Microsoft-Konto erstellt hat (und keiner der Benutzer, die über Azure AD hinzugefügt wurden). Dieser Kontobesitzer ist die einzige Person mit Vollzugriff auf das Konto. Hierzu zählt die Möglichkeit, Apps zu löschen, zu erstellen und zu bearbeiten, alle Kontobenutzer zu bearbeiten sowie sämtliche finanziellen Einstellungen und Kontoeinstellungen zu ändern. 

| Rolle                 | Beschreibung              |
|----------------------|--------------------------|
| Manager              | Verfügt über vollständigen Zugriff auf das Konto, kann jedoch keine Steuer- und Auszahlungseinstellungen ändern. Dies umfasst das Verwalten von Benutzern in Dev Center. Beachten Sie jedoch, dass die Fähigkeit zum Erstellen und Löschen von Benutzern von den Berechtigungen des Kontos in Azure AD abhängig ist. Das heißt, wenn einem Benutzer die Manager-Rolle zugewiesen ist, er jedoch nicht über Administratorberechtigungen im Azure AD der Organisation verfügt, kann er keine neuen Benutzer erstellen oder Benutzer aus dem Verzeichnis löschen (er kann jedoch die Dev Center-Rolle eines Benutzers ändern). |
| Entwickler            | Kann Pakete hochladen und Apps und Add-Ons einreichen sowie den [Nutzungsbericht](usage-report.md) für Telemetriedetails einsehen. Kann keine finanziellen Informationen oder Kontoeinstellungen anzeigen.   |
| Mitwirkender im Geschäftsbereich | Kann [Integritäts](health-report.md)- und [Nutzungs](usage-report.md)-Berichte anzeigen. Kann keine Produkte erstellen oder übermitteln, Kontoeinstellungen ändern oder finanzielle Informationen anzeigen.                                         |
| Mitwirkender im Finanzbereich  | Kann [Auszahlungsberichte](payout-summary.md), finanzielle Informationen und Erwerbsberichte anzeigen. Kann keine Änderungen an Apps, Add-Ons oder Kontoeinstellungen vornehmen.                                                                                                                                   |
| Händler             | Kann auf [Kundenbewertungen reagieren](respond-to-customer-reviews.md) und nicht finanzbezogene [Analyseberichte](analytics.md) einsehen. Kann keine Änderungen an Apps, Add-Ons oder Kontoeinstellungen vornehmen.      |

In der nachfolgenden Tabelle sind einige der spezifischen Features aufgeführt, die für diese Rollen (und für den Kontobesitzer) verfügbar sind.

|                                 |    Kontobesitzer                 |    Manager                       |    Entwickler                     |    Mitwirkender im Geschäftsbereich    |    Mitwirkender im Finanzbereich    |    Händler                      |
|---------------------------------|----------------------------------|----------------------------------|----------------------------------|----------------------------|---------------------------|----------------------------------|
|    Erwerbsbericht           |    Kann anzeigen                      |    Kann anzeigen                      |     Kein Zugriff                    |     Kein Zugriff              |    Kann anzeigen               |    Kein Zugriff                     |
|    Feedbackbericht/Antworten    |    Kann Feedback anzeigen und senden    |    Kann Feedback anzeigen und senden    |    Kann Feedback anzeigen und senden    |     Kein Zugriff              |     Kein Zugriff             |    Kann Feedback anzeigen und senden    |
|    Integritätsbericht                |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                |     Kein Zugriff             |    Kein Zugriff                     |
|    Nutzungsbericht                 |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                |     Kein Zugriff             |    Kein Zugriff                     |
|    Auszahlungskonto               |    Kann aktualisieren                    |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |
|    Steuerprofil                  |    Kann aktualisieren                    |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |
|    Auszahlungsübersicht               |    Kann anzeigen                      |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |

Wenn keine der standardmäßigen Rollen geeignet ist oder wenn Sie den Zugriff auf bestimmte Apps und/oder Add-Ons einschränken möchten, können Sie benutzerdefinierte Berechtigungen für den Benutzer gewähren, indem Sie auf **Berechtigungen anpassen** klicken. Weitere Informationen finden Sie unter [Festlegen benutzerdefinierter Berechtigungen für Kontenbenutzer](set-custom-permissions-for-account-users.md).

## <a name="add-and-manage-account-users"></a>Hinzufügen und Verwalten von Kontobenutzern

Klicken Sie zum Angeben von Benutzern, die Sie Ihrem Dev Center-Konto hinzufügen und denen Sie eine Rolle zuweisen möchten, auf **Benutzer hinzufügen**.

Sie können einen oder mehrere Benutzer aus dem Verzeichnis Ihrer Organisation dem Dev Center-Konto hinzufügen. Wenn Sie mehrere Benutzer gleichzeitig hinzufügen, müssen Sie ihnen die gleiche Rolle zuweisen. Wenn Sie Benutzer hinzufügen, ihnen jedoch unterschiedliche Rollen zuweisen möchten, wiederholen Sie die folgenden Schritte für jede Rolle.

Sie können auch Benutzer zum Zugriff auf Ihr Konto einladen, ohne sie zum Verzeichnis Ihrer Organisation hinzuzufügen.

**Hinzufügen von Benutzern aus dem Verzeichnis Ihrer Organisation**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Wählen Sie in der angezeigten Liste einen oder mehrere Benutzer aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
3.  Wenn Sie die Benutzer ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die dieser Gruppe von Benutzern zugewiesen werden sollen.
5.  Klicken Sie auf **Speichern**.

Wenn Sie einem völlig neuen Benutzerkonto Zugriff auf Dev Center gewähren möchten, können Sie im Abschnitt **Benutzer verwalten** ein Konto erstellen. 

Standardmäßig ist das Optionsfeld **Zu Azure AD hinzufügen** aktiviert. Wenn Sie dieses aktiviert lassen, wird ein neues Konto im Verzeichnis Ihrer Organisation erstellt und der betreffende Benutzer Ihrem Dev Center-Konto hinzugefügt. Wenn Sie keine neuen Konten im Verzeichnis Ihrer Organisation erstellen möchten, Benutzer aber mit ihren Microsoft-Konten auf Ihr Konto zugreifen können sollen, wählen Sie stattdessen **Benutzer per E-Mail einladen**.

Wenn der neue Benutzer ein [Konto als globaler Administrator](http://go.microsoft.com/fwlink/p/?LinkId=746654) im Verzeichnis Ihrer Organisation haben soll, markieren Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator mit vollständiger Kontrolle über alle Verzeichnisressourcen machen**. Dadurch erhält der Benutzer den vollständigen Zugriff auf alle administrativen Features im Azure AD Ihrer Organisation. Er kann dann Benutzer im Verzeichnis Ihrer Organisation hinzufügen und verwalten (jedoch nicht in Dev Center, sofern Sie dem Konto nicht die dazu erforderliche(n) [Rolle/Berechtigungen](#roles-and-permissions) zuweisen. Wenn Sie dieses Kontrollkästchen markieren, müssen Sie eine **E-Mail-Adresse zur Kennwortwiederherstellung** für den Benutzer angeben.

**Erstellen eines neuen Benutzerkontos in Dev Center und im Verzeichnis Ihrer Organisation**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neuer Benutzer**.
3.  Stellen Sie sicher, dass das Optionsfeld **Zu Azure AD hinzufügen** aktiviert ist.
4.  Geben Sie den Vornamen, den Nachnamen und den Benutzernamen für den neuen Benutzer ein.
5.  Geben Sie eine E-Mail-Adresse an, die der Benutzer verwenden kann, um sein Kennwort wiederherzustellen. Dies ist nur erforderlich, wenn Sie das Kontrollkästchen ***Diesen Benutzer in Azure AD zum globalen Administrator machen** markiert haben.
6.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die dem neuen Benutzer zugewiesen werden sollen, oder weisen Sie angepasste Berechtigungen zu.
7.  Wählen Sie im Abschnitt **Gruppenmitgliedschaft** alle Gruppen aus, denen der neue Benutzer angehören soll.
8.  Klicken Sie auf **Speichern**.
9.  Auf der Bestätigungsseite werden die Anmeldedaten für den neuen Benutzer angezeigt, z.B. ein temporäres Kennwort. Notieren Sie sich diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.

**Erstellen eines neuen Benutzerkontos in Dev Center, ohne den Benutzer zum Verzeichnis Ihrer Organisation zuzuweisen**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neuer Benutzer**.
3.  Markieren Sie das Optionsfeld **Benutzer per E-Mail einladen**.
3.  Geben Sie eine oder mehrere E-Mails Adressen (bis zu zehn) mit Kommata oder Semikola als Trennzeichen ein.
4.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die dem neuen Benutzer zugewiesen werden sollen, oder weisen Sie angepasste Berechtigungen zu.
6.  Klicken Sie auf **Speichern**.

Die Benutzer, die Sie eingeladen haben, erhalten eine E-Mail-Nachricht mit einer Einladung zum Zugriff auf Ihr Dev Center-Konto. Jeder Benutzer muss die Einladung annehmen, bevor er auf Ihr Konto zugreifen kann. Um die Einladung erneut zu senden, suchen Sie den Benutzer auf Ihrer **Benutzer verwalten**-Seite und klicken Sie auf seine E-Mail-Adresse (oder auf den Text **Einladung ausstehend**), um das Konto zu bearbeiten. Klicken Sie dann am unteren Rand der Seite, auf **Einladung senden**.

Änderungen an den Benutzerkonten, die Sie Ihrem Dev Center-Konto hinzugefügt haben, können Sie im Abschnitt **Benutzer verwalten** vornehmen. Beachten Sie, dass Änderungen des Benutzernamens oder der Gruppenmitgliedschaft des Benutzers im Verzeichnis der Organisation und nicht nur im Dev Center-Konto widergespiegelt werden. Änderungen an der Rolle eines Benutzers wirken sich nur auf dessen jeweiligen Dev Center-Zugriff aus.

**Bearbeiten eines Benutzerkontos**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Benutzerkontos, das bearbeitet werden soll.
2.  Sie können die folgenden Änderungen vornehmen:
    -   Bearbeiten Sie den Vornamen, den Nachnamen oder den Benutzernamen des Benutzers. Diese Änderungen werden im Verzeichnis Ihrer Organisation vorgenommen.
    -   Aktivieren bzw. deaktivieren Sie im Abschnitt **Rollen** die Rolle(n), die Sie für diesen Benutzer hinzufügen oder entfernen möchten, oder weisen Sie ihm angepasste Berechtigungen zu.
    -   Aktivieren bzw. deaktivieren Sie im Abschnitt **Gruppenmitgliedschaft** die Gruppe(n), denen der Benutzer beitreten bzw. aus denen der Benutzer entfernt werden soll. Diese Änderungen werden im Verzeichnis Ihrer Organisation vorgenommen.

3.  Klicken Sie auf **Speichern**.

Wenn Sie das Kennwort für ein Benutzerkonto ändern müssen, das Sie dem Dev Center-Konto hinzugefügt haben, können Sie die notwendigen Schritte im Abschnitt **Benutzer verwalten** ausführen. Dadurch wird das Verzeichniskennwort des Benutzers und nicht nur sein Kennwort für den Dev Center-Zugriff geändert.

**Ändern des Verzeichniskennworts eines Benutzers**

Wenn Sie bei der Erstellung des Benutzerkontos eine **E-Mail-Adresse zur Kennwortwiederherstellung** angegeben haben, kann der Benutzer sein eigenes Kennwort zurücksetzen. Sie können das Kennwort eines Benutzers auch aktualisieren, indem Sie die folgenden Schritte befolgen.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Benutzerkontos, das bearbeitet werden soll.
2.  Klicken Sie am unteren Rand der Seite auf die Schaltfläche **Kennwort zurücksetzen**.
3.  Auf einer Bestätigungsseite werden die Anmeldeinformationen für den Benutzer angezeigt, einschließlich eines temporären Kennworts.

   > **Wichtig**  Drucken oder kopieren Sie diese Informationen, und stellen Sie sie dem neuen Benutzer bereit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.

## <a name="add-and-manage-groups"></a>Hinzufügen und Verwalten von Gruppen

Wenn Sie dem Dev Center-Konto eine Gruppe aus dem Verzeichnis der Organisation hinzufügen, kann jeder Benutzer, der Mitglied dieser Gruppe ist, mit den Berechtigungen für die der Gruppe zugewiesenen Rolle darauf zugreifen. Beachten Sie, dass alle an Gruppen vorgenommenen Änderungen (u.a. Änderungen von Name oder Mitgliedschaft) im Verzeichnis der Organisation widergespiegelt werden.

Wenn Sie mehrere Gruppen gleichzeitig hinzufügen, müssen Sie ihnen die gleiche Rolle zuweisen. Wenn Sie Gruppen hinzufügen, ihnen jedoch unterschiedliche Rollen zuweisen möchten, wiederholen Sie die folgenden Schritte für jede Rolle.

**Hinzufügen von Gruppen aus dem Verzeichnis der Organisation**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Gruppen hinzufügen**.
2.  Wählen Sie in der angezeigten Liste eine oder mehrere Gruppen aus. Im Suchfeld können Sie nach bestimmten Gruppen suchen.
3.  Wenn Sie die Gruppen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die diesen Gruppen zugewiesen werden sollen, oder weisen Sie angepasste Berechtigungen zu.
5.  Klicken Sie auf **Speichern**.

Wenn Sie einer völlig neuen Gruppe den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer verwalten** eine neue Gruppe erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation eine neue Gruppe erstellt wird.

**Erstellen eines neuen Gruppenkontos**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Gruppen hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neue Gruppe**.
3.  Geben Sie den Anzeigenamen für die neue Gruppe ein.
4.  Wählen Sie eine oder mehrere Rollen aus, die der neuen Gruppe zugewiesen werden sollen, oder weisen Sie benutzerdefinierte Berechtigungen zu. Alle Mitglieder der Gruppe können mit den Berechtigungen für die betreffende Rolle auf Ihr Dev Center-Konto zugreifen.
5.  Wählen Sie in der angezeigten Liste einen oder mehrere Benutzer aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
6.  Wenn Sie die Benutzer ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
7.  Klicken Sie auf **Speichern**.

Änderungen an den Gruppenkonten, die Sie Ihrem Dev Center-Konto hinzugefügt haben, können Sie im Abschnitt **Benutzer verwalten** vornehmen. Beachten Sie, dass Änderungen des Gruppennamens oder der Gruppenmitgliedschaft im Verzeichnis der Organisation und nicht nur im Dev Center-Konto widergespiegelt werden. Änderungen an der Rolle einer Gruppe wirken sich nur auf den Dev Center-Zugriff der Gruppe aus.

**Bearbeiten eines Gruppenkontos**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Gruppenkontos, das bearbeitet werden soll.
2.  Nehmen Sie zum Bearbeiten der Gruppeninformationen die gewünschten Änderungen am Gruppennamen vor. Diese Änderungen werden im Verzeichnis Ihrer Organisation vorgenommen.
3.  Wenn Sie die Gruppenrolle ändern möchten, aktivieren bzw. deaktivieren Sie die Rolle(n), die auf die Gruppe angewendet werden sollen, oder weisen Sie angepasste Berechtigungen zu.
4.  Klicken Sie auf **Speichern**.

## <a name="add-and-manage-azure-ad-applications"></a>Hinzufügen und Verwalten von Azure AD-Anwendungen

Sie können Anwendungen oder Diensten, die Teil der Azure AD-Instanz Ihrer Organisation sind, den Zugriff auf Ihr Dev Center-Konto gewähren.

Wenn Sie mehrere Azure AD-Apps gleichzeitig hinzufügen, müssen Sie ihnen die gleiche Rolle zuweisen. Wenn Sie Gruppen hinzufügen, ihnen jedoch unterschiedliche Rollen zuweisen möchten, wiederholen Sie die folgenden Schritte für jede Rolle.

**Hinzufügen von Azure AD-Apps aus Verzeichnis der Organisation**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**.
2.  Wählen Sie eine oder Azure AD-Anwendungen aus der angezeigten Liste aus. Mithilfe des Suchfelds können Sie nach bestimmten Azure AD-Apps suchen.
3.  Wenn Sie die Azure AD-Apps ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die diesen Azure AD-Anwendungen zugewiesen werden sollen, oder weisen Sie angepasste Berechtigungen zu.
5.  Klicken Sie auf **Speichern**.

Wenn Sie einem völlig neuen Azure AD-Anwendungskonto den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer verwalten** ein neues Konto erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation ein neues Konto erstellt wird.

> **Tipp** Wenn Sie diese Azure AD-Anwendung hauptsächlich für die Dev Center-Authentifizierung verwenden, und Benutzer nicht direkt auf sie zugreifen müssen, können Sie für die **Antwort-URL** und **App-ID-URI** jede beliebige gültige Adresse eingeben, solange diese Werte nicht von einer anderen Azure AD-Anwendung in Ihrem Verzeichnis verwendet werden.

**Erstellen einer neuen Azure AD-Anwendung**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **New Azure AD application**.
3.  Geben Sie die **Antwort-URL** für die neue Azure AD-App ein. Dies ist die URL, mit der sich Benutzer anmelden und Ihre Azure AD-App verwenden können (wird auch als App-URL oder Anmelde-URL bezeichnet). Die **Antwort-URL** darf nicht mehr als 256 Zeichen enthalten.
4.  Geben Sie den **App-ID-URI** für die neue Azure AD-App ein. Dies ist ein logischer Bezeichner für die Azure AD-App, der beim Senden einer Anforderung für einmaliges Anmelden an Azure AD angezeigt wird. Beachten Sie, dass der **App-ID-URI** für jede Azure AD-App im Verzeichnis eindeutig sein muss und nicht mehr als 256 Zeichen enthalten darf.
5.  Wählen Sie im Abschnitt **Rollen** eine oder mehrere Rollen aus, die der neuen Azure AD-Anwendung zugewiesen werden sollen, oder weisen Sie angepasste Berechtigungen zu.
6.  Klicken Sie auf **Speichern**.

Nachdem Sie eine Azure AD-Anwendung hinzugefügt oder erstellt haben, können Sie zum Abschnitt **Verwalten von Benutzern** zurückkehren und auf den Namen der Anwendung klicken, um die Einstellungen für die Anwendung zu überprüfen, einschließlich Mandanten-ID, Client-ID, Antwort-URL und App-ID-URI.

> **Hinweis** Wenn Sie beabsichtigen, die REST-APIs zu verwenden, die von den [Windows Store-Diensten](../monetize/using-windows-store-services.md) bereitgestellt werden, benötigen Sie die die auf dieser Seite angezeigten Werte für die Mandanten-ID und die Client-ID, um ein Azure AD-Zugriffstoken abzurufen, das Sie für die Authentifizierung der Aufrufe von Diensten verwenden können.   

Änderungen an Azure AD-Apps, die Sie Ihrem Dev Center-Konto hinzugefügt haben, können Sie im Abschnitt **Benutzer verwalten** vornehmen. Beachten Sie, dass Änderungen der Antwort-URL und des App-ID-URI im Verzeichnis der Organisation und nicht nur im Dev Center-Konto widergespiegelt werden. Rollenänderungen wirken sich nur auf die Berechtigungen der Azure AD-App in Dev Center aus.

**Bearbeiten einer Azure AD-App**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Azure AD-Anwendungskontos, das bearbeitet werden soll.
2.  Geben Sie zum Ändern der **Antwort-URL** oder des **App-ID-URI** die neuen Werte hier ein. Diese Änderungen werden im Verzeichnis Ihrer Organisation vorgenommen.
3.  Wenn Sie die Rolle einer Azure AD-Anwendung ändern möchten, aktivieren bzw. deaktivieren Sie die Rolle(n), die angewendet werden sollen, oder weisen Sie angepasste Berechtigungen zu.
4.  Klicken Sie auf **Speichern**.

Wenn die Azure AD-Anwendung Daten in Microsoft Azure AD liest und schreibt, benötigt sie einen Schlüssel. Sie können Schlüssel für eine Azure AD-App erstellen, indem Sie ihre Informationen in Dev Center bearbeiten. Sie können auch Schlüssel entfernen, die nicht mehr benötigt werden.

**Verwalten von Schlüsseln für eine Azure AD-App**

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen der Azure AD-App.

    > **Tipp**  Wenn Sie auf den Namen der Azure AD-App klicken, werden Ihnen alle aktiven Schlüssel für die Azure AD-App mit dem jeweiligen Erstellungs- und Ablaufdatum des Schlüssels angezeigt. Klicken Sie auf **Entfernen**, um einen nicht mehr benötigten Schlüssel zu entfernen.

2.  Klicken Sie auf **Add new key**, um einen neuen Schlüssel hinzuzufügen.

3.  Es wird ein Bildschirm mit den Werten für **Client-ID** und **Schlüssel** angezeigt.

    > **Wichtig**  Drucken oder kopieren Sie diese Informationen, da Sie nach dem Verlassen dieser Seite nicht mehr auf diese zugreifen können.

4.  Klicken Sie auf **Weiteren Schlüssel hinzufügen**, wenn Sie weitere Schlüssel erstellen möchten.

## <a name="view-history-for-account-users"></a>Verlauf für Kontobenutzer anzeigen

Als Kontobesitzer können Sie den detaillierten Browserverlauf für alle weiteren Benutzer, die Sie dem Konto hinzugefügt haben, anzeigen.

Klicken Sie auf der Seite **Benutzer verwalten** bei dem Benutzer, dessen Browserverlauf Sie überprüfen möchten, auf den Link unter **Letzte Aktivität**. Sie können die URLs aller Seiten anzeigen, die der Benutzer in den letzten 30Tagen besucht habt.

## <a name="removing-users-groups-and-azure-ad-applications"></a>Entfernen von Benutzern, Gruppen und Azure AD-Anwendungen

Um einen Benutzer, eine Gruppe oder eine Azure AD-Anwendung aus Ihrem Dev Center-Konto zu entfernen, klicken Sie auf den Link **Entfernen**, der auf der Seite **Benutzer verwalten** neben dem jeweiligen Namen angezeigt wird. Nachdem Sie das Entfernen bestätigt haben, kann der Benutzer, die Gruppe oder die Azure AD-Anwendung nicht mehr auf Ihr Dev Center-Konto zugreifen (es sei denn, Sie fügen das Element später wieder hinzu).

> **Hinweis**  Wenn Sie Benutzer, Gruppen oder Azure AD-Anwendungen entfernen, bedeutet dies, dass diese nicht mehr auf Ihr Dev Center-Konto zugreifen können. Dadurch werden nicht die betreffenden Benutzer, Gruppen oder Azure AD-Apps aus dem Verzeichnis der Organisation gelöscht.

 

 

 
