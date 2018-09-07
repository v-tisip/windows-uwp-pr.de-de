---
author: jnHs
Description: You can add users, groups, and Azure AD applications to your Dev Center account.
title: Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Dev Center-Konto
ms.author: wdg-dev-content
ms.date: 07/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Azure Ad-Anwendung, Aad, Benutzer, Gruppen, mehrere Benutzer, mit mehreren Benutzern
ms.localizationpriority: medium
ms.openlocfilehash: 97502a0a2863ed6f7ab2ce5d842fbebc1ae8091c
ms.sourcegitcommit: 53ba430930ecec8ea10c95b390fe6e654fe363e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3416998"
---
# <a name="add-users-groups-and-azure-ad-applications-to-your-dev-center-account"></a>Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Dev Center-Konto

Der Abschnitt **Benutzer** des Windows Dev Center (unter **kontoeinstellungen**) können Sie die Azure Active Directory verwenden, um Benutzer zu Ihrem Dev Center-Konto hinzuzufügen. Jedem Benutzer wird eine Rolle (oder benutzerdefinierte Berechtigungen) zugewiesen, mit der er bestimmte Zugriffsberechtigungen für das Konto erhält. Sie können ebenfalls [Anwendergruppen](#groups) und [Azure AD-Anwendungen](#azure-ad-applications) hinzufügen, um Ihnen Zugriff auf Ihr Dev Center-Konto zu gewährleisten.

Nachdem Benutzer auf das Konto hinzugefügt wurden, können Sie [Kontodetails bearbeiten](#edit), [Rollen und Berechtigungen](set-custom-permissions-for-account-users.md) ändern oder [Benutzer entfernen](#remove).

> [!IMPORTANT]
> Sie müssen zunächst [Ihr Dev Center-Konto dem Mandanten des Azure Active Directory Ihres Unternehmens zuordnen](associate-azure-ad-with-dev-center.md), wenn Sie Ihrem Konto Benutzer hinzufügen möchten. 

Beim Hinzufügen von Benutzern, müssen Sie den Zugriff auf Ihr Dev Center-Konto angeben, indem Sie ihnen eine [Rolle oder Gruppe von benutzerdefinierten Berechtigungen](set-custom-permissions-for-account-users.md) zuweisen. 

Beachten Sie, dass alle Dev Center-Benutzer (inklusive Gruppen und Azure AD-Anwendungen) über ein aktives Konto im [Azure AD-Mandanten verfügen müssen, das mit Ihrem Dev Center-Konto verknüpft ist](associate-azure-ad-with-dev-center.md). Die Benutzerverwaltung erfolgt pro Mandant. Sie müssen sich mit einem Managerkonto auf dem Mandanten anmelden, wenn Sie Benutzer hinzufügen oder bearbeiten möchten. Durch das Erstellen eines neuen Benutzers im Dev Center wird ebenfalls ein Konto für diesen Benutzer auf dem Azure AD-Mandanten erstellt, auf dem Sie angemeldet sind. Wenn der Namen eines Benutzers im Dev Center geändert wird, wirken sich diese Änderungen auf den Azure AD-Mandanten Ihrer Organisation aus.

> [!NOTE]
> Wenn Ihre Organisation die [Verzeichnisintegration](http://go.microsoft.com/fwlink/p/?LinkID=724033) zum Synchronisieren des lokalen Verzeichnisdienst mit Ihrem AzureAD verwendet, können Sie in DevCenter keine neuen Benutzer, Gruppen oder AzureAD-Anwendungen erstellen. Sie (oder ein anderer Administrator in Ihrem lokalen Verzeichnis) müssen sie direkt im lokalen Verzeichnis erstellen, bevor sie in DevCenter angezeigt und hinzugefügt werden können.


<span id="users" />

## <a name="add-users-to-your-dev-center-account"></a>Hinzufügen von Benutzern zu Ihrem Dev Center-Konto

Um Ihrem Dev Center-Konto Benutzer hinzuzufügen, wechseln Sie zur Seite **Benutzer** unter **Kontoeinstellungen**, und wählen Sie **Benutzer hinzufügen** aus. Sie müssen mit einem Managerkonto auf dem Azure AD-Mandanten angemeldet sein, auf dem Sie arbeiten möchten. 

### <a name="add-existing-users"></a>Hinzufügen vorhandener Benutzer 

Sie können Benutzer auswählen, die bereits im Mandanten Ihrer Organisation vorhanden sind und ihnen Zugriff auf Ihr Dev Center-Konto gewähren. 

<span id="from-directory" />

1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Dashboards), und wählen Sie die **kontoeinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2.  Wählen Sie auf der Seite **Benutzer** **Benutzer hinzufügen** aus. 
3.  Wählen Sie in der angezeigten Liste einen oder mehrere Benutzer aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als einen Benutzer hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigung zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Benutzer mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.
4.  Wenn Sie die Benutzer ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Benutzer wünschen.
6.  Klicken Sie auf **Speichern**.

### <a name="additional-methods-for-adding-users"></a>Zusätzliche Methoden zum Hinzufügen von Benutzern

Wenn Sie sich mit einem Managerkonto angemeldet haben, das über [globale Administrator](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)berechtigungen für den von Ihnen verwendeten Azure AD-Mandanten verfügt, werden zusätzliche Optionen angeboten, um dem Dev Center-Konto Benutzer hinzuzufügen. Sie müssen eine der folgenden Optionen auswählen:

-   **Hinzufügen vorhandener Benutzer**: Wählen Sie Benutzer, die bereits im Verzeichnis Ihrer Organisation vorhanden sind, und gewähren Sie ihnen Zugriff auf Ihr Dev Center-Konto mit der oben beschriebenen Methode.
-   **Neue Benutzer erstellen**: Erstellen Sie völlig neue Benutzerkonten sowohl das Verzeichnis Ihrer Organisation hinzu und Dev Center-Konto
-   **Invite outside users** (Externe Benutzer einladen): Laden Sie Benutzer per E-Mail ein, die derzeit nicht im Verzeichnis der Organisation vorhanden sind. Diese werden eingeladen, auf Ihr Dev Center-Konto zuzugreifen. Es wird ein neues [Gastbenutzer](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)-Konto für sie in Ihrem Azure AD-Mandanten erstellt.

<span id="new-user" />

### <a name="create-new-users"></a>Erstellen neuer Benutzer

> [!IMPORTANT]
> Sie müssen mit einem globalen Administratorkonto auf Ihrem Azure AD-Mandanten angemeldet sein, um neue Benutzer zu erstellen.

1.  Wählen Sie von der Seite " **Benutzer** " (unter **kontoeinstellungen**) **Benutzer hinzufügen**und dann **neue Benutzer erstellen**.
2.  Geben Sie den Vornamen, den Nachnamen und den Benutzernamen für den neuen Benutzer ein.
3.  Wenn der neue Benutzer ein [Konto als globaler Administrator](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) im Verzeichnis Ihrer Organisation haben soll, markieren Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator mit vollständiger Kontrolle über alle Verzeichnisressourcen machen**. Dadurch erhält der Benutzer den vollständigen Zugriff auf alle administrativen Features im Azure AD Ihrer Organisation. Er kann dann Benutzer im Verzeichnis Ihrer Organisation hinzufügen und verwalten (jedoch nicht in Dev Center, sofern Sie dem Konto nicht die dazu erforderliche(n) [Rolle/Berechtigungen](set-custom-permissions-for-account-users.md)) zuweisen. Wenn Sie dieses Kontrollkästchen markieren, müssen Sie eine **E-Mail-Adresse zur Kennwortwiederherstellung** für den Benutzer angeben.
4.  Wenn Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator machen** markiert haben, geben Sie eine E-Mail-Adresse ein, die der Benutzer verwenden kann, um sein Kennwort wiederherzustellen.
5.  Wählen Sie im Abschnitt **Gruppenmitgliedschaft** alle Gruppen aus, denen der neue Benutzer angehören soll.
6.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für den ausgewählten Benutzer wünschen.
7.  Klicken Sie auf **Speichern**.
8.  Auf der Bestätigungsseite werden die Anmeldedaten für den neuen Benutzer angezeigt, z.B. ein temporäres Kennwort. Notieren Sie sich diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.


<span id="email" />

### <a name="invite-outside-users"></a>Einladen externer Benutzer

> [!IMPORTANT]
> Sie müssen auf Ihrem Azure AD-Mandanten mit einem globalen Administratorkonto angemeldet sein, um externe Benutzer einzuladen.

1.  Wählen Sie von der Seite " **Benutzer** " (unter **kontoeinstellungen**) **Benutzer hinzufügen**und dann **Benutzer per e-Mail einladen**.
1.  Geben Sie eine oder mehrere E-Mail-Adressen ein (bis zu zehn), die durch Kommas oder Semikolons getrennt sind.
2.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für den ausgewählten Benutzer wünschen.
3.  Klicken Sie auf **Speichern**.

Die von Ihnen eingeladenen Benutzer erhalten eine E-Mail-Einladung für Ihr Konto. Es wird ein neues [Gastbenutzer](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)-Konto für sie in Ihrem Azure AD-Mandanten erstellt. Jeder Benutzer muss die Einladung annehmen, bevor er auf Ihr Konto zugreifen kann.

Um die Einladung erneut zu senden, suchen Sie den Benutzer auf Ihrer **Benutzer**-Seite heraus, und wählen Sie seine E-Mail-Adresse (oder den Text **Einladung ausstehend**) aus. Klicken Sie anschließend am unteren Rand der Seite auf **Einladung senden**.

> [!IMPORTANT]
> Sie können externen Benutzern, die Sie zum Beitritt auf Ihr Dev Center-Konto eingeladen haben, die gleichen Funktionen und Berechtigungen wie andere Benutzer zuweisen. Allerdings können externe Benutzern bestimmte Aufgaben in Visual Studio wie z.B. das Assoziieren einer App mit dem Store oder das Erstellen von Paketen zum Hochladen in den Store nicht durchführen. Wenn ein Benutzer diese Aufgaben durchführen muss, wählen Sie **Erstellen von neuen Benutzern** anstelle von **externe Benutzer einladen**. (Wenn Sie diese Benutzer nicht dem vorhandenen Azure AD-Mandanten hinzufügen möchten, können Sie [einen neuen Mandanten erstellen](../publish/associate-azure-ad-with-dev-center.md#create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account), und anschließend für sie neue Benutzerkonten im Mandanten erstellen.) 


### <a name="changing-a-users-directory-password"></a>Ändern des Verzeichniskennworts eines Benutzers

Wenn ein Benutzer sein Kennwort ändern muss, kann er dies selber tun, wenn Sie ihm beim Erstellen des Benutzerkontos eine **E-Mail-Adresse zur Kennwortwiederherstellung** bereitgestellt haben. Sie können das Kennwort eines Benutzers auch aktualisieren, indem Sie die folgenden Schritte durchführen (wenn Sie sich mit einem globalen Administratorkonto in Ihrem Azure AD-Mandanten angemeldet haben, um das Kennwort des Benutzers zu ändern). Beachten Sie, dass dies das Kennwort des Benutzers in Ihrem Azure AD-Mandanten sowie das Kennwort ändert, das er verwendet, um Zugriff auf Dev Center zu erhalten. 

1.  Wählen Sie die Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen des Benutzerkontos, das Sie bearbeiten möchten.
2.  Wählen Sie die Schaltfläche " **Kennwort zurücksetzen** " am unteren Rand der Seite.
3.  Auf einer Bestätigungsseite werden die Anmeldeinformationen für den Benutzer angezeigt, einschließlich eines temporären Kennworts.

    > [!IMPORTANT]
    >  Drucken oder kopieren Sie diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.

<span id="groups" />

## <a name="add-groups-to-your-dev-center-account"></a>Hinzufügen von Gruppen zu Ihrem Dev Center-Konto

Sie können eine Gruppe aus dem Verzeichnis Ihrer Organisation dem Dev Center-Konto hinzufügen. Daraufhin kann jeder Benutzer, der Mitglied dieser Gruppe ist, mit den Berechtigungen der dieser Gruppe zugewiesenen Rolle darauf zugreifen.

### <a name="add-groups-from-your-organizations-directory"></a>Hinzufügen von Gruppen aus dem Verzeichnis der Organisation

1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Dashboards), und wählen Sie die **kontoeinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2. Wählen Sie die Seite " **Benutzer** " **Hinzufügen von Gruppen**aus.
2.  Wählen Sie in der angezeigten Liste eine oder mehrere Gruppen aus. Im Suchfeld können Sie nach bestimmten Gruppen suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als eine Gruppe hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigung zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Gruppen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.

3.  Wenn Sie die Gruppen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Gruppen wünschen. Alle Mitglieder der Gruppe können auf das Dev Center-Konto mit den Berechtigungen zugreifen, die Sie der Gruppe zugewiesen haben, unabhängig von den Rollen/Berechtigungen, die mit individuellen Konto verknüpft sind.
5.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-group-account-in-your-organizations-directory-and-add-it-to-your-dev-center-account"></a>Erstellen eines neuen Gruppenkontos für das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Dev Center-Konto

Wenn Sie einer völlig neuen Gruppe den Zugriff auf Dev Center ermöglichen möchten, können Sie im Abschnitt **Benutzer** eine neue Gruppe erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation eine neue Gruppe erstellt wird.

1.  Klicken Sie auf der Seite " **Benutzer** " (unter **kontoeinstellungen**) auf **Gruppen hinzufügen**.
2.  Wählen Sie auf der nächsten Seite **neue Gruppe**ein.
3.  Geben Sie den Anzeigenamen für die neue Gruppe ein.
4.  Geben Sie die [Rollen oder angepasste Berechtigungen](set-custom-permissions-for-account-users.md) für die Gruppe an. Alle Mitglieder der Gruppe können auf das Dev Center-Konto mit den Berechtigungen zugreifen, die Sie der Gruppe zugewiesen haben, unabhängig von den Rollen/Berechtigungen, die mit individuellen Konto verknüpft sind.
5.  Wählen Sie den/die Benutzer, die der neuen Gruppe in der Liste zugewiesen werden sollen, aus der angezeigten Liste aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
6.  Wenn Sie mit der Auswahl der Benutzer fertig sind, klicken Sie auf **Ausgewählte hinzufügen**, um diese der neuen Gruppe hinzuzufügen.
7.  Klicken Sie auf **Speichern**.


<span id="azure-ad-applications" />

## <a name="add-azure-ad-applications-to-your-dev-center-account"></a>Hinzufügen von Azure AD-Anwendungen zu Ihrem Dev Center-Konto

Sie können Anwendungen oder Diensten, die Teil der Azure AD-Instanz Ihrer Organisation sind, den Zugriff auf Ihr Dev Center-Konto gewähren. Diese Benutzerkonten für die Azure AD-Anwendung können zum Aufrufen der über [Microsoft Store Services](../monetize/using-windows-store-services.md) bereitgestellten REST-APIs genutzt werden.


### <a name="add-azure-ad-applications-from-your-organizations-directory"></a>Hinzufügen von Azure AD-Anwendungen aus dem Verzeichnis Ihrer Organisation

1.  1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Dashboards), und wählen Sie die **kontoeinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2. Wählen Sie auf der Seite **Benutzer** **Azure AD-Anwendungen hinzufügen** aus.
3.  Wählen Sie eine oder mehrere Azure AD-Anwendungen aus der angezeigten Liste aus. Mithilfe des Suchfelds können Sie nach bestimmten Azure AD-Anwendungen suchen.
    > [!TIP]
    > Wenn Sie Ihrem Dev Center-Konto mehr als eine Azure AD-Anwendung hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder die gleiche benutzerdefinierte Berechtigung zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Azure AD-Anwendungen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierten Berechtigungen.

4.  Wenn Sie die Azure AD-Anwendungen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Azure AD-Anwendungen wünschen.
6.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-azure-ad-application-account-in-your-organizations-directory-and-add-it-to-your-dev-center-account"></a>Erstellen eines neuen Azure AD-Anwendung-Kontos für das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Dev Center-Konto

Wenn Sie einem völlig neuen Azure AD-Anwendungskonto den Zugriff auf Dev Center gestatten möchten, können Sie im Abschnitt **Benutzer** ein neues Konto erstellen. Beachten Sie, dass hierdurch nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation ein neues Konto erstellt wird.

> [!TIP]
> Wenn Sie diese Azure AD-Anwendung hauptsächlich für die Dev Center-Authentifizierung verwenden, und Benutzer nicht direkt auf sie zugreifen müssen, können Sie für die **Antwort-URL** und **App-ID-URI** jede beliebige gültige Adresse eingeben, solange diese Werte nicht von einer anderen Azure AD-Anwendung in Ihrem Verzeichnis verwendet werden.

1.  Wählen Sie die Seite " **Benutzer** " (unter **kontoeinstellungen**) **Azure AD-Apps hinzufügen**.
2.  Wählen Sie auf der nächsten Seite das **neue Azure AD-Anwendung**.
3.  Geben Sie die **Antwort-URL** für die neue Azure AD-App ein. Dies ist die URL, mit der sich Benutzer anmelden und Ihre Azure AD-App verwenden können (wird auch als App-URL oder Anmelde-URL bezeichnet). Die **Antwort-URL** darf nicht länger als 256 Zeichen sein und muss innerhalb des Verzeichnisses eindeutig sein.
4.  Geben Sie den **App-ID-URI** für die neue Azure AD-App ein. Dies ist ein logischer Bezeichner für die Azure AD-App, der beim Senden einer Anforderung für einmaliges Anmelden an Azure AD angezeigt wird. Beachten Sie, dass der **App-ID-URI** für jede Azure AD-App im Verzeichnis eindeutig sein muss und nicht mehr als 256 Zeichen enthalten darf. Weitere Informationen zur **App-ID-URI** finden Sie unter [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#changing-the-application-registration-to-support-multi-tenant).
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die Azure AD-Anwendungen wünschen.
6.  Klicken Sie auf **Speichern**.

Nachdem Sie eine Azure AD-Anwendung hinzugefügt oder erstellt haben, können Sie zum Abschnitt **Benutzer** zurückkehren und den Namen der Anwendung auswählen, um die Einstellungen für die Anwendung zu überprüfen, einschließlich Mandanten-ID, Client-ID, Antwort-URL und App-ID-URI.

> [!NOTE]
> Wenn Sie beabsichtigen, die REST-APIs zu verwenden, die von den [Microsoft Store-Diensten](../monetize/using-windows-store-services.md) bereitgestellt werden, benötigen Sie die auf dieser Seite angezeigten Werte für die Mandanten-ID und die Client-ID, um ein Azure AD-Zugriffstoken abzurufen, das Sie für die Authentifizierung der Aufrufe von Diensten verwenden können.   

<span id="manage-keys" />

### <a name="manage-keys-for-an-azure-ad-application"></a>Verwalten von Schlüsseln für eine Azure AD-App

Wenn die Azure AD-App Daten in Microsoft Azure AD liest und schreibt, benötigt sie einen Schlüssel. Sie können Schlüssel für eine Azure AD-App erstellen, indem Sie ihre Informationen in Dev Center bearbeiten. Sie können auch Schlüssel entfernen, die nicht mehr benötigt werden.

1.  Wählen Sie aus der Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen der Azure AD-App ein.
    > [!TIP]
    > Wenn Sie auf den Namen der Azure AD-App klicken, sehen Sie alle aktiven Schlüssel für die Azure AD-App mit dem jeweiligen Erstellungs- und Ablaufdatum des Schlüssels. Klicken Sie auf **Entfernen**, um einen nicht mehr benötigten Schlüssel zu entfernen.

2.  Um einen neuen Schlüssel hinzuzufügen, wählen Sie **neuen Schlüssel hinzufügen**.
3.  Es wird ein Bildschirm mit den Werten für **Client-ID** und **Schlüssel** angezeigt.
    > [!IMPORTANT]
    > Drucken oder kopieren Sie diese Informationen, da Sie nach dem Verlassen dieser Seite nicht mehr darauf zugreifen können.

4.  Wenn Sie weitere Schlüssel erstellen möchten, wählen Sie **eine andere Taste hinzufügen**.

<span id="edit" />

## <a name="edit-a-user-group-or-azure-ad-application"></a>Bearbeiten von Benutzern, Gruppen oder Azure AD-Anwendungen

Nachdem Sie Ihrem Dev Center-Konto Benutzer, Gruppen oder Azure AD-Anwendungen hinzugefügt haben, können Sie Änderungen an deren Kontoinformationen vornehmen. 

> [!IMPORTANT]
> Änderungen an der [Rolle oder Berechtigung](set-custom-permissions-for-account-users.md) wirken sich nur auf den jeweiligen Dev Center-Zugriff aus. Alle anderen Änderungen (wie der Name eines Benutzers oder der Gruppenmitgliedschaft oder der Antwort-URL und App-ID-URI für eine Azure AD-Anwendung) werden sowohl im Azure AD-Mandanten Ihrer Organisation als auch im Dev Center-Konto widergespiegelt. 

1.  Wählen Sie die Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen des Benutzer-, Gruppen oder Azure AD-Anwendungskontos, das Sie bearbeiten möchten.
2.  Nehmen Sie die gewünschten Änderungen vor. Die Elemente, die Sie bearbeiten können, lauten wie folgt:
    -   Sie können den Vornamen, den Nachnamen oder den Benutzernamen eines **Benutzers** bearbeiten. Sie können ebenfalls Gruppen im Abschnitt **Gruppenmitgliedschaft** auswählen oder deaktivieren, um die Gruppenmitgliedschaft zu aktualisieren.
    -   Für eine **Gruppe** können Sie den Namen der Gruppe bearbeiten. (Um Gruppenmitgliedschaft zu aktualisieren, bearbeiten Sie die Benutzer, die Sie der Gruppe hinzufügen oder daraus entfernen möchten und nehmen Sie im Abschnitt **Gruppenmitgliedschaft** Änderungen vor.)
    -   Für eine **Azure AD-Anwendung** können Sie neue Werte für die **Antwort-URL** oder **App-ID-URI** eingeben.
    Beachten Sie, dass diese Änderungen nicht nur in Ihrem Dev Center-Konto, sondern auch im Verzeichnis der Organisation vorgenommen werden.
3.  Wählen Sie für Änderungen im Zusammenhang mit dem Zugriff auf das Dev Center die Rollen aus, die Sie anwenden oder deaktivieren möchten oder wählen Sie **Berechtigungen anpassen** aus, um die gewünschten Änderungen vorzunehmen. Diese Änderungen wirken sich nur auf den Zugriff auf das Dev Center aus und ändern nicht die Berechtigungen des Azure AD-Mandanten der Organisation.
3.  Klicken Sie auf **Speichern**.


## <a name="view-history-for-account-users"></a>Verlauf für Kontobenutzer anzeigen

Als Kontobesitzer können Sie den detaillierten Browserverlauf für alle weiteren Benutzer, die Sie dem Konto hinzugefügt haben, anzeigen.

Wählen Sie auf der Seite " **Benutzer** " (unter **kontoeinstellungen**) den Link unter **letzte Aktivität** für den Benutzer, dessen Browserverlauf Sie überprüfen möchten. Sie können die URLs aller Seiten anzeigen, die der Benutzer in den letzten 30Tagen besucht habt.

<span id="remove" />

## <a name="remove-users-groups-and-azure-ad-applications"></a>Entfernen von Benutzern, Gruppen und Azure AD-Anwendungen

Um einen Benutzer, Gruppen oder Azure AD-Anwendung aus Ihrem Dev Center-Konto zu entfernen, wählen Sie die **Entfernen** Link, der über den Namen auf der Seite " **Benutzer** " angezeigt wird. Nachdem Sie das Entfernen bestätigt haben, kann der Benutzer, die Gruppe oder die Azure AD-Anwendung nicht mehr auf Ihr Dev Center-Konto zugreifen (es sei denn, Sie fügen das Element später wieder hinzu).

> [!IMPORTANT]
> Wenn Sie Benutzer, Gruppen oder eine Azure AD-Anwendungen entfernen, bedeutet dies, das sie nicht mehr auf Ihr Dev Center-Konto zugreifen können. Dadurch werden **nicht** die betreffenden Benutzer, Gruppen oder Azure AD-Anwendungen aus dem Verzeichnis der Organisation gelöscht.

 

