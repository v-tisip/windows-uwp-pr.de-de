---
author: jnHs
Description: In order to add and manage account users, you must first associate your Dev Center account with your organization's Azure Active Directory.
title: Zuordnen Ihres Azure Active Directory zum Dev Center-Konto
ms.author: wdg-dev-content
ms.date: 08/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Azure Ad, Azure-Mandant, AAD-Mandant, Azure AD-Mandant, Mandantenverwaltung, Mandanten
ms.localizationpriority: medium
ms.openlocfilehash: dd729d76705849c981516109da39bbd27c140286
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4150619"
---
# <a name="associate-azure-active-directory-with-your-dev-center-account"></a>Zuordnen Ihres Azure Active Directory zum Dev Center-Konto

Zum [Hinzufügen und Verwalten von Kontobenutzern](add-users-groups-and-azure-ad-applications.md) müssen Sie zunächst dem Azure Active Directory Ihres Unternehmens Ihr Dev Center-Konto zuordnen. 

Windows Dev Center nutzt Azure AD zum Verwalten mehrerer Benutzer und zum Zugriff auf das Konto. Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD. Andernfalls können Sie innerhalb von Dev Center ohne zusätzliche Kosten einen neuen Azure AD-Mandanten erstellen.

> [!TIP]
> Dieses Thema gilt speziell für das Entwicklerprogramm für Windows-Apps. Das Zuordnen eines Mandanten und das Verwalten von Benutzern für Konten im Desktopanwendungsprogramm (siehe [Windows-Desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#add-and-manage-account-users), um weitere Informationen zu erhalten) und im Windows-Hardware-Entwicklerprogramm verhält sich allerdings ähnlich (Verweise auf die **Manager**rolle gelten dabei ebenfalls für die **Administrator**rolle. Weitere Informationen finden Sie unter [Dashboard-Verwaltung](https://docs.microsoft.com/windows-hardware/drivers/dashboard/dashboard-administration)).

Ebenso können mehrere Dev Center-Konten einem Azure AD-Mandant zugeordnet werden. Sie müssen nur einen Azure AD-Mandanten haben, der mit Ihrem Dev Center-Konto verknüpft ist, um mehrere Kontobenutzer hinzuzufügen, Sie haben allerdings auch die Möglichkeit, mehrere Azure AD-Mandanten einem einzelnen Dev Center-Konto hinzuzufügen. Jeder Benutzer mit einer **Manager**-Rolle im Dev Center-Konto hat die Möglichkeit zum Hinzufügen und Entfernen von Azure AD-Mandanten.

> [!IMPORTANT]
> Nachdem Sie Ihr Dev Center-Konto dem Azure AD-Mandant zugeordnet haben, müssen Sie sich am Dev Center als Anwender im gleichen Mandanten anmelden, der die **Manager**-Rolle hat, um Kontobenutzer hinzuzufügen und zu verwalten.


## <a name="associate-your-dev-center-account-with-your-organizations-existing-azure-ad-tenant"></a>Ordnen Sie Ihr Dev Center-Konto dem vorhandenen Azure AD-Mandanten Ihrer Organisation zu

Wenn Ihre Organisation Azure AD bereits verwendet, gehen Sie folgendermaßen vor, um Ihr Dev Center-Konto zu verknüpfen.

1.  Wählen Sie aus dem [Windows Dev Center-Dashboard](https://partner.microsoft.com/dashboard)das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Dashboards), und wählen Sie dann **kontoeinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Mandanten**aus.
2.  Wählen Sie **Zuordnen von AzureAD zu Ihrem Dev Center-Konto**.
3.  Geben Sie Ihre Azure AD-Anmeldeinformationen für den Mandanten ein, den Sie zuordnen möchten.
4.  Überprüfen Sie den Organisations- und den Domänennamen für den Azure AD-Mandant. Wählen Sie zum Abschließen der Zuordnung **Bestätigen** aus.
5.  Wenn die Zuordnung erfolgreich abgeschlossen wurde, können Sie nun auf dem Abschnitt **Benutzer** Ihres Dev Centers Kontobenutzer hinzufügen und verwalten.

> [!IMPORTANT]
> Um neue Benutzer zu erstellen oder andere Änderungen an Ihrem Azure AD vorzunehmen, müssen Sie sich mit einem Konto beim Azure AD-Mandanten anmelden, das über [über globale Administratorberechtigungen](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) für den Mandanten verfügt. Sie benötigen allerdings keine globale Administratorberechtigungen, um Mandanten zuzuordnen oder bereits vorhandene Benutzer dem Mandanten Dev Center-Konto hinzufügen.


## <a name="create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account"></a>Erstellen eines völlig neuen Azure AD, um diesem Ihr Dev Center-Konto zuzuordnen

Wenn Sie ein neues Azure AD einrichten müssen, um diesem Ihr Dev Center-Konto zuzuordnen, gehen Sie folgendermaßen vor.

1.  Wählen Sie aus dem [Windows Dev Center-Dashboard](https://partner.microsoft.com/dashboard)das Zahnradsymbol (in der Nähe der oberen rechten Ecke des Dashboards), und wählen Sie dann **kontoeinstellungen**. Wählen Sie im Menü " **Einstellungen** " **Mandanten**aus.
2.  Wählen Sie **Neues Azure AD erstellen**.
3.  Geben Sie die Verzeichnisinformationen für das neue Azure AD ein:
    - **Domänenname**: Der eindeutige Name, der für Ihre Azure AD-Domäne verwendet wird, zusammen mit „.onmicrosoft.com“. Wenn Sie beispielsweise „beispiel“ eingegeben haben, wäre Ihre Azure AD-Domäne „beispiel.onmicrosoft.com“.
    - **Kontakt-E-Mail-Adresse**: Eine E-Mail-Adresse, unter der wir Sie hinsichtlich Ihres Kontos erreichen können, wenn notwendig.
    - **Benutzerkontoinformationen für den globalen Administrator**: Vorname, Nachname, Benutzername und Kennwort, die Sie für das neue globale Administratorkonto verwenden möchten.
4.  Klicken Sie auf **Erstellen**, um die neue Domäne und die Kontoinformationen zu bestätigen.
5.  Melden Sie sich mit dem neuen Azure AD-Benutzernamen und -Kennwort als globaler Administrator an, um [zusätzliche Kontobenutzer hinzuzufügen und zu verwalten](add-users-groups-and-azure-ad-applications.md).


## <a name="manage-azure-ad-tenant-associations"></a>Verwalten von Azure AD-Mandantenzuordnungen

Nachdem Sie einen Azure AD-Mandanten mit Ihrem Dev Center-Konto verknüpft haben, können Sie neue Mandanten hinzufügen oder vorhandene Mandanten aus der Seite **Mandanten** entfernen.


### <a name="add-multiple-azure-ad-tenants-to-your-dev-center-account"></a>Hinzufügen von mehreren Azure AD-Mandanten zu Ihrem Dev Center-Konto

Jeder Benutzer mit einer **Manager**-Rolle für das Dev Center-Konto kann Azure AD-Mandanten mit diesem Konto verknüpfen.

Wählen Sie zum Zuordnen eines neuen Mandanten **Associate another Azure AD tenant** aus und befolgen Sie die oben angegebenen Schritte. Beachten Sie, dass Sie zur Angabe Ihrer Anmeldeinformationen in dem Azure AD-Mandanten aufgefordert werden, den Sie verknüpfen möchten.


### <a name="remove-an-azure-ad-tenant-from-your-dev-center-account"></a>Entfernen Sie einen Azure AD-Mandanten aus Ihrem Dev Center-Konto

Jeder Benutzer mit einer **Manager**-Rolle für das Dev Center-Konto kann Azure AD-Mandanten von diesem Konto entfernen.

> [!IMPORTANT]
> Beim Entfernen eines Mandanten können sich alle Benutzer, die dem Dev Center-Konto über diesen Mandanten hinzugefügt wurden, nicht mehr auf dem Konto anmelden. 

Um einen Mandanten zu entfernen, suchen Sie den Namen auf der Seite " **Mandanten** " (in den **kontoeinstellungen**), und wählen Sie dann **Entfernen**. Sie werden aufgefordert, zu bestätigen, dass Sie den Mandanten entfernen möchten. Danach können sich keine Dev Center-Benutzer dieses Mandanten im Dev Center-Konto mehr anmelden, und alle Berechtigungen, die Sie für diesen Benutzer konfiguriert haben, werden entfernt.

> [!TIP]
> Sie können keinen Mandanten entfernen, wenn Sie über ein Konto im gleichen Mandanten derzeit in Dev Center angemeldet sind. Um einen Mandanten zu entfernen, müssen Sie sich im Dev Center als **Manager** für einen anderen Mandanten anmelden, der dem Konto zugeordnet ist. Wenn nur ein Mandanten dem Konto zugeordnet ist, kann dieser Mandant nur nach der Anmeldung mithilfe des Microsoft-Kontos entfernt werden, das das Konto eröffnete.


