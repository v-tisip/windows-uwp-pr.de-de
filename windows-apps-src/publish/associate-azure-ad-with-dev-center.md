---
author: jnHs
Description: "Zum Hinzufügen und Verwalten von Kontobenutzern müssen Sie zunächst dem Azure Active Directory Ihres Unternehmens Ihr Dev Center-Konto zuordnen."
title: Zuordnen Ihres Azure Active Directory zum Dev Center-Konto
ms.author: wdg-dev-content
ms.date: 07/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: ace9470cc707206461baa8c3dd72828ea68a8eb4
ms.sourcegitcommit: eaacc472317eef343b764d17e57ef24389dd1cc3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2017
---
# <a name="associate-azure-active-directory-with-your-dev-center-account"></a>Zuordnen Ihres Azure Active Directory zum Dev Center-Konto

Zum [Hinzufügen und Verwalten von Kontobenutzern](add-users-groups-and-azure-ad-applications.md) müssen Sie zunächst dem Azure Active Directory Ihres Unternehmens Ihr Dev Center-Konto zuordnen. 

Windows Dev Center nutzt Azure AD zum Verwalten mehrerer Benutzer und zum Zuweisen von Rollen. Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD. Andernfalls können Sie innerhalb von Dev Center ohne zusätzliche Kosten einen neuen Azure AD-Mandanten erstellen.

> [!IMPORTANT]
> Um Azure AD Ihrem Dev Center-Konto zuzuordnen, müssen Sie sich bei Ihrer Azure AD-Mandantenverwaltung mit einem Konto als [globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) anmelden.
> 
> Nachdem Sie Ihr Dev Center-Konto dem Azure AD zugeordnet haben, müssen Sie sich am Dev Center stets mithilfe des globalen Azure AD-Administratorkontos (und nicht mit einem persönlichen Microsoft-Konto) anmelden, um Kontobenutzer hinzuzufügen und zu verwalten.

Beachten Sie, dass einem Azure AD-Mandanten jeweils nur ein Dev Center-Konto zugeordnet werden kann. Ebenso kann einem Dev Center-Konto auch nur ein Azure AD-Mandant zugeordnet werden. Nachdem Sie diese Zuordnung festgelegt haben, können Sie sie erst nach Rücksprache mit dem Support wieder entfernen.


## <a name="associate-your-dev-center-account-with-your-organizations-existing-azure-ad-tenant"></a>Ordnen Sie Ihr Dev Center-Konto dem vorhandenen Azure AD-Mandanten Ihrer Organisation zu

Wenn Ihre Organisation Azure AD bereits verwendet, gehen Sie folgendermaßen vor, um Ihr Dev Center-Konto zu verknüpfen.

1.  Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.
2.  Klicken Sie auf die **Schaltfläche zum Zuordnen Ihres Dev Center-Kontos zu Azure AD**.
3.  Melden Sie sich bei Ihrem AzureAD-Konto an. Dieses Konto muss über Berechtigungen des [globalen Administrators](http://go.microsoft.com/fwlink/?LinkId=746654) verfügen, damit die Zuordnung eingerichtet werden kann.
4.  Überprüfen Sie den Organisations- und den Domänennamen für den Azure AD-Mandant. Klicken Sie zum Abschließen der Zuordnung auf **Bestätigen**.
5.  Wenn die Zuordnung erfolgreich abgeschlossen wurde, können Sie nun auf dem Abschnitt **Benutzer verwalten** Ihres Dev Centers Kontobenutzer hinzufügen und verwalten.


## <a name="create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account"></a>Erstellen eines völlig neuen Azure AD, um diesem Ihr Dev Center-Konto zuzuordnen

Wenn Sie ein neues Azure AD einrichten müssen, um diesem Ihr Dev Center-Konto zuzuordnen, gehen Sie folgendermaßen vor.

1.  Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.
2.  Klicken Sie auf die Schaltfläche **Neues Azure AD erstellen**.
3.  Geben Sie die Verzeichnisinformationen für das neue Azure AD ein:
 - **Domänenname**: Der eindeutige Name, der für Ihre Azure AD-Domäne verwendet wird, zusammen mit „.onmicrosoft.com“. Wenn Sie beispielsweise „beispiel“ eingegeben haben, wäre Ihre Azure AD-Domäne „beispiel.onmicrosoft.com“.
 - **Kontakt-E-Mail-Adresse**: Eine E-Mail-Adresse, unter der wir Sie hinsichtlich Ihres Kontos erreichen können, wenn notwendig.
 - **Benutzerkontoinformationen für den globalen Administrator**: Vorname, Nachname, Benutzername und Kennwort, die Sie für das neue globale Administratorkonto verwenden möchten.
4.  Klicken Sie auf **Erstellen**, um die neue Domäne und die Kontoinformationen zu bestätigen.
5.  Melden Sie sich mit dem neuen Azure AD-Benutzernamen und -Kennwort als globaler Administrator an, um [zusätzliche Kontobenutzer hinzuzufügen und zu verwalten](add-users-groups-and-azure-ad-applications.md).



