---
author: jnHs
Description: Add users to your Dev Center account and assign them roles with specific permissions.
title: Verwalten von Kontobenutzern
ms.assetid: 9245F0D0-7D8F-4741-AFB4-FBA5601D0A9B
ms.author: wdg-dev-content
ms.date: 07/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Kontobenutzer, Verwalten von Benutzern, Azure Ad, Verwalten mehrerer Benutzer, mehrere Benutzer
ms.localizationpriority: medium
ms.openlocfilehash: bef703958f8f04cd55d887dfa8840d1ed3fbeba5
ms.sourcegitcommit: 7efffcc715a4be26f0cf7f7e249653d8c356319b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "3115868"
---
# <a name="manage-account-users"></a><span data-ttu-id="d59ba-103">Verwalten von Kontobenutzern</span><span class="sxs-lookup"><span data-stu-id="d59ba-103">Manage account users</span></span>

<span data-ttu-id="d59ba-104">Sie können mit Azure Active Directory Ihrem Dev Center-Konto Benutzer hinzufügen und diese verwalten.</span><span class="sxs-lookup"><span data-stu-id="d59ba-104">You can use Azure Active Directory to add and manage additional users in your Dev Center account.</span></span> <span data-ttu-id="d59ba-105">Sie können die Rolle oder benutzerdefinierte Berechtigung für jeden Benutzer bestimmen.</span><span class="sxs-lookup"><span data-stu-id="d59ba-105">You can define the role or custom permissions that each user should have.</span></span> <span data-ttu-id="d59ba-106">Sie können eine Rolle auch einer Gruppe von Benutzern oder einer Azure AD-App zuweisen.</span><span class="sxs-lookup"><span data-stu-id="d59ba-106">You can also assign a role to a group of users, or to an Azure AD application.</span></span>

<span data-ttu-id="d59ba-107">Zum Hinzufügen und Verwalten von Kontobenutzern müssen Sie zunächst dem Azure Active Directory Ihres Unternehmens Ihr Dev Center-Konto zuordnen.</span><span class="sxs-lookup"><span data-stu-id="d59ba-107">In order to add and manage account users, you must first associate your Dev Center account with your organization's Azure Active Directory.</span></span> 

<span data-ttu-id="d59ba-108">In diesem Abschnitt werden die folgenden Schritte beschrieben:</span><span class="sxs-lookup"><span data-stu-id="d59ba-108">This section describes how to do the following:</span></span>

-   [<span data-ttu-id="d59ba-109">Zuordnen Ihres Azure Active Directory zum Dev Center-Konto</span><span class="sxs-lookup"><span data-stu-id="d59ba-109">Associate Azure Active Directory with your Dev Center account</span></span>](associate-azure-ad-with-dev-center.md)
-   [<span data-ttu-id="d59ba-110">Hinzufügen von Benutzern, Gruppen und Azure AD-Anwendungen zu Ihrem Dev Center-Konto</span><span class="sxs-lookup"><span data-stu-id="d59ba-110">Add users, groups, and Azure AD applications to your Dev Center account</span></span>](add-users-groups-and-azure-ad-applications.md)
-   [<span data-ttu-id="d59ba-111">Legen Sie Rollen und benutzerdefinierte Berechtigungen für Kontenbenutzer fest</span><span class="sxs-lookup"><span data-stu-id="d59ba-111">Set roles and custom permissions for account users</span></span>](set-custom-permissions-for-account-users.md)

> [!TIP]
> <span data-ttu-id="d59ba-112">Dieser Abschnitt gilt speziell für das Entwicklerprogramm für Windows-Apps. Das Zuordnen eines Mandanten und das Verwalten von Benutzern für Konten im Windows-Hardware-Entwicklerprogramm (weitere Informationen finden Sie unter [Dashboard-Verwaltung](https://docs.microsoft.com/windows-hardware/drivers/dashboard/dashboard-administration)) oder im Windows-Desktopanwendungsprogramm verhält sich allerdings ähnlich (Weitere Informationen finden Sie unter [Windows-Desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#add-and-manage-account-users)).</span><span class="sxs-lookup"><span data-stu-id="d59ba-112">This section is specific to the Windows apps developer program, but associating a tenant and managing users works similarly for accounts in the Windows Hardware Developer Program (see [Dashboard Administration](https://docs.microsoft.com/windows-hardware/drivers/dashboard/dashboard-administration) for more info) or in the Windows Desktop Application Program (see [Windows Desktop Application Program](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#add-and-manage-account-users) for more info).</span></span>
