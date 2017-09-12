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
# <a name="associate-azure-active-directory-with-your-dev-center-account"></a><span data-ttu-id="af639-104">Zuordnen Ihres Azure Active Directory zum Dev Center-Konto</span><span class="sxs-lookup"><span data-stu-id="af639-104">Associate Azure Active Directory with your Dev Center account</span></span>

<span data-ttu-id="af639-105">Zum [Hinzufügen und Verwalten von Kontobenutzern](add-users-groups-and-azure-ad-applications.md) müssen Sie zunächst dem Azure Active Directory Ihres Unternehmens Ihr Dev Center-Konto zuordnen.</span><span class="sxs-lookup"><span data-stu-id="af639-105">In order to [add and manage account users](add-users-groups-and-azure-ad-applications.md), you must first associate your Dev Center account with your organization's Azure Active Directory.</span></span> 

<span data-ttu-id="af639-106">Windows Dev Center nutzt Azure AD zum Verwalten mehrerer Benutzer und zum Zuweisen von Rollen.</span><span class="sxs-lookup"><span data-stu-id="af639-106">Windows Dev Center leverages Azure AD for multi-user management and roles assignment.</span></span> <span data-ttu-id="af639-107">Wenn in Ihrer Organisation bereits mit Office365 oder anderen Unternehmensdiensten von Microsoft gearbeitet wird, verfügen Sie bereits über Azure AD.</span><span class="sxs-lookup"><span data-stu-id="af639-107">If your organization already uses Office 365 or other business services from Microsoft, you already have Azure AD.</span></span> <span data-ttu-id="af639-108">Andernfalls können Sie innerhalb von Dev Center ohne zusätzliche Kosten einen neuen Azure AD-Mandanten erstellen.</span><span class="sxs-lookup"><span data-stu-id="af639-108">Otherwise, you can create a new Azure AD tenant from within Dev Center at no additional charge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af639-109">Um Azure AD Ihrem Dev Center-Konto zuzuordnen, müssen Sie sich bei Ihrer Azure AD-Mandantenverwaltung mit einem Konto als [globaler Administrator](http://go.microsoft.com/fwlink/?LinkId=746654) anmelden.</span><span class="sxs-lookup"><span data-stu-id="af639-109">To associate Azure AD with your Dev Center account, you will need to sign in to your Azure AD tenant with a [global administrator](http://go.microsoft.com/fwlink/?LinkId=746654) account.</span></span>
> 
> <span data-ttu-id="af639-110">Nachdem Sie Ihr Dev Center-Konto dem Azure AD zugeordnet haben, müssen Sie sich am Dev Center stets mithilfe des globalen Azure AD-Administratorkontos (und nicht mit einem persönlichen Microsoft-Konto) anmelden, um Kontobenutzer hinzuzufügen und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="af639-110">After you associate your Dev Center account with Azure AD, you’ll always need sign in to Dev Center using the Azure AD global administrator account (and not a personal Microsoft account) in order to add and manage account users.</span></span>

<span data-ttu-id="af639-111">Beachten Sie, dass einem Azure AD-Mandanten jeweils nur ein Dev Center-Konto zugeordnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="af639-111">Note that only one Dev Center account can be associated with an Azure AD tenant.</span></span> <span data-ttu-id="af639-112">Ebenso kann einem Dev Center-Konto auch nur ein Azure AD-Mandant zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="af639-112">Similarly, only one Azure AD tenant can be associated with a Dev Center account.</span></span> <span data-ttu-id="af639-113">Nachdem Sie diese Zuordnung festgelegt haben, können Sie sie erst nach Rücksprache mit dem Support wieder entfernen.</span><span class="sxs-lookup"><span data-stu-id="af639-113">Once you establish the association, you won't be able to remove it without contacting support.</span></span>


## <a name="associate-your-dev-center-account-with-your-organizations-existing-azure-ad-tenant"></a><span data-ttu-id="af639-114">Ordnen Sie Ihr Dev Center-Konto dem vorhandenen Azure AD-Mandanten Ihrer Organisation zu</span><span class="sxs-lookup"><span data-stu-id="af639-114">Associate your Dev Center account with your organization’s existing Azure AD tenant</span></span>

<span data-ttu-id="af639-115">Wenn Ihre Organisation Azure AD bereits verwendet, gehen Sie folgendermaßen vor, um Ihr Dev Center-Konto zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="af639-115">If your organization already uses Azure AD, follow these steps to link your Dev Center account.</span></span>

1.  <span data-ttu-id="af639-116">Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.</span><span class="sxs-lookup"><span data-stu-id="af639-116">Go to your **Account settings** and click **Manage users**.</span></span>
2.  <span data-ttu-id="af639-117">Klicken Sie auf die **Schaltfläche zum Zuordnen Ihres Dev Center-Kontos zu Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="af639-117">Click the **Associate Azure AD with your Dev Center account** button.</span></span>
3.  <span data-ttu-id="af639-118">Melden Sie sich bei Ihrem AzureAD-Konto an.</span><span class="sxs-lookup"><span data-stu-id="af639-118">Sign in to your Azure AD account.</span></span> <span data-ttu-id="af639-119">Dieses Konto muss über Berechtigungen des [globalen Administrators](http://go.microsoft.com/fwlink/?LinkId=746654) verfügen, damit die Zuordnung eingerichtet werden kann.</span><span class="sxs-lookup"><span data-stu-id="af639-119">This account must have [global administrator](http://go.microsoft.com/fwlink/?LinkId=746654) permission in order to set up the association.</span></span>
4.  <span data-ttu-id="af639-120">Überprüfen Sie den Organisations- und den Domänennamen für den Azure AD-Mandant.</span><span class="sxs-lookup"><span data-stu-id="af639-120">Review the organization and domain name for your Azure AD tenant.</span></span> <span data-ttu-id="af639-121">Klicken Sie zum Abschließen der Zuordnung auf **Bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="af639-121">To complete the association, click **Confirm**.</span></span>
5.  <span data-ttu-id="af639-122">Wenn die Zuordnung erfolgreich abgeschlossen wurde, können Sie nun auf dem Abschnitt **Benutzer verwalten** Ihres Dev Centers Kontobenutzer hinzufügen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="af639-122">If the association is successful, you will then be ready to add and manage account users in the **Manage users** section in Dev Center.</span></span>


## <a name="create-a-brand-new-azure-ad-to-associate-with-your-dev-center-account"></a><span data-ttu-id="af639-123">Erstellen eines völlig neuen Azure AD, um diesem Ihr Dev Center-Konto zuzuordnen</span><span class="sxs-lookup"><span data-stu-id="af639-123">Create a brand new Azure AD to associate with your Dev Center account</span></span>

<span data-ttu-id="af639-124">Wenn Sie ein neues Azure AD einrichten müssen, um diesem Ihr Dev Center-Konto zuzuordnen, gehen Sie folgendermaßen vor.</span><span class="sxs-lookup"><span data-stu-id="af639-124">If you need to set up a new Azure AD to link with your Dev Center account, follow these steps.</span></span>

1.  <span data-ttu-id="af639-125">Wechseln Sie zu den **Kontoeinstellungen**, und klicken Sie auf **Benutzer verwalten**.</span><span class="sxs-lookup"><span data-stu-id="af639-125">Go to your **Account settings** and click **Manage users**.</span></span>
2.  <span data-ttu-id="af639-126">Klicken Sie auf die Schaltfläche **Neues Azure AD erstellen**.</span><span class="sxs-lookup"><span data-stu-id="af639-126">Click the **Create new Azure AD** button.</span></span>
3.  <span data-ttu-id="af639-127">Geben Sie die Verzeichnisinformationen für das neue Azure AD ein:</span><span class="sxs-lookup"><span data-stu-id="af639-127">Enter the directory information for your new Azure AD:</span></span>
 - <span data-ttu-id="af639-128">**Domänenname**: Der eindeutige Name, der für Ihre Azure AD-Domäne verwendet wird, zusammen mit „.onmicrosoft.com“.</span><span class="sxs-lookup"><span data-stu-id="af639-128">**Domain name**: The unique name that we’ll use for your Azure AD domain, along with “.onmicrosoft.com”.</span></span> <span data-ttu-id="af639-129">Wenn Sie beispielsweise „beispiel“ eingegeben haben, wäre Ihre Azure AD-Domäne „beispiel.onmicrosoft.com“.</span><span class="sxs-lookup"><span data-stu-id="af639-129">For example, if you entered “example”, your Azure AD domain would be “example.onmicrosoft.com”.</span></span>
 - <span data-ttu-id="af639-130">**Kontakt-E-Mail-Adresse**: Eine E-Mail-Adresse, unter der wir Sie hinsichtlich Ihres Kontos erreichen können, wenn notwendig.</span><span class="sxs-lookup"><span data-stu-id="af639-130">**Contact email**: An email address where we can contact you about your account if necessary.</span></span>
 - <span data-ttu-id="af639-131">**Benutzerkontoinformationen für den globalen Administrator**: Vorname, Nachname, Benutzername und Kennwort, die Sie für das neue globale Administratorkonto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="af639-131">**Global administrator user account info**: The first name, last name, username, and password that you want to use for the new global administrator account.</span></span>
4.  <span data-ttu-id="af639-132">Klicken Sie auf **Erstellen**, um die neue Domäne und die Kontoinformationen zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="af639-132">Click **Create** to confirm the new domain and account info.</span></span>
5.  <span data-ttu-id="af639-133">Melden Sie sich mit dem neuen Azure AD-Benutzernamen und -Kennwort als globaler Administrator an, um [zusätzliche Kontobenutzer hinzuzufügen und zu verwalten](add-users-groups-and-azure-ad-applications.md).</span><span class="sxs-lookup"><span data-stu-id="af639-133">Sign in with your new Azure AD global administrator username and password to begin [adding and managing additional account users](add-users-groups-and-azure-ad-applications.md).</span></span>



