---
author: jnHs
Description: "Sie können Ihrem Dev Center-Konto Benutzer, Gruppen und Azure AD-Anwendungen hinzufügen."
title: "Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Dev Center-Konto"
ms.author: wdg-dev-content
ms.date: 07/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 32f62d6022d075e71ce6bcc15e1603a2e11a68a5
ms.sourcegitcommit: 23cda44f10059bcaef38ae73fd1d7c8b8330c95e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2017
---
# <a name="add-users-groups-and-azure-ad-applications-to-your-dev-center-account"></a>Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Dev Center-Konto

Im Abschnitt [Verwalten von Benutzern](manage-account-users.md) des Dev Centers können Sie mithilfe von Azure Active Directory Ihrem Dev Center-Konto Benutzer hinzufügen. Jedem Benutzer wird eine Rolle (oder benutzerdefinierte Berechtigungen) zugewiesen, mit der er bestimmte Zugriffsberechtigungen für das Konto erhält. Sie können ebenfalls [Anwendergruppen](#groups) und [Azure AD-Anwendungen](#azure-ad-applications) hinzufügen, um Ihnen Zugriff auf Ihr Dev Center-Konto zu gewährleisten.

Nachdem Benutzer auf das Konto hinzugefügt wurden, können Sie [Kontodetails bearbeiten](#edit), [Rollen und Berechtigungen](set-custom-permissions-for-account-users.md) ändern oder [Benutzer entfernen](#remove).

> [!IMPORTANT]
> Zum Hinzufügen von Kontobenutzern müssen Sie zunächst [Ihr Dev Center-Konto dem Mandanten des Azure Active Directory Ihres Unternehmens zuordnen](associate-azure-ad-with-dev-center.md). 

Beachten Sie beim Hinzufügen von Benutzern Folgendes. (Dies gilt sowohl für Gruppen und Azure AD-Anwendungen als auch für einzelne Benutzer).

-   Alle Dev Center-Benutzer müssen über ein aktives Konto im Verzeichnis Ihrer Organisation verfügen. Das Erstellen eines neuen Benutzers im Dev Center erstellt ebenfalls ein Konto für diesen Benutzer im Azure AD-Mandant Ihrer Organisation.
-   Wenn Sie am Namen eines Benutzers in Dev Center [Änderungen vornehmen](#edit), werden diese Änderungen auch im Azure AD-Mandanten der Organisation vorgenommen.
-   Beim Hinzufügen von Benutzern, müssen Sie den Zugriff auf das Dev Center-Konto angeben, indem Sie ihnen eine [Rolle oder Gruppe von benutzerdefinierten Berechtigungen](set-custom-permissions-for-account-users.md) zuweisen. 

> [!NOTE]
> Wenn Ihre Organisation die [Verzeichnisintegration](http://go.microsoft.com/fwlink/p/?LinkID=724033) zum Synchronisieren des lokalen Verzeichnisdienst mit Ihrem AzureAD verwendet, können Sie in DevCenter keine neuen Benutzer, Gruppen oder AzureAD-Anwendungen erstellen. Sie (oder ein anderer Administrator in Ihrem lokalen Verzeichnis) müssen sie direkt im lokalen Verzeichnis erstellen, bevor sie in DevCenter angezeigt und hinzugefügt werden können.


<span id="users" />
## <a name="add-users-to-your-dev-center-account"></a>Hinzufügen von Benutzern zu Ihrem Dev Center-Konto

Sie können Ihrem Dev Center-Konto einzelne Benutzer wie folgt hinzufügen:
-   Hinzufügen von Benutzern, die bereits im Verzeichnis Ihrer Organisation vorhanden sind
-   Erstellen eines neuen Benutzers für das Verzeichnis Ihrer Organisation und für Ihr Dev Center-Konto
-   Fügen Sie vorhandenen Benutzer hinzu, die derzeit nicht im Verzeichnis Ihrer Organisation vorhanden sind


<span id="from-directory" />
### <a name="add-users-from-your-organizations-directory"></a>Hinzufügen von Benutzern aus dem Verzeichnis Ihrer Organisation

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Wählen Sie in der angezeigten Liste einen oder mehrere Benutzer aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als einen Benutzer hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Benutzer mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.

3.  Wenn Sie die Benutzer ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Benutzer wünschen.
5.  Klicken Sie auf **Speichern**.


<span id="new-user" />
### <a name="create-a-new-user-account-in-your-organizations-directory-and-add-them-to-your-dev-center-account"></a>Erstellen eines neuen Benutzerkontos für das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Dev Center-Konto

Wenn Sie einem völlig neuen Konto in Ihrem Azure AD-Mandanten den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer verwalten** ein neues Konto erstellen, indem Sie auf **Neuer Benutzer** klicken. 

> [!IMPORTANT]
> Sie müssen mit einem globalen Administratorkonto in Ihrem Azure AD-Mandanten angemeldet sein, um dem Verzeichnis einen neuen Benutzer hinzuzufügen.

Wenn der neue Benutzer ein [Konto als globaler Administrator](http://go.microsoft.com/fwlink/p/?LinkId=746654) im Verzeichnis Ihrer Organisation haben soll, markieren Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator mit vollständiger Kontrolle über alle Verzeichnisressourcen machen**. Dadurch erhält der Benutzer den vollständigen Zugriff auf alle administrativen Features im Azure AD Ihrer Organisation. Er kann dann Benutzer im Verzeichnis Ihrer Organisation hinzufügen und verwalten (jedoch nicht in Dev Center, sofern Sie dem Konto nicht die dazu erforderliche(n) [Rolle/Berechtigungen](set-custom-permissions-for-account-users.md)) zuweisen. Wenn Sie dieses Kontrollkästchen markieren, müssen Sie eine **E-Mail-Adresse zur Kennwortwiederherstellung** für den Benutzer angeben.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neuer Benutzer**.
3.  Stellen Sie sicher, dass das Optionsfeld **Zu Azure AD hinzufügen** aktiviert ist, um ein neues Konto im Verzeichnis Ihrer Organisation zu erstellen und den betreffenden Benutzer Ihrem Dev Center-Konto hinzuzufügen. 
4.  Geben Sie den Vornamen, den Nachnamen und den Benutzernamen für den neuen Benutzer ein.
5.  Geben Sie eine E-Mail-Adresse an, die der Benutzer verwenden kann, um sein Kennwort wiederherzustellen. Dies ist nur erforderlich, wenn Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator machen** markiert haben.
6.  Wählen Sie im Abschnitt **Gruppenmitgliedschaft** alle Gruppen aus, denen der neue Benutzer angehören soll.
7.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für den ausgewählten Benutzer wünschen.
8.  Klicken Sie auf **Speichern**.
9.  Auf der Bestätigungsseite werden die Anmeldedaten für den neuen Benutzer angezeigt, z.B. ein temporäres Kennwort. Notieren Sie sich diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.


<span id="email" />
### <a name="add-a-user-from-outside-of-your-azure-ad-tenant-to-your-dev-center-account-and-your-directory"></a>Hinzufügen eines Benutzers auf Ihr Dev Center-Konto und Verzeichnis von außerhalb Ihres Azure AD-Mandanten

Gehen Sie wie folgt vor, um Benutzer auf Ihr Konto einzuladen, die zurzeit nicht Teil Ihres Azure AD-Mandanten sind. Die Benutzer erhalten eine E-Mail-Einladung für ihr Konto und es wird ein neues [Gastbenutzer](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)-Konto für sie in Ihrem Azure AD-Mandanten erstellt. 

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Benutzer hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neuer Benutzer**.
3.  Markieren Sie das Optionsfeld **Benutzer per E-Mail einladen**.
3.  Geben Sie eine oder mehrere E-Mails Adressen (bis zu zehn) mit Kommata oder Semikola als Trennzeichen ein.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für den ausgewählten Benutzer wünschen.
6.  Klicken Sie auf **Speichern**.

Die Benutzer, die Sie eingeladen haben, erhalten eine E-Mail-Nachricht mit einer Einladung zum Zugriff auf Ihr Dev Center-Konto. Jeder Benutzer muss die Einladung annehmen, bevor er auf Ihr Konto zugreifen kann.

Um die Einladung erneut zu senden, suchen Sie den Benutzer auf Ihrer **Benutzer verwalten**-Seite und wählen Sie seine E-Mail-Adresse (oder auf den Text **Einladung ausstehend**) aus, um das Konto zu bearbeiten. Klicken Sie dann am unteren Rand der Seite, auf **Einladung senden**.


### <a name="changing-a-users-directory-password"></a>Ändern des Verzeichniskennworts eines Benutzers

Wenn Sie das Kennwort für ein Benutzerkonto ändern müssen, das Sie dem Dev Center-Konto hinzugefügt haben, können Sie die notwendigen Schritte im Abschnitt **Benutzer verwalten** ausführen. Beachten Sie, dass dies das Kennwort des Benutzers in Ihrem Azure AD-Mandanten zusammen mit dem Kennwort ändert, das er verwendet, um Zugriff auf Dev Center zu erhalten. 

Wenn Sie bei der Erstellung des Benutzerkontos eine **E-Mail-Adresse zur Kennwortwiederherstellung** angegeben haben, kann der Benutzer sein eigenes Kennwort zurücksetzen. Sie können das Kennwort eines Benutzers auch aktualisieren, indem Sie die folgenden Schritte befolgen.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Benutzerkontos, das bearbeitet werden soll.
2.  Klicken Sie am unteren Rand der Seite auf die Schaltfläche **Kennwort zurücksetzen**.
3.  Auf einer Bestätigungsseite werden die Anmeldeinformationen für den Benutzer angezeigt, einschließlich eines temporären Kennworts.
    > [!IMPORTANT]
    >  Drucken oder kopieren Sie diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.

<span id="groups" />
## <a name="add-groups-to-your-dev-center-account"></a>Hinzufügen von Gruppen zu Ihrem Dev Center-Konto

Sie können eine Gruppe aus dem Verzeichnis Ihrer Organisation dem Dev Center-Konto hinzufügen. Daraufhin kann jeder Benutzer, der Mitglied dieser Gruppe ist, mit den Berechtigungen der dieser Gruppe zugewiesenen Rolle darauf zugreifen.

### <a name="add-groups-from-your-organizations-directory"></a>Hinzufügen von Gruppen aus dem Verzeichnis der Organisation

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Gruppen hinzufügen**.
2.  Wählen Sie in der angezeigten Liste eine oder mehrere Gruppen aus. Im Suchfeld können Sie nach bestimmten Gruppen suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als eine Gruppe hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Gruppen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.

3.  Wenn Sie die Gruppen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Gruppen wünschen. Alle Mitglieder der Gruppe können auf das Dev Center-Konto mit den Berechtigungen zugreifen, die Sie der Gruppe zugewiesen haben, unabhängig von den Rollen/Berechtigungen, die mit individuellen Konto verknüpft sind.
5.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-group-account-in-your-organizations-directory-and-add-it-to-your-dev-center-account"></a>Erstellen eines neuen Gruppenkontos für das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Dev Center-Konto

Wenn Sie einer völlig neuen Gruppe den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer verwalten** eine neue Gruppe erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation eine neue Gruppe erstellt wird.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Gruppen hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **Neue Gruppe**.
3.  Geben Sie den Anzeigenamen für die neue Gruppe ein.
4.  Geben Sie die [Rollen oder angepasste Berechtigungen](set-custom-permissions-for-account-users.md) für die Gruppe an. Alle Mitglieder der Gruppe können auf das Dev Center-Konto mit den Berechtigungen zugreifen, die Sie der Gruppe zugewiesen haben, unabhängig von den Rollen/Berechtigungen, die mit individuellen Konto verknüpft sind.
5.  Wählen Sie den/die Benutzer, die der neuen Gruppe in der Liste zugewiesen werden sollen, aus der angezeigten Liste aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
6.  Wenn Sie mit der Auswahl der Benutzer fertig sind, klicken Sie auf **Ausgewählte hinzufügen**, um diese der neuen Gruppe hinzuzufügen.
7.  Klicken Sie auf **Speichern**.


<span id="azure-ad-applications" />
## <a name="add-azure-ad-applications-to-your-dev-center-account"></a>Hinzufügen von Azure AD-Anwendungen zu Ihrem Dev Center-Konto

Sie können Anwendungen oder Diensten, die Teil der Azure AD-Instanz Ihrer Organisation sind, den Zugriff auf Ihr Dev Center-Konto gewähren.

### <a name="add-azure-ad-applications-from-your-organizations-directory"></a>Hinzufügen von Azure AD-Anwendungen aus Verzeichnis der Organisation

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**.
2.  Wählen Sie eine oder Azure AD-Anwendungen aus der angezeigten Liste aus. Mithilfe des Suchfelds können Sie nach bestimmten Azure AD-Anwendungen suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als eine Azure AD-Anwendung hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Azure AD-Anwendungen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierten Berechtigungen.

3.  Wenn Sie die Azure AD-Anwendungen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Azure AD-Anwendungen wünschen.
5.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-azure-ad-application-account-in-your-organizations-directory-and-add-it-to-your-dev-center-account"></a>Erstellen eines neuen Azure AD-Anwendung-Kontos für das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Dev Center-Konto

Wenn Sie einem völlig neuen Azure AD-Anwendungskonto den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer verwalten** ein neues Konto erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation ein neues Konto erstellt wird.

> [!TIP]
> Wenn Sie diese Azure AD-Anwendung hauptsächlich für die Dev Center-Authentifizierung verwenden, und Benutzer nicht direkt auf sie zugreifen müssen, können Sie für die **Antwort-URL** und **App-ID-URI** jede beliebige gültige Adresse eingeben, solange diese Werte nicht von einer anderen Azure AD-Anwendung in Ihrem Verzeichnis verwendet werden.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf **Azure AD-Apps hinzufügen**.
2.  Klicken Sie auf der nächsten Seite auf **New Azure AD application**.
3.  Geben Sie die **Antwort-URL** für die neue Azure AD-App ein. Dies ist die URL, mit der sich Benutzer anmelden und Ihre Azure AD-App verwenden können (wird auch als App-URL oder Anmelde-URL bezeichnet). Die **Antwort-URL** darf nicht mehr als 256 Zeichen enthalten.
4.  Geben Sie den **App-ID-URI** für die neue Azure AD-App ein. Dies ist ein logischer Bezeichner für die Azure AD-App, der beim Senden einer Anforderung für einmaliges Anmelden an Azure AD angezeigt wird. Beachten Sie, dass der **App-ID-URI** für jede Azure AD-App im Verzeichnis eindeutig sein muss und nicht mehr als 256 Zeichen enthalten darf.
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die Azure AD-Anwendungen wünschen.
6.  Klicken Sie auf **Speichern**.

Nachdem Sie eine Azure AD-Anwendung hinzugefügt oder erstellt haben, können Sie zum Abschnitt **Verwalten von Benutzern** zurückkehren und auf den Namen der Anwendung klicken, um die Einstellungen für die Anwendung zu überprüfen, einschließlich Mandanten-ID, Client-ID, Antwort-URL und App-ID-URI.

> [!NOTE]
> Wenn Sie beabsichtigen, die REST-APIs zu verwenden, die von den [Windows Store-Diensten](../monetize/using-windows-store-services.md) bereitgestellt werden, benötigen Sie die die auf dieser Seite angezeigten Werte für die Mandanten-ID und die Client-ID, um ein Azure AD-Zugriffstoken abzurufen, das Sie für die Authentifizierung der Aufrufe von Diensten verwenden können.   

<span id="manage-keys" />
### <a name="manage-keys-for-an-azure-ad-application"></a>Verwalten von Schlüsseln für eine Azure AD-App

Wenn die Azure AD-App Daten in Microsoft Azure AD liest und schreibt, benötigt sie einen Schlüssel. Sie können Schlüssel für eine Azure AD-App erstellen, indem Sie ihre Informationen in Dev Center bearbeiten. Sie können auch Schlüssel entfernen, die nicht mehr benötigt werden.

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen der Azure AD-App.
    > [!TIP]
    > Wenn Sie auf den Namen der Azure AD-App klicken, sehen Sie alle aktiven Schlüssel für die Azure AD-App mit dem jeweiligen Erstellungs- und Ablaufdatum des Schlüssels. Klicken Sie auf **Entfernen**, um einen nicht mehr benötigten Schlüssel zu entfernen.

2.  Klicken Sie auf **Add new key**, um einen neuen Schlüssel hinzuzufügen.
3.  Es wird ein Bildschirm mit den Werten für **Client-ID** und **Schlüssel** angezeigt.
    > [!IMPORTANT]
    > Drucken oder kopieren Sie diese Informationen, da Sie nach dem Verlassen dieser Seite nicht mehr darauf zugreifen können.

4.  Klicken Sie auf **Add another key**, wenn Sie weitere Schlüssel erstellen möchten.

<span id="edit" />
## <a name="edit-a-user-group-or-azure-ad-application"></a>Bearbeiten von Benutzern, Gruppen oder Azure AD-Anwendungen

Nachdem Sie Ihrem Dev Center-Konto Benutzer, Gruppen oder Azure AD-Anwendungen hinzugefügt haben, können Sie Änderungen an deren Kontoinformationen vornehmen. 

> [!IMPORTANT]
> Änderungen an der Rolle oder Berechtigung wirken sich nur auf deren jeweiligen Dev Center-Zugriff aus. Alle anderen Änderungen (wie der Name eines Benutzers oder der Gruppenmitgliedschaft oder der Antwort-URL und App-ID-URI für eine Azure AD-Anwendung) werden sowohl im Azure AD-Mandanten Ihrer Organisation als auch im Dev Center-Konto widergespiegelt. 

1.  Klicken Sie auf der Seite **Benutzer verwalten** auf den Namen des Benutzer-, Gruppen- oder Azure AD-Anwendungskontos, das bearbeitet werden soll.
2.  Nehmen Sie die gewünschten Änderungen vor. Die Elemente, die Sie bearbeiten können, lauten wie folgt:
    -   Sie können den Vornamen, den Nachnamen oder den Benutzernamen eines **Benutzers** bearbeiten. Sie können ebenfalls Gruppen im Abschnitt **Gruppenmitgliedschaft** auswählen oder deaktivieren, um die Gruppenmitgliedschaft zu aktualisieren.
    -   Für eine **Gruppe** können Sie den Namen der Gruppe bearbeiten. (Um Gruppenmitgliedschaft zu aktualisieren, bearbeiten Sie die Benutzer, die Sie der Gruppe hinzufügen oder daraus entfernen möchten und nehmen Sie im Abschnitt **Gruppenmitgliedschaft** Änderungen vor.)
    -   Für eine **Azure AD-Anwendung** können Sie neue Werte für die **Antwort-URL** oder **App-ID-URI** eingeben.
    Beachten Sie, dass diese Änderungen nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation vorgenommen werden.
3.  Wählen Sie für Änderungen im Zusammenhang mit dem Zugriff auf das Dev Center die Rollen aus, die Sie anwenden oder deaktivieren möchten oder wählen Sie **Berechtigungen anpassen** aus, um die gewünschten Änderungen vorzunehmen. Diese Änderungen wirken sich nur auf den Zugriff auf das Dev Center aus und ändern nicht die Berechtigungen des Azure AD-Mandanten der Organisation.
3.  Klicken Sie auf **Speichern**.


## <a name="view-history-for-account-users"></a>Verlauf für Kontobenutzer anzeigen

Als Kontobesitzer können Sie den detaillierten Browserverlauf für alle weiteren Benutzer, die Sie dem Konto hinzugefügt haben, anzeigen.

Klicken Sie auf der Seite **Benutzer verwalten** bei dem Benutzer, dessen Browserverlauf Sie überprüfen möchten, auf den Link unter **Letzte Aktivität**. Sie können die URLs aller Seiten anzeigen, die der Benutzer in den letzten 30Tagen besucht habt.

<span id="remove" />
## <a name="remove-users-groups-and-azure-ad-applications"></a>Entfernen von Benutzern, Gruppen und Azure AD-Apps

Um einen Benutzer, eine Gruppe oder eine Azure AD-Anwendung aus Ihrem Dev Center-Konto zu entfernen, klicken Sie auf den Link **Entfernen**, der auf der Seite **Benutzer verwalten** neben dem jeweiligen Namen angezeigt wird. Nachdem Sie das Entfernen bestätigt haben, kann der Benutzer, die Gruppe oder die Azure AD-Anwendung nicht mehr auf Ihr Dev Center-Konto zugreifen (es sei denn, Sie fügen das Element später wieder hinzu).

> [!IMPORTANT] 
> Wenn Sie Benutzer, Gruppen oder eine Azure AD-Apps entfernen, bedeutet dies, das sie nicht mehr auf Ihr Dev Center-Konto zugreifen können. Dadurch werden **nicht** die betreffenden Benutzer, Gruppen oder Azure AD-Apps aus dem Verzeichnis der Organisation gelöscht.

 

