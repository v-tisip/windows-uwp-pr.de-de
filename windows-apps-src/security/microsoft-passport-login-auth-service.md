---
title: Erstellen eines Windows Hello-Anmeldedienstes
description: Dies ist Teil 2 der umfassenden Schritt-für-Schritt-Lösung zum Verwenden von Windows Hello als Alternative zu herkömmlichen Authentifizierungssystemen mit Benutzername und Kennwort in Windows 10-Apps für die Universelle Windows-Plattform (UWP).
ms.assetid: ECC9EF3D-E0A1-4BC4-94FA-3215E6CFF0E4
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 839d44c992977fdad8863203b84116b2faeba76d
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7556394"
---
# <a name="create-a-windows-hello-login-service"></a><span data-ttu-id="aeddf-104">Erstellen eines Windows Hello-Anmeldedienstes</span><span class="sxs-lookup"><span data-stu-id="aeddf-104">Create a Windows Hello login service</span></span>

<span data-ttu-id="aeddf-105">Dies ist Teil 2 der umfassenden Schritt-für-Schritt-Lösung zum Verwenden von Windows Hello als Alternative zu herkömmlichen Authentifizierungssystemen mit Benutzername und Kennwort in Windows 10-Apps für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="aeddf-105">This is Part 2 of a complete walkthrough on how to use Windows Hello as an alternative to traditional username and password authentication systems in Windows 10 UWP (Universal Windows platform) apps.</span></span> <span data-ttu-id="aeddf-106">Dieser Artikel führt Teil 1, [Microsoft Passport-Anmelde-App](microsoft-passport-login.md), weiter und erweitert die Funktionalität, um zu veranschaulichen, wie Sie Windows Hello in Ihre vorhandene Anwendung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="aeddf-106">This article picks up where Part 1, [Windows Hello login app](microsoft-passport-login.md), left off and extends the functionality to demonstrate how you can integrate Windows Hello into your existing application.</span></span>

<span data-ttu-id="aeddf-107">Die Erstellung dieses Projekts setzt Erfahrung mit C# und XAML voraus.</span><span class="sxs-lookup"><span data-stu-id="aeddf-107">In order to build this project, you'll need some experience with C#, and XAML.</span></span> <span data-ttu-id="aeddf-108">Außerdem muss Visual Studio2015 (mindestens Community Edition) auf einem Computer unter Windows10 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-108">You'll also need to be using Visual Studio 2015 (Community Edition or greater) on a Windows 10 machine.</span></span>

## <a name="exercise-1-server-side-logic"></a><span data-ttu-id="aeddf-109">Übung 1: Serverseitige Logik</span><span class="sxs-lookup"><span data-stu-id="aeddf-109">Exercise 1: Server Side Logic</span></span>


<span data-ttu-id="aeddf-110">In dieser Übung beginnen Sie mit der in der ersten Übung erstellten Windows-Hello-Anwendung und erstellen einen lokalen Pseudoserver und eine Pseudodatenbank.</span><span class="sxs-lookup"><span data-stu-id="aeddf-110">In this exercise you will be starting with the Windows Hello application built in the first lab and creating a local mock server and database.</span></span> <span data-ttu-id="aeddf-111">Diese praktische Übung soll vermitteln, wie Windows Hello in ein vorhandenes System integriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="aeddf-111">This hands on lab is designed to teach how Windows Hello could be integrated into an existing system.</span></span> <span data-ttu-id="aeddf-112">Mit einem Pseudoserver und einer Pseudodatenbank werden viele Einstellungen ohne Bezug vermieden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-112">By using a mock server and mock database a lot of unrelated setup is eliminated.</span></span> <span data-ttu-id="aeddf-113">In Ihren eigenen Anwendungen müssen Sie die Pseudoobjekte durch die echten Dienste und Datenbanken ersetzen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-113">In your own applications you will need to replace the mock objects with the real services and databases.</span></span>

-   <span data-ttu-id="aeddf-114">Öffnen Sie zunächst die PassportLogin-Projektmappe aus der ersten praktischen Übung für Passport.</span><span class="sxs-lookup"><span data-stu-id="aeddf-114">To begin, open up the PassportLogin solution from the first Passport Hands On Lab.</span></span>
-   <span data-ttu-id="aeddf-115">Beginnen Sie mit dem Implementieren des Pseudoservers und der Pseudodatenbank.</span><span class="sxs-lookup"><span data-stu-id="aeddf-115">You will start by implementing the mock server and mock database.</span></span> <span data-ttu-id="aeddf-116">Erstellen Sie einen neuen Ordner namens „AuthService“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-116">Create a new folder called "AuthService".</span></span> <span data-ttu-id="aeddf-117">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe „PassportLogin (Universelle Windows-App)“, und wählen Sie „Hinzufügen“ > „Neuer Ordner“ aus.</span><span class="sxs-lookup"><span data-stu-id="aeddf-117">In solution explorer right click on the solution "PassportLogin (Universal Windows)" and select Add > New Folder.</span></span>
-   <span data-ttu-id="aeddf-118">Erstellen Sie UserAccount- und PassportDevices-Klassen, die als Modelle für in der Pseudodatenbank zu speichernde Daten dienen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-118">Create UserAccount and PassportDevices classes that will act as models for data to be saved in the mock database.</span></span> <span data-ttu-id="aeddf-119">Das Benutzerkonto ist ähnlich wie das auf einem herkömmlichen Authentifizierungsserver implementierte Benutzermodell.</span><span class="sxs-lookup"><span data-stu-id="aeddf-119">The UserAccount will be similar to the user model implemented on a traditional authentication server.</span></span> <span data-ttu-id="aeddf-120">Klicken Sie mit der rechten Maustaste auf den Ordner „AuthService“, und fügen Sie die neue Klasse „UserAccount.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-120">Right click on the AuthService folder and add a new class called "UserAccount.cs."</span></span>

    ![Windows Hello - Autorisierung Ordner erstellen](images/passport-auth-1.png)

    ![Windows Hello - Autorisierung Klasse erstellen](images/passport-auth-2.png)

-   <span data-ttu-id="aeddf-123">Ändern Sie die Klassendefinition in öffentlich und fügen Sie die folgenden öffentlichen Eigenschaften hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-123">Change the class definition to be public and then add the following public properties.</span></span> <span data-ttu-id="aeddf-124">Sie benötigen den folgenden Verweis.</span><span class="sxs-lookup"><span data-stu-id="aeddf-124">You will need the following reference.</span></span>

    ```cs
    using System.ComponentModel.DataAnnotations;
     
    namespace PassportLogin.AuthService
    {
        public class UserAccount
        {
            [Key, Required]
            public Guid UserId { get; set; }
            [Required]
            public string Username { get; set; }
            public string Password { get; set; }
            // public List<PassportDevice> PassportDevices = new List<PassportDevice>();
        }
    }
    ```

    <span data-ttu-id="aeddf-125">Möglicherweise haben Sie die auskommentierte Liste von PassportDevices bemerkt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-125">You may have noticed the commented out list of PassportDevices.</span></span> <span data-ttu-id="aeddf-126">Dies ist eine Änderung, die Sie an einem vorhandenen Benutzermodell in der aktuellen Implementierung vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-126">This is a modification you will need to make to an existing user model in your current implementation.</span></span> <span data-ttu-id="aeddf-127">Die Liste von PassportDevices enthält eine Geräte-ID, den öffentlichen Schlüssel aus Windows Hello und ein [**KeyCredentialAttestationResult**](https://msdn.microsoft.com/library/windows/apps/dn973034).</span><span class="sxs-lookup"><span data-stu-id="aeddf-127">The list of PassportDevices will contain a deviceID, the public key made from Windows Hello, and a [**KeyCredentialAttestationResult**](https://msdn.microsoft.com/library/windows/apps/dn973034).</span></span> <span data-ttu-id="aeddf-128">Für diese praktische Übung müssen Sie das KeyAttestationResult implementieren, da es von Windows Hello nur auf Geräten mit TPM (Trusted Platform Module)-Chip bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-128">For this hands on lab you will need to implement the keyAttestationResult as they are only provided by Windows Hello on devices that have a TPM (Trusted Platform Modules) chip.</span></span> <span data-ttu-id="aeddf-129">Das **KeyCredentialAttestationResult** ist eine Kombination aus mehreren Eigenschaften und muss zum Speichern und Laden mit einer Datenbank geteilt werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-129">The **KeyCredentialAttestationResult** is a combination of multiple properties and would need to be split in order to save and load them with a database.</span></span>

-   <span data-ttu-id="aeddf-130">Erstellen Sie im Ordner „AuthService“ die neue Klasse „PassportDevice.cs“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-130">Create a new class in the AuthService folder called "PassportDevice.cs".</span></span> <span data-ttu-id="aeddf-131">Dies ist das Modell für die Windows-Hello-Geräte, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="aeddf-131">This is the model for the Windows Hello devices as discussed above.</span></span> <span data-ttu-id="aeddf-132">Definieren Sie die Klasse als öffentliche Klasse und fügen Sie die folgenden Eigenschaften hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-132">Change the class definition to be public and add the following properties.</span></span>

    ```cs
    namespace PassportLogin.AuthService
    {
        public class PassportDevice
        {
            // These are the new variables that will need to be added to the existing UserAccount in the Database
            // The DeviceName is used to support multiple devices for the one user.
            // This way the correct public key is easier to find as a new public key is made for each device.
            // The KeyAttestationResult is only used if the User device has a TPM (Trusted Platform Module) chip, 
            // in most cases it will not. So will be left out for this hands on lab.
            public Guid DeviceId { get; set; }
            public byte[] PublicKey { get; set; }
            // public KeyCredentialAttestationResult KeyAttestationResult { get; set; }
        }
    }
    ```

-   <span data-ttu-id="aeddf-133">Kehren Sie zu „UserAccount.cs“ zurück, und entfernen Sie Kommentare aus der Liste der Windows-Hello-Geräte.</span><span class="sxs-lookup"><span data-stu-id="aeddf-133">Return to in UserAccount.cs and uncomment the list of Windows Hello devices.</span></span>

    ```cs
    using System.Collections.Generic;
     
    namespace PassportLogin.AuthService
    {
        public class UserAccount
        {
            [Key, Required]
            public Guid UserId { get; set; }
            [Required]
            public string Username { get; set; }
            public string Password { get; set; }
            public List<PassportDevice> PassportDevices = new List<PassportDevice>();
        }
    }
    ```

-   <span data-ttu-id="aeddf-134">Da das Modell für das Benutzerkonto und PassportDevice erstellt wurde, müssen Sie in AuthService eine weitere neue Klasse erstellen, die als Pseudodatenbank dient.</span><span class="sxs-lookup"><span data-stu-id="aeddf-134">With the model for the UserAccount and the PassportDevice created, you need to create another new class in the AuthService that will act as the mock database.</span></span> <span data-ttu-id="aeddf-135">Dies ist die Pseudodatenbank, aus der Sie eine Liste von Benutzerkonten lokal speichern und laden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-135">As this is a mock database from where you will be saving and loading a list of user accounts locally.</span></span> <span data-ttu-id="aeddf-136">In der realen Welt wäre dies Ihre Datenbankimplementierung.</span><span class="sxs-lookup"><span data-stu-id="aeddf-136">In the real world this would be your database implementation.</span></span> <span data-ttu-id="aeddf-137">Erstellen Sie in AuthService die neue Klasse „MockStore.cs“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-137">Create a new class in AuthService called "MockStore.cs".</span></span> <span data-ttu-id="aeddf-138">Definieren Sie die Klasse als öffentliche Klasse.</span><span class="sxs-lookup"><span data-stu-id="aeddf-138">Change the class definition to public.</span></span>
-   <span data-ttu-id="aeddf-139">Das der Pseudospeicher eine Liste von Benutzerkonten lokal speichert und lädt, können Sie die Logik zum Speichern und Laden dieser Liste mit einem XmlSerializer-Element implementieren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-139">As the mock store will save and load a list of user accounts locally you can implement the logic to save and load that list using an XmlSerializer.</span></span> <span data-ttu-id="aeddf-140">Außerdem müssen Sie sich den Dateinamen und Speicherort merken.</span><span class="sxs-lookup"><span data-stu-id="aeddf-140">You will also need to remember the filename and save location.</span></span> <span data-ttu-id="aeddf-141">Implementieren Sie Folgendes in „MockStore.cs“:</span><span class="sxs-lookup"><span data-stu-id="aeddf-141">In MockStore.cs implement the following:</span></span>

```cs
    using System.IO;
    using System.Linq;
    using System.Xml.Serialization;
    using Windows.Storage;

    namespace PassportLogin.AuthService
    {
        public class MockStore
        {
            private const string USER_ACCOUNT_LIST_FILE_NAME = "userAccountsList.txt";
            // This cannot be a const because the LocalFolder is accessed at runtime
            private string _userAccountListPath = Path.Combine(
                ApplicationData.Current.LocalFolder.Path, USER_ACCOUNT_LIST_FILE_NAME);
            private List<UserAccount> _mockDatabaseUserAccountsList;
     
    #region Save and Load Helpers
            /// <summary>
            /// Create and save a useraccount list file. (Replacing the old one)
            /// </summary>
            private async void SaveAccountListAsync()
            {
                string accountsXml = SerializeAccountListToXml();
     
                if (File.Exists(_userAccountListPath))
                {
                    StorageFile accountsFile = await StorageFile.GetFileFromPathAsync(_userAccountListPath);
                    await FileIO.WriteTextAsync(accountsFile, accountsXml);
                }
                else
                {
                    StorageFile accountsFile = await ApplicationData.Current.LocalFolder.CreateFileAsync(USER_ACCOUNT_LIST_FILE_NAME);
                    await FileIO.WriteTextAsync(accountsFile, accountsXml);
                }
            }
     
            /// <summary>
            /// Gets the useraccount list file and deserializes it from XML to a list of useraccount objects.
            /// </summary>
            /// <returns>List of useraccount objects</returns>
            private async void LoadAccountListAsync()
            {
                if (File.Exists(_userAccountListPath))
                {
                    StorageFile accountsFile = await StorageFile.GetFileFromPathAsync(_userAccountListPath);
     
                    string accountsXml = await FileIO.ReadTextAsync(accountsFile);
                    DeserializeXmlToAccountList(accountsXml);
                }
     
                // If the UserAccountList does not contain the sampleUser Initialize the sample users
                // This is only needed as it in a Hand on Lab to demonstrate a user migrating
                // In the real world user accounts would just be in a database
                if (!_mockDatabaseUserAccountsList.Any(f => f.Username.Equals("sampleUsername")))
                {
                    //If the list is empty InitializeSampleAccounts and return the list
                    //InitializeSampleUserAccounts();
                }
            }
     
            /// <summary>
            /// Uses the local list of accounts and returns an XML formatted string representing the list
            /// </summary>
            /// <returns>XML formatted list of accounts</returns>
            private string SerializeAccountListToXml()
            {
                XmlSerializer xmlizer = new XmlSerializer(typeof(List<UserAccount>));
                StringWriter writer = new StringWriter();
                xmlizer.Serialize(writer, _mockDatabaseUserAccountsList);
                return writer.ToString();
            }
     
            /// <summary>
            /// Takes an XML formatted string representing a list of accounts and returns a list object of accounts
            /// </summary>
            /// <param name="listAsXml">XML formatted list of accounts</param>
            /// <returns>List object of accounts</returns>
            private List<UserAccount> DeserializeXmlToAccountList(string listAsXml)
            {
                XmlSerializer xmlizer = new XmlSerializer(typeof(List<UserAccount>));
                TextReader textreader = new StreamReader(new MemoryStream(Encoding.UTF8.GetBytes(listAsXml)));
                return _mockDatabaseUserAccountsList = (xmlizer.Deserialize(textreader)) as List<UserAccount>;
            }
    #endregion
        }
    }
```

-   <span data-ttu-id="aeddf-142">Möglicherweise haben Sie in der Load-Methode bemerkt, dass eine InitializeSampleUserAccounts-Methode auskommentiert wurde. Sie müssen diese Methode in MockStore.cs erstellen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-142">In the load method you may have noticed that an InitializeSampleUserAccounts method was commented out. You will need to create this method in the MockStore.cs.</span></span> <span data-ttu-id="aeddf-143">Diese Methode füllt die Liste der Benutzerkonten, sodass eine Anmeldung stattfinden kann.</span><span class="sxs-lookup"><span data-stu-id="aeddf-143">This method will populate the user accounts list so that a login can take place.</span></span> <span data-ttu-id="aeddf-144">In der realen Welt würde die Benutzerdatenbank bereits gefüllt sein.</span><span class="sxs-lookup"><span data-stu-id="aeddf-144">In the real world the user database would already be populated.</span></span> <span data-ttu-id="aeddf-145">In diesem Schritt erstellen Sie auch einen Konstruktor, der die Benutzerliste und den Ladeaufruf initialisiert.</span><span class="sxs-lookup"><span data-stu-id="aeddf-145">In this step you will also be creating a constructor that will initialise the user list and call load.</span></span>

    ```cs
    namespace PassportLogin.AuthService
    {
        public class MockStore
        {
            private const string USER_ACCOUNT_LIST_FILE_NAME = "userAccountsList.txt";
            // This cannot be a const because the LocalFolder is accessed at runtime
            private string _userAccountListPath = Path.Combine(
                ApplicationData.Current.LocalFolder.Path, USER_ACCOUNT_LIST_FILE_NAME);
            private List<UserAccount> _mockDatabaseUserAccountsList;
     
            public MockStore()
            {
                _mockDatabaseUserAccountsList = new List& lt; UserAccount & gt; ();
                LoadAccountListAsync();
            }

            private void InitializeSampleUserAccounts()
            {
                // Create a sample Traditional User Account that only has a Username and Password
                // This will be used initially to demonstrate how to migrate to use Windows Hello

                UserAccount sampleUserAccount = new UserAccount()
                {
                    UserId = Guid.NewGuid(),
                    Username = "sampleUsername",
                    Password = "samplePassword",
                };

                // Add the sampleUserAccount to the _mockDatabase
                _mockDatabaseUserAccountsList.Add(sampleUserAccount);
                SaveAccountListAsync();
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-146">Entfernen Sie nun, da die InitalizeSampleUserAccounts-Methode vorhanden ist, Kommentare aus dem Methodenaufruf in der LoadAccountListAsync-Methode.</span><span class="sxs-lookup"><span data-stu-id="aeddf-146">Now that the InitalizeSampleUserAccounts method exists uncomment the method call in the LoadAccountListAsync method.</span></span>

    ```cs
    private async void LoadAccountListAsync()
    {
        if (File.Exists(_userAccountListPath))
        {
            StorageFile accountsFile = await StorageFile.GetFileFromPathAsync(_userAccountListPath);

            string accountsXml = await FileIO.ReadTextAsync(accountsFile);
            DeserializeXmlToAccountList(accountsXml);
        }

        // If the UserAccountList does not contain the sampleUser Initialize the sample users
        // This is only needed as it in a Hand on Lab to demonstrate a user migrating
        // In the real world user accounts would just be in a database
        if (!_mockDatabaseUserAccountsList.Any(f = > f.Username.Equals("sampleUsername")))
                {
            //If the list is empty InitializeSampleAccounts and return the list
            InitializeSampleUserAccounts();
        }
    }
    ```

-   <span data-ttu-id="aeddf-147">Die Liste der Benutzerkonten im Pseudospeicher kann jetzt gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-147">The user accounts list in mock store can now be saved and loaded.</span></span> <span data-ttu-id="aeddf-148">Andere Teile der Anwendung müssen Zugriff auf diese Liste haben, es müssen also Methoden zum Abrufen dieser Daten vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="aeddf-148">Other parts of the application will need to have access to this list so there will need to be some methods to retrieve this data.</span></span> <span data-ttu-id="aeddf-149">Fügen Sie unter der InitializeSampleUserAccounts-Methode die folgenden get-Methoden hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-149">Underneath the InitializeSampleUserAccounts method, add the following get methods.</span></span> <span data-ttu-id="aeddf-150">Damit können Sie eine Benutzer-ID, einen einzelnen Benutzer, eine Liste von Benutzern für ein bestimmtes Windows-Hello-Gerät und außerdem den öffentlichen Schlüssel für den Benutzer auf einem bestimmten Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-150">They will allow you to get a userid, a single user, a list of users for a specific Windows Hello device, and also get the public key for the user on a specific device.</span></span>

    ```cs
    public Guid GetUserId(string username)
    {
        if (_mockDatabaseUserAccountsList.Any())
        {
            UserAccount account = _mockDatabaseUserAccountsList.FirstOrDefault(f => f.Username.Equals(username));
            if (account != null)
            {
                return account.UserId;
            }
        }
        return Guid.Empty;
    }

    public UserAccount GetUserAccount(Guid userId)
    {
        return _mockDatabaseUserAccountsList.FirstOrDefault(f => f.UserId.Equals(userId));
    }

    public List<UserAccount> GetUserAccountsForDevice(Guid deviceId)
    {
        List<UserAccount> usersForDevice = new List<UserAccount>();

        foreach (UserAccount account in _mockDatabaseUserAccountsList)
        {
            if (account.PassportDevices.Any(f => f.DeviceId.Equals(deviceId)))
            {
                usersForDevice.Add(account);
            }
        }

        return usersForDevice;
    }

    public byte[] GetPublicKey(Guid userId, Guid deviceId)
    {
        UserAccount account = _mockDatabaseUserAccountsList.FirstOrDefault(f => f.UserId.Equals(userId));
        if (account != null)
        {
            if (account.PassportDevices.Any())
            {
                return account.PassportDevices.FirstOrDefault(p => p.DeviceId.Equals(deviceId)).PublicKey;
            }
        }
        return null;
    }
    ```

-   <span data-ttu-id="aeddf-151">Die nächsten zu implementierenden Methoden führen einfache Vorgänge zum Hinzufügen und Entfernen eines Kontos sowie zum Entfernen eines Geräts durch.</span><span class="sxs-lookup"><span data-stu-id="aeddf-151">The next methods to implement will handle simple operations to add account, remove account, and also remove device.</span></span> <span data-ttu-id="aeddf-152">Das Entfernen von Geräten ist erforderlich, weil Windows Hello gerätespezifisch ist.</span><span class="sxs-lookup"><span data-stu-id="aeddf-152">Remove device is needed as Windows Hello is device specific.</span></span> <span data-ttu-id="aeddf-153">Für jedes Gerät, bei dem Sie sich anmelden, wird von Windows Hello ein neues Paar aus einem öffentlichen und einem privaten Schlüssel erstellt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-153">For each device to which you log in, a new public and private key pair will be created by Windows Hello.</span></span> <span data-ttu-id="aeddf-154">Das ist vergleichbar mit einem unterschiedlichen Kennwort für jedes Gerät, bei dem Sie sich anmelden. Der einzige Unterschied besteht darin, dass nicht Sie sich alle diese Kennwörter merken müssen, sondern der Server.</span><span class="sxs-lookup"><span data-stu-id="aeddf-154">It is like having a different password for each device you sign in on, the only thing is you don’t need to remember all those passwords the server does.</span></span> <span data-ttu-id="aeddf-155">Fügen Sie die folgenden Methoden in „MockStore.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-155">Add the following methods into the MockStore.cs</span></span>

    ```cs
    public UserAccount AddAccount(string username)
    {
        UserAccount newAccount = null;
        try
        {
            newAccount = new UserAccount()
            {
                UserId = Guid.NewGuid(),
                Username = username,
            };

            _mockDatabaseUserAccountsList.Add(newAccount);
            SaveAccountListAsync();
        }
        catch (Exception)
        {
            throw;
        }
        return newAccount;
    }

    public bool RemoveAccount(Guid userId)
    {
        UserAccount userAccount = GetUserAccount(userId);
        if (userAccount != null)
        {
            _mockDatabaseUserAccountsList.Remove(userAccount);
            SaveAccountListAsync();
            return true;
        }
        return false;
    }

    public bool RemoveDevice(Guid userId, Guid deviceId)
    {
        UserAccount userAccount = GetUserAccount(userId);
        PassportDevice deviceToRemove = null;
        if (userAccount != null)
        {
            foreach (PassportDevice device in userAccount.PassportDevices)
            {
                if (device.DeviceId.Equals(deviceId))
                {
                    deviceToRemove = device;
                    break;
                }
            }
        }

        if (deviceToRemove != null)
        {
            //Remove the PassportDevice
            userAccount.PassportDevices.Remove(deviceToRemove);
            SaveAccountListAsync();
        }

        return true;
    }
    ```

- <span data-ttu-id="aeddf-156">Fügen Sie in der MockStore-Klasse eine Methode hinzu, die einem vorhandenen Benutzerkonto Windows-Hello-bezogene Informationen hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-156">In the MockStore class add a method that will add Windows Hello related information to an existing UserAccount.</span></span> <span data-ttu-id="aeddf-157">Diese Methode wird PassportUpdateDetails genannt und nutzt Parameter zum Identifizieren des Benutzers und die Windows-Hello-Details.</span><span class="sxs-lookup"><span data-stu-id="aeddf-157">This method will be called PassportUpdateDetails and will take parameters to identify the user, and the Windows Hello details.</span></span> <span data-ttu-id="aeddf-158">Das KeyAttestationResult ist beim Erstellen eines PassportDevice auskommentiert, in einer echten Anwendung würden Sie dies anfordern.</span><span class="sxs-lookup"><span data-stu-id="aeddf-158">The KeyAttestationResult has been commented out when creating a PassportDevice, in a real world application you would require this.</span></span>

    ```cs
    using Windows.Security.Credentials;

    public void PassportUpdateDetails(Guid userId, Guid deviceId, byte[] publicKey, 
        KeyCredentialAttestationResult keyAttestationResult)
    {
        UserAccount existingUserAccount = GetUserAccount(userId);
        if (existingUserAccount != null)
        {
            if (!existingUserAccount.PassportDevices.Any(f => f.DeviceId.Equals(deviceId)))
            {
                existingUserAccount.PassportDevices.Add(new PassportDevice()
                {
                    DeviceId = deviceId,
                    PublicKey = publicKey,
                    // KeyAttestationResult = keyAttestationResult
                });
            }
        }
        SaveAccountListAsync();
    }
    ```

- <span data-ttu-id="aeddf-159">Die MockStore-Klasse ist jetzt fertig. Da dies die Datenbank darstellt, sollte sie als privat eingestuft werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-159">The MockStore class is now complete, as this represents the database it should be considered private.</span></span> <span data-ttu-id="aeddf-160">Zum Zugriff auf MockStore ist eine AuthService-Klasse zum Bearbeiten der Daten in der Datenbank erforderlich.</span><span class="sxs-lookup"><span data-stu-id="aeddf-160">In order to access the MockStore an AuthService class is needed to manipulate the database data.</span></span> <span data-ttu-id="aeddf-161">Erstellen Sie im Ordner „AuthService“ die neue Klasse „AuthService.cs“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-161">In the AuthService folder create a new class called "AuthService.cs".</span></span> <span data-ttu-id="aeddf-162">Definieren Sie die Klasse als öffentliche Klasse, und fügen Sie ein Singleton-Instanzmuster hinzu, um sicherzustellen, dass nur eine Instanz erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-162">Change the class definition to public and add a singleton instance pattern to make sure only one instance is ever created.</span></span>

    ```cs
    namespace PassportLogin.AuthService
    {
        public class AuthService
        {
            // Singleton instance of the AuthService
            // The AuthService is a mock of what a real world server and service implementation would be
            private static AuthService _instance;
            public static AuthService Instance
            {
                get
                {
                    if (null == _instance)
                    {
                        _instance = new AuthService();
                    }
                    return _instance;
                }
            }

            private AuthService()
            { }
        }
    }
    ```

-   <span data-ttu-id="aeddf-163">Die AuthService-Klasse muss eine Instanz der MockStore-Klasse erstellen und den Zugriff auf die Eigenschaften des MockStore-Objekts gewähren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-163">The AuthService class will need to create an instance of the MockStore class and provide access to the properties of the MockStore object.</span></span>

    ```cs
    namespace PassportLogin.AuthService
    {
        public class AuthService
        {
            //Singleton instance of the AuthService
            //The AuthService is a mock of what a real world server and database implementation would be
            private static AuthService _instance;
            public static AuthService Instance
            {
                get
                {
                    if (null == _instance)
                    {
                        _instance = new AuthService();
                    }
                    return _instance;
                }
            }
     
            private MockStore _mockStore = new MockStore();
     
            public Guid GetUserId(string username)
            {
                return _mockStore.GetUserId(username);
            }
     
            public UserAccount GetUserAccount(Guid userId)
            {
                return _mockStore.GetUserAccount(userId);
            }
     
            public List<UserAccount> GetUserAccountsForDevice(Guid deviceId)
            {
                return _mockStore.GetUserAccountsForDevice(deviceId);
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-164">Sie benötigen Methoden in der AuthService-Klasse für den Zugriff auf Methoden zum Hinzufügen, Entfernen und Aktualisieren von Passport-Details im MockStore-Objekt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-164">You need methods in the AuthService class to access add, remove, and update passport details methods in the MockStore object.</span></span> <span data-ttu-id="aeddf-165">Fügen Sie am Ende der AuthService-Klassendatei die folgenden Methoden hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-165">At the end of the AuthService class file add the following methods.</span></span>

    ```cs
    using Windows.Security.Credentials;

    public void Register(string username)
    {
        _mockStore.AddAccount(username);
    }

    public bool PassportRemoveUser(Guid userId)
    {
        return _mockStore.RemoveAccount(userId);
    }

    public bool PassportRemoveDevice(Guid userId, Guid deviceId)
    {
        return _mockStore.RemoveDevice(userId, deviceId);
    }

    public void PassportUpdateDetails(Guid userId, Guid deviceId, byte[] publicKey, 
        KeyCredentialAttestationResult keyAttestationResult)
    {
        _mockStore.PassportUpdateDetails(userId, deviceId, publicKey, keyAttestationResult);
    }
    ```

-   <span data-ttu-id="aeddf-166">Die AuthService-Klasse muss eine Methode zum Überprüfen der Anmeldeinformationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-166">The AuthService class will need to provide a method to validate credentials.</span></span> <span data-ttu-id="aeddf-167">Diese Methode verwendet einen Benutzernamen und ein Kennwort und stellt sicher, dass das Konto vorhanden und das Kennwort gültig ist.</span><span class="sxs-lookup"><span data-stu-id="aeddf-167">This method will take a username and password and make sure that account exists and the password is valid.</span></span> <span data-ttu-id="aeddf-168">Ein vorhandenes System würde über eine äquivalente Methode verfügen, die überprüft, ob der Benutzer autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="aeddf-168">An existing system would have an equivalent method to this that checks the user is authorized.</span></span> <span data-ttu-id="aeddf-169">Fügen Sie die folgende ValidateCredentials-Methode der Datei „AuthService.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-169">Add the following ValidateCredentials to the AuthService.cs file.</span></span>

    ```cs
    public bool ValidateCredentials(string username, string password)
    {
        if (!string.IsNullOrEmpty(username) && !string.IsNullOrEmpty(password))
        {
            // This would be used for existing accounts migrating to use Passport
            Guid userId = GetUserId(username);
            if (userId != Guid.Empty)
            {
                UserAccount account = GetUserAccount(userId);
                if (account != null)
                {
                    if (string.Equals(password, account.Password))
                    {
                        return true;
                    }
                }
            }
        }
        return false;
    }
    ```

-   <span data-ttu-id="aeddf-170">Die AuthService-Klasse benötigt eine Abfrageanforderungsmethode, die eine Abfrage an den Client zurückgibt, um den jeweiligen Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-170">The AuthService class needs a request challenge method that will return a challenge to the client to validate the user is who they claim to be.</span></span> <span data-ttu-id="aeddf-171">Dann wird eine Methode in der AuthService-Klasse benötigt, um die signierte Abfrage vom Client zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-171">Then a method is needed in the AuthService class to receive the signed challenge back from the client.</span></span> <span data-ttu-id="aeddf-172">Für diese praktische Übung wurde die Methode, mit der Sie ermitteln, ob die signierte Abfrage abgeschlossen wurde, unvollständig gelassen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-172">For this hands on lab the method of how you determine if the signed challenge has been completed has been left incomplete.</span></span> <span data-ttu-id="aeddf-173">Jede Implementierung von Windows Hello in ein vorhandenes Authentifizierungssystem ist etwas anders.</span><span class="sxs-lookup"><span data-stu-id="aeddf-173">Every implementation of Windows Hello into an existing authentication system will be slightly different.</span></span> <span data-ttu-id="aeddf-174">Der auf dem Server gespeicherte öffentliche Schlüssel muss mit dem Ergebnis übereinstimmen, das der Client an den Server zurückgegeben hat.</span><span class="sxs-lookup"><span data-stu-id="aeddf-174">The public key stored on the server needs to match with the result the client returned to the server.</span></span> <span data-ttu-id="aeddf-175">Fügen Sie diese beiden Methoden zu „AuthService.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-175">Add these two methods to AuthService.cs.</span></span>

    ```cs
    using Windows.Security.Cryptography;
    using Windows.Storage.Streams;

    public IBuffer PassportRequestChallenge()
    {
        return CryptographicBuffer.ConvertStringToBinary("ServerChallenge", BinaryStringEncoding.Utf8);
    }

    public bool SendServerSignedChallenge(Guid userId, Guid deviceId, byte[] signedChallenge)
    {
        // Depending on your company polices and procedures this step will be different
        // It is at this point you will need to validate the signedChallenge that is sent back from the client.
        // Validation is used to ensure the correct user is trying to access this account. 
        // The validation process will use the signedChallenge and the stored PublicKey 
        // for the username and the specific device signin is called from.
        // Based on the validation result you will return a bool value to allow access to continue or to block the account.

        // For this sample validation will not happen as a best practice solution does not apply and will need to 
           // be configured for each company.
        // Simply just return true.

        // You could get the User's Public Key with something similar to the following:
        byte[] userPublicKey = _mockStore.GetPublicKey(userId, deviceId);
        return true;
    }
    ```

## <a name="exercise-2-client-side-logic"></a><span data-ttu-id="aeddf-176">Übung 2: Clientseitige Logik</span><span class="sxs-lookup"><span data-stu-id="aeddf-176">Exercise 2: Client Side Logic</span></span>

<span data-ttu-id="aeddf-177">In dieser Übung ändern Sie die clientseitigen Ansichten und Hilfsklassen aus der ersten Übung, um die AuthService-Klasse zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-177">In this exercise you will be changing the client side views and helper classes from the first lab to use the AuthService class.</span></span> <span data-ttu-id="aeddf-178">In der realen Welt wäre AuthService der Authentifizierungsserver, und Sie müssten Web-APIs zum Senden und Empfangen von Daten vom Server verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-178">In the real world the AuthService would be the authentication server and you would need to use Web API’s to send and receive data from the server.</span></span> <span data-ttu-id="aeddf-179">Für diese praktische Übung sind Client und Server der Einfachheit halber lokal.</span><span class="sxs-lookup"><span data-stu-id="aeddf-179">For this hands on lab client and server are all local to keep things simple.</span></span> <span data-ttu-id="aeddf-180">Das Ziel ist es, zu erfahren, wie Sie die Windows-Hello-API verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-180">The objective is to learn how to use the Windows Hello APIs.</span></span>

-   <span data-ttu-id="aeddf-181">In „MainPage.Xaml.cs“ können Sie den AccountHelper.LoadAccountListAsync-Methodenaufruf in der geladenen Methode entfernen, da die AuthService-Klasse eine Instanz von MockStore erstellt, die die Kontenliste lädt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-181">In the MainPage.xaml.cs you can remove the AccountHelper.LoadAccountListAsync method call in the loaded method as the AuthService class creates an instance of the MockStore which loads the accounts list.</span></span> <span data-ttu-id="aeddf-182">Die geladene Methode sollte nun wie unten dargestellt aussehen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-182">The loaded method should now look like below.</span></span> <span data-ttu-id="aeddf-183">Dabei wird die Definition der asynchronen Methode entfernt, da nichts erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-183">Note the async method definition is removed as nothing is being awaiting.</span></span>

    ```cs
    private void MainPage_Loaded(object sender, RoutedEventArgs e)
    {
        Frame.Navigate(typeof(UserSelection));
    }
    ```

-   <span data-ttu-id="aeddf-184">Aktualisieren Sie die Schnittstelle der Anmeldeseite, um die Eingabe eines Kennworts anzufordern.</span><span class="sxs-lookup"><span data-stu-id="aeddf-184">Update the Login page interface to require a passport be entered.</span></span> <span data-ttu-id="aeddf-185">Diese praktische Übung veranschaulicht, wie ein vorhandenes System migriert werden kann, um Windows Hello zu nutzen. Vorhandene Konten haben einen Benutzernamen und ein Kennwort.</span><span class="sxs-lookup"><span data-stu-id="aeddf-185">This hands on lab demonstrates how an existing system could be migrated to use Windows Hello and existing accounts will have a username and a password.</span></span> <span data-ttu-id="aeddf-186">Aktualisieren Sie außerdem die Erklärung am unteren Rand der XAML, damit das Standardkennwort enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="aeddf-186">Also update the explanation at the bottom of the XAML to include the default password.</span></span> <span data-ttu-id="aeddf-187">Aktualisieren Sie die folgende XAML in „Login.xaml“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-187">Update the following XAML in Login.xaml</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock Text="Login" FontSize="36" Margin="4" TextAlignment="Center"/>

        <TextBlock x:Name="ErrorMessage" Text="" FontSize="20" Margin="4" Foreground="Red" TextAlignment="Center"/>

        <TextBlock Text="Enter your credentials below" Margin="0,0,0,20"
                   TextWrapping="Wrap" Width="300"
                   TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>

        <StackPanel Orientation="Horizontal" HorizontalAlignment="Center">
          <!-- Username Input -->
          <TextBlock x:Name="UserNameTextBlock" Text="Username: "
                 FontSize="20" Margin="4" Width="100"/>
          <TextBox x:Name="UsernameTextBox" PlaceholderText="sampleUsername" Width="200" Margin="4"/>
        </StackPanel>

        <StackPanel Orientation="Horizontal" HorizontalAlignment="Center">
          <!-- Password Input -->
          <TextBlock x:Name="PasswordTextBlock" Text="Password: "
                 FontSize="20" Margin="4" Width="100"/>
          <PasswordBox x:Name="PasswordBox" PlaceholderText="samplePassword" Width="200" Margin="4"/>
        </StackPanel>

        <Button x:Name="PassportSignInButton" Content="Login" Background="DodgerBlue" Foreground="White"
            Click="PassportSignInButton_Click" Width="80" HorizontalAlignment="Center" Margin="0,20"/>

        <TextBlock Text="Don't have an account?"
                    TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>
        <TextBlock x:Name="RegisterButtonTextBlock" Text="Register now"
                   PointerPressed="RegisterButtonTextBlock_OnPointerPressed"
                   Foreground="DodgerBlue"
                   TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>

        <Border x:Name="PassportStatus" Background="#22B14C"
                   Margin="0,20" Height="100">
          <TextBlock x:Name="PassportStatusText" Text="Windows Hello is ready to use!"
                 Margin="4" TextAlignment="Center" VerticalAlignment="Center" FontSize="20"/>
        </Border>

        <TextBlock x:Name="LoginExplaination" FontSize="24" TextAlignment="Center" TextWrapping="Wrap" 
            Text="Please Note: To demonstrate a login, validation will only occur using the default username 
            'sampleUsername' and default password 'samplePassword'"/>

      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="aeddf-188">Im CodeBehind der Login-Klasse müssen Sie die private Kontovariable oben in der Klasse in eine Benutzerkontovariable ändern.</span><span class="sxs-lookup"><span data-stu-id="aeddf-188">In the Login class code behind you will need to change the Account private variable at the top of the class to be a UserAccount.</span></span> <span data-ttu-id="aeddf-189">Ändern Sie das OnNavigateTo-Ereignis zum Umwandeln des Typs in ein Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="aeddf-189">Change the OnNavigateTo event to cast the type to be a UserAccount.</span></span> <span data-ttu-id="aeddf-190">Sie benötigen den folgenden Verweis.</span><span class="sxs-lookup"><span data-stu-id="aeddf-190">You will need the following reference.</span></span>

    ```cs
    using PassportLogin.AuthService;

    namespace PassportLogin.Views
    {
        public sealed partial class Login : Page
        {
            private UserAccount _account;
            private bool _isExistingAccount;

            public Login()
            {
                this.InitializeComponent();
            }

            protected override async void OnNavigatedTo(NavigationEventArgs e)
            {
                //Check Windows Hello is setup and available on this machine
                if (await MicrosoftPassportHelper.MicrosoftPassportAvailableCheckAsync())
                {
                    if (e.Parameter != null)
                    {
                        _isExistingAccount = true;
                        //Set the account to the existing account being passed in
                        _account = (UserAccount)e.Parameter;
                        UsernameTextBox.Text = _account.Username;
                        SignInPassport();
                    }
                }
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-191">Da die Anmeldeseite ein UserAccount-Objekt statt des vorherigen Account-Objekts verwendet, muss „MicrosoftPassportHelper.cs“ aktualisiert werden, um ein Benutzerkonto als Parameter für bestimmte Methoden zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-191">As the Login page is using a UserAccount object instead of the previous Account object the MicrosoftPassportHelper.cs will need to be updated to use a UserAccount as a parameter for some methods.</span></span> <span data-ttu-id="aeddf-192">Sie müssen die folgenden Parameter für die Methoden CreatePassportKeyAsync, RemovePassportAccountAsync und GetPassportAuthenticationMessageAsync ändern.</span><span class="sxs-lookup"><span data-stu-id="aeddf-192">You will need to change the following parameters for the CreatePassportKeyAsync, RemovePassportAccountAsync and GetPassportAuthenticationMessageAsync methods.</span></span> <span data-ttu-id="aeddf-193">Da die UserAccount-Klasse eine GUID für eine Benutzer-ID enthält, verwenden Sie zu Beginn die ID an mehreren Orten, um spezifischer sein.</span><span class="sxs-lookup"><span data-stu-id="aeddf-193">As the UserAccount class has a Guid for a UserId you will start using the Id in more places to be more specific.</span></span>

    ```cs
    public static async Task<bool> CreatePassportKeyAsync(Guid userId, string username)
    {
        KeyCredentialRetrievalResult keyCreationResult = await KeyCredentialManager.RequestCreateAsync(username, KeyCredentialCreationOption.ReplaceExisting);
    }

    public static async void RemovePassportAccountAsync(UserAccount account)
    {

    }
    public static async Task<bool> GetPassportAuthenticationMessageAsync(UserAccount account)
    {
        KeyCredentialRetrievalResult openKeyResult = await KeyCredentialManager.OpenAsync(account.Username);
        //Calling OpenAsync will allow the user access to what is available in the app and will not require user credentials again.
        //If you wanted to force the user to sign in again you can use the following:
        //var consentResult = await Windows.Security.Credentials.UI.UserConsentVerifier.RequestVerificationAsync(account.Username);
        //This will ask for the either the password of the currently signed in Microsoft Account or the PIN used for Windows Hello.

        if (openKeyResult.Status == KeyCredentialStatus.Success)
        {
            //If OpenAsync has succeeded, the next thing to think about is whether the client application requires access to backend services.
            //If it does here you would Request a challenge from the Server. The client would sign this challenge and the server
            //would check the signed challenge. If it is correct it would allow the user access to the backend.
            //You would likely make a new method called RequestSignAsync to handle all this
            //e.g. RequestSignAsync(openKeyResult);
            //Refer to the second Windows Hello sample for information on how to do this.

            //For this sample there is not concept of a server implemented so just return true.
            return true;
        }
        else if (openKeyResult.Status == KeyCredentialStatus.NotFound)
        {
            //If the _account is not found at this stage. It could be one of two errors. 
            //1. Windows Hello has been disabled
            //2. Windows Hello has been disabled and re-enabled cause the Windows Hello Key to change.
            //Calling CreatePassportKey and passing through the account will attempt to replace the existing Windows Hello Key for that account.
            //If the error really is that Windows Hello is disabled then the CreatePassportKey method will output that error.
            if (await CreatePassportKeyAsync(account.UserId, account.Username))
            {
                //If the Passport Key was again successfully created, Windows Hello has just been reset.
                //Now that the Passport Key has been reset for the _account retry sign in.
                return await GetPassportAuthenticationMessageAsync(account);
            }
        }

        // Can't use Passport right now, try again later
        return false;
    }
    ```

-   <span data-ttu-id="aeddf-194">Die SignInPassport-Methode in der Datei „Login.xaml.cs“ muss aktualisiert werden, um AuthService anstelle von AccountHelper zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-194">The SignInPassport method in Login.xaml.cs file will need to be updated to use the AuthService instead of the AccountHelper.</span></span> <span data-ttu-id="aeddf-195">Die Überprüfung der Anmeldeinformationen erfolgt über AuthService.</span><span class="sxs-lookup"><span data-stu-id="aeddf-195">Validation of credentials will happen through the AuthService.</span></span> <span data-ttu-id="aeddf-196">Für diese praktische Übung ist „sampleUsername“ das einzige konfigurierte Konto.</span><span class="sxs-lookup"><span data-stu-id="aeddf-196">For this hands on lab the only configured account is "sampleUsername".</span></span> <span data-ttu-id="aeddf-197">Dieses Konto wird in der InitializeSampleUserAccounts-Methode in „MockStore.cs“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-197">This account is created in the InitializeSampleUserAccounts method in MockStore.cs.</span></span> <span data-ttu-id="aeddf-198">Aktualisieren Sie jetzt die SignInPassport-Methode in „Login.xaml.cs“ entsprechend dem folgenden Codeausschnitt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-198">Update the SignInPassport method in Login.xaml.cs now to reflect the code snippet below.</span></span>

    ```cs
    private async void SignInPassportAsync()
    {
        if (_isExistingLocalAccount)
        {
            if (await MicrosoftPassportHelper.GetPassportAuthenticationMessageAsync(_account))
            {
                Frame.Navigate(typeof(Welcome), _account);
            }
        }
        else if (AuthService.AuthService.Instance.ValidateCredentials(UsernameTextBox.Text, PasswordBox.Password))
        {
            Guid userId = AuthService.AuthService.Instance.GetUserId(UsernameTextBox.Text);

            if (userId != Guid.Empty)
            {
                //Now that the account exists on server try and create the necessary passport details and add them to the account
                bool isSuccessful = await MicrosoftPassportHelper.CreatePassportKeyAsync(userId, UsernameTextBox.Text);
                if (isSuccessful)
                {
                    Debug.WriteLine("Successfully signed in with Windows Hello!");
                    //Navigate to the Welcome Screen. 
                    _account = AuthService.AuthService.Instance.GetUserAccount(userId);
                    Frame.Navigate(typeof(Welcome), _account);
                }
                else
                {
                    //The passport account creation failed.
                    //Remove the account from the server as passport details were not configured
                    AuthService.AuthService.Instance.PassportRemoveUser(userId);

                    ErrorMessage.Text = "Account Creation Failed";
                }
            }
        }
        else
        {
            ErrorMessage.Text = "Invalid Credentials";
        }
    }
    ```

-   <span data-ttu-id="aeddf-199">Da Windows Hello ein unterschiedliches Paar aus öffentlichem/privatem Schlüssel für jedes Konto auf jedem Gerät erstellt, muss auf der Begrüßungsseite eine Liste der registrierten Geräte für das angemeldete Konto angezeigt werden, und jedes muss vergessen werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-199">As Windows Hello will create a different public and private key pair for each account on each device the Welcome page will need to display a list of registered devices for the logged in account, and allow each one to be forgotten.</span></span> <span data-ttu-id="aeddf-200">Fügen Sie in „Welcome.xaml“ in der folgenden XAML darunter ForgetButton hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-200">In Welcome.xaml add in the following XAML underneath the ForgetButton.</span></span> <span data-ttu-id="aeddf-201">Dadurch wird die Schaltfläche „Gerät vergessen“, ein Fehlertextbereich und eine Liste zum Anzeigen aller Geräte implementiert.</span><span class="sxs-lookup"><span data-stu-id="aeddf-201">This will implement a forget device button, an error text area and a list to display all devices.</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock x:Name="Title" Text="Welcome" FontSize="40" TextAlignment="Center"/>
        <TextBlock x:Name="UserNameText" FontSize="28" TextAlignment="Center" Foreground="Black"/>

        <Button x:Name="BackToUserListButton" Content="Back to User List" Click="Button_Restart_Click"
               HorizontalAlignment="Center" Margin="0,20" Foreground="White" Background="DodgerBlue"/>

        <Button x:Name="ForgetButton" Content="Forget Me" Click="Button_Forget_User_Click"
               Foreground="White"
               Background="Gray"
               HorizontalAlignment="Center"/>

        <Button x:Name="ForgetDeviceButton" Content="Forget Device" Click="Button_Forget_Device_Click"
               Foreground="White"
               Background="Gray"
               Margin="0,40,0,20"
               HorizontalAlignment="Center"/>

        <TextBlock x:Name="ForgetDeviceErrorTextBlock" Text="Select a device first"
                  TextWrapping="Wrap" Width="300" Foreground="Red"
                  TextAlignment="Center" VerticalAlignment="Center" FontSize="16" Visibility="Collapsed"/>

        <ListView x:Name="UserListView" MaxHeight="500" MinWidth="350" Width="350" HorizontalAlignment="Center">
          <ListView.ItemTemplate>
            <DataTemplate>
              <Grid Background="Gray" Height="50" Width="350" HorizontalAlignment="Center" VerticalAlignment="Stretch" >
                <TextBlock Text="{Binding DeviceId}" HorizontalAlignment="Center" TextAlignment="Center" VerticalAlignment="Center"
                          Foreground="White"/>
              </Grid>
            </DataTemplate>
          </ListView.ItemTemplate>
        </ListView>
      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="aeddf-202">In der Datei „Welcome.xaml.cs“ müssen Sie die private Kontovariable oben in der Klasse in eine private Benutzerkontovariable ändern.</span><span class="sxs-lookup"><span data-stu-id="aeddf-202">In the Welcome.xaml.cs file you will need to change the private Account variable at the top of the class to be a private UserAccount variable.</span></span> <span data-ttu-id="aeddf-203">Aktualisieren Sie dann die OnNavigatedTo-Methode, um AuthService zu verwenden und Informationen für das aktuelle Konto abzurufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-203">Then update the OnNavigatedTo method to use the AuthService and retrieve information for the current account.</span></span> <span data-ttu-id="aeddf-204">Wenn Sie die Kontoinformationen haben, können Sie die ItemSource der Liste zum Anzeigen der Geräte konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-204">When you have the account information you can set the itemsource of the list to display the devices.</span></span> <span data-ttu-id="aeddf-205">Sie müssen einen Verweis auf den AuthService-Namespace hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-205">You will need to add a reference to the AuthService namespace.</span></span>

    ```cs
    using PassportLogin.AuthService;

    namespace PassportLogin.Views
    {
        public sealed partial class Welcome : Page
        {
            private UserAccount _activeAccount;

            public Welcome()
            {
                InitializeComponent();
            }

            protected override void OnNavigatedTo(NavigationEventArgs e)
            {
                _activeAccount = (UserAccount)e.Parameter;
                if (_activeAccount != null)
                {
                    UserAccount account = AuthService.AuthService.Instance.GetUserAccount(_activeAccount.UserId);
                    if (account != null)
                    {
                        UserListView.ItemsSource = account.PassportDevices;
                        UserNameText.Text = account.Username;
                    }
                }
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-206">Da Sie AuthService beim Entfernen eines Kontos verwenden, kann der Verweis auf AccountHelper in der Button\_Forget\_User\_Click-Methode entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-206">As you will be using the AuthService when removing an account the reference to the AccountHelper in the Button\_Forget\_User\_Click method can be removed.</span></span> <span data-ttu-id="aeddf-207">Die Methode sollte nun folgendermaßen aussehen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-207">The method should now look as below.</span></span>

    ```cs
    private void Button_Forget_User_Click(object sender, RoutedEventArgs e)
    {
        //Remove it from Windows Hello
        MicrosoftPassportHelper.RemovePassportAccountAsync(_activeAccount);

        Debug.WriteLine("User " + _activeAccount.Username + " deleted.");

        //Navigate back to UserSelection page.
        Frame.Navigate(typeof(UserSelection));
    }
    ```

-   <span data-ttu-id="aeddf-208">Die MicrosoftPassportHelper-Methode verwendet AuthService nicht, um das Konto zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-208">The MicrosoftPassportHelper method is not using the AuthService to remove the account.</span></span> <span data-ttu-id="aeddf-209">Sie müssen einen Aufruf für AuthService durchführen und die Benutzer-ID übergeben.</span><span class="sxs-lookup"><span data-stu-id="aeddf-209">You need to make a call to the AuthService and pass the userId.</span></span>

    ```cs
    public static async void RemovePassportAccountAsync(UserAccount account)
    {
        //Open the account with Windows Hello
        KeyCredentialRetrievalResult keyOpenResult = await KeyCredentialManager.OpenAsync(account.Username);

        if (keyOpenResult.Status == KeyCredentialStatus.Success)
        {
            // In the real world you would send key information to server to unregister
            AuthService.AuthService.Instance.PassportRemoveUser(account.UserId);
        }

        //Then delete the account from the machines list of Passport Accounts
        await KeyCredentialManager.DeleteAsync(account.Username);
    }
    ```

-   <span data-ttu-id="aeddf-210">Bevor Sie die Implementierung der Welcome-Seitenklasse abschließen können, müssen Sie eine Methode in „MicrosoftPassportHelper.cs“ erstellen, mit der ein Gerät entfernt werden kann.</span><span class="sxs-lookup"><span data-stu-id="aeddf-210">Before you can finish implementing the Welcome page class, you need to create a method in MicrosoftPassportHelper.cs that will allow a device to be removed.</span></span> <span data-ttu-id="aeddf-211">Erstellen Sie eine neue Methode, die PassportRemoveDevice in AuthService PassportRemoveDevice aufruft.</span><span class="sxs-lookup"><span data-stu-id="aeddf-211">Create a new method that will call PassportRemoveDevice in AuthService.</span></span>

    ```cs
    public static void RemovePassportDevice(UserAccount account, Guid deviceId)
    {
        AuthService.AuthService.Instance.PassportRemoveDevice(account.UserId, deviceId);
    }
    ```

-   <span data-ttu-id="aeddf-212">Implementieren Sie in „Welcome.xaml.cs“ das Forget Device-Click-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="aeddf-212">In Welcome.xaml.cs implement the Forget Device click event.</span></span> <span data-ttu-id="aeddf-213">Dadurch wird das ausgewählte Gerät aus der Liste mit den Geräten verwendet und „Gerät entfernen“ mit PassportHelper aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-213">This will use the selected device from the list of devices and use the passport helper to call remove device.</span></span>

    ```cs
    private void Button_Forget_Device_Click(object sender, RoutedEventArgs e)
    {
        PassportDevice selectedDevice = UserListView.SelectedItem as PassportDevice;
        if (selectedDevice != null)
        {
            //Remove it from Windows Hello
            MicrosoftPassportHelper.RemovePassportDevice(_activeAccount, selectedDevice.DeviceId);

            Debug.WriteLine("User " + _activeAccount.Username + " deleted.");

            if (!UserListView.Items.Any())
            {
                //Navigate back to UserSelection page.
                Frame.Navigate(typeof(UserSelection));
            }
        }
        else
        {
            ForgetDeviceErrorTextBlock.Visibility = Visibility.Visible;
        }
    }
    ```

-   <span data-ttu-id="aeddf-214">Die nächste Seite, die Sie aktualisieren, ist die UserSelection-Seite.</span><span class="sxs-lookup"><span data-stu-id="aeddf-214">The next page you will update is the UserSelection page.</span></span> <span data-ttu-id="aeddf-215">Die UserSelection-Seite muss AuthService verwenden, um alle Benutzerkonten für das aktuelle Gerät abzurufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-215">The UserSelection page will need to use the AuthService to retrieve all user accounts for the current device.</span></span> <span data-ttu-id="aeddf-216">Zurzeit besteht keine Möglichkeit für Sie, eine Geräte-ID zur Übergabe an AuthService abzurufen, damit Benutzerkonten für dieses Gerät zurückgegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="aeddf-216">Currently there is no way for you get a device id to pass to the AuthService so it can return user accounts for that device.</span></span> <span data-ttu-id="aeddf-217">Erstellen Sie im Ordner „Utils“ die neue Klasse „Helpers.cs“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-217">In the Utils folder create a new class called "Helpers.cs".</span></span> <span data-ttu-id="aeddf-218">Definieren Sie die Klasse als öffentliche, statische Klasse, und fügen Sie dann die folgende Methode hinzu, mit der Sie die aktuelle Geräte-ID abrufen können.</span><span class="sxs-lookup"><span data-stu-id="aeddf-218">Change the class definition to be public static and then add the following method that will allow you to retrieve the current device id.</span></span>

    ```cs
    using Windows.Security.ExchangeActiveSyncProvisioning;

    namespace PassportLogin.Utils
    {
        public static class Helpers
        {
            public static Guid GetDeviceId()
            {
                //Get the Device ID to pass to the server
                EasClientDeviceInformation deviceInformation = new EasClientDeviceInformation();
                return deviceInformation.Id;
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-219">In der UserSelection-Seitenklasse muss nur der CodeBehind geändert werden, nicht die Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="aeddf-219">In the UserSelection page class only the code behind needs to change, not the user interface.</span></span> <span data-ttu-id="aeddf-220">Aktualisieren Sie in „UserSelection.xaml.cs“ die geladene Methode und die Methode zur Benutzerauswahl, damit die UserAccount-Klasse anstelle der Account-Klasse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-220">In UserSelection.xaml.cs update the loaded method and the user selection method to use the UserAccount class instead of the Account class.</span></span> <span data-ttu-id="aeddf-221">Sie müssen außerdem alle Benutzer für dieses Gerät über AuthService abrufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-221">You will also need to get all users for this device through the AuthService.</span></span>

    ```cs
    using System.Linq;
    using PassportLogin.AuthService;

    namespace PassportLogin.Views
    {
        public sealed partial class UserSelection : Page
        {
            public UserSelection()
            {
                InitializeComponent();
                Loaded += UserSelection_Loaded;
            }

            private void UserSelection_Loaded(object sender, RoutedEventArgs e)
            {
                List<UserAccount> accounts = AuthService.AuthService.Instance.GetUserAccountsForDevice(Helpers.GetDeviceId());

                if (accounts.Any())
                {
                    UserListView.ItemsSource = accounts;
                    UserListView.SelectionChanged += UserSelectionChanged;
                }
                else
                {
                    //If there are no accounts navigate to the LoginPage
                    Frame.Navigate(typeof(Login));
                }
            }

            /// <summary>
            /// Function called when an account is selected in the list of accounts
            /// Navigates to the Login page and passes the chosen account
            /// </summary>
            private void UserSelectionChanged(object sender, RoutedEventArgs e)
            {
                if (((ListView)sender).SelectedValue != null)
                {
                    UserAccount account = (UserAccount)((ListView)sender).SelectedValue;
                    if (account != null)
                    {
                        Debug.WriteLine("Account " + account.Username + " selected!");
                    }
                    Frame.Navigate(typeof(Login), account);
                }
            }
        }
    }
    ```

-   <span data-ttu-id="aeddf-222">Die PassportRegister-Seite muss den CodeBehind aktualisieren, die Benutzeroberfläche muss nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-222">The PassportRegister page needs to update the code behind, the user interface does not need changing.</span></span> <span data-ttu-id="aeddf-223">Entfernen Sie in „PassportRegister.xaml.cs“ die private Kontovariable oben in der Klasse, da sie nicht mehr benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-223">In PassportRegister.xaml.cs remove the private Account variable at the top of the class as it is no longer needed.</span></span> <span data-ttu-id="aeddf-224">Aktualisieren Sie das RegisterButton-Click-Ereignis für die Verwendung von AuthService.</span><span class="sxs-lookup"><span data-stu-id="aeddf-224">Update the RegisterButton click event to use the AuthService.</span></span> <span data-ttu-id="aeddf-225">Diese Methode erstellt ein neues Benutzerkonto und versucht dann, dessen Passport-Details zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-225">This method will create a new UserAccount and then try and update its passport details.</span></span> <span data-ttu-id="aeddf-226">Falls Passport keinen Passport-Schlüssel erstellen kann, wird das Konto entfernt, da der Registrierungsprozess fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="aeddf-226">If passport fails to create a passport key the account will be removed as the registration process failed.</span></span>

    ```cs
    private async void RegisterButton_Click_Async(object sender, RoutedEventArgs e)
    {
        ErrorMessage.Text = "";

        //Validate entered credentials are acceptable
        if (!string.IsNullOrEmpty(UsernameTextBox.Text))
        {
            //Register an Account on the AuthService so that we can get back a userId
            AuthService.AuthService.Instance.Register(UsernameTextBox.Text);
            Guid userId = AuthService.AuthService.Instance.GetUserId(UsernameTextBox.Text);

            if (userId != Guid.Empty)
            {
                //Now that the account exists on server try and create the necessary passport details and add them to the account
                bool isSuccessful = await MicrosoftPassportHelper.CreatePassportKeyAsync(userId, UsernameTextBox.Text);
                if (isSuccessful)
                {
                    //Navigate to the Welcome Screen. 
                    Frame.Navigate(typeof(Welcome), AuthService.AuthService.Instance.GetUserAccount(userId));
                }
                else
                {
                    //The passport account creation failed.
                    //Remove the account from the server as passport details were not configured
                    AuthService.AuthService.Instance.PassportRemoveUser(userId);

                    ErrorMessage.Text = "Account Creation Failed";
                }
            }
        }
        else
        {
            ErrorMessage.Text = "Please enter a username";
        }
    }
    ```

-   <span data-ttu-id="aeddf-227">Erstellen Sie die Anwendung, und führen Sie sie aus (F5).</span><span class="sxs-lookup"><span data-stu-id="aeddf-227">Build and run the application (F5).</span></span> <span data-ttu-id="aeddf-228">Melden Sie sich beim Beispielbenutzerkonto mit den Anmeldeinformationen „sampleUsername“ und „samplePassword“ an.</span><span class="sxs-lookup"><span data-stu-id="aeddf-228">Sign into the sample user account, with the credentials "sampleUsername" and "samplePassword".</span></span> <span data-ttu-id="aeddf-229">Auf dem Willkommensbildschirm bemerken Sie vielleicht, dass die Schaltfläche „Gerät vergessen“ angezeigt wird, es aber keine Geräte gibt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-229">On the welcome screen you may notice the Forget devices button is displayed but there are no devices.</span></span> <span data-ttu-id="aeddf-230">Wenn Sie einen Benutzer erstellen oder migrieren, damit dieser mit Windows Hello arbeitet, werden die Passport-Informationen nicht an AuthService übergeben.</span><span class="sxs-lookup"><span data-stu-id="aeddf-230">When you are creating or migrating a user to work with Windows Hello the passport information is not being pushed to the AuthService.</span></span>

    ![Windows Hello-Anmeldebildschirm](images/passport-auth-3.png)

    ![Windows-Hello-Anmeldung erfolgreich](images/passport-auth-4.png)

-   <span data-ttu-id="aeddf-233">Zum Übertragen der Passport-Informationen zu AuthService muss „MicrosoftPassportHelper.cs“ aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-233">To get the passport information to the AuthService the MicrosoftPassportHelper.cs will need to be updated.</span></span> <span data-ttu-id="aeddf-234">In der CreatePassportKeyAsync-Methode müssen Sie, damit im Erfolgsfall nicht nur „true“ zurückgegeben wird, eine neue Methode aufrufen, die versucht, KeyAttestation abzurufen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-234">In the CreatePassportKeyAsync method, instead of only returning true in the case that it is successful, you will need to call a new method which will try to get the KeyAttestation.</span></span> <span data-ttu-id="aeddf-235">In dieser praktischen Übung werden diese Informationen nicht in AuthService aufgezeichnet. Sie erfahren jedoch, wie diese Informationen clientseitig abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-235">While this hands on lab is not recording this information in the AuthService you will learn how you would get it this information on the client side.</span></span> <span data-ttu-id="aeddf-236">Aktualisieren Sie die CreatePassportKeyAsync-Methode.</span><span class="sxs-lookup"><span data-stu-id="aeddf-236">Update the CreatePassportKeyAsync method.</span></span>

    ```cs
    public static async Task<bool> CreatePassportKeyAsync(Guid userId, string username)
    {
        KeyCredentialRetrievalResult keyCreationResult = await KeyCredentialManager.RequestCreateAsync(username, KeyCredentialCreationOption.ReplaceExisting);

        switch (keyCreationResult.Status)
        {
            case KeyCredentialStatus.Success:
                Debug.WriteLine("Successfully made key");
                await GetKeyAttestationAsync(userId, keyCreationResult);
                return true;
            case KeyCredentialStatus.UserCanceled:
                Debug.WriteLine("User cancelled sign-in process.");
                break;
            case KeyCredentialStatus.NotFound:
                // User needs to setup Windows Hello
                Debug.WriteLine("Windows Hello is not setup!\nPlease go to Windows Settings and set up a PIN to use it.");
                break;
            default:
                break;
        }

        return false;
    }
    ```

-   <span data-ttu-id="aeddf-237">Erstellen Sie diese GetKeyAttestationAsync-Methode in „MicrosoftPassportHelper.cs“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-237">Create this GetKeyAttestationAsync method in MicrosoftPassportHelper.cs.</span></span> <span data-ttu-id="aeddf-238">Diese Methode veranschaulicht, wie Sie alle erforderlichen Informationen abrufen, die von Windows Hello für jedes Konto für ein bestimmtes Gerät bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="aeddf-238">This method will demonstrate how to obtain all the necessary information that can be provided by Windows Hello for each account on a specific device.</span></span>

    ```cs
    using Windows.Storage.Streams;

    private static async Task GetKeyAttestationAsync(Guid userId, KeyCredentialRetrievalResult keyCreationResult)
    {
        KeyCredential userKey = keyCreationResult.Credential;
        IBuffer publicKey = userKey.RetrievePublicKey();
        KeyCredentialAttestationResult keyAttestationResult = await userKey.GetAttestationAsync();
        IBuffer keyAttestation = null;
        IBuffer certificateChain = null;
        bool keyAttestationIncluded = false;
        bool keyAttestationCanBeRetrievedLater = false;
        KeyCredentialAttestationStatus keyAttestationRetryType = 0;

        if (keyAttestationResult.Status == KeyCredentialAttestationStatus.Success)
        {
            keyAttestationIncluded = true;
            keyAttestation = keyAttestationResult.AttestationBuffer;
            certificateChain = keyAttestationResult.CertificateChainBuffer;
            Debug.WriteLine("Successfully made key and attestation");
        }
        else if (keyAttestationResult.Status == KeyCredentialAttestationStatus.TemporaryFailure)
        {
            keyAttestationRetryType = KeyCredentialAttestationStatus.TemporaryFailure;
            keyAttestationCanBeRetrievedLater = true;
            Debug.WriteLine("Successfully made key but not attestation");
        }
        else if (keyAttestationResult.Status == KeyCredentialAttestationStatus.NotSupported)
        {
            keyAttestationRetryType = KeyCredentialAttestationStatus.NotSupported;
            keyAttestationCanBeRetrievedLater = false;
            Debug.WriteLine("Key created, but key attestation not supported");
        }

        Guid deviceId = Helpers.GetDeviceId();
        //Update the Pasport details with the information we have just gotten above.
        //UpdatePassportDetails(userId, deviceId, publicKey.ToArray(), keyAttestationResult);
    }
    ```

-   <span data-ttu-id="aeddf-239">Möglicherweise haben Sie in der soeben hinzugefügten GetKeyAttestationAsync-Methode bemerkt, dass die letzte Zeile auskommentiert wurde. Diese letzte Zeile ist eine neue Methode, die Sie erstellen, mit der alle Windows Hello-Informationen an AuthService gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-239">You may have noticed in the GetKeyAttestationAsync method that you just added the last line was commented out. This last line will be a new method you create that will send all the Windows Hello information to the AuthService.</span></span> <span data-ttu-id="aeddf-240">In der realen Welt müssten Sie diese an einen echten Server mit einer Web-API senden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-240">In the real world you would need to send this to an actual server with a Web API.</span></span>

    ```cs
    using System.Runtime.InteropServices.WindowsRuntime;

    public static bool UpdatePassportDetails(Guid userId, Guid deviceId, byte[] publicKey, KeyCredentialAttestationResult keyAttestationResult)
    {
        //In the real world you would use an API to add Passport signing info to server for the signed in _account.
        //For this tutorial we do not implement a WebAPI for our server and simply mock the server locally 
        //The CreatePassportKey method handles adding the Windows Hello account locally to the device using the KeyCredential Manager

        //Using the userId the existing account should be found and updated.
        AuthService.AuthService.Instance.PassportUpdateDetails(userId, deviceId, publicKey, keyAttestationResult);
        return true;
    }
    ```

-   <span data-ttu-id="aeddf-241">Entfernen Sie Kommentare aus der letzten Zeile in der GetKeyAttestationAsync-Methode, damit die Windows-Hello-Informationen an AuthService gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-241">Uncomment the last line in the GetKeyAttestationAsync method so that the Windows Hello information is being sent to the AuthService.</span></span>
-   <span data-ttu-id="aeddf-242">Erstellen Sie die Anwendung, führen Sie sie aus und melden Sie sich mit den Standardanmeldeinformationen wie zuvor an.</span><span class="sxs-lookup"><span data-stu-id="aeddf-242">Build and run the application and sign in with the default credentials as before.</span></span> <span data-ttu-id="aeddf-243">Auf dem Willkommensbildschirm sehen Sie jetzt, dass das Geräte-ID angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-243">On the welcome screen you will now see that the device Id is displayed.</span></span> <span data-ttu-id="aeddf-244">Wenn Sie sich auf einem anderen Gerät angemeldet haben, wird dieses hier ebenfalls angezeigt (bei einem in der Cloud gehosteten Authentifizierungsdienst).</span><span class="sxs-lookup"><span data-stu-id="aeddf-244">If you signed in on another device that would also be displayed here (if you had a cloud hosted auth service).</span></span> <span data-ttu-id="aeddf-245">Für diese praktische Übung wird die tatsächliche Geräte-ID angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aeddf-245">For this hands on lab the actual device Id is being displayed.</span></span> <span data-ttu-id="aeddf-246">Bei einer echten Implementierung sollten Sie einen Anzeigenamen anzeigen, den eine Person verstehen und verwenden kann, um die einzelnen Geräte zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="aeddf-246">In a real implementation you would want to display a friendly name that a person could understand and use to determine each device.</span></span>

    ![Windows-Hello-Anmeldung erfolgreich Geräte-ID](images/passport-auth-5.png)

-   21. <span data-ttu-id="aeddf-248">Zum Abschluss dieser praktischen Übung benötigen Sie eine Anforderung und Abfrage für Benutzer, wenn sie auf der Benutzerauswahlseite eine Auswahl treffen und sich erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="aeddf-248">To complete this hands on lab you need a request and challenge for the user when they select from the user selection page and sign back in.</span></span> <span data-ttu-id="aeddf-249">AuthService besitzt zwei Methoden, die Sie erstellt haben, um eine Abfrage anzufordern. Eine davon verwendet eine signierte Abfrage.</span><span class="sxs-lookup"><span data-stu-id="aeddf-249">The AuthService has two methods that you created to request a challenge, one that uses a signed challenge.</span></span> <span data-ttu-id="aeddf-250">Erstellen Sie in „MicrosoftPassportHelper.cs“ die neue Methode „RequestSignAsync“. Dies fordert eine Abfrage von AuthService an, signiert diese Abfrage lokal mithilfe einer Passport-API und sendet die signierte Abfrage an AuthService.</span><span class="sxs-lookup"><span data-stu-id="aeddf-250">In MicrosoftPassportHelper.cs create a new method called "RequestSignAsync" This will request a challenge from the AuthService, locally sign that challenge using a Passport API and send the signed challenge to the AuthService.</span></span> <span data-ttu-id="aeddf-251">In dieser praktischen Übung empfängt AuthService die signierte Abfrage und gibt „true“ zurück.</span><span class="sxs-lookup"><span data-stu-id="aeddf-251">In this hands on lab the AuthService will receive the signed challenge and return true.</span></span> <span data-ttu-id="aeddf-252">In einer tatsächlichen Implementierung müssten Sie einen Überprüfungsmechanismus implementieren, um festzustellen, ob die Abfrage vom richtigen Benutzer auf dem richtigen Gerät signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="aeddf-252">In an actual implementation you would need to implement a verification mechanism to determine is the challenge was signed by the correct user on the correct device.</span></span> <span data-ttu-id="aeddf-253">Fügen Sie die unten angegebene Methode zu „MicrosoftPassportHelper.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="aeddf-253">Add the method below to the MicrosoftPassportHelper.cs</span></span>

    ```cs
    private static async Task<bool> RequestSignAsync(Guid userId, KeyCredentialRetrievalResult openKeyResult)
    {
        // Calling userKey.RequestSignAsync() prompts the uses to enter the PIN or use Biometrics (Windows Hello).
        // The app would use the private key from the user account to sign the sign-in request (challenge)
        // The client would then send it back to the server and await the servers response.
        IBuffer challengeMessage = AuthService.AuthService.Instance.PassportRequestChallenge();
        KeyCredential userKey = openKeyResult.Credential;
        KeyCredentialOperationResult signResult = await userKey.RequestSignAsync(challengeMessage);

        if (signResult.Status == KeyCredentialStatus.Success)
        {
            // If the challenge from the server is signed successfully
            // send the signed challenge back to the server and await the servers response
            return AuthService.AuthService.Instance.SendServerSignedChallenge(
                userId, Helpers.GetDeviceId(), signResult.Result.ToArray());
        }
        else if (signResult.Status == KeyCredentialStatus.UserCanceled)
        {
            // User cancelled the Windows Hello PIN entry.
        }
        else if (signResult.Status == KeyCredentialStatus.NotFound)
        {
            // Must recreate Windows Hello key
        }
        else if (signResult.Status == KeyCredentialStatus.SecurityDeviceLocked)
        {
            // Can't use Windows Hello right now, remember that hardware failed and suggest restart
        }
        else if (signResult.Status == KeyCredentialStatus.UnknownError)
        {
            // Can't use Windows Hello right now, try again later
        }

        return false;
    }
    ```

-   22. <span data-ttu-id="aeddf-254">Rufen Sie in der MicrosoftPassportHelper-Klasse die RequestSignAsync-Methode aus der GetPassportAuthenticationMessageAsync-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="aeddf-254">In the MicrosoftPassportHelper class call the RequestSignAsync method from the GetPassportAuthenticationMessageAsync method.</span></span>

    ```cs
    public static async Task<bool> GetPassportAuthenticationMessageAsync(UserAccount account)
    {
        KeyCredentialRetrievalResult openKeyResult = await KeyCredentialManager.OpenAsync(account.Username);
        // Calling OpenAsync will allow the user access to what is available in the app and will not require user credentials again.
        // If you wanted to force the user to sign in again you can use the following:
        // var consentResult = await Windows.Security.Credentials.UI.UserConsentVerifier.RequestVerificationAsync(account.Username);
        // This will ask for the either the password of the currently signed in Microsoft Account or the PIN used for Windows Hello.

        if (openKeyResult.Status == KeyCredentialStatus.Success)
        {
            //If OpenAsync has succeeded, the next thing to think about is whether the client application requires access to backend services.
            //If it does here you would Request a challenge from the Server. The client would sign this challenge and the server
            //would check the signed challenge. If it is correct it would allow the user access to the backend.
            //You would likely make a new method called RequestSignAsync to handle all this
            //e.g. RequestSignAsync(openKeyResult);
            //Refer to the second Windows Hello sample for information on how to do this.

            return await RequestSignAsync(account.UserId, openKeyResult);
        }
        else if (openKeyResult.Status == KeyCredentialStatus.NotFound)
        {
            //If the _account is not found at this stage. It could be one of two errors. 
            //1. Windows Hello has been disabled
            //2. Windows Hello has been disabled and re-enabled cause the Windows Hello Key to change.
            //Calling CreatePassportKey and passing through the account will attempt to replace the existing Windows Hello Key for that account.
            //If the error really is that Windows Hello is disabled then the CreatePassportKey method will output that error.
            if (await CreatePassportKeyAsync(account.UserId, account.Username))
            {
                //If the Passport Key was again successfully created, Windows Hello has just been reset.
                //Now that the Passport Key has been reset for the _account retry sign in.
                return await GetPassportAuthenticationMessageAsync(account);
            }
        }

        // Can't use Windows Hello right now, try again later
        return false;
    }
    ```

-   <span data-ttu-id="aeddf-255">In dieser Übung haben Sie die clientseitige Anwendung für die Verwendung von AuthService aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="aeddf-255">Throughout this exercise, you have updated the client side application to use the AuthService.</span></span> <span data-ttu-id="aeddf-256">Dadurch können Sie auf die Account-Klasse und die AccountHelper-Klasse verzichten.</span><span class="sxs-lookup"><span data-stu-id="aeddf-256">By doing this you have been able to eliminate the need for the Account class and the AccountHelper class.</span></span> <span data-ttu-id="aeddf-257">Löschen Sie die Account-Klasse, den Ordner „Models“ und die AccountHelper-Klasse im Ordner „Utils“.</span><span class="sxs-lookup"><span data-stu-id="aeddf-257">Delete the Account class, the Models folder, and the AccountHelper class in the Utils folder.</span></span> <span data-ttu-id="aeddf-258">Sie müssen alle Verweise auf den Models-Namensraum in der gesamten Anwendung entfernen, bevor die Projektmappe erfolgreich erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="aeddf-258">You will need to remove all reference to the Models namespace throughout the application before the solution will successfully build.</span></span>
-   <span data-ttu-id="aeddf-259">Erstellen Sie die Anwendung, führen Sie sie aus und nutzen Sie Windows Hello mit dem Pseudoserver und der Pseudodatenbank.</span><span class="sxs-lookup"><span data-stu-id="aeddf-259">Build and run the application and enjoy using Windows Hello with the mock service and database.</span></span>

<span data-ttu-id="aeddf-260">In dieser praktischen Übung wurde Ihnen vermittelt, wie Sie bei der Authentifizierung von einem Windows 10-Computer mithilfe der Windows-Hello-API die Notwendigkeit von Kennwörtern ersetzen.</span><span class="sxs-lookup"><span data-stu-id="aeddf-260">In this hands on lab you have learned how to use the Windows Hello APIs to replace the need for passwords when using authenticate from a Windows 10 machine.</span></span> <span data-ttu-id="aeddf-261">Wenn Sie bedenken, wie viel Energie von Benutzern zum Verwalten von Kennwörtern und zur Unterstützung verlorener Kennwörter in vorhandenen Systemen aufgewendet wird, sollte der Vorteil des Wechsels zu diesem neuen Windows-Hello-Authentifizierungssystem offensichtlich sein.</span><span class="sxs-lookup"><span data-stu-id="aeddf-261">When you consider how much energy is expended by people maintaining passwords and supporting lost passwords in existing systems, you should see the benefit of moving to this new Windows Hello system of authentication.</span></span>

<span data-ttu-id="aeddf-262">Wir haben Ihnen in Form einer Übung die Details bereitgestellt, wie Sie die Authentifizierung dienst- und serverseitig implementieren.</span><span class="sxs-lookup"><span data-stu-id="aeddf-262">We have left as an exercise for you the details of how you will implement the authentication on the service and server side.</span></span> <span data-ttu-id="aeddf-263">Es wird erwartet, dass die meisten von Ihnen über Systeme verfügen, die migriert werden müssen, um mit der Arbeit mit Windows Hello zu beginnen. Die Details der einzelnen Systeme unterscheiden sich.</span><span class="sxs-lookup"><span data-stu-id="aeddf-263">It is expected that most of you will have existing systems that will need to be migrated to start working with Windows Hello and the details of each system will differ.</span></span>

## <a name="related-topics"></a><span data-ttu-id="aeddf-264">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="aeddf-264">Related topics</span></span>

* [<span data-ttu-id="aeddf-265">Windows Hello</span><span class="sxs-lookup"><span data-stu-id="aeddf-265">Windows Hello</span></span>](microsoft-passport.md)
* [<span data-ttu-id="aeddf-266">Windows Hello-Anmelde-App</span><span class="sxs-lookup"><span data-stu-id="aeddf-266">Windows Hello login app</span></span>](microsoft-passport-login.md)