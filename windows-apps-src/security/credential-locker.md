---
title: Schließfach für Anmeldeinformationen
description: In diesem Artikel wird beschrieben, wie Apps für die universelle Windows-Plattform (UWP) mit dem Schließfach für Anmeldeinformationen Benutzeranmeldeinformationen sicher speichern und abrufen können und sie zwischen den Geräten mit dem Microsoft-Konto des Benutzers per Roaming übertragen können.
ms.assetid: 7BCC443D-9E8A-417C-B275-3105F5DED863
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: c6412f28e60ed0401fb96098fd38128a37491c8d
ms.sourcegitcommit: 7efffcc715a4be26f0cf7f7e249653d8c356319b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "3128342"
---
# <a name="credential-locker"></a><span data-ttu-id="aaa43-104">Schließfach für Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="aaa43-104">Credential locker</span></span>




<span data-ttu-id="aaa43-105">In diesem Artikel wird beschrieben, wie Apps für die universelle Windows-Plattform (UWP) mit dem Schließfach für Anmeldeinformationen Benutzeranmeldeinformationen sicher speichern und abrufen können und sie zwischen den Geräten mit dem Microsoft-Konto des Benutzers per Roaming übertragen können.</span><span class="sxs-lookup"><span data-stu-id="aaa43-105">This article describes how Universal Windows Platform (UWP) apps can use the Credential Locker to securely store and retrieve user credentials, and roam them between devices with the user's Microsoft account.</span></span>

<span data-ttu-id="aaa43-106">Angenommen, Sie haben eine App, die eine Verbindung mit einem Dienst herstellt, um auf geschützte Dateien wie z.B. Mediendateien, soziale Netzwerke usw. zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-106">For example, you have an app that connects to a service to access protected resources such as media files, or social networking.</span></span> <span data-ttu-id="aaa43-107">Ihr Dienst erfordert Anmeldeinformationen für jeden Benutzer.</span><span class="sxs-lookup"><span data-stu-id="aaa43-107">Your service requires login information for each user.</span></span> <span data-ttu-id="aaa43-108">Sie haben die Benutzeroberfläche in Ihre App integriert, die den Benutzernamen und das Kennwort für den Benutzer abruft; diese Informationen werden dann für die Anmeldung des Benutzers am Dienst verwendet.</span><span class="sxs-lookup"><span data-stu-id="aaa43-108">You’ve built UI into your app that gets the username and password for the user, which is then used to log the user into the service.</span></span> <span data-ttu-id="aaa43-109">Mit der API des Schließfachs für Anmeldeinformationen können Sie den Benutzernamen und das Kennwort für den Benutzer speichern und diese Informationen leicht abrufen und den Benutzer automatisch anmelden, wenn er Ihre App das nächste Mal startet, und zwar unabhängig vom verwendeten Gerät.</span><span class="sxs-lookup"><span data-stu-id="aaa43-109">Using the Credential Locker API, you can store the username and password for your user and easily retrieve them and log the user in automatically the next time they open your app, regardless of what device they're on.</span></span>

<span data-ttu-id="aaa43-110">Benutzeranmeldedaten, die in CredentialLocker gespeichert sind, laufen *nicht* ab, sind *nicht* von [**ApplicationData.RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625) betroffen und werden *nicht* aufgrund von Inaktivität wie herkömmliche Roamingdaten bereinigt.</span><span class="sxs-lookup"><span data-stu-id="aaa43-110">User credentials stored in the CredentialLocker do *not* expire, are *not* affected by the [**ApplicationData.RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625), and will *not* be cleared out due to inactivity like traditional roaming data.</span></span> <span data-ttu-id="aaa43-111">Sie können jedoch nur bis zu 20 Anmeldedaten pro App in CredentialLocker speichern.</span><span class="sxs-lookup"><span data-stu-id="aaa43-111">However, you can only store up to 20 credentials per app in the CredentialLocker.</span></span>

<span data-ttu-id="aaa43-112">Die Funktionsweise des Schließfachs für Anmeldeinformationen sieht für Domänenkonten etwas anders aus.</span><span class="sxs-lookup"><span data-stu-id="aaa43-112">Credential locker works a little differently for domain accounts.</span></span> <span data-ttu-id="aaa43-113">Wenn für Ihr Microsoft-Konto Anmeldeinformationen gespeichert sind und Sie dieses Konto mit einem Domänenkonto (z.B. das Konto, das Sie bei der Arbeit nutzen) verknüpfen, wandern Ihre Anmeldeinformationen zu diesem Domänenkonto.</span><span class="sxs-lookup"><span data-stu-id="aaa43-113">If there are credentials stored with your Microsoft account, and you associate that account with a domain account (such as the account that you use at work), your credentials will roam to that domain account.</span></span> <span data-ttu-id="aaa43-114">Neue Anmeldeinformationen, die während einer Anmeldung mit dem Domänenkonto hinzugefügt werden, werden jedoch nicht servergespeichert.</span><span class="sxs-lookup"><span data-stu-id="aaa43-114">However, any new credentials added when signed on with the domain account won’t roam.</span></span> <span data-ttu-id="aaa43-115">So wird sichergestellt, dass private Anmeldeinformationen für die Domäne nicht außerhalb der Domäne verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="aaa43-115">This ensures that private credentials for the domain aren’t exposed outside of the domain.</span></span>

## <a name="storing-user-credentials"></a><span data-ttu-id="aaa43-116">Speichern von Benutzeranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="aaa43-116">Storing user credentials</span></span>


1.  <span data-ttu-id="aaa43-117">Rufen Sie mithilfe des [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081)-Objekts aus dem [**Windows.Security.Credentials**](https://msdn.microsoft.com/library/windows/apps/br227089)-Namespace einen Verweis auf das Schließfach für Anmeldeinformationen ab.</span><span class="sxs-lookup"><span data-stu-id="aaa43-117">Obtain a reference to the Credential Locker using the [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081) object from the [**Windows.Security.Credentials**](https://msdn.microsoft.com/library/windows/apps/br227089) namespace.</span></span>
2.  <span data-ttu-id="aaa43-118">Erstellen Sie ein [**PasswordCredential**](https://msdn.microsoft.com/library/windows/apps/br227061)-Objekt, das einen Bezeichner für Ihre App, den Benutzernamen und das Kennwort enthält, und übergeben Sie sie an die [**PasswordVault.Add**](https://msdn.microsoft.com/library/windows/apps/hh701231)-Methode, um die Anmeldeinformationen dem Schließfach hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-118">Create a [**PasswordCredential**](https://msdn.microsoft.com/library/windows/apps/br227061) object that contains an identifier for your app, the username and the password, and pass that to the [**PasswordVault.Add**](https://msdn.microsoft.com/library/windows/apps/hh701231) method to add the credential to the locker.</span></span>

```cs
var vault = new Windows.Security.Credentials.PasswordVault();
vault.Add(new Windows.Security.Credentials.PasswordCredential(
    "My App", username, password));
```

## <a name="retrieving-user-credentials"></a><span data-ttu-id="aaa43-119">Abrufen von Benutzeranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="aaa43-119">Retrieving user credentials</span></span>


<span data-ttu-id="aaa43-120">Zum Abrufen von Benutzeranmeldeinformationen aus dem Schließfach für Anmeldeinformationen mithilfe eines Verweises auf das [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081)-Objekt stehen verschiedene Optionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="aaa43-120">You have several options for retrieving user credentials from the Credential Locker after you have a reference to the [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081) object.</span></span>

-   <span data-ttu-id="aaa43-121">Mit der [**PasswordVault.RetrieveAll**](https://msdn.microsoft.com/library/windows/apps/br227088)-Methode können Sie alle Anmeldeinformationen abrufen, die der Benutzer im Schließfach für Ihre App bereitgestellt hat.</span><span class="sxs-lookup"><span data-stu-id="aaa43-121">You can retrieve all the credentials the user has supplied for your app in the locker with the [**PasswordVault.RetrieveAll**](https://msdn.microsoft.com/library/windows/apps/br227088) method.</span></span>

-   <span data-ttu-id="aaa43-122">Wenn Ihnen der Benutzername für die gespeicherten Anmeldeinformationen bekannt ist, können Sie mit der [**PasswordVault.FindAllByUserName**](https://msdn.microsoft.com/library/windows/apps/br227084)-Methode alle Anmeldeinformationen für diesen Benutzernamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-122">If you know the username for the stored credentials, you can retrieve all the credentials for that username with the [**PasswordVault.FindAllByUserName**](https://msdn.microsoft.com/library/windows/apps/br227084) method.</span></span>

-   <span data-ttu-id="aaa43-123">Wenn Ihnen der Ressourcenname für die gespeicherten Anmeldeinformationen bekannt ist, können Sie mit der [**PasswordVault.FindAllByResource**](https://msdn.microsoft.com/library/windows/apps/br227083)-Methode alle Anmeldeinformationen für diesen Ressourcennamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-123">If you know the resource name for the stored credentials, you can retrieve all the credentials for that resource name with the [**PasswordVault.FindAllByResource**](https://msdn.microsoft.com/library/windows/apps/br227083) method.</span></span>

-   <span data-ttu-id="aaa43-124">Und wenn Ihnen sowohl der Benutzer- als auch der Ressourcenname für bestimmte Anmeldeinformationen bekannt ist, können Sie diese Anmeldeinformationen mithilfe der [**PasswordVault.Retrieve**](https://msdn.microsoft.com/library/windows/apps/br227087)-Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-124">Finally, if you know both the username and the resource name for a credential, you can retrieve just that credential with the [**PasswordVault.Retrieve**](https://msdn.microsoft.com/library/windows/apps/br227087) method.</span></span>

<span data-ttu-id="aaa43-125">Sehen wir uns ein Beispiel an, in dem wir den Ressourcennamen global in einer App gespeichert haben und den Benutzer automatisch anmelden, wenn wir entsprechende Anmeldeinformationen finden.</span><span class="sxs-lookup"><span data-stu-id="aaa43-125">Let’s look at an example where we have stored the resource name globally in an app and we log the user on automatically if we find a credential for them.</span></span> <span data-ttu-id="aaa43-126">Wenn mehrere Anmeldeinformationen für einen Benutzer gefunden werden, wird der Benutzer dazu aufgefordert, Standardanmeldeinformationen für die Anmeldung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-126">If we find multiple credentials for the same user, we ask the user to select a default credential to use when logging on.</span></span>

```cs
private string resourceName = "My App";
private string defaultUserName;

private void Login()
{
    var loginCredential = GetCredentialFromLocker();

    if (loginCredential != null)
    {
        // There is a credential stored in the locker.
        // Populate the Password property of the credential
        // for automatic login.
        loginCredential.RetrievePassword();
    }
    else
    {
        // There is no credential stored in the locker.
        // Display UI to get user credentials.
        loginCredential = GetLoginCredentialUI();
    }

    // Log the user in.
    ServerLogin(loginCredential.UserName, loginCredential.Password);
}


private Windows.Security.Credentials.PasswordCredential GetCredentialFromLocker()
{
    Windows.Security.Credentials.PasswordCredential credential = null;

    var vault = new Windows.Security.Credentials.PasswordVault();
    var credentialList = vault.FindAllByResource(resourceName);
    if (credentialList.Count > 0)
    {
        if (credentialList.Count == 1)
        {
            credential = credentialList[0];
        }
        else
        {
            // When there are multiple usernames,
            // retrieve the default username. If one doesn't
            // exist, then display UI to have the user select
            // a default username.

            defaultUserName = GetDefaultUserNameUI();

            credential = vault.Retrieve(resourceName, defaultUserName);
        }
    }

    return credential;
}
```

## <a name="deleting-user-credentials"></a><span data-ttu-id="aaa43-127">Löschen von Benutzeranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="aaa43-127">Deleting user credentials</span></span>


<span data-ttu-id="aaa43-128">Das Löschen von Benutzeranmeldeinformationen im Schließfach für Anmeldeinformationen ist ebenfalls ein schneller Prozess mit zwei Schritten.</span><span class="sxs-lookup"><span data-stu-id="aaa43-128">Deleting user credentials in the Credential Locker is also a quick, two-step process.</span></span>

1.  <span data-ttu-id="aaa43-129">Rufen Sie mithilfe des [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081)-Objekts aus dem [**Windows.Security.Credentials**](https://msdn.microsoft.com/library/windows/apps/br227089)-Namespace einen Verweis auf das Schließfach für Anmeldeinformationen ab.</span><span class="sxs-lookup"><span data-stu-id="aaa43-129">Obtain a reference to the Credential Locker using the [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081) object from the [**Windows.Security.Credentials**](https://msdn.microsoft.com/library/windows/apps/br227089) namespace.</span></span>

2.  <span data-ttu-id="aaa43-130">Übergeben Sie die zu löschenden Anmeldeinformationen an die [**PasswordVault.Remove**](https://msdn.microsoft.com/library/windows/apps/hh701242)-Methode.</span><span class="sxs-lookup"><span data-stu-id="aaa43-130">Pass the credential you want to delete to the [**PasswordVault.Remove**](https://msdn.microsoft.com/library/windows/apps/hh701242) method.</span></span>

```cs
var vault = new Windows.Security.Credentials.PasswordVault();
vault.Remove(new Windows.Security.Credentials.PasswordCredential(
    "My App", username, password));
```

## <a name="best-practices"></a><span data-ttu-id="aaa43-131">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="aaa43-131">Best practices</span></span>


<span data-ttu-id="aaa43-132">Verwenden Sie das Schließfach für Anmeldeinformationen nur für Kennwörter und nicht für größere Daten-BLOBs.</span><span class="sxs-lookup"><span data-stu-id="aaa43-132">Only use the credential locker for passwords and not for larger data blobs.</span></span>

<span data-ttu-id="aaa43-133">Speichern Sie Kennwörter nur unter den folgenden Bedingungen im Schließfach für Anmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="aaa43-133">Save passwords in the credential locker only if the following criteria are met:</span></span>

-   <span data-ttu-id="aaa43-134">Der Benutzer hat sich erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="aaa43-134">The user has successfully signed in.</span></span>
-   <span data-ttu-id="aaa43-135">Der Benutzer hat dem Speichern von Kennwörtern zugestimmt.</span><span class="sxs-lookup"><span data-stu-id="aaa43-135">The user has opted to save passwords.</span></span>

<span data-ttu-id="aaa43-136">Speichern Sie Anmeldeinformationen niemals als Nur-Text mit App-Daten oder Roamingeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="aaa43-136">Never store credentials in plain-text using app data or roaming settings.</span></span>
