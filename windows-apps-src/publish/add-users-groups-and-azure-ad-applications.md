---
Description: You can add users, groups, and Azure AD applications to your Partner Center account.
title: Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Partner Center-Konto
ms.date: 10/31/2018
ms.topic: article
keywords: Windows 10, Uwp, Azure Ad-Anwendung, Aad, Benutzer, gruppieren, mehrere Benutzer, mehrere Benutzer
ms.localizationpriority: medium
ms.openlocfilehash: 7dd300aa6a37c205e01c6f73d95ef1818d516fc0
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8217233"
---
# <a name="add-users-groups-and-azure-ad-applications-to-your-partner-center-account"></a>Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Partner Center-Konto

Der Abschnitt **Benutzer** für [Partner Center](https://partner.microsoft.com/dashboard) (unter **kontoeinstellungen**) können Sie die Azure Active Directory verwenden, um Ihr Partner Center-Konto Benutzer hinzufügen. Jedem Benutzer wird eine Rolle (oder benutzerdefinierte Berechtigungen) zugewiesen, mit der er bestimmte Zugriffsberechtigungen für das Konto erhält. Sie können auch [Gruppen von Benutzern](#groups) und [Azure AD-Anwendungen](#azure-ad-applications) , um ihnen den Zugriff auf Ihr Partner Center-Konto gewähren hinzufügen.

Nachdem Benutzer auf das Konto hinzugefügt wurden, können Sie [Kontodetails bearbeiten](#edit), [Rollen und Berechtigungen](set-custom-permissions-for-account-users.md) ändern oder [Benutzer entfernen](#remove).

> [!IMPORTANT]
> Um Ihr Konto Benutzer hinzufügen, müssen Sie die erste [Ordnen Sie Ihr Partner Center-Konto mit Azure Active Directory-Mandanten Ihrer Organisation](associate-azure-ad-with-dev-center.md). 

Wenn Sie Benutzer hinzufügen, müssen Sie den Zugriff auf Ihr Partner Center-Konto angeben, indem sie eine [Rolle oder Gruppe von benutzerdefinierten Berechtigungen](set-custom-permissions-for-account-users.md)zuweisen. 

Bedenken Sie, dass alle Partner Center-Benutzer (einschließlich von Gruppen und Azure AD-Anwendungen) ein aktives Konto in [Azure AD-Mandanten, der Ihr Partner Center-Konto zugeordnet ist,](associate-azure-ad-with-dev-center.md)vorhanden sein müssen. Die Benutzerverwaltung erfolgt pro Mandant. Sie müssen sich mit einem Managerkonto auf dem Mandanten anmelden, wenn Sie Benutzer hinzufügen oder bearbeiten möchten. Erstellen eines neuen Benutzers im Partner Center wird ebenfalls erstellt ein Konto für diesen Benutzer in Azure AD-Mandanten mit dem Sie angemeldet sind und Änderungen an den Namen eines Benutzers im Partner Center wird die gleiche Änderungen in Azure AD-Mandanten Ihrer Organisation.

> [!NOTE]
> Wenn Ihre Organisation [Verzeichnisintegration](http://go.microsoft.com/fwlink/p/?LinkID=724033) zum Synchronisieren des lokalen Verzeichnisdienst mit Ihrem Azure AD verwendet, nicht Sie neue Benutzer, Gruppen oder Azure AD-Apps in Partner Center erstellen. Sie (oder ein anderer Administrator in Ihrem lokalen Verzeichnis) müssen sie direkt im lokalen Verzeichnis erstellen, bevor Sie werden sehen und diese im Partner Center hinzufügen können.


<span id="users" />

## <a name="add-users-to-your-partner-center-account"></a>Hinzufügen von Benutzern zu Ihrem Partner Center-Konto

Um Ihr Partner Center-Konto Benutzer hinzuzufügen, wechseln Sie zu der Seite " **Benutzer** " in den **kontoeinstellungen** , und wählen Sie **Benutzer hinzufügen.** Sie müssen mit einem Managerkonto auf dem Azure AD-Mandanten angemeldet sein, auf dem Sie arbeiten möchten. 

### <a name="add-existing-users"></a>Hinzufügen vorhandener Benutzer 

Sie können Benutzer auswählen, die bereits im Mandanten Ihrer Organisation vorhanden sind und ihnen Zugriff auf Ihr Partner Center-Konto gewähren. 

<span id="from-directory" />

1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Partner Center), und wählen Sie dann die **entwicklereinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2.  Wählen Sie auf der Seite **Benutzer** **Benutzer hinzufügen** aus. 
3.  Wählen Sie in der angezeigten Liste einen oder mehrere Benutzer aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
    > [!TIP]
    > Wenn Sie mehrere Benutzer auf dem Partner Center-Konto hinzufügen möchten, müssen Sie diesen die gleiche Rolle oder Gruppe von benutzerdefinierten Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Benutzer mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.
4.  Wenn Sie die Benutzer ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Benutzer wünschen.
6.  Klicken Sie auf **Speichern**.

### <a name="additional-methods-for-adding-users"></a>Zusätzliche Methoden zum Hinzufügen von Benutzern

Wenn Sie mit einem Managerkonto angemeldet haben, die auch [globale](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) Administratorberechtigungen für Azure AD-Mandanten hat, Sie arbeiten, verfügen Sie über zusätzliche Optionen Ihr Partner Center-Konto Benutzer hinzu. Sie müssen eine der folgenden Optionen auswählen:

-   **Hinzufügen vorhandener Benutzer**: Benutzer, die bereits im Verzeichnis Ihrer Organisation vorhanden sind, und gewähren Sie ihnen Zugriff auf Ihr Partner Center-Konto mit der oben beschriebenen Methode auswählen.
-   **Neue Benutzer erstellen**: Erstellen Sie völlig neue Benutzerkonten sowohl das Verzeichnis Ihrer Organisation hinzu und Ihr Partner Center-Konto
-   **Invite outside users** (Externe Benutzer einladen): Laden Sie Benutzer per E-Mail ein, die derzeit nicht im Verzeichnis der Organisation vorhanden sind. Diese werden eingeladen, auf Ihr Partner Center-Konto zugreifen, und ein neues [Gast](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) -Benutzerkonto für sie in Ihrem Azure AD-Mandanten erstellt.

<span id="new-user" />

### <a name="create-new-users"></a>Erstellen neuer Benutzer

> [!IMPORTANT]
> Sie müssen mit einem globalen Administratorkonto auf Ihrem Azure AD-Mandanten angemeldet sein, um neue Benutzer zu erstellen.

1.  Wählen Sie von der Seite " **Benutzer** " (unter **kontoeinstellungen**) **Benutzer hinzufügen**und dann **neue Benutzer erstellen**.
2.  Geben Sie den Vornamen, den Nachnamen und den Benutzernamen für den neuen Benutzer ein.
3.  Wenn der neue Benutzer ein [Konto als globaler Administrator](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) im Verzeichnis Ihrer Organisation haben soll, markieren Sie das Kontrollkästchen **Diesen Benutzer in Azure AD zum globalen Administrator mit vollständiger Kontrolle über alle Verzeichnisressourcen machen**. Dadurch erhält der Benutzer den vollständigen Zugriff auf alle administrativen Features im Azure AD Ihrer Organisation. Er kann dann hinzufügen und Verwalten von Benutzern in das Verzeichnis Ihrer Organisation (jedoch nicht im Partner-Center, sofern Sie dem Konto die entsprechenden [Rolle/Berechtigungen](set-custom-permissions-for-account-users.md)gewähren). Wenn Sie dieses Kontrollkästchen markieren, müssen Sie eine **E-Mail-Adresse zur Kennwortwiederherstellung** für den Benutzer angeben.
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
> Externe Benutzer, die Sie für den Beitritt einladen kann Ihr Partner Center-Konto die gleichen Rollen und Berechtigungen wie andere Benutzer zugewiesen werden. Allerdings können externe Benutzern bestimmte Aufgaben in Visual Studio wie z.B. das Assoziieren einer App mit dem Store oder das Erstellen von Paketen zum Hochladen in den Store nicht durchführen. Wenn ein Benutzer diese Aufgaben durchführen muss, wählen Sie **Erstellen von neuen Benutzern** anstelle von **externe Benutzer einladen**. (Wenn Sie diese Benutzer nicht dem vorhandenen Azure AD-Mandanten hinzufügen möchten, können Sie [einen neuen Mandanten erstellen](../publish/associate-azure-ad-with-dev-center.md#create-a-brand-new-azure-ad-to-associate-with-your-partner-center-account), und anschließend für sie neue Benutzerkonten im Mandanten erstellen.) 


### <a name="changing-a-users-directory-password"></a>Ändern des Verzeichniskennworts eines Benutzers

Wenn ein Benutzer sein Kennwort ändern muss, kann er dies selber tun, wenn Sie ihm beim Erstellen des Benutzerkontos eine **E-Mail-Adresse zur Kennwortwiederherstellung** bereitgestellt haben. Sie können das Kennwort eines Benutzers auch aktualisieren, indem Sie die folgenden Schritte durchführen (wenn Sie sich mit einem globalen Administratorkonto in Ihrem Azure AD-Mandanten angemeldet haben, um das Kennwort des Benutzers zu ändern). Beachten Sie, dass dadurch ändert sich das Kennwort des Benutzers in Ihrem Azure AD-Mandanten zusammen mit dem Kennwort sie verwenden, um Zugriff auf Partner Center. 

1.  Wählen Sie die Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen des Benutzerkontos, das Sie bearbeiten möchten.
2.  Wählen Sie die Schaltfläche " **Kennwort zurücksetzen** " am unteren Rand der Seite.
3.  Auf einer Bestätigungsseite werden die Anmeldeinformationen für den Benutzer angezeigt, einschließlich eines temporären Kennworts.

    > [!IMPORTANT]
    >  Drucken oder kopieren Sie diese Informationen, und teilen Sie sie dem neuen Benutzer mit, da Sie nach dem Verlassen dieser Seite nicht mehr auf das temporäre Kennwort zugreifen können.

<span id="groups" />

## <a name="add-groups-to-your-partner-center-account"></a>Hinzufügen von Gruppen zu Ihrem Partner Center-Konto

Sie können eine Gruppe aus dem Verzeichnis Ihrer Organisation für Ihr Partner Center-Konto hinzufügen. Daraufhin kann jeder Benutzer, der Mitglied dieser Gruppe ist, mit den Berechtigungen der dieser Gruppe zugewiesenen Rolle darauf zugreifen.

### <a name="add-groups-from-your-organizations-directory"></a>Hinzufügen von Gruppen aus dem Verzeichnis der Organisation

1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Partner Center), und wählen Sie dann die **entwicklereinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2. Wählen Sie die Seite " **Benutzer** " **Hinzufügen von Gruppen**aus.
2.  Wählen Sie in der angezeigten Liste eine oder mehrere Gruppen aus. Im Suchfeld können Sie nach bestimmten Gruppen suchen.
    > [!TIP]
    > Wenn Sie mehr als einer Gruppe hinzufügen zu Ihrem Partner Center-Konto auswählen, müssen Sie diesen die gleiche Rolle oder Gruppe von benutzerdefinierten Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Gruppen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierte Berechtigungen.

3.  Wenn Sie die Gruppen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
4.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Gruppen wünschen. Alle Mitglieder der Gruppe werden möglicherweise Zugriff auf Ihr Partner Center-Konto mit den Berechtigungen, dass Sie auf die Gruppe, unabhängig von den Rollen/Berechtigungen mit individuellen Konto anwenden.
5.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-group-account-in-your-organizations-directory-and-add-it-to-your-partner-center-account"></a>Erstellen eines neuen Gruppenkontos in das Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Partner Center-Konto

Wenn Sie einer völlig neuen Gruppe Zugriff auf Partner Center gewähren möchten, können Sie im Abschnitt **Benutzer** eine neue Gruppe erstellen. Beachten Sie, dass die neue Gruppe im Verzeichnis Ihrer Organisation und nicht nur im Partner Center-Konto erstellt wird.

1.  Klicken Sie auf der Seite " **Benutzer** " (unter **entwicklereinstellungen**) auf **Gruppen hinzufügen**.
2.  Wählen Sie auf der nächsten Seite **neue Gruppe**ein.
3.  Geben Sie den Anzeigenamen für die neue Gruppe ein.
4.  Geben Sie die [Rollen oder angepasste Berechtigungen](set-custom-permissions-for-account-users.md) für die Gruppe an. Alle Mitglieder der Gruppe werden möglicherweise Zugriff auf Ihr Partner Center-Konto mit den Berechtigungen, dass Sie auf die Gruppe, unabhängig von den Rollen/Berechtigungen mit individuellen Konto anwenden.
5.  Wählen Sie den/die Benutzer, die der neuen Gruppe in der Liste zugewiesen werden sollen, aus der angezeigten Liste aus. Im Suchfeld können Sie nach bestimmten Benutzern suchen.
6.  Wenn Sie mit der Auswahl der Benutzer fertig sind, klicken Sie auf **Ausgewählte hinzufügen**, um diese der neuen Gruppe hinzuzufügen.
7.  Klicken Sie auf **Speichern**.


<span id="azure-ad-applications" />

## <a name="add-azure-ad-applications-to-your-partner-center-account"></a>Hinzufügen von Azure AD-Anwendungen zu Ihrem Partner Center-Konto

Sie können Anwendungen oder Dienste, die Teil Ihrer Organisation Azure AD auf Ihr Partner Center-Konto zugreifen. Diese Benutzerkonten für die Azure AD-Anwendung können zum Aufrufen der über [Microsoft Store Services](../monetize/using-windows-store-services.md) bereitgestellten REST-APIs genutzt werden.


### <a name="add-azure-ad-applications-from-your-organizations-directory"></a>Hinzufügen von Azure AD-Anwendungen aus dem Verzeichnis Ihrer Organisation

1.  1.  Wählen Sie das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Partner Center), und wählen Sie dann die **entwicklereinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Benutzer**aus.
2. Wählen Sie auf der Seite **Benutzer** **Azure AD-Anwendungen hinzufügen** aus.
3.  Wählen Sie eine oder mehrere Azure AD-Anwendungen aus der angezeigten Liste aus. Mithilfe des Suchfelds können Sie nach bestimmten Azure AD-Anwendungen suchen.
    > [!TIP]
    > Wenn Sie mehr als eine Azure AD-Anwendung hinzufügen zu Ihrem Partner Center-Konto auswählen, müssen Sie diesen die gleiche Rolle oder Gruppe von benutzerdefinierten Berechtigungen zuweisen. Wiederholen Sie zum Hinzufügen mehrerer Azure AD-Anwendungen mit anderen Rollenberechtigungen die unten beschriebenen Schrittefür alle Rollen oder benutzerdefinierten Berechtigungen.

4.  Wenn Sie die Azure AD-Anwendungen ausgewählt haben, klicken Sie auf **Ausgewählte hinzufügen**.
5.  Geben Sie im Abschnitt **Rollen** an, welche [Rollen oder angepassten Berechtigungen](set-custom-permissions-for-account-users.md) Sie für die ausgewählten Azure AD-Anwendungen wünschen.
6.  Klicken Sie auf **Speichern**.


### <a name="create-a-new-azure-ad-application-account-in-your-organizations-directory-and-add-it-to-your-partner-center-account"></a>Erstellen Sie ein neues Azure AD-Anwendung für das Konto im Verzeichnis Ihrer Organisation und hinzufügen auf Ihr Partner Center-Konto

Wenn Sie Partner Center-Zugriff auf einem völlig neuen Azure AD-Anwendungskonto gewähren möchten, können Sie im Abschnitt **Benutzer** erstellen. Beachten Sie, dass dies ein neues Konto im Verzeichnis Ihrer Organisation, nicht nur im Partner Center-Konto erstellt wird.

> [!TIP]
> Wenn Sie diese Azure AD-Anwendung hauptsächlich für Partner Center-Authentifizierung verwenden, und Benutzer direkt auf Sie zugreifen nicht benötigen, können Sie jede beliebige gültige Adresse für die **Antwort-URL** und **App-ID-URI**, eingeben, solange diese Werte nicht von allen anderen Azure verwendet werden AD-Anwendung in Ihrem Verzeichnis.

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

Wenn die Azure AD-App Daten in Microsoft Azure AD liest und schreibt, benötigt sie einen Schlüssel. Sie können Schlüssel für eine Azure AD-Anwendung erstellen, indem Sie ihre Informationen im Partner Center bearbeiten. Sie können auch Schlüssel entfernen, die nicht mehr benötigt werden.

1.  Wählen Sie aus der Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen der Azure AD-App.
    > [!TIP]
    > Wenn Sie auf den Namen der Azure AD-App klicken, sehen Sie alle aktiven Schlüssel für die Azure AD-App mit dem jeweiligen Erstellungs- und Ablaufdatum des Schlüssels. Klicken Sie auf **Entfernen**, um einen nicht mehr benötigten Schlüssel zu entfernen.

2.  Um einen neuen Schlüssel hinzuzufügen, wählen Sie **neuen Schlüssel hinzufügen**.
3.  Es wird ein Bildschirm mit den Werten für **Client-ID** und **Schlüssel** angezeigt.
    > [!IMPORTANT]
    > Drucken oder kopieren Sie diese Informationen, da Sie nach dem Verlassen dieser Seite nicht mehr darauf zugreifen können.

4.  Wenn Sie weitere Schlüssel erstellen möchten, wählen Sie **eine andere Schlüssel hinzufügen**.

<span id="edit" />

## <a name="edit-a-user-group-or-azure-ad-application"></a>Bearbeiten von Benutzern, Gruppen oder Azure AD-Anwendungen

Nachdem Sie Benutzer, Gruppen oder Azure AD-Anwendungen zu Ihrem Partner Center-Konto hinzugefügt haben, können Sie Änderungen an deren Kontoinformationen vornehmen. 

> [!IMPORTANT]
> Änderungen an der [Rolle oder Berechtigung](set-custom-permissions-for-account-users.md) wirken sich nur auf Partner Center-Zugriff aus. Alle anderen Änderungen (z. B. das ändern den Namen eines Benutzers oder der Gruppenmitgliedschaft oder der Antwort-URL und App-ID-URI für eine Azure AD-Anwendung) werden in Ihrer Organisation Azure AD-Mandanten ebenfalls im Partner Center-Konto widergespiegelt. 

1.  Wählen Sie die Seite " **Benutzer** " (unter **kontoeinstellungen**) den Namen des Benutzer-, Gruppen oder Azure AD-Anwendungskontos, das Sie bearbeiten möchten.
2.  Nehmen Sie die gewünschten Änderungen vor. Die Elemente, die Sie bearbeiten können, lauten wie folgt:
    -   Sie können den Vornamen, den Nachnamen oder den Benutzernamen eines **Benutzers** bearbeiten. Sie können ebenfalls Gruppen im Abschnitt **Gruppenmitgliedschaft** auswählen oder deaktivieren, um die Gruppenmitgliedschaft zu aktualisieren.
    -   Für eine **Gruppe** können Sie den Namen der Gruppe bearbeiten. (Um Gruppenmitgliedschaft zu aktualisieren, bearbeiten Sie die Benutzer, die Sie der Gruppe hinzufügen oder daraus entfernen möchten und nehmen Sie im Abschnitt **Gruppenmitgliedschaft** Änderungen vor.)
    -   Für eine **Azure AD-Anwendung** können Sie neue Werte für die **Antwort-URL** oder **App-ID-URI** eingeben.
    Denken Sie daran, dass diese Änderungen in das Verzeichnis Ihrer Organisation auch im Partner Center-Konto vorgenommen werden.
3.  Aktivieren Sie für Änderungen im Zusammenhang mit Zugriff auf Partner Center oder deaktivieren Sie die Rolle(n), die Sie anwenden möchten, oder wählen Sie **Anpassen Berechtigungen** und die gewünschten Änderungen vornehmen möchten. Diese Änderungen nur wirken auf Partner Center zugreifen und ändert sich nicht auf die Berechtigungen in Azure AD-Mandanten Ihrer Organisation.
3.  Klicken Sie auf **Speichern**.


## <a name="view-history-for-account-users"></a>Verlauf für Kontobenutzer anzeigen

Als Kontobesitzer können Sie den detaillierten Browserverlauf für alle weiteren Benutzer, die Sie dem Konto hinzugefügt haben, anzeigen.

Wählen Sie auf der Seite " **Benutzer** " (unter **kontoeinstellungen**) den Link unter **letzte Aktivität** für den Benutzer, dessen Browserverlauf Sie überprüfen möchten. Sie können die URLs aller Seiten anzeigen, die der Benutzer in den letzten 30Tagen besucht habt.

<span id="remove" />

## <a name="remove-users-groups-and-azure-ad-applications"></a>Entfernen von Benutzern, Gruppen und Azure AD-Anwendungen

Um einen Benutzer, Gruppen oder Azure AD-Anwendung aus Ihrem Partner Center-Konto zu entfernen, wählen Sie die Verknüpfung **Entfernen** , die über den Namen auf der Seite " **Benutzer** " angezeigt wird. Nachdem Sie bestätigt haben, dass Sie sie entfernen möchten, werden diese Benutzer, Gruppen oder Azure AD-Anwendung nicht mehr auf Ihr Partner Center-Konto zugreifen (es sei denn, Sie es später erneut hinzufügen).

> [!IMPORTANT]
> Entfernen eines Benutzers, eine Gruppe oder eine Azure AD-Anwendung bedeutet, dass es nicht mehr auf Ihr Partner Center-Konto zugreifen kann. Dadurch werden **nicht** die betreffenden Benutzer, Gruppen oder Azure AD-Anwendungen aus dem Verzeichnis der Organisation gelöscht.

 

